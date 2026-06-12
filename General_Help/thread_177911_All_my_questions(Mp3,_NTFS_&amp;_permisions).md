---
title: "All my questions(Mp3, NTFS &amp; permisions)"
date: 2006-05-17
forum: General Help
---

### Post by vincister on 2006-05-17
Once more I must write that I have 2 problems, but this time one maybe is depending on other

1. I open some mp3 from my other partition(NTFS) with the Rythmobox or whatever its called. But I got error that such file is not an audio stream. Whats wrong?

2. How to configure permisions to my user for accesing windows partitions(NTFS)
I have tried using command "sudo nautilus" afterwards my root password and then I should be able to change in properties for each partition, but when I tick any checkbox (read, write or execute) it says something like disk is read only. Where the hell I can find and remove this "read-only".
And the access to those partitions is only for root user, cause it's the owner, but not for the root user group. My user is set to group root.

By the way when I click to Synaptic via the desktop menu, nothing happens. Afterwards I used console to start it and then I got error that only root can use synaptic. WDF? Why it didnt tell me this error when I click via menu? Why did not it asked for root pass? Is there something I should set up?

And why root cannot login via login screen, is it only available in console mode or something like that?

---

### Post by Jimorie on 2006-05-17
I can't answer all your questions, but I think I can say something.

[quote="vincister"]2. How to configure permisions to my user for accesing windows partitions(NTFS)

I have tried using command "sudo nautilus" afterwards my root password and then I should be able to change in properties for each partition, but when I tick any checkbox (read, write or execute) it says something like disk is read only. Where the hell I can find and remove this "read-only".

And the access to those partitions is only for root user, cause it's the owner, but not for the root user group. My user is set to group root.[/quote]
That the disk is read only has nothing to do with permissions, but how the disk is mounted. The disk is mounted as read-only. And I don't think Linux can do any better with NTFS disks. Last I heard, Linux can read NTFS but not write. So you won't be able to change this. You should be able to change read permissions on the mount point so that your regular user can read the disk, however.

This probably didn't help you at all... But good luck. =)

---

### Post by Sutekh on 2006-05-17
[quote=vincister]1. I open some mp3 from my other partition(NTFS) with the Rythmobox or whatever its called. But I got error that such file is not an audio stream. Whats wrong?[/quote]

In regards to the MP3 problem, this is because MP3 are a patent encumbered format, Ubuntu won't ship with the codecs as it goes against their philosophy of free software.  

That's not to say they can't be installed.  The Ubuntu Wiki has information on how to install the packages you need.

[Ubuntu Wiki - Restricted Formats - MP3]("https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970")


[quote=vincister] 2. How to configure permisions to my user for accesing windows partitions(NTFS)[/quote]
To setup the permissions for access to windows partitions, I would recommend you start with this link

[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

[quote=vincister]By the way when I click to Synaptic via the desktop menu, nothing happens. Afterwards I used console to start it and then I got error that only root can use synaptic.[/quote]
Synaptic must be started as root, as in using **sudo  **or **gksudo**, the latter offers the graphical dialog box to enter your password.  The shortcut on your desktop may not take that into account.  

Starting Synaptic from the System -> Administration menu should ask for your password (it should be using **gksudo synaptic**), which is all that is required to gain root access.

[Ubuntu Wiki - Root and Sudo]("https://wiki.ubuntu.com/RootSudo") can explain the root/sudo deal in a clearer way for you.

By default the root account is not enabled, so you can't logon as root via the login screen.

---

### Post by easyease on 2006-05-17
have you tried playing the mp3's in another player? xmms for example...

---

### Post by easyease on 2006-05-17
well done sutekh! was going to mention codecs if it wasnt just a rhythmbox problem. :-D

---

### Post by Sutekh on 2006-05-17
Yep, if the error is "file not an audio stream" you know its the MP3 plugins.

---

### Post by vincister on 2006-05-17
The promblem is that I don't have Internet at home (yet) so I cannot get any plugins or other software:( 

this is why I cant say if other media players says smthg about those mp3


And how to set the read access for my user to NTFS partitions?

---

### Post by easyease on 2006-05-17
ok mate, the one page i always visit if ive got a fresh install of ubuntu is.....
  [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
Do you have a cd writer or removable usb drive on the pc you are accessing the internet on at the moment? if so you could download the packages and take them home with you to install later.....

---

### Post by Sutekh on 2006-05-17
I posted a link before that will show you how to mount NTFS partitions with the needed permissions

[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

---

### Post by easyease on 2006-05-17
you can download the "essential codecs package" from here to your desktop, then take it home with you.
 [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

---

### Post by vincister on 2006-05-17
Ok, thanks I will try to download some packages I need and bring them home.

I thought that packages can only be downloaded trought synaptic and no otherwise, but you have made me change my mind. Thanx once more.

---

### Post by easyease on 2006-05-17
yes it does seem that way at first but i think you are about to learn where a "terminal" comes in very useful. :-D 
when you get the package home you should type in "sudo dpkg -i " into the terminal, 
 then drag and drop the package into the terminal window and press enter, enter your password and it should install for you.

---

### Post by easyease on 2006-05-17
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by vincister on 2006-05-18
Hm, so I can install software this way you mentioned above. But where can I download nvidia.glx for example? I was told that I need it for my video card to work properly together with nVidia chipset and AMD64

And I just downloaded those mp3 plugins and player from that address you gave me, I will se if I can install them. Thanks...

---

### Post by Sutekh on 2006-05-18
If you need the drivers for your video card, you should look here first.

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")
 
  - Method 1 is by far the easiest method (nvidia-glx), and will install the Ubuntu repository NVIDIA drivers (v7667)
 
  - Method 2 is a little harder and can be used to install any version of the proprietry NVIDIA drivers.

---

### Post by leonbrio on 2006-05-20
well... i was just running xmms with gksudo (so it could acess my sata nfts with my mp3s) but guess the topics helpes alot.

still, just been less than hour on linux. wish i had some player like WMP.
winamp(xmms) just doesn't handle 30gb of mp3 well (its hard to find misstaged files )

---

