---
title: "How to Recover grub2"
date: 2010-05-27
forum: General Help
---

### Post by dynamics on 2010-05-27
Friends,
Once again an update broke my Lucid :-(
When I start my laptop, I can't see the options to choose a kernal or Windows as I used to see before. I know my grub is deleted or overwritten after recent automatic update (on 27th May 10). 
Now I have a bootable 10.04 CD.
Please let me know how to recover the grub2. I don't want to reinstall my linux or windows. 
Thanks in advance.
Sometimes Ubuntu updates are annoying :mad:

---

### Post by philinux on 2010-05-27
chroot.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by wojox on 2010-05-27
Just reinstall Grub2 from a LiveCD [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by dynamics on 2010-05-27
Thanks,
One quick question....
Right now I inserted 10.04 CD and chose Try Ubuntu.....
The CD drive was busy since last 20 mins or so and now suddenly its quit.....
A blank screen......
What to do...... Even the live CD sucked?

---

### Post by dynamics on 2010-05-27
OK!
Finally I recovered the grub.........!!!!!

VERY IMPORTANT NOTE: Do not try this unless you know clearly in which partition your root, home and windows are :-(

1. Download Ubuntu image 
2. Download unetbootin-windows to create bootable image
3. Run unetbootin-windows and choose Defaut --> ISO --> browse the downloaded image and Run. Your bootable USB is ready
4. Start the system and boot from USB (Choose Default)
5. Immediately the Ubuntu desktop appears. Now open the terminal and do the following
 i.   $ sudo i
 ii.  $ mkdir /media/root
 iii. $ mount /dev/(your root partition) /media/root
            Note: Be cautious to mount your correct root partition (test one by one like **sda2 **or **sda5 **or **sda6**). 
iv. $   sudo grub-install --root-directory=/media/root /dev/sda

6. Reboot the system.

Try this @ your own risk. It worked for me.

---

### Post by dcstar on 2010-05-27
> **dynamics said:**
> OK!
Finally I recovered the grub.........!!!!!
.........
Try this @ your own risk. It worked for me.

So this thread is Solved, is it?

---

