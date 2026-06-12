---
title: "burg help"
date: 2011-08-16
forum: General Help
---

### Post by LatinaLover93 on 2011-08-16
when i boot my laptop, burg shows the same thing two times, as shown below
[IMG]http://i640.photobucket.com/albums/uu128/anthonypage93/Screenshot-1.png[/IMG]
does anybody know how i get rid of the extra two?

---

### Post by drs305 on 2011-08-16
I can't speak directly regarding BURG, since I don't use it, but it appears your menu is displaying multiple kernels for the same OS, as well as their associated recovery modes. 

Each time a new kernel is introduced it is added to the menu, and the older ones remain as well. The menu grows accordingly. 

There are tools you can use to hide the older kernels, although I don't know how they interact with BURG. The tools include Ubuntu Tweak and Grub Customizer. The former can actually remove older kernels from your machine (so they won't appear in your menu). Keep at least one older kernel you know works. Grub Customizer, if it works with BURG, would simply remove the kernels you select from appearing in the menu, even though they are still on your machine.

The recovery mode being displayed is controlled in GRUB with the /etc/default/grub file. BURG probably uses a /etc/default/burg file. If you don't want to see the 'Recovery' mode options, you would remove the # symbol from the start of BURG's equivalent of GRUB_DISABLE_RECOVERY="true"
Then update burg for the change to take effect.

The "Rm Kernel" and "Customizer" links in my signature line will tell you more about the two apps I mentioned.

---

### Post by LatinaLover93 on 2011-08-16
your tools should work, since burg uses grub to function, ill find out now though

---

### Post by LatinaLover93 on 2011-08-16
and for a quick fix, come to find out all i needed to do is press f while burg was open to hide the older kernels, but your tools did work. so problem solved either way

---

