---
title: "no prompt for entry into grub"
date: 2009-12-05
forum: General Help
---

### Post by wpshooter on 2009-12-05
Why is it that there is no count-down prompt for entry into the grub menu when booting the Karmic version of Ubuntu as there was with previous versions of Ubuntu ?

Thanks.

---

### Post by lisati on 2009-12-05
grub has been replaced with grub2. I don't actually use Karmic, but read somewhere in the forums that you need to hold down the shift key when you boot or something of that nature.....

---

### Post by sisco311 on 2009-12-05
If Ubuntu is the only OS, then, by default, the grub menu is hidden. To get into the boot menu, you have to hold down the Shift key during bootup.

[uhelp]community/Grub2[/uhelp]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]
[thread=1195275]The Grub 2 Guide[/thread]

---

### Post by wpshooter on 2009-12-05
> **sisco311 said:**
> If Ubuntu is the only OS, then, by default, the grub menu is hidden. To get into the boot menu, you have to hold down the Shift key during bootup.

[uhelp]community/Grub2[/uhelp]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]
[thread=1195275]The Grub 2 Guide[/thread]

Held down the SHIFT key and nothing happens (i.e. no grub) just continues on with boot !!!

---

### Post by Manyette on 2009-12-05
It may not be what you want, but you can load "startup-manager" in Synaptic, which will allow you to control such things as which kernel to boot and other boot items.

---

### Post by ranch hand on 2009-12-05
Do NOT use Start Up Manager yet.  It is not ready for grub2 yet.  It is getting there.  Give it time.

If you do not know how grub2 works and you screw it with SUM you will be for ever getting it straight.

Read the link in my sig.  It is just an overview but will give you an idea what grub2 does and how.

The first three links at the bottom of my post are great.  The 2nd and 3rd are here on the forums.  A lot of the information is stuff that we worked out in 9.10 testing, starting with Alpha2 when grub2 came on the scene.

Watch out for a lot of the blogs and so forth on the net.  Many of these folks have  never used or even seen grub2.  They do have very nice graphics.

---

### Post by Manyette on 2009-12-06
Hi Ranchhand, Something you said bothers me.  First of all, I'm using startup-manager with Karmic, and it seems to work just fine.  Now the reason I'm using it is because I do NOT get any startup menu when Karmic boots, and from what you said, I should.  The only thing I see on boot is "GRUB LOADING", and then right to the splash screen.  And the ESC key does not allow entry to the menu, as the older version of GRUB did.  So I loaded startup-manager out of desparation, having no other alternative.  I did, as advised, run the sudo update-grub first thing off, but no difference.  So while it is working fine for me I have a couple of questions:

1 - Should I get the old selction menu on boot with GRUB 2?
2 - Should the ESC key allow access to it?

Meanwhile, I"m going to go and follow some of your links and see what info is to be had therein. And as the others said, thanks very much for the post.

---

### Post by akakingess on 2009-12-06
You will find the answers in the links, but no, if Ubuntu is the only OS installed Grub2 goes straight to the login splash screen unlike original Grub, and if you need to see the menu, I believe it is now the Shift key instead of ESC.

---

### Post by ranch hand on 2009-12-06
Try the shift key instead.  I have no idea why they changed this but there it is.

If you want to see the menu all the time (I have one machine with Intrepid on it and nothing else, the menu is NOT hidden - drives me up the wall if it is) go to /etc/default/grub and edit this line;
```

## GRUB_HIDDEN_TIMEOUT=0

``` 
so that it looks like tis one.  The menu will no longer be hidden.

The second line beneath that one is where you set your menu timeout.

All you need to do to do this is run;
```

sudo gedit /etc/default/grub

```

---

### Post by Manyette on 2009-12-06
Hi Akakingess, you are correct, and I should have checked for myself.  The shift key does birng up the menu, although someone earlier said it didn't on their machine, but it does on mine, and works ad "advertised".  I guess I can unload the startup-manager now.  This newbie thanks you sir.

---

### Post by Manyette on 2009-12-06
My thanks to you as well, Ranchand.  Appreciate all the help.

---

