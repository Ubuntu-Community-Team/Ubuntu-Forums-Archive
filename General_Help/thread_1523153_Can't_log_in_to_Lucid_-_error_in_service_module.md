---
title: "Can't log in to Lucid - error in service module"
date: 2010-07-03
forum: General Help
---

### Post by Jamesss on 2010-07-03
I recently installed 10.04 with a realtime kernel and after running some upgrades I can now no longer log in. It was previously set to automatically log in, now I get to the log in screen, click on Automatic Login and it says: Unable to open session. If I click my username and then enter my password it says the same thing. I can ctl-alt-F1 to the CLI and if I then enter username and password I get:

```
Last Login: Sat Jul  3 12:24:51 BST 2010 on tty1
Linux james-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation: https://help.ubuntu.com

0 packages can be updated
0 updates are security updates


Error in service module

Ubuntu 10.04 LTS james-laptop tty1

james-laptop login:
```

I have already booted to the live cd to change the kernel back to 2.6.32-23-generic and the problem is the same. 

I can't post the output of any commands, as I can't login!!

---

### Post by excalq on 2010-09-24
Did you find a resolution to this issue? We're now seeing the same issue.

---

### Post by Jamesss on 2010-09-25
No, I'm afraid not. I went back to using Hardy. This was on a 1.6Ghz 500MB Compaq NC6000 laptop in case this helps anyone...

---

### Post by cossins71 on 2010-11-27
Hi,
  I am also having this problem on 10.04 netbook. All of a sudden I cannot logon and if I try to do so from the terminal it gives me the "error in service module". 
  Also I have tried grub as a way of looking at my disk partitioing and as i only have ubuntu on the laptop it automatically jumps away from grub to booting, is there a way to stop this?
  Does anyone have a solution to the "error in service module" issue as I am in bolivia on holiday and need to dump my photos onto my laptop.
 
Many thanks
 
Ben

---

