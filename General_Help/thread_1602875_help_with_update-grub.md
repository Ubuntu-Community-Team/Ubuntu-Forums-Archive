---
title: "help with update-grub"
date: 2010-10-22
forum: General Help
---

### Post by apena81 on 2010-10-22
Ok so i got ubuntu 10.10 to install on sda1, I have windows xp on another drive, sdb. 

I can only get the ubuntu live cd to boot when i select the option "nomodeset" otherwise i get a black screen and my monitor led blinks as if no signal is coming in. 

When i boot from the hard drive, i get the same thing. So i did 

"sudo gedit /etc/default/grub" 

and added this line:

 "GRUB_CMDLINE_LINUX="nomodeset"" 

now i just have to do "sudo update-grub" and/or "sudo update-grub2" but when i do this from the live cd, i get this message: 

"ubuntu@ubuntu:~$ sudo update-grub2
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."

or
"ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."

I believe i have my ubuntu partition mounted, (i did so with this cmd " sudo mount /dev/sda1 /mnt"

Is that how you mount it? 
Can someone help me update this grub file so i can see if it boots up?

Thanks

---

### Post by sikander3786 on 2010-10-22
If it is an Nvidia or ATI graphics card, you don't need to add that parameter permanently. Just install the proprietary graphics card and the problem will go away.

If it is an Intel chipset, go throught the following instructios.

Boot from the hard disk using the 'nomodeset' parameter. From inside Ubuntu (not from the live CD), edit /etc/default/grub and add 'nomodeset' as you mentioned above.

Now from the same session, run

```
sudo update-grub
```

And you'll be good to go. No need to boot off a live cd.

---

