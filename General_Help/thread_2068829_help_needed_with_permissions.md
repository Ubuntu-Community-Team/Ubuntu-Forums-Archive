---
title: "help needed with permissions"
date: 2012-10-10
forum: General Help
---

### Post by n.foster on 2012-10-10
Hi, I need some help with changing permissions with my newly installed 12.04. I use an sd card via my camera, to load mp3 music for listening through my tv, I know it may sound odd, but it means I have no need for a hi-fi !
I have tried a few methods including GParted and pysdm, but both ask me to load the 12.04cd at some point, but when the cd is in, I can't get anything to happen. The cd was burt in April, and when I did a fresh install of 12.04 last week, I needed half a gig of updates, so I'm thinking I haven't the correct cd the programs are asking for. you will need to talk me through a fix step by step, as I'm not too confident in the use of the terminal, but I'm willing to learn !
many thanks Neal

---

### Post by bab1 on 2012-10-10
> **n.foster said:**
> Hi, I need some help with changing permissions with my newly installed 12.04. I use an sd card via my camera, to load mp3 music for listening through my tv, I know it may sound odd, but it means I have no need for a hi-fi !
Are you trying to listen to the mp3's via a PC?  What errors do you get?  What exactly are you doing at that time?> 

I have tried a few methods including GParted and pysdm, but both ask me to load the 12.04cd at some point, but when the cd is in, I can't get anything to happen.
What will GParted or pysdm do?  To change file permissions using the terminal you can use **chmod**.  The tool **chmod** is part of the basic OS install.> 
The cd was burt in April, and when I did a fresh install of 12.04 last week, I needed half a gig of updates, so I'm thinking I haven't the correct cd the programs are asking for. you will need to talk me through a fix step by step, as I'm not too confident in the use of the terminal, but I'm willing to learn !
many thanks Neal

No need for the CD to change file permissions.  A little better description may be of help though.  :-)

---

### Post by n.foster on 2012-10-10
> **bab1 said:**
> What will GParted or pysdm do?  To change file permissions using the terminal you can use **chmod**.  The tool **chmod** is part of the basic OS instal
I was just following google leads with ref to GParted and pysdm, I saw a thread somewhere about chmod, but I was a little confused by it, not knowing what to enter into he terminal. Is it simple, as I dont want to screw anything up !!

---

### Post by bab1 on 2012-10-10
> **n.foster said:**
> I was just following google leads with ref to GParted and pysdm, I saw a thread somewhere about chmod, but I was a little confused by it, not knowing what to enter into he terminal. Is it simple, as I dont want to screw anything up !!

Lets start at the beginning then.  What is the exact nature of your problem?  It's sufficient to just describe what you are attempting to do and what errors you get when it doesn't work.  Your OP doesn't really describe the problem very well.

---

### Post by n.foster on 2012-10-10
> **bab1 said:**
> Lets start at the beginning then.  What is the exact nature of your problem?  It's sufficient to just describe what you are attempting to do and what errors you get when it doesn't work.  Your OP doesn't really describe the problem very well.

right, when I mount the camera, I can access and view the files on the sd card, but it wont let me change anything, it says that I'm not the owner and I can't change permissions, this is what I need help with, as all I want to do is copy and paste files from the pc to the card. I've tried with the ipod too, same problem there.

---

### Post by bab1 on 2012-10-10
> **n.foster said:**
> right, when I mount the camera, I can access and view the files on the sd card, but it wont let me change anything, it says that I'm not the owner and I can't change permissions, this is what I need help with, as all I want to do is copy and paste files from the pc to the card. I've tried with the ipod too, same problem there.

Do you know where the camera mounts to (i.e. /media/camera)?  I assume you are looking at the files using the GUI (Nautilus).  What version of Ubuntu are we using?

---

### Post by n.foster on 2012-10-10
/media/usb1 !
yes I access the files through the launch bar on the left and I'm using 12.04 precise pangolin

---

### Post by bab1 on 2012-10-10
> **n.foster said:**
> /media/usb1 !
yes I access the files through the launch bar on the left and I'm using 12.04 precise pangolin

Right now I'm on a workstation that is running 10.04 so I have to guess at this.  What happens if you hit ALT+f2.  I think you will get a command launcher.  If you do get a command line, try this```
gksudo nautilus
```... This launches Nautilus as root (admin) and you should be able to change permissions with a right click >> permissions.

---

### Post by n.foster on 2012-10-10
thanks bab1, I've just tried this and changed the permissions to read-write, then when I click the tab to save the changes, they revert back to blank? it seems it's not allowing me to do this.

---

### Post by bab1 on 2012-10-10
> **n.foster said:**
> thanks bab1, I've just tried this and changed the permissions to read-write, then when I click the tab to save the changes, they revert back to blank? it seems it's not allowing me to do this.

That's because the sd card is not formatted as a Linux file system.  If you move the file to your home directory then it can be successfully changed.

You do NOT want to reformat the sd card!  You really don't have to.  Use Nautilus as the user root.  You should be able transfer them as the user root.  

The only way to overcome this is for you to mount the sd card with you designated as the user.  As it stands right now the automount uses root as the owner.

---

### Post by n.foster on 2012-10-10
thanks, it makes some sense when it is explained like that, some files are being copied to the usb now, so I'll let you know if it has worked !
is there a way of changing the automount to a new user?


EDIT: yes it did work! files were transferred ok, many thanks with that bab1 :)

---

