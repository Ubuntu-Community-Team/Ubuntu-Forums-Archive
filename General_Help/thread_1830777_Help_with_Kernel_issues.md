---
title: "Help with Kernel issues"
date: 2011-08-22
forum: General Help
---

### Post by Kduke on 2011-08-22
Hello All,

I haven't been an Ubuntu user for very long, maybe a little over a year now, however, I have finally come across an issue that has me stumped.

The most recent kernel update, to version 2.6.38-11 has been a horror.  It hangs on boot up.  Sometimes I can get to the log in screen, then it hangs there as well.  However, after 3-5 reboots (which is absolutely annoying to do when I just want to use my computer), it sometimes loads up finally.


However, if I go to older Linux version in the Grub menu, then I can select 2.6.38-10 and it runs just fine.

So I am looking for a way to fix this problem, whether it be removing the most recent kernel update, or making 2.6.38-10 boot up by default.

I noticed that the kernels are listed in the synaptic package manager, but I am afraid to remove the most recent one via synaptic.  Is it as simple as removing the Linux version and headers I don't want, or are there other things I need to do in order to make 2.6.38-10 my default kernel at start-up?

Sorry for the long post, I just wanted to be as detailed as possible.  Thanks to everyone who reads this and I look forward to your responses!

---

### Post by Script Warlock on 2011-08-22
you can use startup manager and choose whatever kernel is working on your machine as to avoid also messing with grub.

---

### Post by realzippy on 2011-08-22
```
sudo apt-get remove linux-image-2.6.38-11-generic  linux-headers-2.6.38-11-generic
```

```
sudo update-grub
```

---

### Post by Bobhuber on 2011-08-22
> **Kduke said:**
> Hello All,

I haven't been an Ubuntu user for very long, maybe a little over a year now, however, I have finally come across an issue that has me stumped.

The most recent kernel update, to version 2.6.38-11 has been a horror.  It hangs on boot up.  Sometimes I can get to the log in screen, then it hangs there as well.  However, after 3-5 reboots (which is absolutely annoying to do when I just want to use my computer), it sometimes loads up finally.


However, if I go to older Linux version in the Grub menu, then I can select 2.6.38-10 and it runs just fine.

So I am looking for a way to fix this problem, whether it be removing the most recent kernel update, or making 2.6.38-10 boot up by default.

I noticed that the kernels are listed in the synaptic package manager, but I am afraid to remove the most recent one via synaptic.  Is it as simple as removing the Linux version and headers I don't want, or are there other things I need to do in order to make 2.6.38-10 my default kernel at start-up?

Sorry for the long post, I just wanted to be as detailed as possible.  Thanks to everyone who reads this and I look forward to your responses!
Remove it following the posts and try reinstalling the update without anything running except the update manager. I had the same problem and the second install fixed it. Fsarchiver can be your best friend with Linux if you have the room to store the backup file on an extra partition or drive.

---

### Post by Kduke on 2011-08-23
I tried the above posts.  Firstly, the changing the start-up manager settings seem to be a harmless way to fix the problem, which I am using now.

I tried to un-install the kernel and headers via the above commands, however, I see some strange message about something currently running on the kernel and the computer locked up.  Sorry I did not think to write down the message, it had something to do with my NVIDIA drivers I believe.

After the reboot I tried to un-install them again, however it says the dpkg process was interrupted.  I fixed that error as well.

For now, I will just boot the older kernel via the start-up configuration.  Perhaps I will wait until kernel 3.0 comes out or something.  Thank you everyone for your help.  I will wait to see if there are a few more posts until I mark the thread solved.

---

### Post by recluce on 2011-08-23
Similar issues here with 2.6.38-11 (on Xubuntu 11.04) - configuration of the kernel failed. Thankfully, aptitude rolled back the changes to  a point were the system boots to the 2.6.38-10 kernel by default.

However, removing the broken kernel does not work either, the configuration script crashes with an error. Does anybody check new kernel versions before release?

In any case, I can currently neither remove nor reinstall 2.6.38-11 :(

---

