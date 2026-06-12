---
title: "Trouble with chmod"
date: 2011-05-25
forum: General Help
---

### Post by tonezone on 2011-05-25
I am having a lot of trouble with chmod in ubuntu 11.04 natty narwhale x64. When I try running shell scripts the same way that other people have online I get much different results: usually the scripts will not run. For instance I often see chmod +x <script>.sh then sudo sh ./<script>.sh and when I read threads on how to use a program everyone else seems to say that the command worked fine. However, every time I run sudo sh ./<script>.sh I get the error: command not found. I can get some scripts to work by doing chmod 777 <script>.sh and then sh ./<script.sh>. but sometimes it will say permission denied and give no further output. Other times it will give an error that points to a different file or files and say that those files returned a permission denied command. So then I go chmod 777 those files and sometimes it works and sometimes it doesn't. Right now I am trying to run a program called vlinac. This is some output from the command line of trying to install it:

tony@Tiamat:/media/DataStorage/downloads/vlinac$ sh ./startIoc.sh
exec: 48: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/vlinac: Permission denied
./startIoc.sh: 45: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/caRepeater: Permission denied
tony@Tiamat:/media/DataStorage/downloads/vlinac$ chmod -c 777 ./bin/linux-x86_64/vlinac
mode of `./bin/linux-x86_64/vlinac' changed to 0777 (rwxrwxrwx)
tony@Tiamat:/media/DataStorage/downloads/vlinac$ chmod -c 777 ./bin/linux-x86_64/caRepeater
mode of `./bin/linux-x86_64/caRepeater' changed to 0777 (rwxrwxrwx)
tony@Tiamat:/media/DataStorage/downloads/vlinac$ sh ./startIoc.shexec: 48: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/vlinac: Permission denied
./startIoc.sh: 45: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/caRepeater: Permission denied
tony@Tiamat:/media/DataStorage/downloads/vlinac$ sudo sh ./startIoc.sh
[sudo] password for tony: 
exec: 48: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/vlinac: Permission denied
./startIoc.sh: 45: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/caRepeater: Permission denied
tony@Tiamat:/media/DataStorage/downloads/vlinac$ chmod 777 startIoc.sh
tony@Tiamat:/media/DataStorage/downloads/vlinac$ sh ./startIoc.sh
exec: 48: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/vlinac: Permission denied
./startIoc.sh: 45: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/caRepeater: Permission denied

---

### Post by webofunni on 2011-05-25
try 

```

chmod -vR 755 /media/DataStorage/downloads/vlinac/bin/*

```

---

### Post by tonezone on 2011-05-26
Still didn't work. here's what I got:

tony@Tiamat:/media/DataStorage/downloads/vlinac$ chmod -vR 755 /media/DataStorage/downloads/vlinac/bin/*
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/alh' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/alh_printer' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/caRepeater' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/medm' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/msi' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/probe' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/StripTool' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-ppc/vlinac' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/alh' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/alh_printer' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/caRepeater' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/medm' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/msi' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/probe' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/StripTool' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/darwin-x86/vlinac' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/alh' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/alh_printer' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/caRepeater' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/medm' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/msi' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/probe' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/StripTool' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86/vlinac' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/alh' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/alh_printer' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/caRepeater' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/medm' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/msi' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/probe' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/StripTool' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/linux-x86_64/vlinac' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/alh' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/alh_printer' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/caRepeater' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/medm' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/msi' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/probe' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/StripTool' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-sparc/vlinac' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/alh' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/alh_printer' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/caRepeater' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/medm' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/msi' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/probe' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/StripTool' changed to 0755 (rwxr-xr-x)
mode of `/media/DataStorage/downloads/vlinac/bin/solaris-x86/vlinac' changed to 0755 (rwxr-xr-x)
tony@Tiamat:/media/DataStorage/downloads/vlinac$ ls
alh            lib               startIoc.bat        startStripTool.bat
bin            Makefile          startIoc.command    startStripTool.command
configure      medm              startIoc.sh         startStripTool.sh
CVS            README            startMedm.bat       st.cmd
db             README.txt        startMedm.command   StripTool
dbd            README.Win32.txt  startMedm.sh        vlinacApp
documentation  startAlh.bat      startProbe.bat
graphics       startAlh.command  startProbe.command
installApp     startAlh.sh       startProbe.sh
tony@Tiamat:/media/DataStorage/downloads/vlinac$ sudo sh startIoc.sh
[sudo] password for tony: 
exec: 48: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/vlinac: Permission denied
startIoc.sh: 45: /media/DataStorage/downloads/vlinac/bin/linux-x86_64/caRepeater: Permission denied


In the block where permissions are being changed it shows these two, but when I call them I still get permission denied. Also the readme specifically says to run the startIoc.sh file. It mentions line 45 for vlinac and line 48 for carepeater. It may be that these lines point to other files that are giving the permission denied errors. However I cannot open the files to see where they point.

---

### Post by webofunni on 2011-05-26
Can you move that directory to your home folder and try ? Hope there is enough space.

```

cp -vrf /media/DataStorage/downloads/vlinac ~/
cd ~/vlinac
chmod 755 startIoc.sh
sudo ./startIoc.sh

```

---

### Post by gzarkadas on 2011-05-26
Either your media is mounted with noexec option or simply the files that vlinac calls are not executable. If it is the first case, moving the files to your home folder will work (unless of course your system mounts /home as a separate partition with noexec option). If it is the second, moving the files to your home folder will *not* work.

Please post the output of the `mount' command (open a terminal window and type it). Only the line that references /media/DataStorage is needed here, you can omit the others.

---

### Post by webofunni on 2011-05-26
Yes,

```

cat /etc/fstab
sudo blkid

```

---

### Post by Morbius1 on 2011-05-26
There is another possible explantion for this phenomenon. /media/DataStorage is an NTFS or Fat32 partition.

Doing a chmod -vR will happily tell you that it's changing permissions but of course it's not because it can't.

---

### Post by tonezone on 2011-05-26
> **Morbius1 said:**
> There is another possible explantion for this phenomenon. /media/DataStorage is an NTFS or Fat32 partition.

Doing a chmod -vR will happily tell you that it's changing permissions but of course it's not because it can't.

Well that explains it. I had formatted DataStorage as NTFS. My root directory is a 120GB solid state drive, and Data storage is a 2 TB normal hard drive. That's why I was storing everything on DataStorage. Anyway I backed up all the files on DataStorage and converted it into ext4. I ran the script again, but was stopped because it was missing a dependency which I was also unable to install before. Anyway I have to wait until the problems installing the dependancy are fixed before this program will work, but it looks like chmod is working fine now. Thanks for all the help.

---

