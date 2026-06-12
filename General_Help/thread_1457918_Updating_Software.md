---
title: "Updating Software"
date: 2010-04-19
forum: General Help
---

### Post by G-Sun on 2010-04-19
Hi!
I'm having all these newbie-questions
(My win xp-disk crashed, so trying Ubuntu Studio)

First:
I wanted to update Firefox from 3.0 somthing to 3.6.
I downloaded the update in Firefox (Tools/Download),
but then.. how do I run it?

Thanks!

---

### Post by G-Sun on 2010-04-19
My next question are:
What is Ubuntus answer to Win Task Manager -where I can see cpu-usage and so on?
Where do I find system information like version-number for my Ubuntu, hardware overview etc.?

Thanks!

---

### Post by Onesimus on 2010-04-19
G-Sun,

What version of Ubuntu Studio are you using ?

I am running Ubuntu 9.10, and the Firefox version is 3.59.

With regards to the hardware information, you could download Sysinfo using the Ubuntu Software Centre.

The CPU information can be obtained from System->Administrator->System Monitor

Hope this helps

---

### Post by 3rdalbum on 2010-04-19
> **G-Sun said:**
> Hi!
I'm having all these newbie-questions
(My win xp-disk crashed, so trying Ubuntu Studio)

First:
I wanted to update Firefox from 3.0 somthing to 3.6.
I downloaded the update in Firefox (Tools/Download),
but then.. how do I run it?

Thanks!

Welcome to Linux.

If you want to install software that is not in the normal Ubuntu repositories, then the best way to do that is to add a repository that contains the software you want. That way it stays up to date, is easy to install and remove, etc.

This is a howto that I found for adding a new repository to your system that contains Firefox 3.6.

[http://www.webupd8.org/2009/10/install-firefox-36-beta1pre-in-ubuntu.html]("http://www.webupd8.org/2009/10/install-firefox-36-beta1pre-in-ubuntu.html")

As for your other question, System > Administration > System Monitor.

---

### Post by klemes on 2010-04-19
The version of Firefox that you download from the web is simply installed by untaring (uncompressing) the contents of the downloaded package into your home directory.
But I do not recommend this.
You have better choose to install it through the official Ubuntu repositories through Synaptic or using the aptitude or the apt-get command in console.
This way it will be properly upgraded every time there is a new version trough the update manager.

For this purpose try:

```
sudo apt-get install firefox-3.5
```Sorry but I am not sure if firefox 3.6 exists in the Karmic repos but it certainly exists in the Lucid ones .But you can check this for your version of Ubuntu by typing:

```
apt-cache search firefox-3.6
```or by directly browsing the contents of packages.ubuntu.com url.

---

### Post by G-Sun on 2010-04-19
> **Onesimus said:**
> 
What version of Ubuntu Studio are you using ?
Thanks! Installed Sysinfo :) So, my version is: Ubuntu 8.04 (hardy)

---

### Post by G-Sun on 2010-04-19
> **3rdalbum said:**
> Welcome to Linux.

If you want to install software that is not in the normal Ubuntu repositories, then the best way to do that is to add a repository that contains the software you want. That way it stays up to date, is easy to install and remove, etc.

This is a howto that I found for adding a new repository to your system that contains Firefox 3.6.

[http://www.webupd8.org/2009/10/install-firefox-36-beta1pre-in-ubuntu.html](http://www.webupd8.org/2009/10/install-firefox-36-beta1pre-in-ubuntu.html)

As for your other question, System > Administration > System Monitor.
Thanks!
The System Monitor was what I was looking for yes :)

Repository.. A nice word, but I don't know what it means :) I can guess though.. I'll see what I manage

---

### Post by Onesimus on 2010-04-19
There is a new Long Term Support (LTS) version about to come out in the next week or two. I suggest that you consider upgrading to this version, this will ensure that you have the latest versions of the software installed on your machine.

---

