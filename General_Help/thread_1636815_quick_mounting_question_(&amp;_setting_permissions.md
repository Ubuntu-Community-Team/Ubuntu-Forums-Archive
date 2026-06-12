---
title: "quick mounting question (&amp; setting permissions)"
date: 2010-12-03
forum: General Help
---

### Post by 0949er on 2010-12-03
Hey guys, Ok so I have had this problem where my dvd rom drive is auto-mounting DVD's without the "unhide" option. Well, I have a few questions about that. 

A) Is is possible to make my ubuntu auto-mount with the unhide option by default? 

-second-

B) if its not possible, how should I go about manually doing this? And furthermore, how can/do I set the permission on the mount so that my current users can access the drive AND so that is has execute permissions on it?

I honestly have been searching here and google and playing around with chmod and I just cant get it. I just wasted 45 min copying a 7 gig dvd to my harddrive hoping I could figure it out (nope).

Any advice? 

If I do 
```

sudo mount /dev/sr0 /mnt/cdrom -o unhide

```

it does not give me any permission for my current user, and for the life of me (and yes, I have run "man chmod" I cannot figure out how to set the permission of /mnt/cdrom so that I can have executable permissions ( I need to run a installer that should be able to access all files on the dvd)

Please help.

---

### Post by WorMzy on 2010-12-03
A) Sure. Open fstab by pressing Alt+F2, then typing:
```
gksu gedit /etc/fstab
```
and click run (or press enter), then and add this line to it:
```
/dev/cdrom /media/cd auto ro,user,noauto,unhide 0 0
```

Save and exit, and the next time you put a cd into the cd tray, this should take effect. No restart necessary.

B) You can specify ownership in the fstab file too. Just add uid=###, gid=###, and umask=### to the comma seperated list of options (ro,user,noauto,unhide). uid and gid stand for user ID and group ID, the default user has uid 1000 and gid 1000, find out your user ID by opening a terminal (Applications -> Accessories -> Terminal) and running

```
echo $UID
```
Your default gid is normally identical to your uid, but I think you can run "echo $GID" in case you're unsure.

```
/dev/cdrom /media/cd auto ro,user,noauto,unhide**,uid=1000,gid=1000** 0 0
```

umask is a little more tricky to understand. It sets the default permissions for the user, group, and others, in that order. The first number specifies the user's permissions, and so on. e.g. umask=027 means that user (0) has unrestricted permissions (can read+write+execute*), group (2) can read and execute, and others (7) can't do anything.

0 = read, write and execute
1 = read and write
2 = read and execute
3 = read
4 = write and execute
5 = write
6 = execute
7 = no permissions

*Although, this is a CD, so chances are you *can't* write to it

---

### Post by WorMzy on 2010-12-03
Oh, just a note; you will need to create /media/cd if it doesn't already exist.

Open a terminal again and run:
```
sudo mkdir /media/cd
```

---

### Post by 0949er on 2010-12-03
Ok thank you so much. Now when I try to run "wine" on the "isntaller.exe" on the dvd rom, I get the following error:

The file '/media/dvd-rom/Installer.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.


Is this something that I just should "sudo chmod 777 /media/dvd-rom/Installer.exe" ?

---

### Post by 0949er on 2010-12-03
> **WorMzy said:**
> Oh, just a note; you will need to create /media/cd if it doesn't already exist.

Open a terminal again and run:
```
sudo mkdir /media/cd
```

haha yeah I scratched my head for a second when nothing happend and figured it was because the directory "/media/cd" doesnt exist. So I made one called "dvd-rom" :) (and "chmod 777 /media/dvd-rom", was that a bad idea?)

---

### Post by WorMzy on 2010-12-03
Well, you'll need to update the fstab entry, but the directory doesn't actually matter, neither do the permissions you give to the folder (so there's not much point chmoding it). So long as the entry says that it should mount the disk to /media/cd, then it'll keep trying to mount it there until you tell it otherwise, whether or not /media/dvd-rom exists or not.

I don't think chmoding the installer will work either. So try editing the fstab entry again and set the umask to 000, then eject the disk and put it back in. If that doesn't help, then add mode=777 to the options and try again.

---

### Post by 0949er on 2010-12-03
Hey sorry I left the apartment but before I left I tried 

```
sudo chmod 777 /mnt/dvd-Rom/installer.exe
```

And received the same error. It says the filesysten is mounted as read-only is that a problem? I mean I know its a cd but should it be mounted as read only+execute?

---

### Post by 0949er on 2010-12-03
ok bear with me guys.

So from the user manual of "mount" I read this:

```

user   Allow an ordinary user to mount the filesystem.  The name of the
              mounting  user  is  written  to  mtab so that he can unmount the
              filesystem again.   This  option  implies  the  options  **noexec**,
             ** nosuid**,  and  **nodev** (unless overridden by subsequent options, as
              in the option line user,exec,dev,suid).

```

So, it assumes noexec, whic I assume means "no execution", so how do I mount it with the user flag AND execution privilages? 

```

/dev/sr0 /media/dvd-rom auto ro,user,noauto,unhide,**exec**(?),uid=1000,gid=1000 0 0

```

Thank you again.

---

### Post by 0949er on 2010-12-03
now it has no errors when I right click and go to "open with wine", but nothing happens.

---

### Post by WorMzy on 2010-12-04
Can you try to launch it from a terminal? Just type

```
wine /media/dvd-rom/installer.exe
```

---

### Post by 0949er on 2010-12-04
> **WorMzy said:**
> Can you try to launch it from a terminal? Just type

```
wine /media/dvd-rom/installer.exe
```


Wine 1.2.1(stable):
```

swooshonln@power-house:/media/dvd-rom$ wine Installer.exe 
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
swooshonln@power-house:/media/dvd-rom$ wine Installer.exe 
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
swooshonln@power-house:/media/dvd-rom$

```Wine 1.3.8(beta):
```

swooshonln@power-house:/media/dvd-rom$ wine Installer.exe 
fixme:process:GetLogicalProcessorInformation ((nil),0x33f5e4): stub
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:process:GetLogicalProcessorInformation ((nil),0xd7c5cc): stub
fixme:process:GetLogicalProcessorInformation ((nil),0xd7c5d4): stub
fixme:process:GetLogicalProcessorInformation ((nil),0xe7e99c): stub
swooshonln@power-house:/media/dvd-rom$

```Thats it. no other erros, nothing. Any ideas?

---

### Post by WorMzy on 2010-12-04
Seems to be a common bug: [http://bugs.winehq.org/show_bug.cgi?id=23824](http://bugs.winehq.org/show_bug.cgi?id=23824)

There are a couple of suggestions, 1) use dd to copy the contents of the disk to the hard drive, then run it, or 2) use a "digital downloader" from Blizzard (presumably these are freely available from the Blizzard website.

---

