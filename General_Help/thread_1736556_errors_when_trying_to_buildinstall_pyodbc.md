---
title: "errors when trying to build/install pyodbc"
date: 2011-04-22
forum: General Help
---

### Post by woodsonoversoul on 2011-04-22
Hello all,
   I just downloaded and extracted the latest version of pyodbc from it's github repo, and when I try to install it using:
```
python setup.py build install
```

I get the following output:
```
dan@dan-netbook:/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4$ python setup.py build install
fatal: No names found, cannot describe anything.
WARNING: git describe failed with: 32768 
WARNING: Unable to determine version.  Using 3.1.0.0
running build
running build_ext
building 'pyodbc' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DPYODBC_VERSION=3.1.0-unsupported -I/usr/include/python2.6 -c /opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/pyodbcdbg.cpp -o build/temp.linux-i686-2.6/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/pyodbcdbg.o -Wno-write-strings
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
/usr/include/python2.6/datetime.h:186: warning: ‘PyDateTimeAPI’ defined but not used
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DPYODBC_VERSION=3.1.0-unsupported -I/usr/include/python2.6 -c /opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp -o build/temp.linux-i686-2.6/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.o -Wno-write-strings
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: invalid conversion from ‘const char*’ to ‘Py_ssize_t’
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: invalid conversion from ‘unsigned int’ to ‘const char*’
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: invalid conversion from ‘void (*)(PyObject*)’ to ‘Py_ssize_t’
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: invalid conversion from ‘long int’ to ‘PyBufferProcs*’
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: invalid conversion from ‘char*’ to ‘long int’
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: invalid conversion from ‘PyObject* (*)(PyObject*)’ to ‘Py_ssize_t’
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: cannot convert ‘PyMethodDef*’ to ‘PyObject* (*)(PyObject*)’ in initialization
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: cannot convert ‘PyMemberDef*’ to ‘PyMethodDef*’ in initialization
/opt/lampp/htdocs/ap.py/tempdel/mkleehammer-pyodbc-3d7ddc4/src/cursor.cpp:2038: error: cannot convert ‘PyGetSetDef*’ to ‘PyMemberDef*’ in initialization
error: command 'gcc' failed with exit status 1

```

Any idea what could be causing these errors?
Thanks in advance...

---

### Post by oldfred on 2011-04-22
What python are you using?

pyodbc says this.
A Python 3.x port has been [checked in]("http://github.com/mkleehammer/pyodbc/tree/v3") and will be released soon! 


Your error says this:
Unable to determine version.  Using 3.1.0.0

---

### Post by woodsonoversoul on 2011-04-22
2.6.5 hmmm...

I assumed that was referring to the version of the module. I'll see if I can find how to specify my version of python...

Thanks.

---

### Post by oldfred on 2011-04-22
It should default to 2.6 then unless you specify otherwise. Is the 3.1.0.0 then the module?

Or did they just check in the new version for python 3 and you happend to get it?

---

