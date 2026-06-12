---
title: "How do I install programs?"
date: 2006-01-28
forum: General Help
---

### Post by Elakt on 2006-01-28
Do I have to use console whole the time or is it easier ways? I wanna install xmms help is apriciated :)

---

### Post by xtacocorex on 2006-01-28
In KDE you can use Adept to search for and install packages from the repositories, it should be in System in Kmenu.

From the command line it would be:
```
sudo apt-get install xmms
```

---

### Post by Elakt on 2006-01-28
thx mate it worked :D

---

### Post by xtacocorex on 2006-01-28
Glad I could help.

---

### Post by rykel on 2006-01-28
[QUOTE=Elakt]Do I have to use console whole the time or is it easier ways? I wanna install xmms help is apriciated :)[/QUOTE]

hi elakt,

there are primarily 3 ways to install any program in linux...

1.   the easiest and most recent way is to install autopackages. (see [http://www.autopackage.org]("http://www.autopackage.org"))

however, being a relatively new kid on the block, the no. of autopackages available is still little.

2.   the other way is to install debs or rpms. these files are created for debian/debian-like and red hat/red hat-like distros respectively.

for debs, the fastest way to get them is to use synaptics package manager and install them from the repositories provided with the distro. (applies to ubuntu)

if u come across a lone deb file, you can install it in a terminal with "**sudo dpkg -i NAME.deb**"

for rpms, there is usually a GUI prompt asking if u woould like to install using the native package manager, and thus keep track of its existence. (eg. fedora and suse)

3. last but not least, compile each individual program for ur system. the advantage of this approach is tat the software is uniquely "created" for your PC, although most windows users will be horrified at compiling any program themselves.

hope tat helps!!!   \\:D/

---

### Post by Elakt on 2006-01-28
nice :) thx for all :)

now hm I wonder winamp was one thing now the video..I used VLC in windows for all my movies..wich dist should I use to install it on kubuntu?

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by rykel on 2006-01-28
[QUOTE=Elakt]nice :) thx for all :)

now hm I wonder winamp was one thing now the video..I used VLC in windows for all my movies..wich dist should I use to install it on kubuntu?

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)[/QUOTE]

to the best of my knowledge, vlc for ubuntu is best installed from synaptics package manager. simply enable "Universe" and "Multiverse" repositories and do a search for **vlc**.

to enable a repository in synaptics, do some clicking around in the menus of that program!

---

### Post by Elakt on 2006-01-28
synapsis packet manager same thing I installed xmms from or?

---

### Post by rykel on 2006-01-28
[QUOTE=Elakt]synapsis packet manager same thing I installed xmms from or?[/QUOTE]

synaptics package manager is the GUI for *apt-get*, which u used to install xmms.

tat is, installing _***xmms***_ from synaptics package manager is the same as **sudo apt-get install xmms**. apt-get runs in a terminal, while synaptics is graphical.

---

### Post by Elakt on 2006-01-28
okok nice :)

now I downloaded vlc-0.8.4a.tar.bz2.md5

and I went into that program..but it doesn't find that file or anything on VLC or videolan :P *n00b*

---

### Post by aysiu on 2006-01-28
[QUOTE=Elakt]okok nice :)

now I downloaded vlc-0.8.4a.tar.bz2.md5

and I went into that program..but it doesn't find that file or anything on VLC or videolan :P *n00b*[/QUOTE] You don't need to download **anything** separately. Just enable extra repositories (see the first link of my signature) and then ```
sudo apt-get update
sudo apt-get install vlc
``` or use Adept or Synaptic Package Manager.

apt-get, Adept, and Synaptic Package Manager download **and** install everything for you--just pick which programs you want.

---

### Post by lowey23 on 2006-01-28
You may find this excellent article to be of some help.

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Cheers

---

### Post by Elakt on 2006-01-28
I read it all and I did that manuall stuff...and it updated some..now it works!! wohooo! ty all!!

---

### Post by Elakt on 2006-01-28
now my final question is I have a usb drive for 250 gb..I can reach it all and use all files..I changed some rights..but I can't delete or move filis within the drive..it says I can't create some trash command..and I have read the forums and I dont understand all the guiding..aint it some command u can do to just monitor all with full rights this sudo stuff?


[http://www.psychocats.net/linux/permissions.php](http://www.psychocats.net/linux/permissions.php)

this konqueror? is this something for me? creating a shortcut to it automatically or does this only affect all the intern disks...?

---

### Post by aysiu on 2006-01-28
[QUOTE=Elakt]now my final question is I have a usb drive for 250 gb..I can reach it all and use all files..I changed some rights..but I can't delete or move filis within the drive..it says I can't create some trash command..and I have read the forums and I dont understand all the guiding..aint it some command u can do to just monitor all with full rights this sudo stuff?[/QUOTE] That's where the fourth link of my signature comes in handy. It's instructions for Windows partitions, but the same approach applies for external hard drives, too, as they're usually FAT32 or NTFS.

---

### Post by christooss on 2006-01-28
you have chown the map that usb drive is mounted at.

sudo chown <user_name> /media/<map_name>

Change username with your user name and <mp_name> with mape the drive is mounted to.

---

### Post by Elakt on 2006-01-28
now I got some kind of SU problem when I try acess my rights lol

---

### Post by christooss on 2006-01-28
sudo asks you foryou user password which you set at installation

---

### Post by Elakt on 2006-01-28
hm okay but it's a error msg nothing really to fill in....I am not sure if I backed up that sources list..and I can't edit it in the file..since I dont have the rights wich I am trying to access but I can't hmm

---

### Post by Elakt on 2006-01-28
how to change your default group in TEXT mode? anyone knows how to do?

---

### Post by rykel on 2006-01-28
[QUOTE=lowey23]You may find this excellent article to be of some help.

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Cheers[/QUOTE]

hi,

i thoroughly enjoyed the psychocats' site on installing programs in ubuntu... i think it is well and clearly written.

however, i was wondering if it might be updated with a write-up on installing **[autopackages]("http://www.autopackage.org")**, since this is the most recent way to set up software in any distro, and its popularity is gaining... i myself uses autopackages whenever possible.

---

### Post by knives on 2006-02-08
Thanks to Elakt for starting this wonderful topic...

---

