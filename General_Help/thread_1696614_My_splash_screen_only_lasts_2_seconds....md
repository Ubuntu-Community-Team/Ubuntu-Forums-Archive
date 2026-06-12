---
title: "My splash screen only lasts 2 seconds..."
date: 2011-02-27
forum: General Help
---

### Post by Mr. ViC on 2011-02-27
Hey guys.

So, today I've installed a new splash screen:

```
http://gnome-look.org/content/show.php/AzenisBuntu+plymouth+themes?content=138960
```

And after the burg screen (yes, I have burg installed too) and some other stuff while booting, the splash screen only appears like 2 seconds before the login screen. I can't even enjoy it lol.

Is there any way I can make it last longer?

Thanks.

---

### Post by Frogs Hair on 2011-02-27
If the full animation is running all the way through , I'm not sure you can prolong it.

---

### Post by andymorton on 2011-02-27
> **Mr. ViC said:**
> Hey guys.

So, today I've installed a new splash screen:

```
http://gnome-look.org/content/show.php/AzenisBuntu+plymouth+themes?content=138960
```

And after the burg screen (yes, I have burg installed too) and some other stuff while booting, the splash screen only appears like 2 seconds before the login screen. I can't even enjoy it lol.

Is there any way I can make it last longer?

Thanks.



Put the following commands in to the terminal and it will show for longer. 

sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u

andy :)

P.S. Note that there are spaces between 'sudo and '-s' and 'initramfs' and '-u'.

---

### Post by Mr. ViC on 2011-02-27
No, like, doesn't even complete the animation.

I can watch the splash screen for more time when shutting down ubuntu than when booting up.

andymorton - I'll try that out, thank you.

Edit: Damn that worked just **PERFECT**!

It's awesome now! Thanks a lot Andy! :D

---

### Post by Mithrandir95 on 2011-06-01
> sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -uThanks Andy!!!  Had the same problem, the above worked perfectly.

---