### Post by G-Sun on 2010-04-19
> **klemes said:**
> 
```
apt-cache search firefox-3.6
```or by directly browsing the contents of packages.ubuntu.com url.
Hm.. I don't know if I will become friend with this Consol (I guess that's the name for Terminal in my norwegian version).
And it asks me of my password all the time, but don't accept any input.
Sorry, I get this ms-dos feeling. A little turnoff, but I'll hang on :)

Thanks!

---

### Post by G-Sun on 2010-04-19
> **Onesimus said:**
> There is a new Long Term Support (LTS) version about to come out in the next week or two. I suggest that you consider upgrading to this version, this will ensure that you have the latest versions of the software installed on your machine.
Thanks!
Well that's another question. Is Linux a core? And the distros are using the same core? Or are there different cores? Is Ubuntu one thing? So, the LTS you're talking about, is that all Ubuntu or is it Ubuntu Studio as I've installed?
Many questions.. :)

---

### Post by klemes on 2010-04-19
Linux is the core yes in the meaning of the kernel,but Linux or better GNU/Linux as it is referred by some is also a complete Unix operating system which comlpies with the POSIX standards and also is free under the GNU public licence,of which there many many flavors called distributions.Ubuntu is just one of them and every 6 months(twice a year )there is a new version available at the 4th and at 10th month respectively of the year(hence the enumeration Ubuntu 9.10,Ubuntu 10.4 where in the last example 10 stands for 2010 and 4 for the 4th month-April)
LTS just stands for Long Time Support or Long Term Support or something meaning that it will be supported beyond the 6 month lifecycle of it's other non-LTS counterparts.That's all,no great mystery there...:).

---

### Post by abra1 on 2010-04-19
W elcome to Ubuntu !

- to get to repositories :  System | Administration | Repositories   (you will soon know how to add new entries).
- When you enter your Password in the Terminal you will not necessarily get an acknowledgment (entering a password is a very important security feature of Linux ).
- the next LTS is Lucid  - Ubuntu 10.04  will be supported for 3 years - has the latest features and is very secure.

---

### Post by lovinglinux on 2010-04-19
See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by G-Sun on 2010-04-19
> **lovinglinux said:**
> See the [[COLOR=Sienna]**Installing Other Versions**[/COLOR]]("http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").
Thanks!
So, I can just wait for Ubuntu to include the Firefox-update necessary?

---

### Post by G-Sun on 2010-04-19
> **klemes said:**
> Linux is the core yes in the meaning of the kernel,but Linux or better GNU/Linux as it is referred by some is also a complete Unix operating system which comlpies with the POSIX standards and also is free under the GNU public licence,of which there many many flavors called distributions.Ubuntu is just one of them and every 6 months(twice a year )there is a new version available at the 4th and at 10th month respectively of the year(hence the enumeration Ubuntu 9.10,Ubuntu 10.4 where in the last example 10 stands for 2010 and 4 for the 4th month-April)
LTS just stands for Long Time Support or Long Term Support or something meaning that it will be supported beyond the 6 month lifecycle of it's other non-LTS counterparts.That's all,no great mystery there...:).
Learning, learning :) Thanks!
Do I have to reinstall everything when I choose to upgrade my Ubuntu?

---

### Post by G-Sun on 2010-04-19
> **abra1 said:**
> W elcome to Ubuntu !

- to get to repositories :  System | Administration | Repositories   (you will soon know how to add new entries).
- When you enter your Password in the Terminal you will not necessarily get an acknowledgment (entering a password is a very important security feature of Linux ).
- the next LTS is Lucid  - Ubuntu 10.04  will be supported for 3 years - has the latest features and is very secure.
Thanks! I guess Repositories is called "Synaptic Pakkebehandler" in Norwegian.
-That's always the problem when choosing non-english language for the OS/Software. It often makes using help/forums more difficult..
Ok, so I'll just type my password :)

---

