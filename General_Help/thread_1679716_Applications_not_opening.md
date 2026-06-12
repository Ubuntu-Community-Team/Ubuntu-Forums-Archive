---
title: "Applications not opening"
date: 2011-02-01
forum: General Help
---

### Post by PsyForce on 2011-02-01
Ok, so I'm new to Ubuntu (a few months) and re-new to Linux. Overall I'm really liking Ubuntu (10.10) in many ways, though I've encountered a few problems. The first one I'd like to solve is that some programs are failing to run. Many of them even before I have ever run them at all. Typically I click the icon in the menu and nothing happens. There is one program (that came bundled with Ubuntu) that used to work, but now doesn't. 

I played Quadrapassel (Tetris-like game) for weeks without any problems, then one day it stopped opening. This is the odd one out in that it is the only one that opened previously and now doesn't and also when I open it from the menu, it shows up in the panel and then closes without anything (visible) happening. I read in an older thread that programs should be opened in the terminal to get output...

**Quadrapassel**'s output:

> /usr/games/quadrapassel

The program 'quadrapassel' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 27 error_code 1 request_code 158 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Here are the other programs not working and the terminal output (note that these have never opened, I don't know if that's relevant):

**Battletanks** - The command in the properties has no path, I'm not sure if it's needed or not. Here's what I tried and what happened:

> btanks
[23:45:09.573][engine/src/config.cpp:48]     [error] load: [mrt/file.cpp:36]: fopen("/home/joey/.btanks/bt.xml", "rt"): No such file or directory
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
[23:45:09.643][engine/src/config.cpp:296]     [debug] cleaning up config...

[B]
Bouncy the hungry rabbit[/B] - I'm starting to think I need a path?

> bouncy
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


or not?

> /usr/games/bouncy
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


**Funguloids** - Perhaps there are several problems going on here. I'm not really totally sure what I'm doing so I'm open to pointers :)

> /usr/games/funguloids >dev/null2>&1
bash: dev/null2: No such file or directory


**Bauble**

> /usr/bin/bauble
Traceback (most recent call last):
  File "/usr/bin/bauble", line 28, in <module>
    bauble.main()
  File "/usr/share/bauble/__init__.py", line 175, in main
    import bauble.pluginmgr as pluginmgr
  File "/usr/share/bauble/pluginmgr.py", line 315, in <module>
    class PluginRegistry(db.Base):
  File "/usr/share/bauble/db.py", line 58, in __init__
    super(MapperBase, cls).__init__(classname, bases, dict_)
  File "/usr/lib/python2.6/dist-packages/sqlalchemy/ext/declarative.py", line 1017, in __init__
    _as_declarative(cls, classname, cls.__dict__)
  File "/usr/lib/python2.6/dist-packages/sqlalchemy/ext/declarative.py", line 1010, in _as_declarative
    **mapper_args)
  File "/usr/lib/python2.6/dist-packages/sqlalchemy/orm/__init__.py", line 818, in mapper
    return Mapper(class_, local_table, *args, **params)
  File "/usr/lib/python2.6/dist-packages/sqlalchemy/orm/mapper.py", line 211, in __init__
    self._configure_pks()
  File "/usr/lib/python2.6/dist-packages/sqlalchemy/orm/mapper.py", line 490, in _configure_pks
    (self, self.mapped_table.description))
sqlalchemy.exc.ArgumentError: Mapper Mapper|PluginRegistry|plugin could not assemble any primary key columns for mapped table 'plugin'


So, I'd really appreciate any help. I don't know if these problems are related or not, but they appear to be similar to me :confused:.  If I need to improve my troubleshooting skills, I'd appreciate that advice as well. ;)

---

### Post by LostInBrittany on 2011-02-03
I have just got the same problem, with blender :

> horacio@horacio-desktop:~$ blender
Compiled with Python version 2.6.6.
Checking for installed Python... got it!
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  28
  Current serial number in output stream:  28


Any idea of why or how to solve it ? 

Thanks in advance !

---

### Post by LostInBrittany on 2011-02-03
> **LostInBrittany said:**
> I have just got the same problem, with blender :



Any idea of why or how to solve it ? 

Thanks in advance !

I answer myself ;)

The problem was a corrupt fglrx driver. I had to purge and reinstall it :

```
sudo aptitude purge fglrx
sudo aptitude install fglrx
```

Then a reboot, and problem was solved :)

---

