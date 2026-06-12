---
title: "High IOWait making Ubuntu unusable"
date: 2010-01-22
forum: General Help
---

### Post by Charamei on 2010-01-22
I am disk-caddying between Karmic and XP on a box with the following stats (taken from XP since Ubuntu will barely respond):

AMD Athlon 64 X2 Dual Core Processor 4000+ 2.11 Ghz
3.5 GB RAM

And the CPU's IOWait keeps spiking on the Linux side. I've tried mounting the disk with noatime, to no avail: I've also verified my /etc/fstab file, turned off mount display on the desktop, and tried downgrading to Jaunty, None of these worked, and I'm going to reinstall Karmic this afternoon.

To make matters worse, the system never seems to recover from the spike. Frequently after a spike any attempt to start *any* application (except the shut down menu) throws an error: 'Could not launch [appname]: failed to execute child process [path] (input/output error)'. The shutdown menu will come up, but does not respond to commands, and I have to do a hard shutdown or reset. On a couple of occasions the launch panels have been killed and ended up devoid of any items at all.

This is the disk that I use for work, and I'm getting really frustrated with it. Can anyone offer any suggestions?

---

### Post by Charamei on 2010-01-22
Bump

---

### Post by ianmarcinkowski on 2010-02-11
Downgrade to Jaunty?  

I'm having the same or a very similar problem and have found no solutions yet.

What are the specs of your machine?  Perhaps our machines are similar?

---

### Post by Charamei on 2010-02-12
As I said in the original post, I tried downgrading and it didn't work.

I did manage to fix it eventually, though - by replacing the physical disk when all other options failed. Turns out it was a hardware fault.

---

### Post by ianmarcinkowski on 2010-02-13
Probably not the same problem as I had, then.

---

