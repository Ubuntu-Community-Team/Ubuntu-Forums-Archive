---
title: "install ns-allinone-2.28 in ubuntu 10.04"
date: 2010-09-04
forum: General Help
---

### Post by tkhan on 2010-09-04
hello, i want to install ns-2.28 in ubuntu 10.04 by using ns-allinone-2.28. But after giving the command on terminal ./install it shows a error like the following:

Tcl.cc: In member function ‘void Tcl::eval(char*)’:
Tcl.cc:180: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In member function ‘int TclObject::traceVar(const char*, TclObject*)’:
Tcl.cc:419: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In static member function ‘static int TclClass::create_shadow(void*, Tcl_Interp*, int, const char**)’:
Tcl.cc:507: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc:509: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In static member function ‘static int TclClass::dispatch_instvar(void*, Tcl_Interp*, int, const char**)’:
Tcl.cc:564: error: invalid conversion from ‘const char*’ to ‘char*’
Tcl.cc:569: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc: In member function ‘virtual void TclClass::bind()’:
Tcl.cc:601: warning: deprecated conversion from string constant to ‘char*’
Tcl.cc:603: warning: deprecated conversion from string constant to ‘char*’
make: *** [Tcl.o] Error 1
tclcl-1.16 make failed! Exiting ...

How can i fix the problem, anyone have any idea?..please help.

---

