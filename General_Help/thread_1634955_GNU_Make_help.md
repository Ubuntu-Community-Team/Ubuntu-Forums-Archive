---
title: "GNU Make help"
date: 2010-12-01
forum: General Help
---

### Post by diego_pmc on 2010-12-01
I'm having some issues with my makefiles: I get a lot of syntax errors when trying to run them on Ubuntu, but they work perfectly fine on Windows. I have make version 3.81 on both OSs.

I get all sorts of errors, and some don't even come from my scripts but from those of the compiler (dekitPPC):
> /opt/devkitpro/devkitPPC/bin/bin2s: 1: Syntax error: ")" unexpected
/opt/devkitpro/devkitPPC/bin/powerpc-eabi-as: 1: Syntax error: word unexpected (expecting ")")
sound.d: 1: *** target pattern contains no `%'.  Stop

```
#------------------------------------------------------------------------------- 
# Check if the path to the compiler is known. 
#------------------------------------------------------------------------------- 
ERRMSG := Cannot detect path to devkitPPC. Make sure its path is set in your\ 
             environment. See the INSTALL document for help 
 
ifeq ($(strip $(DEVKITPPC)),) 
$(error $(ERRMSG)) 
endif 
include $(DEVKITPPC)/wii_rules 
 
#------------------------------------------------------------------------------- 
# SRCDIR   - Source code directory name  
# PROJROOT - The root directory of the project tree 
#------------------------------------------------------------------------------- 
SRCDIR    :=  src 
PROJROOT  :=  $(subst :marker:,,$(subst /$(SRCDIR):marker:,,$(CURDIR):marker:)) 
 
#------------------------------------------------------------------------------- 
# SOURCES   - List of directories containing source code files 
# INCLUDES  - List of directories containing header files 
# RESOURCES - List of directories containing resource file 
#------------------------------------------------------------------------------- 
SOURCES    :=  audio file gamestates graphics logger main managers settings \ 
               time userinput 
INCLUDES   :=  audio file gamestates graphics logger main managers settings \ 
               time userinput 
RESOURCES  :=  resources 
 
#------------------------------------------------------------------------------- 
# TARGET     - Name of the output files 
# TARGETDIR  - Directory where target files will be placed 
# BUILDDIR   - Directory where object and intermediate files will be placed 
#------------------------------------------------------------------------------- 
TARGET     :=  boot 
TARGETDIR  :=  bin 
BUILDDIR   :=  build 
 
#------------------------------------------------------------------------------- 
# Extra libraries that need to be linked with the project 
#------------------------------------------------------------------------------- 
LIBS  :=  -lasnd -lmad -lgrrlib -lfreetype -lpngu -lpng -ljpeg -lz -lfat \ 
          -lwiiuse -lbte -logc -lm 
 
#------------------------------------------------------------------------------- 
# Options for generating code 
#------------------------------------------------------------------------------- 
CFLAGS    =  -g -O2 -Wall $(MACHDEP) $(INCLUDE) 
CXXFLAGS  =  $(CFLAGS) 
LDFLAGS   =  -g $(MACHDEP) -Wl,-Map,$(notdir $@).map 
 
#------------------------------------------------------------------------------- 
# List of directories containing libraries, this must be the top level 
# containing include and lib. 
#------------------------------------------------------------------------------- 
LIBDIRS  := 
 
#------------------------------------------------------------------------------- 
ifneq ($(notdir $(CURDIR)),$(BUILDDIR)) 
#------------------------------------------------------------------------------- 
export OUTPUT   :=  $(PROJROOT)/$(TARGETDIR)/$(TARGET) 
export DEPSDIR  :=  $(PROJROOT)/$(BUILDDIR) 
export VPATH    :=  $(foreach dir,$(SOURCES),$(PROJROOT)/$(SRCDIR)/$(dir)) \ 
                       $(foreach dir,$(RESOURCES),$(PROJROOT)/$(SRCDIR)/$(dir)) 
 
