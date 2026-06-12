---
title: "Installin Moizilla Sunbird"
date: 2010-09-11
forum: General Help
---

### Post by M_Mynaardt on 2010-09-11
Hi-Ho, All!  ):P

I wanted to install the Mozilla Sunbird calendar program in my computer.  I liked using that program before I gave M$ Window$ the old heave-ho recently.

Unfortunately, I'm still a bit new to this Linux business.  I downloaded the installation file (sunbird-1.0b1.tar.bz2) from Mozilla's site.  That part was easy; easy-peasy!

***On the other hand*** it's not an easy-to-install deb file.  I found the directions which were:

[INDENT][COLOR="DarkGreen"]
Extract the tarball in the directory where you want to install Sunbird:
     tar -xzvf sunbird-1.0b1.en-US.linux-i686.tar.gz
This will create a sunbird subdirectory of that directory
[/COLOR][/INDENT]

I'm not entirely dim, though.  I know the above command will install the program.  But, I'm just wondering what directory I should install it in.  Would any old directory do?  And if I extract the tar.gz file to just any old place; will the above command create the executable Sunbird file in the /usr/bin/ directory along with all the other executable files too?

I like Sunbird's calendar program; but I don't want to make a mess of installing it...

Thanks in advance for any help and advice...

---

### Post by johngreth on 2010-09-11
installing tarballs in Ubuntu is a mess. The instructions you found are just the first step of extracting the installation files. Running the install is more complicated because you need to worry about compilers and requirements...

Since sunbird isn't in the software manager any more, I suggest installing Thunderbird from the software manager and installing lightning on top of it. That's what I did. Very simple and it looks the same.

---

### Post by wojox on 2010-09-11
Just install it in your /opt directory.

---

### Post by M_Mynaardt on 2010-09-21
I got back to trying to install Sunbird; but I can't seem to copy anything (form the GUI) to the /opt/ directory.  Are there some sorts of shell commands I need to do to make this happen?

---

### Post by gandaran on 2010-09-21
> **M_Mynaardt said:**
> I got back to trying to install Sunbird; but I can't seem to copy anything (form the GUI) to the /opt/ directory.  Are there some sorts of shell commands I need to do to make this happen?
you need root permissions to install in /opt, type in terminal this command to open root nautilus 
```
gksu nautilus
```
I would keep Sunbird installed in the hidden home user directory, theres no need to put it in the root file system, just add a dot to the Sunbird folder (.Sunbird) and make a desktop launcher with the full path to the sunbird launch file.

---

### Post by M_Mynaardt on 2010-09-26
> **gandaran said:**
> you need root permissions to install in /opt, type in terminal this command to open root nautilus 
```
gksu nautilus
```
I would keep Sunbird installed in the hidden home user directory, theres no need to put it in the root file system, just add a dot to the Sunbird folder (.Sunbird) and make a desktop launcher with the full path to the sunbird launch file.

Okay, thanks; I'll try that in a bit...

---

