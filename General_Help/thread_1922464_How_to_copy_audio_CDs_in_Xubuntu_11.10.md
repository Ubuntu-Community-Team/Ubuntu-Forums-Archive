---
title: "How to copy audio CDs in Xubuntu 11.10??"
date: 2012-02-08
forum: General Help
---

### Post by SteveMcMahon2012 on 2012-02-08
I have installed Xubuntu 11.10. I want to copy audio CDs. I'm using Xfburn, which is bundled with Xubuntu 11.10. The problem is, Xfburn allows you to create audio CDs, burn and create ISO images, but it does not offer the option to copy audio CDs. How can I do this with Xubuntu?? I don't mind using the command line to do the copy, but I don't know which commands to use. Also, is there another CD/DVD tool that I can download and install on Xubuntu, such as Brasero? Any help is much appreciated. Thanks!!

---

### Post by Bucky Ball on 2012-02-08
Yea, just install Brasero if you like that. Sound Juicer is also another one I have used without issue and is designed for your purpose. ;)

---

### Post by SteveMcMahon2012 on 2012-02-08
[SIZE=2]Thanks a lot for your reply, Bucky Ball.

Can Brasero be easily installed onto Xubuntu 11.10? Do I just do "[FONT=Courier New]yum install brasero[/FONT]"? Will that work? Is there going to be a bunch of other things that I'm going to need to install beforehand??

Thanks again for your help!!

[/SIZE]

---

### Post by Bucky Ball on 2012-02-08
No, just use software centre. Yes, it will drag in dependencies but not sure what.

For the terminal you would need:

```
sudo apt-get install brasero
```... or for sound-juicer I imagine it would be:

```
sudo apt-get install sound-juicer
```... but that's also available in Software Centre. Yum not used in Ubuntu. ;)

---

### Post by imachavel on 2012-02-08
well also, an idea, how are you copying the cds? from one drive to another? Or by removing the songs from the cds? There is more then one way of doing it.

---

### Post by Bucky Ball on 2012-02-08
> **imachavel said:**
> well also, an idea, how are you copying the cds? from one drive to another? Or by removing the songs from the cds? There is more then one way of doing it.

True. I generally just open the CD and drag/drop the audio files in the folder I want on the hard drive without using software app.

---

### Post by imachavel on 2012-02-08
worked for me:


sudo apt-get install brasero
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
brasero is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
danel@danel-Dimension-4700:~$ sudo apt-get install sound-juicer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gstreamer0.10-lame gstreamer0.10-plugins-really-bad
The following NEW packages will be installed:
  sound-juicer
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,691 kB of archives.
After this operation, 5,108 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe sound-juicer i386 2.32.1+20110330-1 [1,691 kB]
Fetched 1,691 kB in 7s (236 kB/s)                                              
Selecting previously deselected package sound-juicer.
(Reading database ... 281809 files and directories currently installed.)
Unpacking sound-juicer (from .../sound-juicer_2.32.1+20110330-1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Setting up sound-juicer (2.32.1+20110330-1) ...

the image I attached shows juicer is about as simple as it gets. There isn't much you can't do with Ubuntu is there? Btw what is there a windows equivalent to juicer?

---

### Post by Bucky Ball on 2012-02-08
Looks like Brasero was installed already (must be a default in Xubuntu as well as Ubuntu). 

Not sure of Windows equivalents. Haven't used it for this stuff in a loooong time. ;)

---

### Post by SteveMcMahon2012 on 2012-02-09
[SIZE=3]Thanks Bucky Ball and imachavel.
Your posts were very helpful.

I'm going to try Brasero once I get home.

I think sound-juicer is more for ripping CDs, and I don't want to just rip them, I want to do a full copy of an audio CD onto a new blank CD-R, and it seems Brasero can do this for me, and it sounds like it's easy to install onto Xubuntu.

Thanks again for your quick posts. You've been really helpful.
[/SIZE]

---

