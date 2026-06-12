---
title: "ironpython: compile .py file?"
date: 2011-06-25
forum: General Help
---

### Post by d3v1150m471c on 2011-06-25
I've searched google and had no luck with this. Say i have a file called test.py with the contents:
```

#!/usr/bin/python

print "This is a test..."

```

How can I compile this using IronPython?

---

### Post by d3v1150m471c on 2011-06-25
so anywho... the problem i was having is ipy <ironpython> didn't ship with pyc.py so I found this:
```

#####################################################################################
#
#  Copyright (c) Microsoft Corporation. All rights reserved.
#
# This source code is subject to terms and conditions of the Microsoft Public License. A 
# copy of the license can be found in the License.html file at the root of this distribution. If 
# you cannot locate the  Microsoft Public License, please send an email to 
# ironpy@microsoft.com. By using this source code in any fashion, you are agreeing to be bound 
# by the terms of the Microsoft Public License.
#
# You must not remove this notice, or any other, from this software.
#
#
#####################################################################################

"""
pyc: The Command-Line Python Compiler

Usage: ipy.exe pyc.py [options] file [file ...]

Options:
    /out:output_file                          Output file name (default is main_file.<extenstion>)
    /target:dll                               Compile only into dll.  Default
    /target:exe                               Generate console executable stub for startup in addition to dll.
    /target:winexe                            Generate windows executable stub for startup in addition to dll.
    /? /h                                     This message
    
EXE/WinEXE specific options:
    /main:main_file.py                        Main file of the project (module to be executed first)
    /platform:x86                             Compile for x86 only
    /platform:x64                             Compile for x64 only


Example:
    ipy.exe pyc.py /main:Program.py Form.py /target:winexe
"""

import sys
import clr
clr.AddReferenceByPartialName("IronPython")

from System.Collections.Generic import List
import IronPython.Hosting as Hosting
from IronPython.Runtime.Operations import PythonOps
import System
from System.Reflection import Emit
from System.Reflection.Emit import OpCodes, AssemblyBuilderAccess
from System.Reflection import AssemblyName, TypeAttributes, MethodAttributes

def GenerateExe(name, targetKind, platform, machine, main_module):
    """generates the stub .EXE file for starting the app"""    
    aName = AssemblyName(System.IO.FileInfo(name).Name)
    ab = PythonOps.DefineDynamicAssembly(aName, AssemblyBuilderAccess.RunAndSave)
    mb = ab.DefineDynamicModule(name,  aName.Name + '.exe')
    tb = mb.DefineType('PythonMain', TypeAttributes.Public)
    mainMethod = tb.DefineMethod('Main', MethodAttributes.Public | MethodAttributes.Static, int, ())
    gen = mainMethod.GetILGenerator()
    
    # get the ScriptCode assembly...    
    gen.Emit(OpCodes.Ldstr, name + ".dll")
    gen.EmitCall(OpCodes.Call, clr.GetClrType(System.IO.Path).GetMethod("GetFullPath", (clr.GetClrType(str), )), ())
    gen.EmitCall(OpCodes.Call, clr.GetClrType(System.Reflection.Assembly).GetMethod("LoadFile", (clr.GetClrType(str), )), ())
    
    # emit module name
    gen.Emit(OpCodes.Ldstr, System.IO.Path.GetFileNameWithoutExtension(main_module))
    
    gen.Emit(OpCodes.Ldnull)
    
    # call InitializeModule
    gen.EmitCall(OpCodes.Call, clr.GetClrType(PythonOps).GetMethod("InitializeModule"), ())    
    gen.Emit(OpCodes.Ret)
    
    tb.CreateType()
    ab.SetEntryPoint(mainMethod, targetKind)
    ab.Save(aName.Name + '.exe', platform, machine)
    
def Main(args):
    files = []
    main = None          # The main file to start the execution (passed to the PythonCompiler)
    main_name = None     # File which will drive the name of the assembly if "output" not provided
    output = None        # Output assembly name
    target = System.Reflection.Emit.PEFileKinds.Dll
    platform = System.Reflection.PortableExecutableKinds.ILOnly
    machine  = System.Reflection.ImageFileMachine.I386

    for arg in args:
        if arg.startswith("/main:"):
            main_name = main = arg[6:]
            target = System.Reflection.Emit.PEFileKinds.ConsoleApplication
        
        elif arg.startswith("/out:"):
            output = arg[5:]
            
        elif arg.startswith("/target:"):
            tgt = arg[8:]
            if tgt == "exe": target = System.Reflection.Emit.PEFileKinds.ConsoleApplication
            elif tgt == "winexe": target = System.Reflection.Emit.PEFileKinds.WindowApplication
            else: target = System.Reflection.Emit.PEFileKinds.Dll

        elif arg.startswith("/platform:"):
            pform = arg[10:]
            if pform == "x86":
                platform = System.Reflection.PortableExecutableKinds.ILOnly | System.Reflection.PortableExecutableKinds.Required32Bit
                machine  = System.Reflection.ImageFileMachine.I386
            elif pform == "x64":
                platform = System.Reflection.PortableExecutableKinds.ILOnly | System.Reflection.PortableExecutableKinds.PE32Plus
                machine  = System.Reflection.ImageFileMachine.AMD64
            else:
                platform = System.Reflection.PortableExecutableKinds.ILOnly
                machine  = System.Reflection.ImageFileMachine.I386

        elif arg in ["/?", "-?", "/h", "-h"]:
            print __doc__
            sys.exit(0)

        else:
            files.append(arg)

    if not files and not main_name:
        print __doc__
        sys.exit(0)

    if not output and main_name:
        output = System.IO.Path.GetFileNameWithoutExtension(main_name)
    elif not output and files:
        output = System.IO.Path.GetFileNameWithoutExtension(files[0])
        
    print "Input Files:"
    for file in files:
        print "\t%s" % file

    print "Output:\n\t%s" % output
    print "Target:\n\t%s" % target
    print 'Platform:\n\t%s' % platform
    print 'Machine:\n\t%s' % machine

    print 'Compiling...'    
    clr.CompileModules(output + '.dll', mainModule = main_name, *files)
    
    if target != System.Reflection.Emit.PEFileKinds.Dll:
        GenerateExe(output, target, platform, machine, main_name)
    
    print 'Saved to %s' % (output, )

if __name__ == "__main__":
    Main(sys.argv[1:])

```You can chmod it and then run:
```

ipy pyc.py input.py /target:exe

```

