---
title: "Cmake newbie help."
date: 2009-09-18
forum: General Help
---

### Post by casbahdk on 2009-09-18
I would like to install the [GTK-Qt Theme Engine]("http://code.google.com/p/gtk-qt-engine/"). When I tried to do a normal

./configure
make
sudo make install

I got prompted to install cmake as the GTK-Qt Theme Engine uses that. Unfortunately, I have looked at a number of man pages, as well as HowTos, but I am getting waay to much info. All I need to do is how to compile the GTK-Qt Theme Engine. What do I do?

Cheers

---

### Post by bruno9779 on 2009-09-18
just type in a terminal

```
sudo apt-get install cmake
```

and try to compile again

---

### Post by casbahdk on 2009-09-18
Thanks for the quick reply. I have installed cmake as you described. This is what I get:

> /gtk-qt-engine$ ./configure
Warning: The GTK-Qt Theme Engine now uses cmake instead of ./configure.

Found cmake in /usr/bin/cmake, executing it for you...
CMake Error at /usr/share/cmake-2.6/Modules/FindX11.cmake:362 (MESSAGE):
  Could not find X11
Call Stack (most recent call first):
  CMakeLists.txt:4 (FIND_PACKAGE)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

I am not really sure if I used the wrong command or if this is an error generated because something else has gone haywire. I didn't really find any answers to the problem in the man pages.

---

### Post by bruno9779 on 2009-09-18
don't you have a README or INSTALL file between the files on the program you are trying to install?

with cmake the commands for compiling are different

```
cmake
make
make install

```

Sorry for not saying before, I have used cmake only a couple of times and couldn't remember

---

### Post by casbahdk on 2009-09-18
> **bruno9779 said:**
> don't you have a README or INSTALL file between the files on the program you are trying to install?

with cmake the commands for compiling are different

```
cmake
make
make install

```

Sorry for not saying before, I have used cmake only a couple of times and couldn't remember

No worries. I still have problems:
```
gtk-qt-engine$ cmake
cmake version 2.6-patch 2                        
Usage                                            

  cmake [options] <path-to-source>
  cmake [options] <path-to-existing-build>

Options
  -C <initial-cache>          = Pre-load a script to populate the cache.
  -D <var>:<type>=<value>     = Create a cmake cache entry.             
  -U <globbing_expr>          = Remove matching entries from CMake cache.
  -G <generator-name>         = Specify a makefile generator.            
  -Wno-dev                    = Suppress developer warnings.             
  -Wdev                       = Enable developer warnings.               
  -E                          = CMake command mode.                      
  -i                          = Run in wizard mode.                      
  -L[A][H]                    = List non-advanced cached variables.      
  -N                          = View mode only.                          
  -P <file>                   = Process script mode.                     
  --graphviz=[file]           = Generate graphviz of dependencies.       
  --system-information [file] = Dump information about this system.      
  --debug-trycompile          = Do not delete the try compile directories..
  --debug-output              = Put cmake in a debug mode.                 
  --trace                     = Put cmake in trace mode.                   
  --help-command cmd [file]   = Print help for a single command and exit.  
  --help-command-list [file]  = List available listfile commands and exit. 
  --help-commands [file]      = Print help for all commands and exit.      
  --help-compatcommands [file]= Print help for compatibility commands.     
  --help-module module [file] = Print help for a single module and exit.   
  --help-module-list [file]   = List available modules and exit.           
  --help-modules [file]       = Print help for all modules and exit.       
  --help-custom-modules [file]= Print help for all custom modules and exit.
  --help-policy cmp [file]    = Print help for a single policy and exit.   
  --help-policies [file]      = Print help for all policies and exit.      
  --help-property prop [file] = Print help for a single property and exit. 
  --help-property-list [file] = List available properties and exit.        
  --help-properties [file]    = Print help for all properties and exit.    
  --help-variable var [file]  = Print help for a single variable and exit. 
  --help-variable-list [file] = List documented variables and exit.        
  --help-variables [file]     = Print help for all variables and exit.     
  --copyright [file]          = Print the CMake copyright and exit.        
  --help                      = Print usage information and exit.          
  --help-full [file]          = Print full help and exit.                  
  --help-html [file]          = Print full help in HTML format.            
  --help-man [file]           = Print full help as a UNIX man page and exit.
  --version [file]            = Show program name/version banner and exit.  

Generators

The following generators are available on this platform:
  Unix Makefiles              = Generates standard UNIX makefiles.
  CodeBlocks - Unix Makefiles = Generates CodeBlocks project files.
  Eclipse CDT4 - Unix Makefiles
                              = Generates Eclipse CDT 4.0 project files.
  KDevelop3                   = Generates KDevelop 3 project files.
  KDevelop3 - Unix Makefiles  = Generates KDevelop 3 project files.

```

I also tried ```
/gtk-qt-engine$ cmake -i
```

That just gives me a bunch of prompts for variables I have no clue what are.

---

