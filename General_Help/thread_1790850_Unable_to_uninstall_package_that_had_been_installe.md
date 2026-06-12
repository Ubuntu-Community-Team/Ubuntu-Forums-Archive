---
title: "Unable to uninstall package that had been installed with --force-architecture"
date: 2011-06-25
forum: General Help
---

### Post by jorok_tupur on 2011-06-25
I was trying to install Oracle XE (packaged for i386 architecture) to my x86-64 computer by following instruction in [Little Brain]("http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/"). For convenience, here is how I installed them:
```
dpkg -i --force-architecture libaio_0.3.104-1_i386.deb
dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.1_i386.deb
```Now I want to uninstall them. But they are not listed in Synaptic, so I tried dpkg.
```
sudo dpkg -r libaio oracle-xe-universal
```Here is the output:
```
dpkg: warning: there's no installed package matching libaio
dpkg: warning: there's no installed package matching oracle-xe-universal
```Help! How am I supposed to uninstall them?

---

### Post by jorok_tupur on 2011-06-26
To prove that the packages are installed into my system, I attached the screenshots of /var/lib/dpkg/status that shows the packages with installed status.

---

### Post by Bachstelze on 2011-06-26
Try apt-get remove instead of dpkg -r.

---

### Post by jorok_tupur on 2011-06-26
> **Bachstelze said:**
> Try apt-get remove instead of dpkg -r.

This is what I tried:
```
sudo apt-get remove libaio oracle-xe-universal
```
This is the output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libaio
E: Unable to locate package oracle-xe-universal
```

---

### Post by jorok_tupur on 2011-06-27
Some more information:
```
sudo dpkg -l libaio oracle-xe-universal
```
This is the output:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  libaio         <none>         (no description available)
un  oracle-xe-univ <none>         (no description available)

```

---

### Post by jorok_tupur on 2011-07-05
Solved. I just deleted them manually.

Here's what I do.

For libaio:

[LIST=1]
[*]Delete the files listed in /var/lib/dpkg/info/libaio.list
[*]Then delete these files: ```
/var/lib/dpkg/info/libaio.list
/var/lib/dpkg/info/libaio.md5sums
/var/lib/dpkg/info/libaio.postinst
/var/lib/dpkg/info/libaio.postrm
/var/lib/dpkg/info/libaio.shlibs
```
[/LIST]
For oracle-xe-universal:

[LIST=1]
[*]Stop the Oracle XE service (how? described in /var/lib/dpkg/info/oracle-xe-universal.prerm)
[*]Delete the files listed in /var/lib/dpkg/info/oracle-xe-universal.list (there's a lot of them, so use a script or something)
[*]Do the cleanup described in /var/lib/dpkg/info/oracle-xe-universal.postrm (basically these are to remove/delete the Oracle XE service and delete various other files, including menu entries)
[*]Delete the files listed in /var/lib/dpkg/info/oracle-xe-universal.conffiles
[*]Delete the following files: ```
/var/lib/dpkg/info/oracle-xe-universal.conffiles
/var/lib/dpkg/info/oracle-xe-universal.list
/var/lib/dpkg/info/oracle-xe-universal.md5sums
/var/lib/dpkg/info/oracle-xe-universal.postinst
/var/lib/dpkg/info/oracle-xe-universal.postrm
/var/lib/dpkg/info/oracle-xe-universal.preinst
/var/lib/dpkg/info/oracle-xe-universal.prerm
```
[*]Delete the oracle user and dba group.
[/LIST]
The weird thing is that libaio and oracle-xe-universal entries still exists in /var/lib/dpkg/status and /var/lib/dpkg/available. So what I just did is most definitely not a clean uninstall. Meh, whatever.

And if someone do read this stuff while seeking a way to uninstall i386 Oracle XE from their x86-64 computer, please use common sense, don't just blindly delete the files I pointed.

---

### Post by westdart on 2012-02-08
I had major problems when I followed these instruction when it came to re-installing. 

found out later that the package is installed under a different name due to --force-architecture.

To remove try:
sudo dpkg -r oracle-xe:i386

it may work.

---

