---
title: "Error Messages about update manager"
date: 2012-09-09
forum: General Help
---

### Post by rickm1945 on 2012-09-09
I keep getting this error: I also have a red solid circle next to email envelope at the top right side of the screen, showing in screen shot. There was a problem with update. Anybody know what this is? I can not open Software Manager either, it starts to open then just disappears. This all started when I installed this PDF software. How can I remove it? I got it from [http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html](http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html)

My system is giving me error after error. Here are a cople of screen shots that show what I was doing as well as the error. Will post in a reply.

---

### Post by rickm1945 on 2012-09-09
Screen shots of errors.

---

### Post by newb85 on 2012-09-09
> **rickm1945 said:**
> I keep getting this error: I also have a red solid circle next to email envelope at the top right side of the screen, showing in screen shot. There was a problem with update. Anybody know what this is? I can not open Software Manager either, it starts to open then just disappears. This all started when I installed this PDF software. How can I remove it? I got it from [http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html](http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html)

My system is giving me error after error. Here are a cople of screen shots that show what I was doing as well as the error. Will post in a reply.

The messages are clear that there's a problem with line 59 in the sources list file.  So, what does that line say?

You can open the file by

$ gedit /etc/apt/sources.list

Finding the correct line should be easy, since gedit lists the line of your curser at the bottom of the window.

---

### Post by rickm1945 on 2012-09-10
> **newb85 said:**
> The messages are clear that there's a problem with line 59 in the sources list file.  So, what does that line say?

You can open the file by

$ gedit /etc/apt/sources.list

Finding the correct line should be easy, since gedit lists the line of your curser at the bottom of the window.
Line 59 says:```
deb http://archive.canonical.com/precise partner
```

---

### Post by newb85 on 2012-09-10
> **rickm1945 said:**
> Line 59 says:```
deb http://archive.canonical.com/precise partner
```

Try changing it to 

```
deb http://archive.canonical.com/ubuntu precise partner
```

Note that to edit the file, you will need administrator privelages

```
$ sudo gedit /etc/apt/sources.list
```

---

### Post by plucky on 2012-09-10
This is what the line should say ```
deb http://archive.canonical.com/ubuntu precise partner
```

Edit the file and add the **ubuntu**

If that doesn't fix it post the whole sources.list file.

Good Luck

---

### Post by rickm1945 on 2012-09-10
> **plucky said:**
> This is what the line should say ```
deb http://archive.canonical.com/ubuntu precise partner
```Edit the file and add the **ubuntu**

If that doesn't fix it post the whole sources.list file.

Good Luck
No it didn't work. Here is the source. 
```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/precise partner
deb-src http://extras.ubuntu.com/ubuntu precise main

``` can see where ubuntu is missing from several lines I have corrected the lines and now it is working. Thank you for your help. I will mark this thread closed.

---