### Post by lovinglinux on 2010-04-19
> **G-Sun said:**
> Thanks!
So, I can just wait for Ubuntu to include the Firefox-update necessary?

Yes. Nex Ubuntu version will be released on April 29th and it brings Firefox 3.6 with it.

> **G-Sun said:**
> Learning, learning :) Thanks!
Do I have to reinstall everything when I choose to upgrade my Ubuntu?

No, you can upgrade the system to a new Ubuntu version, although some people like me prefer to always do clean installations. If you want to do that too, then I would recommend having a separate partition for home, so you can re-install Ubuntu without losing your personal settings and files.

> **G-Sun said:**
> Thanks! I guess Repositories is called "Synaptic Pakkebehandler" in Norwegian.
-That's always the problem when choosing non-english language for the OS/Software. It often makes using help/forums more difficult..
Ok, so I'll just type my password :)

My native language is Portuguese but my system is in English. Is a lot easier to follow and to recommend any steps.

---

### Post by G-Sun on 2010-04-20
> **lovinglinux said:**
> 
Thanks!

---

### Post by G-Sun on 2010-04-20
I'm trying to update my Ubuntu to read NTFS
[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)
So, how do I deal with dowloads with the extension rpm?

---

### Post by G-Sun on 2010-04-20
I think I managed to install the rpm,
but no success mounting my ntfs-disks.
I'll have to look into forced mounting.

---

### Post by QLee on 2010-04-20
While it is possible to install alien packages (in this case a Red Hat package) on Ubuntu, I want to suggest that it isn't recommended for someone who isn't experienced with Ubuntu and GNU/Linux in general. 

Didn't your install already have the (Ubuntu) ntfs-3g package installed?

It might be possible for us to help more if you detail exactly how you tried to do something and the exact error message dropped when it failed.

---

### Post by G-Sun on 2010-04-20
> **QLee said:**
> 
Didn't your install already have the (Ubuntu) ntfs-3g package installed?.
Yes, it was installed

---

### Post by G-Sun on 2010-04-20
> **QLee said:**
> 
It might be possible for us to help more if you detail exactly how you tried to do something and the exact error message dropped when it failed.
I'm having a disk with 3 partitions NTFS with my documents on,
and I would need to at least read from the disks.
It shows up in "My computer" but when I try to access them it says:
"Can't mount volume"
Details:
"..log file indicates unclean shutdown... Mount is denied because NTFS is marked in use..
Choice 2: Force mount"
Sorry, no way to copy all the details

---

### Post by G-Sun on 2010-04-20
Ok, here is all text:
```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb5 /media/Enriche -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb5 /media/Enriche ntfs-3g force 0 0
```
From ntfs-config

So running this:
```
mount -t ntfs-3g /dev/sdb5 /media/Enriche -o force
```
Success!!
Then trying for the other partitions, but.. messes up I think
I changed the name, but not the sbd-number
So, now I have tree mounted versions of sbd5
..help..

---

### Post by G-Sun on 2010-04-20
ntfs-config:
Unable write-permission for ntfs-devises
Error-messages of the dublicated drives,
and they disappear from Systemmonitor / Filesystems
Good I think :)

---

### Post by G-Sun on 2010-04-20
Enabling the write-permissions again,
the error-messages appear again,
and I can paste the right code into the terminal.
Success!!
I can now read my documents on the disk/partitions :)

---

### Post by abra1 on 2010-04-21
if you have a dual boot  (say XP and Ubuntu ),  you need to first close XP  before you use Ubuntu to access files in Windows.  

If Windows is merely hybernating or the lke, you will get an error when trying to access files in XP.

---

### Post by G-Sun on 2010-04-21
> **abra1 said:**
> if you have a dual boot  (say XP and Ubuntu ),  you need to first close XP  before you use Ubuntu to access files in Windows.  

If Windows is merely hybernating or the lke, you will get an error when trying to access files in XP.
XP is on a corrupted disk in my garbage-can..

---

