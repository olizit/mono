thisdir = class/System.Web.Services
SUBDIRS = 
include ../../build/rules.make

LIBRARY = System.Web.Services.dll

MONOTOUCH_BASED_PROFILE := $(filter monotouch unity, $(PROFILE))
ifdef MONOTOUCH_BASED_PROFILE
LIB_MCS_FLAGS = \
	-nowarn:649 -nowarn:169			\
	-r:$(corlib)				\
	-r:System.dll				\
	-r:System.Xml.dll			\
	-resource:System.Web.Services.Description/wsdl-1.1.xsd,wsdl-1.1.xsd \
	-resource:System.Web.Services.Description/wsdl-1.1-soap.xsd,wsdl-1.1-soap.xsd \
	-resource:System.Web.Services.Description/web-reference.xsd,web-reference.xsd
else
LIB_MCS_FLAGS = \
	-nowarn:649 -nowarn:169			\
	-r:$(corlib)				\
	-r:System.dll				\
	-r:System.EnterpriseServices.dll	\
	-r:System.Xml.dll			\
	-r:System.Web.dll

ifneq (1, $(FRAMEWORK_VERSION_MAJOR))
LIB_MCS_FLAGS += \
	-r:System.Configuration.dll \
	-resource:System.Web.Services.Description/wsdl-1.1.xsd,wsdl-1.1.xsd \
	-resource:System.Web.Services.Description/wsdl-1.1-soap.xsd,wsdl-1.1-soap.xsd \
	-resource:System.Web.Services.Description/web-reference.xsd,web-reference.xsd
endif
endif

TEST_MCS_FLAGS = $(LIB_MCS_FLAGS) -nowarn:618

EXTRA_DISTFILES = \
	System.Web.Services.Description/web-reference.xsd	\
	System.Web.Services.Description/wsdl-1.1.xsd		\
	System.Web.Services.Description/wsdl-1.1-soap.xsd	\
	System.Web.Services.Description/wsdl.genxs		\
	Test/System.Web.Services.Description/*.wsdl

include ../../build/library.make
