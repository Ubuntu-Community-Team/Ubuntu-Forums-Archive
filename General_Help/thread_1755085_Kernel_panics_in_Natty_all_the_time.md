---
title: "Kernel panics in Natty all the time"
date: 2011-05-10
forum: General Help
---

### Post by chocolatecake on 2011-05-10
Hi, I have been a happy Ubuntu and other distros user from 2007 to now. Had my old 7.10 Gutsy Gibbon (Ubuntu Studio actually) that I really felt was time to upgrade. Then I downloaded the ISO image for 11.04 Natty Narwhal past 4 day ago. It gave me an option to install on my old 7.10, upgrading it, then I chose that one not to have to lose my data.

At the very end of the installation (when downloading several packages from the net) I got a kernel panic. 
After that I reinstalled from zero wiping the whole partition, with the same results. It only worked when I disconnected the net cable so it wouldn't download anything during install.
Then I could run the 11.04, but kept getting kernel panics, and after some testings (I thought it was the nvidia video drivers at first) I think it happens after some ammount of network traffic happens.

Memtest went normal, I tried logging with no-effects and I tried some solutions from forums with no results. The pc can be on and working for hours, but after I start surfing the web for some time, I get a freeze.
Sometimes Caps Lock and Scroll Lock leds are flashing, and sometimes just freezes to simply become unresponsive. When it was during the installation I got a message saying it would pop out into console because panic occured and then froze. Anyway I always have to press the reset button.

I would like to be sure if I have some of my hardware broken or if the newest kernel is still green on some hardware support; maybe network.
I'd also like to know if I can install older versions of the kernel; I think that should fix the problem because other distros worked perfectly here before.
I also heard about some kernel-image-pae being different from the ordinary kernel image. Could it help if I change that package?
Any help is appreciated. I'm waiting to install 11.04 in my wife's computer also but of course I don't want to bring any problems on her!

My net card is Nvidia Nforce and my processor is AMD Athlon II X2 with a GForce 9400 for video card
Thanks and sorry for the verbose post!

---

### Post by TheNerdAL on 2011-05-10
Upgrading from a really old version to the newest one isn't recommended. Try to do a fresh install, but backup your files first.

---

### Post by chocolatecake on 2011-05-10
Is what I already did. Twice. It says so in the post (yes it's a little long, I know)

---

### Post by Hedgehog1 on 2011-05-11
chocolatecake,

Might I suggest that you select 10.04.02 LTS as your next Ubuntu distro?  Natty is fun and all, but I think that the stability of the Long Term Support version might be better suited to your hardware (and to your personal 'style').

I would expect the the Kernel Panics will stop for you after a clean install of 10.04.02 on your existing hardware.

***The Hedge***

:KS

---

### Post by chocolatecake on 2011-05-12
That's exactly what I was considering, though this [ 176-pages-long thread about freezes in lucid]("http://ubuntuforums.org/showthread.php?t=1478787&highlight=kernel+panic") didn't make me too comfortable. Anyway I'm just about to burn the ISO and install 10.04.02. It's true it should be more stable. This is not the first time I installed Ubuntu, or other  distros, or different releases, in different hardware and it's the first time I get a kernel panic failure

---

