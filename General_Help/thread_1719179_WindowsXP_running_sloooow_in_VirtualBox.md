---
title: "WindowsXP running sloooow in VirtualBox"
date: 2011-04-01
forum: General Help
---

### Post by Colin@oxford on 2011-04-01
I have WindowsXP installed under VirtualBox.  Most of the time this works fine, but sometimes when I boot it up, it runs so incredibly slowly that it is unusable.  My only solution to this has been to copy out the important data, restore the vdi file from backup and reboot.  This usually solves the problem until next time.  "top" shows that vbox is taking 35% of the memory (which is the amount I have allocated) and about 102% of my dual core's CPU.  Everything else is running OK at the time.

Can anyone suggest a reason for this random snail's pace and better way of fixing it?

---

### Post by sw0rn on 2011-04-01
I had the same problem for awhile. 
IIRC, VirtualBox only uses *one* core. So, even if you had a bajillion cores, VirtualBox can only be a part of the scheduler of the first core. I don't recall ever finding a fix. 

Also, Windows bloats really bad. I did the same thing you did and every time, after a few weeks, Window would get fat and slow and become relatively unusable. 

So, to circumvent this, I just started dual-booting.

I'm looking into a new laptop and I was just wondering about this as well; I wonder, what's the best hardware one can have for Windoze in a virtualbox?

---

### Post by Spyderkid on 2011-04-01
Shutdown all application when using virtual box and also think about allocating memory up to the orange zone for your OSE

---

### Post by 3Miro on 2011-04-01
What is your video card, you may want to double-check the settings especially involving hardware acceleration. Also, make sure to install Guest Addons.

I have used various Nvidia cards on 4GB RAM machine with anywhere from 2 to 6 cores AMD CPU. I have had the same XP .vid installed for years without any trouble.

---

### Post by slooksterpsv on 2011-04-01
Checklist time =D

The above person said check Guest Additions, yup that's #1

If you have any additional apps installed in VBox XP, see how much memory XP is using (taskmgr from run or CTRL+SHIFT+ESCAPE in Windows XP).

What kind of a computer? CPU? 
Does it support Virtualization Technology? (If not give us the CPU model and we can find out, e.g. AMD Athlon 3200+)
How much RAM do you have? How much allocated? Do you have the 2d or 3d acceleration on (can degrade performance)?
In the VM Properties do you have any of these enabled:
[System->Proceessor]
Enable PAE/NX ?

[System->Acceleration]
Enable VT-x/AMD-V ?
Enable Nested Paging ?

[Display->Video]
Video Memory Amount ?
2D ?
3D ?

(We don't want to change these though as doing so may render the VM unbootable)

Go to terminal and run the following (with all VMs shutdown and VirtualBox closed):

```

sudo apt-get install build-essential dkms && sudo /etc/init.d/vboxdrv setup

```

If you haven't installed dkms yourself, that can slow things down.

Let me know, I know I gave you a lot to check, but it flies quick.

---

### Post by oldsoundguy on 2011-04-01
Just curious as I have never populated a computer with more than ONE O/S.

If you are running in virtual, does Windows have the same issues as when it is run alone?

IE .. does it suck up malware wherever it goes on the web?  Does the registry file get out of hand?  Does it leave a lot of dead end/orphan files that have to be removed with a 3rd party clean up program?

I have a couple of Windows boxen on my home net, but seldom take them on line and when I do, I do not SURF .. just go to specific highly trusted sites such as EBay/PayPal or for updates on security programs/hardware.

---

### Post by 3Miro on 2011-04-01
> **oldsoundguy said:**
> 
If you are running in virtual, does Windows have the same issues as when it is run alone?


Windows under Virtual Box runs exactly the same was as Windows would if it were to run on some strange and somewhat limited hardware. Other than speed and graphics acceleration, the rest is exactly the same.

---

### Post by An Sanct on 2011-04-01
> **oldsoundguy said:**
> If you are running in virtual, does Windows have the same issues as when it is run alone?

Short: Yes.

Long: When running a Virtual machine (*VM), the situation is equal to having the machine present and going online through your host computer. So the firewall settings of the host machine apply. The way the OS handles software is the same, same problems with registry, spyware, viruses,... The most noticable difference between a VM and a real machine is GPU utilization, a *real* machine can have *real* 3D acceleration. A VM is not "up" for gaming.

---

### Post by An Sanct on 2011-04-01
> **sw0rn said:**
> VirtualBox only uses *one* core. So, even if you had a bajillion cores, VirtualBox can only be a part of the scheduler of the first core. I don't recall ever finding a fix.

VB has SMP support since version 3.0 (current version: 4.0)

What version are *you* using?

---

### Post by d3v1150m471c on 2011-04-01
oddly enough changing the sound driver for my vm made it go way faster...: i either use pulse audio or null driver now. massive difference.

---

### Post by 3Miro on 2011-04-01
> **d3v1150m471c said:**
> oddly enough changing the sound driver for my vm made it go way faster...: i either use pulse audio or null driver now. massive difference.

Under VB, unless I absolutely need sound and network, I would rather disable them.

---

### Post by Colin@oxford on 2011-04-02
I think that Spyderkid wins - I restarted the machine and had only Thunderbird & Firefox running when I started VBox.  Yesterday I had other programs running (although I think it was only emacs).  All ran smoothly today.

slooksterpsv: I have build-essential installed, but can't see
/etc/init.d/vboxdrv

I have an AMD Athlon 5200+ (dual core) in my Asus box (can't remember the model number at the moment).

Yes, I do have the Guest additions installed.  I allocated 500MB of memory because that is the maximum that I can give it without some of the software on there complaining that there is too little :-)  I am only running XP in order to maintain this legacy stuff.  I don't use a browser on the machine except to get updates and sometimes check on a website I have created.

---

