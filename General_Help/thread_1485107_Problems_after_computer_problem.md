---
title: "Problems after computer problem"
date: 2010-05-16
forum: General Help
---

### Post by bizhat on 2010-05-16
Two days ago i have a computer problem. Computer become slow, i checkec top, found high iowait. I thought it was due to cpu heat, so installed  "lm-sensors", during install hdd become read only, then crashed. I rebooted, it won't boot. After few switch on and off, smoke start coming from power supply (smps). Tech guty replaced SMPS and computer start working fine. It is dual boot, between windows and ubuntu. windows works perfect.

When i boot to ubnuntu, i get some disk error, i have to run e2fsck, i just enter for everything. After that ubuntu started working.

Now problem is, when i play video, i don't get any sound. If i play videos from youtube or espeak tts, i can hear sound.

I see some files in lost+found, now sure what files they are. Look like i lost some important files.

When i try to install a software with apt-get i get error like

```

boby@boby-desktop:~$ sudo apt-get install alsamixergui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  alsamixergui
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/30.0kB of archives.
After this operation, 152kB of additional disk space will be used.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 1.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 2.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 3.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 4.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 5.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 7.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 8.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 9.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 10.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 11.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 12.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 14.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 15.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 16.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 17.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 18.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 20.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 21.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 22.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 24.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 25.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 26.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 28.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 29.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 30.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 32.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 33.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 34.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 36.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 37.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 38.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 39.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 40.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 41.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 42.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 44.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 45.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 46.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 47.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 48.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 49.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 50.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 51.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 52.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 53.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 54.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 55.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 56.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 57.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 59.
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <$__ANONIO__> line 60.
Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 70, <$__ANONIO__> chunk 64.
Selecting previously deselected package alsamixergui.
(Reading database ... 
dpkg: serious warning: files list file for package `lm-sensors' missing, assuming package has no files currently installed.
150081 files and directories currently installed.)
Unpacking alsamixergui (from .../alsamixergui_0.9.0rc2-1-9_i386.deb) ...
Processing triggers for man-db ...
gdbm fatal: read error
Setting up lm-sensors (1:3.0.2-2ubuntu4) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing lm-sensors (--configure):
 subprocess post-installation script returned error exit status 2
Setting up alsamixergui (0.9.0rc2-1-9) ...

Errors were encountered while processing:
 lm-sensors
E: Sub-process /usr/bin/dpkg returned an error code (1)
boby@boby-desktop:~$ 

```

lm-sensors is the software i am trying to install while computer crash.

Can anyone tell how to fix the error ?

---

