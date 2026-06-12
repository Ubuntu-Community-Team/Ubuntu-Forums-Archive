---
title: "Kernel 3.1.0 + Nvidia! HELP."
date: 2011-08-16
forum: General Help
---

### Post by SolidarityK on 2011-08-16
Well, recently I updated the kernel in 11.04 to 3.1.0. During dpkg time it stated problems with Nvidia! I didn't think much of it until I rebooted the system. Now I have had to unplug the card and reverted to intel crap again! 

Does anyone know what I can do to resolve this? Thank you.

---

### Post by tredegar on 2011-08-16
So far as I am aware, ubuntu is not supporting the 3.x kernel with current releases yet.

So if you install a 3.x kernel, bug-fixing is your problem, not theirs, or ours.

I have installed kernels > ubuntu's releases (but still 2.x) on 10.04LTS, and they have worked, with a bit of tweaking, but YMMV.

If the 3.x kernel does not work for you (and you are not prepared to fix it), then you can revert to a previous version of the 2.x kernel at your grub boot screen.

It should continue to work, although you may need to re-install the NVIDIA drivers for your running kernel, depending on how you installed them in the first place.

I expect you'll be able to work it out.

Good luck.

---

### Post by mylittletom on 2011-08-18
My Ubuntu Natty runs with kernel 3.1-RC2 by recompiling  and nvidia-current 280.13 .  I've got a minor problem with dpkg  ( "dpkg:error processing nvidia-current")  when running "sudo apt-get upgrade" .  The rest (suspend/resume/hibernate ...) runs well.  

If you don't mind that bug, then go to NVIDIA website , select your card model and follow their instructions

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Good luck !

---

### Post by scatha on 2011-10-05
I'm now running the new NVIDIA driver 285.05.09 with the Kernel 3.1.0-rc-7-3
works well!... .. it's openSUSE 12.1 Beta but should be applicable for Ubuntu, too - of course at this stage we cannot expect kernel modules, so we need a re-install after each kernel update

---

