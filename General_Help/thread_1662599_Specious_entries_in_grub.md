---
title: "Specious entries in grub"
date: 2011-01-08
forum: General Help
---

### Post by Thryn on 2011-01-08
I have two problems with grub. Firstly, it detects Vista in /dev/sda1 and thus lists it. This is my recovery partition, and doesn't work if you attempt to start Vista using it... I actually don't have Vista, only Windows 7 (on /dev/sda2) and Ubuntu Lucid. I would like to remove it in such a way that it doesn't reappear the next time I update grub.

Secondly, the last time I removed some kernels (by removing the linux-headers files in Synaptic) they didn't get removed from grub, even after I ran sudo update-grub. I forgot to do this right away and did it after I had restarted the computer the next morning. Might this have anything to do with it? I looked in Synaptic, and the files I removed don't show up as installed. Did I forget a step or something?

I ran sudo update-grub again, and this is the output:
```
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
```I had removed 2.6.32-24 and 2.6.32-25.

I know about Grub Customizer, and I suppose I can use it to hide the erroneous entries, but why would it still detect the kernels? I'm going to try to restart using one of the kernels that I shouldn't have anymore and see what happens.

ETA: Well, at least one of those two works. To prove it, the output of uname -r:
2.6.32-24-generic

And yet it still shows up as uninstalled in Synaptic. How do I remove it if Synaptic doesn't do its job?

---

### Post by drs305 on 2011-01-08
For removing kernels, I find ubuntu-tweak does a good job. Here's a link to removing kernels:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")
If they still show up afterward let us know as G2 can import things from other grub configuration files.

To hide the Vista partition, if you are sure you don't need it, you can modify the /etc/grub.d/30_os-prober script. Here's a guide - it's a bit geeky but Section 8 is very simple. It shows how to hide any partition. Run "sudo update-grub" after making the changes and saving the file.
[Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")

---

### Post by oldfred on 2011-01-08
You will notice in drs305 signature many links to grub2 info that is very useful. But I just brute force the issue, by turning off the osprober and copying the windows entries to 40_custom and editing at will. You could then just not copy the Vista entry. If you ever want to rerun the prober you turn turn it back on.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit title:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by Thryn on 2011-01-08
Thank you drs305, that fixed my problems.

I think I know what I was doing wrong - searching for linux-headers instead of linux-image. And didn't find it in synaptic because I was looking for the wrong thing. D'oh! So, the verdict - my error, not a synaptic error. At least as a result of this I now know that ubuntu-tweak is easier to use (never a bad thing) and I am finally rid of the Vista entry.

Thank you too, oldfred, even though by the time you had posted I had already used drs305's solution. You were both very quick in helping me. :o

---

