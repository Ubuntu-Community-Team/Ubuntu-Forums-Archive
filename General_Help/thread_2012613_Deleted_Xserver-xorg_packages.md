---
title: "Deleted Xserver-xorg packages"
date: 2012-06-29
forum: General Help
---

### Post by JiuJitsu500 on 2012-06-29
Hello all, I ran into a huge problem I thought Ubuntu was smart enough to figure out (but alas, it's simply smarter than me.... hehe.)

Anywho, I screwed up and deleted all of the xserver-xorg-video-XXX drivers one one computer (exceot the intel one) to ensure acceleration properly for it, which worked like a charm.

However, moving onto MY laptop, with an Nvidia 560M, I deleted all of them since I have the proprietary driver installed through jockey-gtk. STUPID MOVE!!!

I then rebooted into a low-graphics only, and cannot get networking to work (hangs after trying to load bluetooth, since I have no bluetooth). So, I tried manually downloading the packages again on another laptop, moving to my desktop, using "cd" and "dpkg -i" to install the Intel one, and met with failure again (install worked, problem fix fail). Then, I re-installed nouveau (after checking the log file) but it met with error.... something about the version. SO, I moved on to bigger and better things I thought, and blacklisted every single driver that comes with precise in the modprobe.d/blacklist.conf.

I have also updated initramfs every single time I did anything (in recovery), and STILL cannot simply let Nvidia alone load, and let NO other drivers load. OR, install whichever minimal drivers I need (intel is all I have minus the nvidia-current). I have also ran "dpkg-reconfigure xserver-xorg" in recovery to no avail.

So, since this is going to be something I completely overlooked, and be an incredibly simple answer I hope, can someone help me get this thing to boot back into my normal GUI? I have windows and Mac too, but come on..... hehe.

Thanks in advance again guys!

---

### Post by JiuJitsu500 on 2012-06-29
hello again,

an hour later nearly, and I am still lost. I cannot find the proper nouveau driver, I haven't un-blacklisted anything yet... but I'm working on the solution.

This probably won't help anyone else either, I'm sorry to say, this was a stupid mistake on my part.

In any even, thanks again in advance.

---

### Post by Frogs Hair on 2012-06-29
do you have a desktop in low graphics mode ? If you do and have  the synaptic package manager installed the Xorg packages can be installed from there. Only you would know what packages you removed. Re-installing the Ubuntu desktop may be another option, but you may need to resolve the blacklist issue first.```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by JiuJitsu500 on 2012-06-30
Thanks frog, I like the re-install idea, but the problem is that when I say I can get into low-graphics mode, that's just what the computer says. 

The "fallback graphics" fails to load, and thus, it hangs un virtually any circumstance. I cannot get into anything graphical, and no console login at all. The ONLY thing I have is a recovery root terminal.

IF though, I knew how to log into my network through that, I could re-install ubuntu-desktop. The problem is, even in recovery, because I have no bluetooth, I seem to be unable to turn networking on with the option available. It hangs as it tries to load bluetooth. Sooooo.... I'm still completely at a loss.

I've re-installed fbdev, nouveau, vesa, and intel now (nv being impossible to find since it went obsolete), and un-blacklisted everything in modprobe.d/blacklist.conf... AND I've updated initramfs and ran dpkg-reconfigure xserver-xorg..... the last command giving no options at all.

So, any other way to reconfigure this? Is there a file I can manually edit through a Live CD or through a text-based editor (remember, no networking at all through recovery) to take nouveau, intel, and everything else OFF the list of boot (or configure ONE to be a fallback, since I have an i7, say, intel)???

xserver-xorg-video-XXXX..... does NOT play around hehe.

---

### Post by Frogs Hair on 2012-06-30
When I have been in low graphics mode my resolution is just way off, but that is different than your situation.

You could try installing drivers or  the reinstall command from TTY which is a different run level. Ctrl + Alt + F1 > user name > password > command

After the install commands runs and the user name appears run the following and hope for the best. ```
sudo reboot
```

If there is nothing important stored on Ubuntu a clean installation over the the current installation may be quicker. No doubt you will lean something by trying to repair the current installation.

---

