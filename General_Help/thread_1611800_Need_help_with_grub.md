---
title: "Need help with grub"
date: 2010-11-02
forum: General Help
---

### Post by schnabel45 on 2010-11-02
Hey all,
I really screwed up here, and after an hour and a half of searching I can't figure out what to do.  Here's the situation.  I wanted to install Ubuntu 10.04 onto my flash drive so I could use it on the computer at work.  I wanted to be able to boot into Ubuntu when I plugged the drive in, yet allow the computer to run as normal as far as the IT are concerned when it was not connected.  So I brought it to work along with a second flash drive that has the live installer on it.  I installed Ubuntu onto the flash drive and all went well as far as I could tell, however now I'm in a real bind.

When I remove the live install flash drive, I'm sent into the grub rescue mode and get only the screen below:
```
error: no such device: 04635572
grub rescue>
```My first instinct was to type help to get a list of commands, yet it only returned grub rescue>.

What I need to do is make the computer boot into Windows without reinstalling the OS, so I figured I could just configure Grub to auto boot Windows and (to the non tech savvy co worker) it would look fine to them, or uninstall Grub without having to reinstall Windows.  I assume the first option is going to be the easier, but what do I know though.  

Note: I am able to load the "Live CD" flash drive, in fact that's where I'm posting from as I type.

Can anyone help me with this?
Thanks in advance!

---

### Post by drs305 on 2010-11-02
Is Ubuntu on the main system? If so, you can try to install Grub2 on the main drive. You will need to know the partition on which Ubuntu is installed. To do this, boot to the LiveCD and mount your Ubuntu partition. I will use "sda5" but you will need to change it if necessary.

Make sure sda is your hard drive. If the hard drive is not sda, change *sda* to the correct designation.
Make sure sda5 is your Ubuntu partition. You can check if you aren't sure after you run the first command by opening a browser and checking the contents of /mnt.

Also note you do not add the partition number in the second command.


```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```


If you just want to get Windows back, enable "universe" in the LiveCD Synaptic repository and run this:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
You will get a few warnings about lilo not being fully installed, but disregard them as you aren't installing lilo fully, just getting it to write to the MBR.

---

### Post by schnabel45 on 2010-11-02
This worked perfectly and I'm back in Windows!  Thank you so much for your help!  I owe you and this community quite possibly my job (since i'm just an intern).

---

### Post by drs305 on 2010-11-02
> **schnabel45 said:**
> This worked perfectly and I'm back in Windows!  Thank you so much for your help!  I owe you and this community quite possibly my job (since i'm just an intern).

You are welcome. Hope your next Ubuntu experience works out a little more stress-free!  ;-)

Marking a thread SOLVED helps users looking for threads with solutions and lets the helpers concentrate on unresolved issues. You mark a thread SOLVED via the 'Thread Tools' link near the top right of the first post. Thanks.

---

