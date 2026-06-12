---
title: "Two ubuntu options on grub"
date: 2010-08-11
forum: General Help
---

### Post by Admiral Yi on 2010-08-11
Hi,
After installing updates, I noticed I have two boot options for ubuntu on the grub menu, as well as two reovery options and windows. A little more digging and I found that I have two linux images in /boot, initrd.img-2.6.32-22-generic-pae and initrd.img-2.6.32-24-generic-pae. Running update-grub now looks like this:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found Microsoft Windows XP Professional on /dev/sda1
done

```

Is it safe to delete the older image (I'm assuming that's the one ending in 22) and will this get rid of the second option? Or do I have to do something else? This used to be so much simpler in Grub Legacy

---

### Post by r_s on 2010-08-11
you can use synaptic package manager to remove the older kernel image, however it is recommended to keep a previous kernel image, to be able to choose if something goes wrong with the latest one.

---

### Post by Admiral Yi on 2010-08-11
Ah ok. 

However I would still like to remove it from the grub options. If something goes wrong I can always boot from the live cd and put it back on. How would I go about doing that?

---

### Post by themusicalduck on 2010-08-11
There is a feature in Ubuntu Tweak for removing old kernels too - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

makes it a little bit easier than using synaptic.

---

### Post by r_s on 2010-08-11
you can also manually edit the grub.cfg file, and comment the entries you would not like to be seen in grub.

---

### Post by Admiral Yi on 2010-08-11
@themusicalduck

Ah, thanks. I already have ubuntu tweak, but I never noticed that before.

@r_s

I thought you weren't meant to edit that file in grub 2?

---

### Post by r_s on 2010-08-11
> **Admiral Yi said:**
> 
I thought you weren't meant to edit that file in grub 2?

If you know what you're doing there's no harm , so if you are familiar with that file you can edit it.

---

### Post by Admiral Yi on 2010-08-11
From the grub 2 page on ubuntu wiki:

> Entries should be removed by editing or removing files in the /etc/grub.d folder. The /boot/grub/grub.cfg file is read-only and should not normally be edited directly. 

In grub 2 the config file is built every time you run update-grub and changes accordingly. Your not meant to make the changes yourself. Personally I think that's overly complicated. Grub legacy was much simpler.

---

### Post by TygerTung on 2010-08-11
It is quite handy to have an old kernel there in case an updated one craps out.

This happened to me once, I did a update, and the new updated kernel didn't work, so I just used the previous one until the new distribution came out.

---

### Post by r_s on 2010-08-11
No, grub2 eases the way you do things, for example to add other entries to your grub list,  just add your custom entries to 40_custom file, and run update-grub. In this way a normal user will not alter the grub.cfg file , while in grub legacy you had to manually edit menu.lst to add entries, a slight error could have caused you to go into grub rescue command prompt.

---

