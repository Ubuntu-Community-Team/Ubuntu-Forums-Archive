---
title: "Configuring BURG"
date: 2010-06-19
forum: General Help
---

### Post by Hman242 on 2010-06-19
I've just installed BURG-PC through Synaptic to use as my boot load, but I have no idea how to set it up. I've always had GRUB, which was automatically set up on my Ubuntu install. I have a window open called Debconf that opened automatically that is asking me to configure BURG. It has to entry areas. One, which is blank, label as "Linux Command Line" and another, which already has "quiet splash" in it, is labeled as Linux default Command Line.

Could anyone tell me what I need to enter and help walk me through the configuration? Thanks.

---

### Post by ronnielsen1 on 2010-06-19
Did you install the repository and themes as in the following site

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

---

### Post by ronnielsen1 on 2010-06-19
Ok, reread your post. Choose the default. After you setup everything and reboot your pc, click t to change themes

---

### Post by Hman242 on 2010-06-19
EDIT: Looks like I was able to get it up and running. The only problem is that pressing "t" doesn't bring up a theme list like it should.
EDIT 2: I didn't even install burg-themes from Synaptic, so that would probably be why...

---

### Post by ronnielsen1 on 2010-06-19
And you DID do this? 
> sudo apt-get install burg burg-themes If you did, then read through the web site again making sure you didn't miss something like sudo update-burg. Same site I used> EDIT 2: I didn't even install burg-themes from Synaptic, so that would  probably be why...ok

see if you can figure out how to change icons. I couldn't

---

### Post by Hman242 on 2010-06-19
I see that there is a BURG and GRUB file in ```
/boot
```
When I update BURG, it says it is updating grub.cfg. Does this mean I can still edit the menu in BURG by editing ```
/boot/GRUB/grub.cfg
```

---

### Post by Hman242 on 2010-06-19
While we're on that subject, I would like to ask how I would I could edit the men in BURG. I have four current entries.
```
Ubuntu
Ubuntu(Recovery Mode)
Windows 7
Vista Loader
```
How could I make it so I only have Ubuntu and Windows 7 in the menu?

---

### Post by ronnielsen1 on 2010-06-20
I think grub2 is still in charge, it just has a new shirt on. I used to modify grub frequently trying out different distros but I get lost on grub2 and haven't figured it out yet. With grub it would be a simple matter of editing /boot/grub/menu.lst

---

### Post by ssaint04 on 2010-06-20
> **Hman242 said:**
> While we're on that subject, I would like to ask how I would I could edit the men in BURG. I have four current entries.
```
Ubuntu
Ubuntu(Recovery Mode)
Windows 7
Vista Loader
```
How could I make it so I only have Ubuntu and Windows 7 in the menu?

BURG configures a lot like GRUB2.

Here's the basics: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Check out this thread for renaming, and hiding certain things: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Just replace "GRUB" with "BURG" anywhere it occurs (I.E.: "grub.d" becomes "burg.d")

---

### Post by qwerty2009 on 2010-06-20
I think you just press f at the burg screen 

R = Resolution
T = Themes
I = Information
F = Menu Entries

---

### Post by ronnielsen1 on 2010-06-20
> R = Resolution
T = Themes
I = Information
F = Menu Entries

Thank you. Somehow I missed that

---

### Post by Hman242 on 2010-06-20
Pressing F only removes the Ubuntu Recovery entry. Pressing it again brings that entry back. The GRUB tuts aren't really transitioning over either, but there was one thing that helped me. I just removed the entries from burg.cfg and it's working fine now.

---

