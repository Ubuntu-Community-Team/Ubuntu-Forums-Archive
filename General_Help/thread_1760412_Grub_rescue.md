---
title: "Grub rescue"
date: 2011-05-16
forum: General Help
---

### Post by umwhat on 2011-05-16
so, my friend needed his laptop back for a bit. when he lends it to me again, I try booting up and I get:
"error: unknown filesystem" and then the grub rescue thing.

I tried running sudo grub but it said command not found. then I tried the /sbin/ one. didn't work. Nothing it working. I keep getting errors or being told that only root can do what I want to do.

I know that what i installed ubuntu on was sda7 and the file system type is ext3/ext4. but when I try it I get:
ubuntu@ubuntu:~$ mount /dev/sda7 /mnt
mount: only root can do that

then I try sudo:
ubuntu@ubuntu:~$ sudo mount dev/sda7 /mnt
mount: special device dev/sda7 does not exist

alright, so, apparently, there is no sda7. so i try sda6. same errors.
SO I go lower. SAME errors. What's going on?

---

### Post by umwhat on 2011-05-16
guys, please, help. i'm so frustrated right now, I can't even think straight. 

It looks like sda6 is working now:

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda6
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ 


No idea what's going on here. Not sure what I should do.

---

### Post by ksprasad on 2011-05-16
Try this:
 
~$ sudo grub-install --root-directory=/mnt /dev/sda --force
 
:)
 
note: there is no '6' after 'sda'
 
Regards,
ksprasad

---

### Post by umwhat on 2011-05-16
now I'm getting:
error: symbol not found 'grub_putchar'

after forcing the install it said it installed with no problems.

oh, I put the 6 there. guess I'll try it without it now. wish the boot up from the cd didn't take so long. there's a line of problems about some B43#devicefirmware

---

### Post by umwhat on 2011-05-16
I'm not getting the grub error now, but that screen that shows eveyrhting you can boot up from doesn't come up. It just goes to a black screen with an underscore you can barely see unless you press a key and it makes a loud beeping noise whenever you press a key.

---

### Post by IntentAnalysis on 2011-05-17
I'm a little confused...how do you have a Bash terminal, if you are stuck in Grub Rescue?

---

### Post by umwhat on 2011-05-17
oh, sorry, haha.
I booted from the Live CD.

also, resorted to another partition of Ubuntu, which took about 80gb so I could get GRUB back. Would it be safe to delete that partition now? I was able to get back onto my sda6, so I have no use for the new one.

---

### Post by IntentAnalysis on 2011-05-17
A creative solution ;)  However, if the new partition is where GRUB is installed...perhaps try his command 

```
~$ sudo grub-install --root-directory=/mnt /dev/sda --force
```

in your newly recovered system, and if it works, delete the new partition, and attempt to reboot the computer using the fresh Grub install.  If it fails, you already know of one way out.  I'm going to read up on configuring Grub2...

---

### Post by ksprasad on 2011-05-17
> 
also, resorted to another partition of Ubuntu, which took about 80gb so I could get GRUB back. 

 
:P Good solution.
 
Regards,
ksprasad

---

