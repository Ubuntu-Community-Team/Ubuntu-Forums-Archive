---
title: "Messed up Triple-Boot"
date: 2010-08-17
forum: General Help
---

### Post by pizza-is-good on 2010-08-17
Hello all. Help is needed here quickly.

I have had a dual-boot system running 7 and Ubuntu 10.04 for a while now. I had to install Fedora 13 for a class I'm taking at the college. I decided to make a triple boot system.

The installation went fine, and I am actually using Fedora right now. Here is the problem:

Windows and Fedora I can boot into, but no longer into Ubuntu. When I try to, I get the following error:

```
Error 13: Invalid or unsupported executable format
Press any key to continue...
```Which one is "any key"? (Just kidding. I was adding a bit of humor)

Anayway, so I can now no longer get into Ubuntu, which is bad...:lolflag:
So, I need help. How do I get Ubuntu to work again? I need to be able to get in!

Some info I should mention:

When Fedora installed, it replaced my old grub with a new one with a blue background. Atop the screen it says "GNU GRUB 0.97" I'm not sure if this is GRUB 1 or 2.

Ubuntu is listed as one of the options to boot from, however, there are no Kernel options as before.

If there is anything else you need to know, let me know how to get that info and I'll post it here.

I should note. I don't really like Fedora, not as much as Ubuntu anayway. At least not as much as the nicely working Ubuntu I have.

---

### Post by 101011010010 on 2010-08-17
Hello.
I think one way would be to upgrade to Grub2 in Fedora. You could also downgrade Ubuntu to Grub 0.97.

---

### Post by oldfred on 2010-08-18
You  have grub legacy with Fedora if it is 0.97. It may not support ext4 partitions as Ubuntu added it to Ubuntu's version of old grub with 9.04, but since grub is not maintained others may or may not have added the updates.

You can just reinstall grub2 from Ubuntu's partition to the MBR and it should let you boot everything.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

sudo update-grub

If that does not find Fedora post back. Some others have had issues and there are many solved threads with how to boot Fedora with grub2.

---

### Post by pizza-is-good on 2010-08-18
> **oldfred said:**
> You  have grub legacy with Fedora if it is 0.97. It may not support ext4 partitions as Ubuntu added it to Ubuntu's version of old grub with 9.04, but since grub is not maintained others may or may not have added the updates.

You can just reinstall grub2 from Ubuntu's partition to the MBR and it should let you boot everything.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

sudo update-grub

If that does not find Fedora post back. Some others have had issues and there are many solved threads with how to boot Fedora with grub2.

I will try that and let you know how it goes. Wish me luck.

---

### Post by pizza-is-good on 2010-08-18
OK, I am in the Live CD right now. I just did all the above steps. Will reboot and see if it worked.

BTW```
sudo update-grub
``` did not work. I am guessing that is something I will have to do in Ubuntu once I get in again.

---

### Post by pizza-is-good on 2010-08-18
OK, update here.

Ubuntu is working again. I am back to the same old GRUB I had prior to installing Fedora. That is good.
New problem:
Fedora is not in my list of OSs to boot!

I don't think that is very hard to do, but I have no idea how to go about doing it. I used to be able to edit GRUB 1, but after switching to 2, I never learned how to and forgot how to edit either one.

Any suggestions/tutorials that will get this squared away quickly?

---

### Post by oldfred on 2010-08-18
Did you run the sudo update-grub after booting Ubuntu as that is what finds other operating systems.

If not we have to add a stanza to 40_custom to boot fedora. Some have added a boot stanza  but we have to convert from old grub style to grub2 style. Others have added Fedora's grub to the Fedora partitiion (PBR) rather than the MBR and chainloaded the same way windows is chainloaded.

---

### Post by pizza-is-good on 2010-08-18
> **oldfred said:**
> Did you run the sudo update-grub after booting Ubuntu as that is what finds other operating systems.

No....
I feel ridiculously stupid.](*,)

OK, it works now. Thanks so much oldfred.

Thread is SOLVED.

---

