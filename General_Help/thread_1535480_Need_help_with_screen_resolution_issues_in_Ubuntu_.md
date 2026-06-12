---
title: "Need help with screen resolution issues in Ubuntu 10.04"
date: 2010-07-20
forum: General Help
---

### Post by thefish123 on 2010-07-20
Hi everyone,

I have been running Ubuntu 10.04 on my laptop just about since it came out.  Prior to that I was running 9.10 on the same laptop. I was so happy with 9.10 I thought I could only be happier with 10.04.  I was wrong!

There are some things about 9.10 that I have *lost* in the transition to 10.04.  These bother me quite a bit so much so that I have repeatedly considered going back to 9.10.  Maybe someone can help me.

Please keep in mind this all worked fine under 9.10 on exactly the same hardware.

1) When I connect the external VGA port on my laptop to my 32” Samsung TV it comes up as a 40” Samsung TV and it is impossible to set the correct resolution.  This makes watching TV over the Internet via my notebook impossible (I used to use [www.casttv.com](www.casttv.com) and others).  I have posted about this problem before here [http://ubuntuforums.org/showthread.php?p=9368705#post9368705](http://ubuntuforums.org/showthread.php?p=9368705#post9368705)

2) I cannot change the resolution on the console (the TTY’s 1 to 6).  It used to come up as standard old fashioned VGA (80 columns by 25 rows of text) but now it is much smaller font and much larger console.  The VGA=### in GRUB does nothing.  And this is the only suggestion I seem to be able to find.  From my reading most people seem to like the large console w/ small font.  I dislike it for the reason I will get into next

3) DOSEMU locks up my computer with a blank screen when running in “super” mode on the console.  Pressing Ctrl+Alt+F# accomplishes nothing and either does Ctrl+Alt+Del .  I have to press and hold the power button forcing a hard shutdown (at least this is the only solution I have found).  I used to run DOSEMU on my console (at the aforementioned 80x25 resolution) with the following ```
sudo dosemu –s
```.  This would launch DOSEMU with full rights and allow me to run WordPerfect 5.1 complete with the graphical “print preview” feature.  I could also run many other ancient graphical DOS applications even including Windows 3.1 and many games.  Running these DOS apps on the console at 80x25 meant these apps all looked “normal” as they were intended.  Now, with the huge console (see point #2) and the DOSEMU crashing I am not having any luck.

So, in short to sum up, I have no TV, tinny font on the console and none of my favorite DOS apps of yore.  Remind me again why I upgraded?

Best regards,
The Fish

---

### Post by theOGRE on 2010-07-25
I'm sure somebody can help you out with this. All I can offer is a bump:)
I still use Hardy because there are too many things that don't work for me on this comp with new ubuntu's. I'll have to configure it all soon enough though, as Hardy won't be supported soon. Hope you find help.

---

### Post by prodigy_ on 2010-07-25
> **thefish123 said:**
> 2) I cannot change the resolution on the console (the TTY&#8217;s 1 to 6).
Try [this HOWTO](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml). It's very detailed and worked perfectly for me everywhere, including VMWare setups.

Note that 1280x1024 isn't the only possible option. You can get the list of resolutions that your video card supports with **vbeinfo** command in Grub2 command shell. (Press "C" when in Grub2 boot menu to enter the command shell.) 640x480 and 800x600 are almost guaranteed to be supported so you can try one of those.

---

### Post by thefish123 on 2010-07-27
> **prodigy_ said:**
> Try [this HOWTO](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml). It's very detailed and worked perfectly for me everywhere, including VMWare setups.

Note that 1280x1024 isn't the only possible option. You can get the list of resolutions that your video card supports with **vbeinfo** command in Grub2 command shell. (Press "C" when in Grub2 boot menu to enter the command shell.) 640x480 and 800x600 are almost guaranteed to be supported so you can try one of those.Thanks prodigy, I will give that a try this evening...  I will let you know how it works out for me.

The Fish

---