### Post by PsyForce on 2011-02-05
Hmm, great! So how did you figure that out? Also, I tried this and I get:

> sudo: aptitude: command not found

I tried locate and got this:

> locate aptitude
/etc/bash_completion.d/aptitude
/usr/share/app-install/desktop/aptitude-gtk.desktop
/usr/share/locale-langpack/en_AU/LC_MESSAGES/aptitude.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/aptitude.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/aptitude.mo

I tried running it typing the full path and still got command not found. Any ideas?

---

### Post by dino99 on 2011-02-05
well aptitude can be easily replaced by apt-get for a better result

---

### Post by PsyForce on 2011-02-06
Ok, I've tried purging and reinstalling fglrx and have discovered new issues and run into new problems. It seems that ATI drivers are possibly interfering with fglrx...details:

> sudo aptitude purge fglrx
The following packages will be REMOVED:  
  fglrx{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 65.6MB will be freed.
The following packages have unmet dependencies:
  fglrx-amdcccle: Depends: fglrx but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     fglrx-amdcccle              



Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  fglrx{p} fglrx-amdcccle{a} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 75.1MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 207436 files and directories currently installed.)
Removing fglrx-amdcccle ...
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/share/ati' not empty so not removed.
(Reading database ... 207403 files and directories currently installed.)
Removing fglrx ...
Removing all DKMS Modules

Error! There are no instances of module: fglrx
8.780 located in the DKMS tree.
Done.
update-alternatives: removing manually selected alternative - switching gl_conf to auto mode
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc/ati' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx' not empty so not removed.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Processing triggers for python-support ...


then

> sudo aptitude install fglrx
The following NEW packages will be installed:
  fglrx fglrx-amdcccle{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.1MB of archives. After unpacking 75.1MB will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) maverick/restricted fglrx i386 2:8.780-0ubuntu2 [19.9MB]
Get:2 [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) maverick/restricted fglrx-amdcccle i386 2:8.780-0ubuntu2 [5,177kB]                                                           
Fetched 25.1MB in 58s (429kB/s)                                                                                                                                         
Selecting previously deselected package fglrx.
(Reading database ... 207244 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.780-0ubuntu2_i386.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.780-0ubuntu2_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-amdcccle
                                         
Current status: 1 broken [+1].


Then I noticed this:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

and realized that I have an ATI card ( ATI Mobility Radeon HD 5650 ) and am (if not before) having fglrx related problems. 

Then it gets more complicated, the Ubuntu Update Manager asked if I want to install 'Video driver for the ATI graphics accelerators [ subtext: fglrx (New Install) ]'

I thought that sounded like a good idea so I accept and then I get:

> The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:
fglrx-amdcccle

Soo, I go back to the terminal and do this

> sudo apt-get install -f fglrx-amdcccle
[sudo] password for joey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx-amdcccle is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 fglrx-amdcccle : Depends: fglrx but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

...:confused:...any more ideas?

---

### Post by PsyForce on 2011-02-10
Ooooook, so big update!

I tried to purge my drivers and reload the ATI drivers as shown in the link I posted previously:

> **Problem:  Need to fully remove -fglrx and reinstall -ati from scratch**

 Here is a more aggressive recipe which removes both -fglrx and -ati, and reinstalls the latter: 

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorgOoops, that didn't work somehow and afterward my machine only booted to a blank screen (after the splash screen) with no drumroll. 

But I've just fixed it by:

1st - using the livecd to research my problem and find out that I can...

2nd - hold shift when the text GRUB shows at the top of the screen, which allowed me to 'drop into root terminal'

3rd - Eventually, I figured out that I had indeed removed fglrx and that there were no drivers installed and/or configured.

4th - From the terminal I was able to install the ATI proprietary driver I had installed before (by chmod +x ing it first) and then I ran aticonfig and rebooted.

5th - Now everything works MUUCH better!! 

After 3 or 4 days of trying to find my way around the black/blank screen at bootup, I was able to successfully boot into the GUI and log in normally. I've tested all of the applications that were previously not running and only two are still not running. Bauble and ProjectM (which I didn't mention previously). Even though these two are not running, I'm considering this solved. I also checked Quadrapassel and it is indeed working again. 

It appears that my problem was indeed some kind of conflict between the ATI driver and fglrx, as I have now completely removed fglrx and installed the ATI drivers 'cleanly'. 

All in all I'm glad for having learned a lot and I'm even more glad I have my computer back! :lolflag:

---

