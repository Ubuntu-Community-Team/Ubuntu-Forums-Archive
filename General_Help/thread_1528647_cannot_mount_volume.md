---
title: "cannot mount volume"
date: 2010-07-11
forum: General Help
---

### Post by thebedshow on 2010-07-11
When trying to open a cd drive I it attempts to load it I can hear it spinning in my tower and then I get a cannot mount volume error.  I tried some fixes from other threads it was a lot of typing stuff in the terminal and I am pretty much dumb at this stuff and it didnt help at all.  if anyone knows how I can fix this that would be wonderful

thanks

---

### Post by Pizack on 2010-07-11
go to your media folder (/media) and type this in terminal, tell me the result:```
ls -l
```  

also, go to administration > hardware drivers and see if there's anything there you can install for the cd drive.

---

### Post by thebedshow on 2010-07-11
benjamin@benjamin-desktop:~$ ls -1
Desktop
Documents
Downloads
Examples
Music
Pictures
Public
Templates
Videos

---

### Post by thebedshow on 2010-07-11
the hardware drivers just shows me 2 different video card drivers one that im using and an older version

---

### Post by Pizack on 2010-07-11
you need to change to the media directory first, try this.
```
cd /
cd media
ls -l
```

---

### Post by thebedshow on 2010-07-11
benjamin@benjamin-desktop:/media$ ls -l
total 12
lrwxrwxrwx 1 root root    6 2010-07-09 22:28 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-07-09 22:28 cdrom0
drwxr-xr-x 2 root root 4096 2010-07-11 00:13 externaldisk
drwxr-xr-x 2 root root 4096 2010-07-11 00:16 windows_d


sorry I have no idea about this stuff

---

### Post by Pizack on 2010-07-11
no problem. give me one moment to look up the proper command to change the permissions for your folder.

---

### Post by Pizack on 2010-07-11
```
sudo chown -R your_login:users /media
sudo chmod -R 770 /media
```if you get any errors let me know, but this should fix your problem

Basically what your problem is, is that root owns the folders instead of you.  This will make you own them.  Chmod goes along with this, but I don't have as full of an understanding of that command. Anybody that cares to explain it would be greatly appreciated.

---

### Post by thebedshow on 2010-07-11
I replaced your_login with my login name and got no errors but I get the same cannot mount volume error when trying to access the cd/dvd drive

---

### Post by thebedshow on 2010-07-11
total 12
lrwxrwxrwx 1 benjamin users    6 2010-07-09 22:28 cdrom -> cdrom0
drwxrwx--- 2 benjamin users 4096 2010-07-09 22:28 cdrom0
drwxrwx--- 2 benjamin users 4096 2010-07-11 00:13 externaldisk
drwxrwx--- 2 benjamin users 4096 2010-07-11 00:16 windows_d


is the new ls-l thing

---

### Post by Pizack on 2010-07-11
> **thebedshow said:**
> I replaced your_login with my login name and got no errors but I get the same cannot mount volume error when trying to access the cd/dvd drive

Can you copy and paste the error message for me? I might be able to get a better idea.  You did it right though, grats on that!

---

### Post by thebedshow on 2010-07-11
Cannot Mount Volume.

Invalid mount option when attempting to mount the volume 'UDF Volume'.

---

### Post by Pizack on 2010-07-11
[http://ubuntuforums.org/showthread.php?t=650697&page=2](http://ubuntuforums.org/showthread.php?t=650697&page=2)

Try this thread.  Next time you should search the forums for your specific error message. Hope that helps, haven't read the entire thread, but it is the same issue.  Seems like a problem with the CD and not ubuntu, so try another CD first.  What type of CD is it?

---

### Post by thebedshow on 2010-07-11
its a dvd with files on it

---

### Post by Pizack on 2010-07-11
I suppose that it was made in something other than Ubuntu. That thread should help you if that is the case!  Good luck!

---

### Post by thebedshow on 2010-07-11
and I have already looked at that thread and it does not solve my problem, it works when I was using on my brothers computer that uses windows 7, it is actually a copy of windows 7 and when I try to boot to the dvd from the startup boot manager and I choose to boot from the cd/dvd drive it tries for about 5 seconds then boots into ubuntu normally so...

---

### Post by Pizack on 2010-07-11
> **thebedshow said:**
> and I have already looked at that thread and it does not solve my problem, it works when I was using on my brothers computer that uses windows 7, it is actually a copy of windows 7 and when I try to boot to the dvd from the startup boot manager and I choose to boot from the cd/dvd drive it tries for about 5 seconds then boots into ubuntu normally so...

OH, then what you really need to do, if my assumption that you are trying to install windows with it, is boot from the cd.  This is a BIOS issue.  You need to go into your bios and set it to try to boot from the CD first, before the hard disk.  This is fairly simple, but varies from computer to computer.  Usually you have to hit F8 as the computer boots to get into the bios set up.  Hope this is a good workaround for you.

If this worked, please mark as solved.

---

