---
title: "Ubuntu making extra boot log refrences"
date: 2011-02-03
forum: General Help
---

### Post by larry7 on 2011-02-03
Hi,

I have 10.10 64-bit on a Fujitsu T900. the hard drive has windows seven as well (64-bit). The win7 is the orginal from the manufacture. the boot log originally had (in this order): Win7, Windows Vista (about 100 MB not sure why but can't remove), recovery partition. I put ubuntu on after those three. 

   Some times when the computer goes into suspend mode from ubuntu it will not wake up after wards. the only option it to power i down manually. when it comes back up there is now a second reference to ubuntu in the boot log. this has happened several times. there are now four valid references to ubuntu in the boot loader. 

I need to remove three of them, but i'm concerned that removing them will compromise ubuntu. Also I'm not sure where the boo log in windows seven is. any ideas?

Thanks

---

### Post by oldfred on 2011-02-03
When you say boot log do you mean the grub menu that you choose which system to boot?

I do not use hibernate, as it boots pretty quick for me.

If you have multiple kernels in the menu, you can delete older kernels. We typically recommend that you keep two so you have an older working one just incase.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

and another way:
The easiest way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