#------------------------------------------------------------------------------- 
# Build a list of object files for the project 
#------------------------------------------------------------------------------- 
CFILES    :=  $(foreach dir,$(SOURCES),\ 
                 $(notdir $(wildcard $(PROJROOT)/$(SRCDIR)/$(dir)/*.c))) 
CPPFILES  :=  $(foreach dir,$(SOURCES),\ 
                 $(notdir $(wildcard $(PROJROOT)/$(SRCDIR)/$(dir)/*.cpp))) 
sFILES    :=  $(foreach dir,$(SOURCES),\ 
                 $(notdir $(wildcard $(PROJROOT)/$(SRCDIR)/$(dir)/*.s))) 
SFILES    :=  $(foreach dir,$(SOURCES),\ 
                 $(notdir $(wildcard $(PROJROOT)/$(SRCDIR)/$(dir)/*.S))) 
BINFILES  :=  $(foreach dir,$(RESOURCES),\ 
                 $(notdir $(wildcard $(PROJROOT)/$(SRCDIR)/$(dir)/*.*))) 
 
#------------------------------------------------------------------------------- 
# Use CXX for linking C++ projects, CC for standard C. 
#------------------------------------------------------------------------------- 
ifeq ($(strip $(CPPFILES)),) 
    export LD  :=  $(CC) 
else 
    export LD  :=  $(CXX) 
endif 
 
export OFILES  :=  $(addsuffix .o,$(BINFILES)) \ 
                      $(CPPFILES:.cpp=.o) $(CFILES:.c=.o) \ 
                      $(sFILES:.s=.o) $(SFILES:.S=.o) 
 
#------------------------------------------------------------------------------- 
# Build a list of include paths 
#------------------------------------------------------------------------------- 
export INCLUDE  :=  $(foreach dir,$(INCLUDES), \ 
                       -iquote $(PROJROOT)/$(SRCDIR)/$(dir)) \ 
                       $(foreach dir,$(LIBDIRS),-I$(dir)/include) \ 
                       -I$(PROJROOT)/$(BUILDDIR) \ 
                       -I$(LIBOGC_INC) 
 
#------------------------------------------------------------------------------- 
# Build a list of library paths 
#------------------------------------------------------------------------------- 
export LIBPATHS  :=  $(foreach dir,$(LIBDIRS),-L$(dir)/lib) \ 
                        -L$(LIBOGC_LIB) 
 
#------------------------------------------------------------------------------- 
# Build rules 
#------------------------------------------------------------------------------- 
.PHONY: help build clean rebuild 
 
help: 
    @echo "Check the INSTALL document for make intructions." 
 
build: 
    @cd $(PROJROOT) ; \ 
       [ -d $(BUILDDIR)  ] || mkdir -p $(BUILDDIR) ; \ 
       [ -d $(TARGETDIR) ] || mkdir -p $(TARGETDIR) 
    @$(MAKE) --no-print-directory -C $(PROJROOT)/$(BUILDDIR) -f \ 
       $(PROJROOT)/$(SRCDIR)/Makefile 
 
clean: 
    @echo Cleaning... 
    @cd $(PROJROOT) ; \ 
       rm -fr $(BUILDDIR) $(TARGETDIR)  
 
rebuild: 
    @$(MAKE) --no-print-directory clean 
    @$(MAKE) --no-print-directory build 
 
 
#------------------------------------------------------------------------------- 
else                                    #ifneq ($(notdir $(CURDIR)),$(BUILDDIR)) 
#------------------------------------------------------------------------------- 
DEPENDS  :=  $(OFILES:.o=.d) 
 
#------------------------------------------------------------------------------- 
# Main targets 
#------------------------------------------------------------------------------- 
$(OUTPUT).dol:    $(OUTPUT).elf 
$(OUTPUT).elf:    $(OFILES) 
 
#------------------------------------------------------------------------------- 
# Rules that link in binary data with various extensions. 
#------------------------------------------------------------------------------- 
.SUFFIXES: 
 
%.jpg.o:    %.jpg     
    @echo $(notdir $<) 
    $(bin2o) 
 
%.png.o:    %.png  
    @echo $(notdir $<) 
    $(bin2o)        
  
%.ttf.o:    %.ttf 
    @echo $(notdir $<) 
    $(bin2o) 
 
 
-include $(DEPENDS) 
 
#------------------------------------------------------------------------------- 
endif                                   #ifneq ($(notdir $(CURDIR)),$(BUILDDIR)) 
#-------------------------------------------------------------------------------
```

---

### Post by dino99 on 2010-12-01
this may help, but you can use other debugger found into synaptic

[http://manpages.ubuntu.com/manpages/maverick/man1/gdb.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/gdb.1.html)

---

### Post by cannywizard on 2010-12-01
This looks more like a problem with the code that you're compiling rather than the makefile per se.
Perhaps you can post all of the output.

---

