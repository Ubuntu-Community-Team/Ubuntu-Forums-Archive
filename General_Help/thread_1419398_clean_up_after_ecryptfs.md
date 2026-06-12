---
title: "clean up after ecryptfs"
date: 2010-03-01
forum: General Help
---

### Post by tombaugh on 2010-03-01
Hi all,

First of all I would like to apologize for the fact that I have so little information. I messed up and can't really remember what I did. I was trying to encrypt a folder in my home folder using ecryptfs, and after some unsuccessful attempts (afaik I was supposed to see a new drive mounted) I discovered that I couldn't access any file in my home folder. Of course I panicked, I tried to undo whatever I did, but then the system crashed. Fortunately after rebooting I was able to open my files, and I'm backing them up now. There was an error message right after booting (forgot what, sorry but I was still panicking) and the default view in Nautilus has changed to icon while it should be list view. Apart from that everything appears to be normal. Note that during the whole "event" I did not move any files. Now I would like to clean up, get rid of everything ecryptfs, and make sure that all my data are accessible in the future. I hope someone can give me some advice on that.

So, what did I do? I think I tried something like this first:

```
mkdir /conf
sudo mount -t ecryptfs /conf /conf
```or maybe

```
mkdir /conf
sudo mount -t ecryptfs /home/myname/conf /home/myname/conf
```and because that didn't work I deleted the folder and tried

```
mkdir ~/conf chmod 700 ~/conf
sudo mount -t ecryptfs ~/conf ~/conf
```I used two different passphrases during the two attempts. When trying to mount the folder for the first time I was asked something about "FNEK", and because that was not mentioned in the tutorials I was using I chose the default option (which was a long string of characters). 

After that last attempt nothing in my home folder was readable any more. After rebooting however the conf folder was gone, the files were readable again and my Nautilus settings were messed up. There still is a folder named ECRYPTFS_FNEK_ENCRYPTED.FWaV-[...] in my home folder though.

Many, many thanks in advance...

Edit: Other settings appear to be lost as well, I just started VLC and was asked about album art download policy. Any thoughts on that?

---

