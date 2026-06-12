---
title: "can not boot my vbox(noob)"
date: 2011-07-09
forum: General Help
---

### Post by garypat on 2011-07-09
when i try to open windows in v box


Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.get


when i try reinstall kernel

gary@gary-Dell-DXG051:~$ sudo apt get '/etc/init.d/vboxdrv setup'
[sudo] password for gary: 
apt: invalid flag: get
Usage: apt <apt and javac options> <source files>
where apt options include:
  -classpath <path>          Specify where to find user class files and annotation processor factories
  -cp <path>                 Specify where to find user class files and annotation processor factories
  -d <path>                  Specify where to place processor and javac generated class files
  -s <path>                  Specify where to place processor generated source files
  -source <release>          Provide source compatibility with specified release
  -version                   Version information
  -help                      Print a synopsis of standard options; use javac -help for more options
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system
  -A[key[=value]]            Options to pass to annotation processors
  -nocompile                 Do not compile source files to class files
  -print                     Print out textual representation of specified types
  -factorypath <path>        Specify where to find annotation processor factories
  -factory <class>           Name of AnnotationProcessorFactory to use; bypasses default discovery process
See javac -help for information on javac options.

gary@gary-Dell-DXG051:~$ sudo apt get install '/etc/init.d/vboxdrv setup'
apt: invalid flag: get
Usage: apt <apt and javac options> <source files>
where apt options include:
  -classpath <path>          Specify where to find user class files and annotation processor factories
  -cp <path>                 Specify where to find user class files and annotation processor factories
  -d <path>                  Specify where to place processor and javac generated class files
  -s <path>                  Specify where to place processor generated source files
  -source <release>          Provide source compatibility with specified release
  -version                   Version information
  -help                      Print a synopsis of standard options; use javac -help for more options
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system
  -A[key[=value]]            Options to pass to annotation processors
  -nocompile                 Do not compile source files to class files
  -print                     Print out textual representation of specified types
  -factorypath <path>        Specify where to find annotation processor factories
  -factory <class>           Name of AnnotationProcessorFactory to use; bypasses default discovery process
See javac -help for information on javac options.

---

