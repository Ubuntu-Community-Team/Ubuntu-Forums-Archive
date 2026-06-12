---
title: "building, installing, please explain"
date: 2009-11-10
forum: General Help
---

### Post by jesuisbenjamin on 2009-11-10
Hello there,

I have just installed a python library from [this page]("http://pybrary.net/pyPdf/") for which i needed to "build and install packages".
So OK, i did it, but _what_ did i do actually? I am not familiar with this (especially since synaptic does everything for me) and it may be a good opportunity to learn about building and installing packages.
Below is what i ran in Terminal, if there is anyone who could explain what just happened, it would be nice.

Thanks!

```
benjamin@buddhi:~/Desktop/pyPdf-1.12$ ./setup.py --help-commands
Standard commands:
  build            build everything needed to install
  build_py         "build" pure Python modules (copy to build directory)
  build_ext        build C/C++ extensions (compile/link to build directory)
  build_clib       build C/C++ libraries used by Python extensions
  build_scripts    "build" scripts (copy and fixup #! line)
  clean            clean up temporary files from 'build' command
  install          install everything from build directory
  install_lib      install all Python modules (extensions and pure Python)
  install_headers  install C/C++ header files
  install_scripts  install scripts (Python or otherwise)
  install_data     install data files
  sdist            create a source distribution (tarball, zip file, etc.)
  register         register the distribution with the Python package index
  bdist            create a built (binary) distribution
  bdist_dumb       create a "dumb" built distribution
  bdist_rpm        create an RPM distribution
  bdist_wininst    create an executable installer for MS Windows
  upload           upload binary package to PyPI

usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
   or: setup.py --help [cmd1 cmd2 ...]
   or: setup.py --help-commands
   or: setup.py cmd --help

benjamin@buddhi:~/Desktop/pyPdf-1.12$ ./setup.py build
running build
running build_py
creating build
creating build/lib.linux-i686-2.6
creating build/lib.linux-i686-2.6/pyPdf
copying pyPdf/pdf.py -> build/lib.linux-i686-2.6/pyPdf
copying pyPdf/xmp.py -> build/lib.linux-i686-2.6/pyPdf
copying pyPdf/__init__.py -> build/lib.linux-i686-2.6/pyPdf
copying pyPdf/filters.py -> build/lib.linux-i686-2.6/pyPdf
copying pyPdf/utils.py -> build/lib.linux-i686-2.6/pyPdf
copying pyPdf/generic.py -> build/lib.linux-i686-2.6/pyPdf

benjamin@buddhi:~/Desktop/pyPdf-1.12$ sudo ./setup.py install
[sudo] password for benjamin: 
running install
running build
running build_py
running install_lib
creating /usr/local/lib/python2.6/dist-packages/pyPdf
copying build/lib.linux-i686-2.6/pyPdf/pdf.py -> /usr/local/lib/python2.6/dist-packages/pyPdf
copying build/lib.linux-i686-2.6/pyPdf/xmp.py -> /usr/local/lib/python2.6/dist-packages/pyPdf
copying build/lib.linux-i686-2.6/pyPdf/__init__.py -> /usr/local/lib/python2.6/dist-packages/pyPdf
copying build/lib.linux-i686-2.6/pyPdf/filters.py -> /usr/local/lib/python2.6/dist-packages/pyPdf
copying build/lib.linux-i686-2.6/pyPdf/utils.py -> /usr/local/lib/python2.6/dist-packages/pyPdf
copying build/lib.linux-i686-2.6/pyPdf/generic.py -> /usr/local/lib/python2.6/dist-packages/pyPdf
byte-compiling /usr/local/lib/python2.6/dist-packages/pyPdf/pdf.py to pdf.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/pyPdf/xmp.py to xmp.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/pyPdf/__init__.py to __init__.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/pyPdf/filters.py to filters.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/pyPdf/utils.py to utils.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/pyPdf/generic.py to generic.pyc
running install_egg_info
Writing /usr/local/lib/python2.6/dist-packages/pyPdf-1.12.egg-info

```

---

