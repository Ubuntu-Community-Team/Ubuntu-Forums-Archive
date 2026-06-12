---
title: "Deleted Grub Files"
date: 2010-07-29
forum: General Help
---

### Post by zylvere on 2010-07-29
Hello all! 

I was trying to get a TGA splash screen to work on GRUB2 and after spending a few hours on all of the config files and not having much to show for it, I decided to begin anew. 

Everytime I typed "update-grub", it reloaded all of the images, so I assumed it was re-probing something. 

**Long story short:** I deleted all of the grub config files and reinstalled the packages so that I could begin anew.

I haven't restarted the computer and I think that's a good thing because I still have all of the mount tables loaded with UUID's but I imagine that I wouldn't need to use the Live CD, because my computer is still running. 

Am I hurtin' for certain?  :D

Many thanks for your attention!

---

### Post by john newbuntu on 2010-07-30
drs305 explains about setting up splash images in section #8 of this post titled "Grub 2 Splash Images & Theming".  Follow this to set up your splash screen depending on the version of GRUB2 you have(There are subtle differences depending on the version of grub).
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You can check the version of grub using "sudo grub-install -v" in a terminal.

You mentioned you have deleted all config files which is not a good idea.  Remember that you do not need to alter the grub.cfg file in GRUB2 as it is automatically generated.  But I am not certain if reinstalling the grub packages restored the grub.cfg file in /boot/grub directory. Otherwise, you will end up at a grub-rescue prompt when you boot up.  So, once you modify your theme, please run "sudo update-grub" once and you are good to go.

---

### Post by zylvere on 2010-07-30
No place to brag, but my removal of grub was thorough: after removing the packages, I deleted /etc/defaults/grub, /etc/grub.d/ and /boot/grub/. So update-grub doesn't have anything to work with, it's basically an empty file. 

Because of the reason you mentioned - the varying versions of grub2 - I had changed the background options in many files and one of them was preventing the whole thing from working. 

Anyway, thanks for your answers and I'll see if I can find the answers by doing some real work.

---

### Post by zylvere on 2010-07-30
Ok, I just ran 'update-grub' and it rebuilt all of the images, just like I had hoped it would last night.

Here is what I had to do to fix it: 

First, when I deleted the "/etc/grub.d/" dir, it wasn't replaced when reinstalling the necessary packages. So I went to [this]("http://www.linuxfromscratch.org/hints/downloads/files/grub2.txt") page and rebuilt the binaries and installed it according to the easy-to-follow instructions. But the grub-install wouldn't work. 

After that, I reinstalled the "grub-pc" package, ran "make-install /dev/sda" and then ran a quick "update-grub". I'm not sure if my pc will restart, but I definitely got back to the point where I was last night, but with clean binaries. 


Now to try these wallpapers again!

:D

---

### Post by zylvere on 2010-07-30
One last question - 

After reinstalling everything, my **05_debian_theme** file has vanished! 

I tried to find one online, to no avail.

Where does this file come from? Is it possible to replace? 

Many thanks!

---

### Post by john newbuntu on 2010-07-31
Those files are a part of the grub-common package.  The main GRUB2 package is grub-pc.  However, the *grub-common* package also gets installed along with this.

Now, mind you, I have not tried this, but what you could experiment with is to rename /etc/grub.d to something else and then re-install both the grub-pc and grub-common packages to see if /etc/grub.d gets rebuilt.
Finally, just to be safe, you can run a "sudo dpkg-reconfigure grub-pc" to reconfigure GRUB2.

---

