---
title: "Restarting X Server crashes the machine"
date: 2009-12-27
forum: General Help
---

### Post by Sumo74 on 2009-12-27
I was working with my Nvidia driver, trying to set up my HDMI port connection to my t.v. But every time I plug in the HD cable, or restart the X server, it crashes my system, and then won't allow it to log in. I have had to do 3 fresh installs because this, and I cannot figure out what the problem is. 

The last time, it would get to a shell, and it would looked like it would allow me to type out some commands and forcestart X server, but after a few seconds the screen would start blinking (For a lack of a better word), and it would near impossible to type, so does anyone know what the reason could be or a workaround for this?

Oh Yeah, I am running Ubuntu 9.10 on my Acer Aspire 5810TZ, with an Intel Chipset 4 integrated graphics card.

Thanks in advance.

Also to help clear some of what happened up:

I ran this command
/etc/init.d/gdm restart
After which, my system went to the initial Ubuntu screen (White Ubuntu symbol), and then followed by the tty1 screen, then the screen started blinking. It was near impossible to type, since the rhythm was impossible to detect. I had to do a fresh install.

The original problem came from plugging my HD cable from my laptop to my TV. It worked initially, but had some issues, but I exited out of the dual screen, and after a short amount time needed to restart. Did so, and the initial screen showed up, followed by the little underscore cursor, and then it went to a black screen with two white lines at the top. If I let it seat long enough it would finally crash and restart. If I pressed the power button, the screen would go green, and then crash. I had to do a fresh install for that.

Doing a fresh install isn't a big issue for me, I just hate losing all my files, and I would do it than do a partisan, fight through a bunch of crap to get those files, and then try to remove the old version of Ubuntu. So I am hoping you all can help me figure this issue out.

---

### Post by diablo75 on 2009-12-27
Something you can try is from GRUB, select the latest kernel from the menu (Recovery Mode).  This will load up a text based menu and one of the items in the list will let you drop to a terminal.  Type in this command:

```
sudo dpkg-reconfigure xserver-xorg
```

Once that's done, type:

```
sudo init 6
```

That will restart your machine.  Let it boot normally and cross your fingers (I've never messed with HDMI so I couldn't help you with that).  But if I were to take a guess... maybe the video can only be display via your VGA interface (your LCD screen) or the HDMI, but not both at the same time.

---

### Post by Sumo74 on 2009-12-27
> **diablo75 said:**
> Something you can try is from GRUB, select the latest kernel from the menu (Recovery Mode).  This will load up a text based menu and one of the items in the list will let you drop to a terminal.  Type in this command:

```
sudo dpkg-reconfigure xserver-xorg
```Once that's done, type:

```
sudo init 6
```That will restart your machine.  Let it boot normally and cross your fingers (I've never messed with HDMI so I couldn't help you with that).  But if I were to take a guess... maybe the video can only be display via your VGA interface (your LCD screen) or the HDMI, but not both at the same time.


I use to be able to do that with Grub (Pick a recovery mode of my latest kernel), but for some reason, since I do a complete install of Ubuntu, and got rid of Windows (Did it after my first crash because of this) it doesn't bring that option up anymore.  So could I run this from the Terminal? Or do I have to be in a tty1 shell?

---

### Post by Sumo74 on 2009-12-27
Ok I tried that command in terminal, and it did it again. This is my 4th fresh install. But I was able to get to a recovery screen, but it would not start x up. It said that it could not detect the screen, and that the nvidia driver was not installed. So I am stuck once again.

---

### Post by Sumo74 on 2009-12-29
Sorry for the bump, just trying to figure this out, just can't see what could be going wrong.

---

### Post by Sumo74 on 2010-01-02
Ok I am once again stuck, I cannot for the life of me, see what could be going wrong. I have everything installed and working, and then just trying to restart it, stops x from working, it just doesn't make any sense. Has anyone had this happen to them, or know a solution? If I need to explain it in  more detail I can.

---

### Post by bjk03 on 2010-01-02
Why are you using the nvidia driver? I think the Acer 5810 uses a Intel GMA 4500MHD for graphics.

---

### Post by Sumo74 on 2010-01-02
> **bjk03 said:**
> Why are you using the nvidia driver? I think the Acer 5810 uses a Intel GMA 4500MHD for graphics.
 
Good question, I had searched around the google, and somewhere it had said that you can use nvidia for the Intel graphic card, but it looks like that was wrong, what driver do I need? I have tried the System/Administration/Hardware Drivers and I get nothing in return, so if you could point in the right direction and I should be good to go.

---

### Post by bjk03 on 2010-01-02
I think it should be detected out of the box, no configuration required.

---

### Post by Sumo74 on 2010-01-02
> **bjk03 said:**
> I think it should be detected out of the box, no configuration required.

Well I am having problems with it, because if so, then it is the driver for the Intel chip that causing the crashes. It happens right after I plug in the HDMI cable from my laptop to my TV.

Also, my 3D accelerator is not working either, since I had tried to run Compiz, and it wouldn't work. I know it has that, since when I used Windows my Bumptop UI worked, and it needed that.

---

### Post by bjk03 on 2010-01-02
Are you sure its 9.10 that you are using. From what I've read that 9.10 should have no problems with the 4500 (or Intel graphics in general) I know 9.04 has problems with Intel graphics. When you say you have done a "fresh" install, do you mean that you format the drive and start over with the install?

---

### Post by Sumo74 on 2010-01-02
Yes it is 9.10, and yes, when I say fresh install I mean taking the Ubuntu .iso image cd and do a complete reinstall of the OS, or a fresh install. I delete everything from the original OS, and have no partitions, just the two small partitions Ubuntu makes itself.

---