---

### Post by tgm4883 on 2011-06-25
Err, you don't compile Python. It's an interpreted language that doesn't get compiled.

---

### Post by Spiritof76 on 2011-06-25
> **tgm4883 said:**
> Err, you don't compile Python. It's an interpreted language that doesn't get compiled.

Iropython is a compiler, that is capable of making .exe files. I think it mostly is for windows though, and I don't undertand the impications for Ubuntu or linux

---

### Post by tgm4883 on 2011-06-25
> **Spiritof76 said:**
> Iropython is a compiler, that is capable of making .exe files. I think it mostly is for windows though, and I don't undertand the impications for Ubuntu or linux

I stand corrected then. Thanks for the info.

---

### Post by d3v1150m471c on 2011-06-25
> **tgm4883 said:**
> Err, you don't compile Python. It's an interpreted language that doesn't get compiled.

Yes and no, it compiles to byte code which still requires the interpreter. I'd use py_compile but that does me no good when my goal here is to play around with the ironpython functionality.

ie:
```

#!/usr/bin/python
from py_compile import compile

compile('hello.py', 'hello.pyc')

```Python creates byte code for python programs @ runtime, so if you have a large program it's a nicety you can use to skip the process.


You should check out shedskin sometime, btw. It will convert .py files to c++ , granted it's a bit picky about modules and syntax it's still a very cool program :)

---

