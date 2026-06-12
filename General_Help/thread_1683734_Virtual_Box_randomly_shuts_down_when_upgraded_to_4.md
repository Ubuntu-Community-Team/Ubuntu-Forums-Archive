---
title: "Virtual Box randomly shuts down when upgraded to 4.0"
date: 2011-02-08
forum: General Help
---

### Post by excetara2 on 2011-02-08
I run Ubuntu Lucid and upgraded to 4.0 virtual box recently. Now, the machine is running guest Windows 7 64 bit and randomly shuts the entire virtual box down with no warning. I tried re-installing with the same issue ocurring.

Anyone else experienced this or know what logs to check to see what is going on.

Cheers,
Jeff

---

### Post by slooksterpsv on 2011-02-08
> **excetara2 said:**
> I run Ubuntu Lucid and upgraded to 4.0 virtual box recently. Now, the machine is running guest Windows 7 64 bit and randomly shuts the entire virtual box down with no warning. I tried re-installing with the same issue ocurring.

Anyone else experienced this or know what logs to check to see what is going on.

Cheers,
Jeff

Is it version 4.0 or is it 4.0.2?
What kind of CPU do you have (and does it support Virtualization technology)?
Do you have the following packages installed on your system? dkms build-essential

If not, install those and run: 
```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by excetara2 on 2011-02-08
Yes, I have 4.0.2 and dkms is already installed.

Kernel version I forget how to check but I have an i5-M540 with virtualization support.

I had no problems before updating to the new virtual box and the new linux kernal. When I run the newest kernal and virtual box it actually freezes up the system (video and all where you have to do a hard reboot). I'm not sure this is from virtual box so I tried switching to the previous kernal and VirtualBox randomly shuts off as described.

Cheers,
Jeff

---

### Post by slooksterpsv on 2011-02-08
Alrighty. A couple of things:

1. If you go to a previous kernel you need to re-run 

sudo /etc/init.d/vboxdrv setup

because it bases it off the kernel your using, and uses those headers to compile the kernel modules.

2. uname -a
I'm running: 2.6.35-25
I also have: 2.6.35-22

So if you boot using a previous kernel and it's using the updated dkms modules, but the kernel hasn't implemented those changes for use with the newer dkms (old kernel) then it can randomly try to run a function or access a variable causing the program to SEG FAULT/Crash. So try that.

As for it not running properly in 2.6.35-25, not sure, mine runs flawless. A couple of things, is Virtualization turned on in the BIOS? I'll run Windows 7 64-bit (do an install) and see if it happens on mine, if it does it may be a bug.

---

### Post by excetara2 on 2011-02-08
Should have posted the kernal. I'm running 2.6.32-27 but I also have 2.6.32-28 but as it froze twice last night with this and virtual box on I'm not using it currently. not sure if 28 bug is with virtual box or another conflicting program.

You have to run the dkms setup when switching kernals or it won't boot virtualbox. It detects that the build was run on a different kernal and forces it. I'll run it again and maybe something didn't get built correctly in this kernal this time around.

---

### Post by slooksterpsv on 2011-02-08
> **excetara2 said:**
> Should have posted the kernal. I'm running 2.6.32-27 but I also have 2.6.32-28 but as it froze twice last night with this and virtual box on I'm not using it currently. not sure if 28 bug is with virtual box or another conflicting program.

You have to run the dkms setup when switching kernals or it won't boot virtualbox. It detects that the build was run on a different kernal and forces it. I'll run it again and maybe something didn't get built correctly in this kernal this time around.

See I'm on Maverick, you downloaded the Lucid version of VBox right?

[http://download.virtualbox.org/virtualbox/4.0.2/virtualbox-4.0_4.0.2-69518~Ubuntu~lucid_amd64.deb](http://download.virtualbox.org/virtualbox/4.0.2/virtualbox-4.0_4.0.2-69518~Ubuntu~lucid_amd64.deb)

Not maverick.

---

### Post by excetara2 on 2011-02-08
No, I downloaded the version for lucid. Doubt the maverick version will install on Lucid kernal.

---

### Post by trampgeek on 2011-02-10
FWIW, you're not alone Excetera. I have exactly the same problem (apparently random shutdowns of a Windows7 client on an Ubuntu Lucid host) except that I have 32-bit system. I too have been using VirtualBox for years and haven't had any problems (well, not this particular one, anyway!) until I switched to VirtualBox4 (4.0.2r69518 to be exact). I'm running the same client as before.

Looking at a recent log I see that the power-down was apparently under VirtualBox control rather than a simple crash. The last few lines prior to the full state dump were:

00:42:05.163 PCNet#0: Init: ss32=1 GCRDRA=0x4a3ba420[64] GCTDRA=0x4a3ba020[64]
00:42:05.166 PCNet#0: Init: ss32=1 GCRDRA=0x4a3ba420[64] GCTDRA=0x4a3ba020[64]
00:42:05.166 PCNet#0: Init: ss32=1 GCRDRA=0x4a3ba420[64] GCTDRA=0x4a3ba020[64]
00:42:05.393 Ignoring guest attempt to enter S1 power state (powered-on suspend)!
00:42:05.393 Entering S4 power state (suspend to disk)
00:42:05.393 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.
00:42:05.393 ****************** Guest state at power off ******************

This looks like a "feature not a bug", but it's a feature I'd rather like to turn off! It appears more-or-less equivalent to turning the power off on the running client, which when rebooted announces its displeasure by asking if I want to do a normal startup or a safe-mode startup.

[Edit] Just in case anyone takes me for a total moron, no I did not shutdown VirtualBox by just closing the window and selecting "Just Power Down" in the dialogue box! VirtualBox just decided to shut down when I wasn't looking. Most of the unwanted shutdowns are like that, although some of them have occurred when I was switching to or from full screen mode or switching between displays.

---

### Post by excetara2 on 2011-02-10
K. I will either revert back to an older version or propose this should get fixed. Do you know where to report virtual box bugs?

---

### Post by slooksterpsv on 2011-02-10
> **trampgeek said:**
> 
Looking at a recent log I see that the power-down was apparently under VirtualBox control rather than a simple crash. The last few lines prior to the full state dump were:

00:42:05.163 PCNet#0: Init: ss32=1 GCRDRA=0x4a3ba420[64] GCTDRA=0x4a3ba020[64]
00:42:05.166 PCNet#0: Init: ss32=1 GCRDRA=0x4a3ba420[64] GCTDRA=0x4a3ba020[64]
00:42:05.166 PCNet#0: Init: ss32=1 GCRDRA=0x4a3ba420[64] GCTDRA=0x4a3ba020[64]
00:42:05.393 Ignoring guest attempt to enter S1 power state (powered-on suspend)!
00:42:05.393 Entering S4 power state (suspend to disk)
00:42:05.393 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.
00:42:05.393 ****************** Guest state at power off ******************

This looks like a "feature not a bug", but it's a feature I'd rather like to turn off! It appears more-or-less equivalent to turning the power off on the running client, which when rebooted announces its displeasure by asking if I want to do a normal startup or a safe-mode startup.

[Edit] Just in case anyone takes me for a total moron, no I did not shutdown VirtualBox by just closing the window and selecting "Just Power Down" in the dialogue box! VirtualBox just decided to shut down when I wasn't looking. Most of the unwanted shutdowns are like that, although some of them have occurred when I was switching to or from full screen mode or switching between displays.

Could it be that Windows is trying to switch power states and instead VirtualBox thinks its an ACPI command to turn off the machine? I dunno, I may be way way off but I would submit a bug to VirtualBox (if you can).

---

### Post by excetara2 on 2011-02-10
Interesting comment. It could be something to do with the ACPI and mis-taking of commands on the host machine. It could be the host is erroneously sending it an ACPI shutdown/restart command so the virtual machine thinks it should shutdown automatically. But what would be causing it to misread that or send that signal not sure.

Put thread into Virtualization Thread as never knew there was one till just now.

---

### Post by excetara2 on 2011-02-10
Or it could be the reverse in that there was a regression in upgrading to 4.0. On windows clients it doesn't properly handle power management so this is sent as a signal to shutdown. I will try to investigate further on both because this second option makes more sense to me that it is on the client end whether than the host because doesn't matter the Kernal or Ubuntu version this still occurs.

---

### Post by trampgeek on 2011-02-11
> **excetara2 said:**
> Or it could be the reverse in that there was a regression in upgrading to 4.0. On windows clients it doesn't properly handle power management so this is sent as a signal to shutdown. I will try to investigate further on both because this second option makes more sense to me that it is on the client end whether than the host because doesn't matter the Kernal or Ubuntu version this still occurs.
Yes, I think you're onto it guys. I just checked my guest (Windows 7) Power Management configuration and I see that it was set to sleep after 30 minutes idle when on mains power. Most of my shutdowns seem to have occurred after a period of inactivity and I'm guessing that that period has always been 30 minutes. The log statement "00:42:05.393 Ignoring guest attempt to enter S1 power state (powered-on suspend)!" would correspond to the guest announcing it is going to sleep. VirtualBox apparently then decides to pull the power plug on it instead!

I've changed my guest to never sleep and I suspect that will solve my problems. I'll try to remember to post back here if that's the case but I'll certainly post back here if it's not!

---

### Post by trampgeek on 2011-02-11
Hah. So much for that theory. When I went back to use my Windows7 guest after making that last posting it wasn't there, despite my having changed its power settings. The log is similar:

00:03:42.890 NAT: DHCP offered IP address 10.0.3.15  // All fine up to this point
00:17:59.521 OHCI: USB Operational
00:17:59.545 EHCI: USB Operational
00:17:59.553 PCNet#0: Init: ss32=1 GCRDRA=0x49c12420[64] GCTDRA=0x49c12020[64]
00:17:59.553 PCNet#0: Init: ss32=1 GCRDRA=0x49c12420[64] GCTDRA=0x49c12020[64]
00:17:59.554 PCNet#0: Init: ss32=1 GCRDRA=0x49c12420[64] GCTDRA=0x49c12020[64]
00:17:59.568 OHCI: USB Suspended
00:17:59.569 EHCI: USB Suspended
00:18:00.795 Ignoring guest attempt to enter S1 power state (powered-on suspend)!
00:18:00.795 Entering S4 power state (suspend to disk)
00:18:00.795 Changing the VM state from 'RUNNING' to 'POWERING_OFF'.

but it certainly wasn't 30 minutes of inactivity and anyway I had turned off the "sleep after 30 minutes" setting.

I've also now turned off the option of powering down the display after 15 minutes inactivity but I doubt that's the cause -- that wouldn't put Windows into an S1 state.

Suggestions anyone?

---

### Post by BoudewijnD on 2011-02-12
Hey Guys,

I was also struggling with the same problem that ussually after my screensaver started VB crashed or shut is self down.
I found your thread first but there was no solution just jet.
I googled some more and found this thread on the Vbox forum.
[http://forums.virtualbox.org/viewtopic.php?f=2&t=38232]("http://forums.virtualbox.org/viewtopic.php?f=2&t=38232")

I changed my settings to 
```
VBoxManage setextradata VM_NAME VBoxInternal/Devices/acpi/0/Config/PowerS1Enabled 1
VBoxManage setextradata VM_NAME VBoxInternal/Devices/acpi/0/Config/PowerS4Enabled 1
```

And now I will see what will happen. I will keep you posted.

\BoudewijnD

And by the way if you do run the command in terminal change the VM_NAME in the name of your machine :D I forgot it twice](*,)

---

### Post by excetara2 on 2011-02-12
I turned off all the power settings and haven't had a shut down yet. Haven't tried the above post but I will see what happens first with just setting down all power options within the Windows 7 guest. I'll give it another day to see if it randomly shuts down but 1 day and so far so good.

---

### Post by trampgeek on 2011-02-16
Yay, thanks BoudewijnD. Turning off the guest's power options didn't seem to work for me but those two VBoxManage commands seem to have done the trick for me -- guest has been up for over 24 hours now, which is at least 10 times longer than it has ever managed since the 4.0 install.

---

### Post by BoudewijnD on 2011-02-28
@ tramgeek indeed I tried the option first as posted here. But it still stopt VB after standby. And with the other option ```
VBoxManage setextradata VM_NAME VBoxInternal/Devices/acpi/0/Config/PowerS1Enabled 0
VBoxManage setextradata VM_NAME VBoxInternal/Devices/acpi/0/Config/PowerS4Enabled 0
```
Works fine for 2 days now!!

So change the topic to [Solved]

\BoudewijnD

---

### Post by tmarcou on 2011-03-08
All,  I have been investigating this problem over the last few days.  

ENVIRONMENT:
I have setup three different devices with VirtualBox 4.0.2  The first machine is a MacBook pro(MAC OS), second is a Gateway multimedia desktop (ubuntu 10.10) and the third is an eMachines desktop (ubuntu10.10).  The MAC VB client is Windows 7 The Gateway is client is Win7 and the eMachine is WinXPP. All have VirtualBox 4.0.2 installed and all exhibit the same problem.  Non of these machines had an issue with earlier version of VB.

THE CAUSE:
The problem is related to the Windows computer's power management.  If the "Put computer to sleep" time expires, VB goes down hard.  If I chnage the setting to "Never" then all is well.  This is a diffenetly bug with VB 4.0.2 that needs to be addressed.

---

### Post by da_zhuang on 2012-02-10
Hi all:

I have the same issue, and I'm trying to use the same solution that you guys provided, ```
VboxManage setextradata VM_NAME VBoxInternal/Devices/acpi/0/Config/PowerS1 Enabled 1
```, and replace the VM_NAME with my guest OS name, but virtual box doesn't seem to be able to recognize that name. How can I find that name? Thanks.

---

