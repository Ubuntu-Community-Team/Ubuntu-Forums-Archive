---
title: "does wubi slow down ubuntu in any way ?"
date: 2010-01-19
forum: General Help
---

### Post by starcraftmaster on 2010-01-19
does it ? i heard it will be a slower install

is this all ?

---

### Post by tuddy666 on 2010-01-19
I don't think it slows down Ubuntu. It might install a little slower, but it's still like trying out a "proper" install otherwise. But, everything's easier to remove if you decide you don't like Ubuntu.

But, don't quote me for it, I'm just going on assumptions from the... one time I tried it on a friend's PC.

---

### Post by starcraftmaster on 2010-01-19
Ah well it may be better to get info from some one that knows it will be slower  , just to make sure

---

### Post by mk1w86 on 2010-01-19
As far as I know there will be a slight performance decrease because you are running it from a Windows partition.

If you are asking this question because you are thinking of installing Ubuntu using Wubi I would strongly advise you not to if you are using Ubuntu 9.10 becuase there have been a lot of problem/bugs with Wubi installs.  You would be much better off dual booting properly by installing Ubuntu on its own partition. ;)

---

### Post by wojox on 2010-01-19
You probably won't notice a difference in performance since it actually runs as a Windows application.

---

### Post by mcduck on 2010-01-19
There's a small performance decrease in all reads and writes from the disk, caused by having to work through two file systems (both Windows and Linux).

But that's quite small, you might not really notice it in normal use, only when handling large files (or great amounts of small files).

Apart from that the performance is exactly the same, since even when installed through Wubi you never actually run both operating systems at the same time. Windows isn't running when you boot to Ubuntu. So it definitely doesn't actually *run* as a windows application unlike the above post claims. It's just *installed* as windows application so that you dont have to manually remove the file that contains Ubuntu filesystem if you want to uninstall.

Still, I',m not a great fan of Wubi, it can cause some problems, as the installer and the whole method of installing inside a file on a Windows partition is not nearly as mature as normal installs are, and in case Windows breaks your Ubuntu will be broken as well. You'd just loose many of the benefits of having a dual-boot setup (or running just Ubuntu) without getting any other benefits than not having to create a separate partition for Ubuntu. So use the Live-CD for testing if Ubuntu works for you, install it on external drive or thumb drive if you don't want to mess with your partition layout, and otherwise just make a normal install for best results. :)

---

### Post by starcraftmaster on 2010-01-19
oh i had ubuntu before

just i been having resolution problems and thought i would just try it this way because it seemed much easier

and when i had to get rid of ubuntu (because i could not fix the res problems) i deleted the ubuntu parition which caused windows xp not to boot no more !!!!!!!!!!!!

---

### Post by madscientist032 on 2010-02-13
9.10 installed via wubi works fine for me. The only noticable problems I have is that when Compiz is enabled, opening fullscreen programs (I like Firefox maximized) will slow my machine down for a couple of seconds, and then once the window is ready, everything goes back to the regular speed. It's probably due to the "fade in" effect that Compiz uses when apps are opened. (I'm surprised that the 'wobbly windows' effect isn't sluggish in wubi.)

The only way to really tell is to use a benchmarking software (I used Geekbench) in both a Wubi install as well as in a native, dual-boot configuration. 

And unlike a dual-boot partition, wubi won't let you see the rest of the contents on the hard drive that it was installed to. Then again, wubi was designed to have Windows users test out Linux without fear of breaking their machines. :P

---

