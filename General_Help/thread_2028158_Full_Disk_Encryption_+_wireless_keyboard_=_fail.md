---
title: "Full Disk Encryption + wireless keyboard = fail"
date: 2012-07-17
forum: General Help
---

### Post by omgimdrunk on 2012-07-17
I have installed Ubuntu precise with FDE, however my wireless keyboard doesn't work on that screen, luckily I  had a usb keyboard on hand to log in. Once I am in the fully loaded system, my wireless keyboard begins to work.

Is there a trick to get the keyboard working at boot?

Also I noticed that there is an error about no video right before that, might that have something to do with the lack of peripheral resources?

---

### Post by gandalf3 on 2012-07-17
this may have absolutely nothing to do with what your problem is, but then again, it might.
i don't have FDE, and i am assuming you mean the ubuntu login screen (i guess it can't be much else :P)
i have a wireless key board and no trouble at all logging in
is your key board blue tooth? (mine are the kind with the little USB transceiver thing so to the computer it is like a usb keyboard)

---

### Post by omgimdrunk on 2012-07-18
NO, when the disk is encrypted the OS does not boot up until the disk is decrypted, which means it doesn't even go to the logon screen until you enter the password for the disk.

Why would you post to tell me that you do not have the same settings as me and your system works? How is that helpful at all?

---

### Post by 3Miro on 2012-07-18
The wireless/blue-tooth module (i.e. driver) is stored on the encrypted drive and cannot be loaded until you unlock the root partition. On the other hand, you cannot unlock the root partition unless you use the keyboard to type the password.

The solution is to load the wireless module into the ramdisk (initrd) image that is stored on the boot partition. It is just s single command that you have to run, but couple of Google searches didn't give me the command, I am hitting lots of old information. Lets see if anyone knows how to do this and I will try to look for the command myself.

---

### Post by omgimdrunk on 2012-07-18
> **3Miro said:**
> The wireless/blue-tooth module (i.e. driver) is stored on the encrypted drive and cannot be loaded until you unlock the root partition. On the other hand, you cannot unlock the root partition unless you use the keyboard to type the password.

The solution is to load the wireless module into the ramdisk (initrd) image that is stored on the boot partition. It is just s single command that you have to run, but couple of Google searches didn't give me the command, I am hitting lots of old information. Lets see if anyone knows how to do this and I will try to look for the command myself.

Right when you stated ramdisk, you triggered a lost memory, I remember this from the RHCT training, I will have to recompile the kernel with the module and recreate the ramdisk.  I guess it's not a bad think, I was planning on doing this sometime to speed things up a bit.
I am a bit surprised the UBUNTU team hasn't stumbled across this yet.

---

### Post by 3Miro on 2012-07-18
> **omgimdrunk said:**
> Right when you stated ramdisk, you triggered a lost memory, I remember this from the RHCT training, I will have to recompile the kernel with the module and recreate the ramdisk.  I guess it's not a bad think, I was planning on doing this sometime to speed things up a bit.
I am a bit surprised the UBUNTU team hasn't stumbled across this yet.

No, no, no. You don't have to recompile. Of course, you could recompile, but you don't have to.

Since kernel 2.6, drivers are usually compiled as separate modules (as opposed to build into the kernel). The kernel automatically loads the modules that it needs, but there are some modules that are crucial for booting. inidrd takes care of this by allowing you to load modules before anything else has taken place. For example, the module that is needed to load the filesystem of the root partition should be in initrd, otherwise you cannot mount the root partition to load any other modules. What is unique in  your case is that you need a keyboard module to mount the root partition. There is a single command line that will rebuild initrd and you can tell it to include the keyboard module, this will solve the problem without the need for recompiling.

I just don't know the command and I can't seem to find it with Google.

---

### Post by sbywater on 2012-12-16
This is still the case in Ubuntu 12.10.

---

