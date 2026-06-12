---
title: "On Boot I Have 2 options For Lunix"
date: 2010-02-28
forum: General Help
---

### Post by emagine on 2010-02-28
Hello,

You can see with the attached image, but basically I have the option to boot in two different Linux Os's with (I think) different kernal versions.  Is this normal, or is their a way to get rid of the older version.  Both are exactly the same when I boot into them, they bot contain all my programs and files.

---

### Post by oldos2er on 2010-02-28
Perfectly normal. Kernel updates never remove older kernels, just in case there's a problem. You can use Synaptic or apt-get to uninstall the older kernel, if you wish. ```
sudo apt-get remove linux-image-2.6.31-14-generic
```

---

### Post by spiky001 on 2010-02-28
This is normal when the next kernel upgrade you will get 2 more, you can remove them but it is best to keep the last working version incase something gose wrong with new 1 you can go in on the old version, whenit upgrades come back ask again or you might findout if you are in the forums alot

---

### Post by emagine on 2010-02-28
Ok, sweet.  Thanks guys.  But does it take up extra space on the hard drive and how is the kernal updated?  Is it just done through update manager or must I do it manually?

---

### Post by r_s on 2010-02-28
yes the older kernels take up space and it is a good method to free up some space, however you can always have two most recent kernels so that you are not doomed if anything goes wrong with one.

---

### Post by oldos2er on 2010-02-28
Kernels are fairly small, <4MB.

---

### Post by spiky001 on 2010-02-28
yes they are updated with update manager

---

### Post by blair on 2010-02-28
What you are seeing is called the grub menu. Both are displayed because GRUB is finding two kernels on your hard drive, the original and the one resulting from an automatic system update. The most recent one is displayed first by default.  

Contents of this display are controlled by the /boot/grub/menu.lst file. If you open that file you will see separate sections for each entry in the list on this display. To hide the older entries in the list when your PC boots up (note this is not the same as actually removing the older kernel from your PC) open the menu.lst file as root:

sudo gedit /boot/grub/menu.lst

Scroll to the bottom of this file. You will see multiple sections with the same sequence of commands:

title
uuid
kernel
initd

and possibly other commands.  Each of these blocks/sections corresponds to one entry in the Grub menu.

By putting the comment symbol (#) in front of each line in a section you are telling grub to ignore that. If it ignores a section, it will not display it. You could also simply delete the entire section which of course will result in it not being displayed. 

Be careful what you do in menu.lst as you could break your boot up process.

---

### Post by oldos2er on 2010-02-28
> **blair said:**
> Contents of this display are controlled by the /boot/grub/menu.lst file. 

 A fresh install of 9.10 uses grub2, which no longer uses menu.lst. Grub2 options are controlled by /etc/default/grub, and files in /etc/grub.d/

---

### Post by clarkec321 on 2010-03-09
I've got the same issue, and after another recent update it has started to get even more unwieldy. And It altered my default boot from Win7 to Mem test

---

