---
title: "Grub problem."
date: 2011-03-15
forum: General Help
---

### Post by Mr. ViC on 2011-03-15
Ok now, whenever I try to boot up Ubuntu (I also have Windows 7 installed), this message pops up:

```
[ Minimal BASH-Like line editing is supported.  For the first word, TAB  lists possible command completions.  Anywhere else TAB lists the  possible completions of a device/filename. ]
```And I know this is all my fault, I have copied my /boot/burg folder to my /boot/grub folder, all of it, everything, and then this comes up.

Now I know Im an a-hole and this is all my fault, but still I need some help here, please.

Anyone?

What can I do now?

---

### Post by Mr. ViC on 2011-03-15
Bumping...

---

### Post by drs305 on 2011-03-15
Please download the boot info script and run it from the LiveCD. Post the contents of the RESULTS.txt so we can see what's where.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Mr. ViC on 2011-03-15
Thanks for replying.

I've ran it, the results.txt are attached in this post.

Thank you!

---

### Post by drs305 on 2011-03-15
Let's try the easy way. At the Grub2 prompt:

```
configfile (hd0,6)/boot/grub/grub.cfg
```
That should call up the menu, see if it will boot from the menu.

---

### Post by Mr. ViC on 2011-03-15
Hi!

Thanks a lot, it has booted up to Ubuntu! :D

But now I restarted and keeps with the same error as above, although the command you told me still works.

Now just need to fix the grub, any idea?

Thanks for helping me out!

---

### Post by drs305 on 2011-03-15
If you haven't already done it, run the following to refresh the contents of grub.cfg:

```
sudo update-grub
```

You have some boot files on sda1, but your main install appears to be sda6. Running the above command will ensure the sda6 grub.cfg file is updated.

---

### Post by Mr. ViC on 2011-03-15
Hi.

I have ran it, but the screen is still apearing at the startup. The command works, and I can see the grub menu.

Now also appears the Windows 7 option (it was not appearing before) so it proves it has refreshed indeed.

But that screen is still apearing... :P

Thank you for your time helping me!

---

### Post by drs305 on 2011-03-15
The first part of your RESULTS.txt shows:
>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #6 for (,msdos6)/**mnt/**boot/grub.

Try reinstalling Grub2 to the MBR while running the OS:
```
sudo grub-install /dev/sda
sudo update-grub
```

If it still isn't working, please rerun the boot info script.

---

### Post by Mr. ViC on 2011-03-15
Hi!

The message finally disappeared, and the grub menu is loading with no problems.

Thank you so much for helping out! :D

---

### Post by garvinrick4 on 2011-03-21
Mr. Vic in upper right under thread tools report as Solved please. Thank you.

---

### Post by Mr. ViC on 2011-03-21
Done. :)

---

### Post by Patrick Tobo on 2012-03-28
Seem to be having a similar problem as this. Have tried to follow the instructions however am having some errors returned. 
Have uploaded my results.txt file called RESULTS(pat).txt.. Please help...

---

