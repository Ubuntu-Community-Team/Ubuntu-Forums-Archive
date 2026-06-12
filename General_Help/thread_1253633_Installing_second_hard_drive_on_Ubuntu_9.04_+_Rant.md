---
title: "Installing second hard drive on Ubuntu 9.04 + Rant"
date: 2009-08-30
forum: General Help
---

### Post by twistedcain on 2009-08-30
I manage about 80 users and with the distaste for Vista, coming of Windows 7, and the inevitable end of XP, I have been taking a serious look at Ubuntu. I come from a background in Windows since 97 and have tried Linux distros at various times throughout the years and have always left very disappointed. Typically it was the drivers and lack of ease in installing programs. The recent Ubuntu is the best so far for drivers and using the add/remove and wine has made it so much more user friendly. I love how much I have been able to do using only the GUI.

So yesterday I decide to install a second hard drive on Ubuntu. First though, I'll review how I would accomplish this on Windows XP,

1. Install the hard drive.
2. Open the Disk Management Program.
3. Partition and format new drive. Ready to go!

Now Ubuntu,

1. Install new hard drive.

2. Open Partition Editor program.

3. Partition hard drive.

4. Open Storage Device Manager program.

5. Mount new hard drive.

6. Go to use new hard drive, get told that "I am not the owner, and I do not have permissions to use this drive".

7. Look at area directly above the statement and see that everything is grayed out with no possible way to simply change these permissions.

8. Look for GUI program that allows me to somehow change permissions. A program that could simply ask for a password before allowing me to use it, thus creating all the necessary security. This also makes me wonder why this option is available directly under the properties of the drive itself.

9. Go online trying to find out why something that is so incredibly simple to do with a single GUI on Windows is so completely confusing and over complicated in Ubuntu.

10. Find vague solutions directed towards people who already understand the basics of Linux, including opening a terminal/console control box and changing directories and permissions with the replacement of XXXX without actually fully explaining the entire process as though the person trying to learn has no understanding of the Linux file system thus scaring away people looking to migrate away from what seems to be a much less complicated system that doesn't require such draconian methods to do something that by default should be incredibly simple. Are there really people installing a second hard drive on Ubuntu that by default want to be locked out of the hard drive they just installed?

11. Join Ubuntu forum and write long winded rant in hopes that someone will reply with a link to a simple GUI program that allows me to change drive permissions with no more than a prompt asking for my password.

In all seriousness, I just have to ask why? Why did it even get to this point where I find myself signing up for a forum to get help with something that should be so simple. Beyond that, since it doesn't seem to be simple, why isn't there a tutorial explaining this complicated process in human readable language. Specially in a program that boasts itself "Linux for Human Beings" and not "Linux for Human Beings who have previously used Linux and have a good understanding of the file and permission system and know how to modify such things using console commands". /rant

---

### Post by Liolikas on 2009-08-30
If you find Ubuntu install still too hard for you you should follow tutorial with pictures:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by P4man on 2009-08-30
I gotta admit you have a point :)

There are a few gui tools that I think should be included by default, but that aren't, for some reason, maybe to protect some novice users against their own enthusiasm. For instance, to open a folder in nautilus (file manager) as root, you can't do that without a terminal, unless you install the package "nautilus-gksu"; 

```
sudo apt-get install nautilus-gksu
```

or if you really dislike terminals, find it in synaptic package manager (system > administration), and install it from there. That lets you right click a folder or file, and open it as root. Quite handy if you want to modify permissions on something you dont own.

Another one you will probably like is **pysdm**. Its a gui to manage mount points, and probably exactly what you are missing. install same way, as its in the repositories. Or have a look here:

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

That said, dont think the terminal is your enemy. Its not. Once you get used to it (it takes a while), you will find its your best friend. I think all new window converts react the way you do (I did so too!) but after some practice, they discover how fast and easy it is to do things from a terminal. And how universal. It works across different distro's, it works wether you use KDE or Gnome, or whichever obscure window manager. It works in french and chinese versions. It works when the GUI doesnt :D

But yeah, its just not something you can explore the same way as a gui, so there is a learning path, and I agree with you, it would be nice if just about everything could be done without a terminal. And I bet it can, but it does require some extra packages :)

PS: welcome to the forum, and you would have needed that forum account sooner or later anyway :)

---

### Post by scouser73 on 2009-08-30
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by P4man on 2009-08-30
oh one more thing, im not sure you meanwhile grasped: if you add a drive, and format it with partition editor, you run partition editor as root. Therefore, the new partition is owned by root, not by your user. It really is quite logical, but I agree, not very intuitive..

---

