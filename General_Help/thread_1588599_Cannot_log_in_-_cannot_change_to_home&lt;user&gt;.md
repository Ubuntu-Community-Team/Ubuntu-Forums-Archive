---
title: "Cannot log in - cannot change to /home/&lt;user&gt;"
date: 2010-10-05
forum: General Help
---

### Post by Phoenix_Swelter on 2010-10-05
A little background....

I have a disk going bad and couldn't boot Lucid, so I used Virtualbox on Win7 to create a temporary Kubuntu machine to work getting data from my failing drive. Because it was a temp setup, I did not enable root login.

I logged into Linux at Virtualbox, plugged in my failing drive, and began working on moving stuff over using Konsole. The failing drive was mounted on /media/linux. At some point, trying to do some experimenting, I did a sudo chmod 0400 /media/linux. All hell broke loose. No commands would work. No access to /bin/mv or /bin/ls.....no ability to change directories. It was as though the chmod had been applied to the entire root folder. I double-checked my command...no spaces between / and media.

I figured Virtualbox had gone screwy, so I shut down the machine and re-booted. Cannot log in - cannot change to /home/<user>.

If this were a real disk partition, I would simply boot the Kubuntu CD and chmod again. But this is on the VM. Any ideas what I can do? HELP! I had already backed most of my stuff to the VM!

---

### Post by sanderd17 on 2010-10-05
Can't you create a new VM and mount the virtual disk from the old VM in the newer one?

---

### Post by Phoenix_Swelter on 2010-10-05
> **sanderd17 said:**
> Can't you create a new VM and mount the virtual disk from the old VM in the newer one?

I didn't think that would be possible. Let me work on it. Are you experienced in working with VMs? Do you have any tips?

---

### Post by sanderd17 on 2010-10-05
I use VM's for testing new distros before I install them. 

It should work if you do the following:

* make a new VM and install something like ubuntu, kubuntu or something light like puppy.
* close the VM and go in the VM to settings -> storage. Add a new HDD and on the right, select the HDD from the broken kubuntu install.
* Start the VM. If the broken VM starts, you'll have to press F12 at boot time.

---

### Post by sanderd17 on 2010-10-05
You don't even need to make a new VM. You can use this tutorial:
[http://forums.virtualbox.org/viewtopic.php?f=26&t=33355]("http://forums.virtualbox.org/viewtopic.php?f=26&t=33355")

---

### Post by Phoenix_Swelter on 2010-10-05
> **sanderd17 said:**
> I use VM's for testing new distros before I install them. 

It should work if you do the following:

* make a new VM and install something like ubuntu, kubuntu or something light like puppy.
* close the VM and go in the VM to settings -> storage. Add a new HDD and on the right, select the HDD from the broken kubuntu install.
* Start the VM. If the broken VM starts, you'll have to press F12 at boot time.

Excellent! Thank-you. It worked like a charm.

The steps:

I created a new Linux VM that I named "Recovery".

After it was created and the OS installed, I powered down the Recovery VM, went to the Storage option of the Recovery VM, highlighted the hard drive controller, clicked Add New Attachment to the Storage Tree, and added the broken virtual drive to the tree.

I started the Recovery VM, (I need to improve my skills with finding unmounted file systems on Linux - I had to by-guess/by-golly figure out where the broken virtual drive was located), mounted the broken virtual drive, chmod everything back to normal, closed the VM and started the original Linux VM. Everything is there and in good order. 

Thank-you.

---

