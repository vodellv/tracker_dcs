TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================
# Build an IOC support library

LIBRARY_IOC += biTracker

DBD += biTracker.dbd
#biTracker_SRCS += devBiTracker.c devBoTracker.c devaiTracker.c
biTracker_SRCS += devBiTracker.c devBoTracker.c
biTracker_LIBS += $(EPICS_BASE_IOC_LIBS)

#=============================
# build an ioc application

PROD_IOC = trackerlv

DBD += trackerlv.dbd
# Clock1.dbd will be made up from these files:
trackerlv_DBD += base.dbd
#include definitions for any other support applications needed
trackerlv_DBD += biTracker.dbd

# <name>_registerRecordDeviceDriver.cpp will be created from <name>.dbd
trackerlv_SRCS += trackerlv_registerRecordDeviceDriver.cpp
trackerlv_SRCS_DEFAULT += trklvMain.cpp
trackerlv_SRCS_vxWorks += -nil-

#The following adds support from base/src/vxWorks
trackerlv_OBJS_vxWorks += $(EPICS_BASE_BIN)/vxComLibrary

#add a definition for each support application used by this application
trackerlv_LIBS += biTracker

#NOTES:
#      1)It is not possible to build sncExample both as a component of Clock1
#        and standalone. You must choose only one.
#      2)To build sncExample SNCSEQ must be defined in <top>/configure/RELEASE

#The following builds sncExample as a component of Clock1
#Clock1_SRCS += sncExample.stt
#Clock1_LIBS += seq pv

trackerlv_LIBS += $(EPICS_BASE_IOC_LIBS)

#The following builds sncExample as a standalone application
#PROD_HOST += sncExample
#sncExample_SNCFLAGS += +m
#sncExample_SRCS += sncExample.stt
#sncExample_LIBS += seq pv
#sncExample_LIBS += $(EPICS_BASE_HOST_LIBS)

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

