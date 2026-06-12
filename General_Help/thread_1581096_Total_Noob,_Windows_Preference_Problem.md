---
title: "Total Noob, Windows Preference Problem"
date: 2010-09-24
forum: General Help
---

### Post by Hawkcode on 2010-09-24
Hi,

At work we just got an Ubuntu with Gnome server set up with BackupPC. Works great. We had outside help.

Now I want to learn Ubuntu so I installed Desktop version that I downloaded from here last night.


I installed it into a VMWare Fusion Virtual machine on my MAC. How ever there is one thing driving me nuts, In Windows Preferances I have no check in the "Select windows when mouse moves over them.

However the system acts as if that was turned on. I tried check/unchecking it No Help.

I checked it the rebooted, then unchecked it rebooted, No difference.

Anybody got any idea????  Thanks 

Rich

---

### Post by endotherm on 2010-09-24
do you have desktop effects enabled? I think (can't confirm as i am on a system without DE) that compiz has a plugin that overrides the default window focus handling. try installing the compizconfig settings manager and see if you have an option to turn it on/off from there.

---

### Post by Hawkcode on 2010-09-24
I went into the software installer and it said compizconfig was already installed, however I cant find it in any menu, then went to the Main Menu under Preferences and found Compiz under Other, enabled it but when selected, nothing happens.

Totally alien environment to me.

Thanks

Rich

---

### Post by Cavsfan on 2010-09-24
System > Preferences > Compizconfig Settings Manager

---

### Post by Cavsfan on 2010-09-24
Also, look at System > Preferences > Simple Compizconfig Settings Manager

---

### Post by Hawkcode on 2010-09-24
Its not under any menu. 

I also looked in the Main Menu configuration program and it is not listed there either.

Confused,

Rich

---

### Post by Cavsfan on 2010-09-24
> **Hawkcode said:**
> Its not under any menu. 

I also looked in the Main Menu configuration program and it is not listed there either.

Confused,

Rich

Click on System > Preferences > Compizconfig Settings Manager and click on General Options at the top.
Then on Focus and Raise Behaviour - make sure Click to Focus is checked.

---

### Post by Hawkcode on 2010-09-24
Its not there:

[IMG]http://ralbrecht.net/Temp.jpg[/IMG]

---

### Post by Cavsfan on 2010-09-24
System > Preferences > Synaptic Package Manager
and enter ccsm at the top and install that.

---

### Post by endotherm on 2010-09-24
i believe you can invoke it from the terminal or Alt+F2 with this command:
```

ccsm

```

if you are still unsure that compiz is the culprit, you could always disable desktop effects, and see if it starts behaving as you expect. if it does, then compiz is the issue. if not, then it's back to square one.

---

### Post by Hawkcode on 2010-09-24
Got it installed, Went under General > Focus and Raise behavior

Tried Just Click to Focus, then Raise on Click, then both. Nothing works.

I also went into system > appearence > Visual effects and None is selected.

Thanks

---

### Post by Cavsfan on 2010-09-24
> **Hawkcode said:**
> Got it installed, Went under General > Focus and Raise behavior

Tried Just Click to Focus, then Raise on Click, then both. Nothing works.

I also went into system > appearence > Visual effects and None is selected.

Thanks

If you have "Click to Focus" checked and it still changes focus when the mouse hovers over a windows, I am lost.
I'll try some more digging though.

---

### Post by Cavsfan on 2010-09-24
In order for Compiz to work, you have to have visual effects enabled.
I have mine set to Custom and have Cairo-Dock, Emerald WM, Compiz Icon and all the extra plugins installed.

But, first you want to enable visual effects and maybe you can take control over it.
Do you have the good video driver installed . System > Administration > Hardware drivers?

---

### Post by Hawkcode on 2010-09-24
Got it installed, Went under General > Focus and Raise behavior

Tried Just Click to Focus, then Raise on Click, then both. Nothing works.

I also went into system > appearence > Visual effects and None is selected.

Thanks

---

### Post by Cavsfan on 2010-09-24
You nave to have desktop effects enabled for CCSM to work. See my post above yours.

---

### Post by Hawkcode on 2010-09-24
Tried enabling it and get "Desktop Effects could not be enabled"

---

### Post by Cavsfan on 2010-09-24
> **Hawkcode said:**
> Tried enabling it and get "Desktop Effects could not be enabled"

What video card do you have?
Did you enable the driver for your video card first? 
You must enable the recommended video driver **System** > **Administration** > **Hardware Drivers** before you can enable Desktop effects.

---

### Post by Hawkcode on 2010-09-24
This is running in a VMWare Fusion virtual machine.

There is no video drive showing, only VMWare Virtual Ethernet Driver and Virtual Machine Communication Interface.

???

Is this possible a VMWare issue?

---

### Post by Cavsfan on 2010-09-24
> **Hawkcode said:**
> This is running in a VMWare Fusion virtual machine.

There is no video drive showing, only VMWare Virtual Ethernet Driver and Virtual Machine Communication Interface.

???

Is this possible a VMWare issue?

I thought you did a clean install and my knowledge stops there. It might be related, but I have no idea.

What displays when you enter **lspci** in a terminal? This will list your hardware.

---

### Post by Hawkcode on 2010-09-24
It was a clean install.

It list VGA compatible controller: VMWare SVGA II Adapter

---

### Post by Cavsfan on 2010-09-24
> **Hawkcode said:**
> It was a clean install.

It list VGA compatible controller: VMWare SVGA II Adapter

Sorry, I didn't understand it was a clean install! 

Hopefully someone familiar with your situation will come here and help. 
Just be patient. This forum is great, but it may take a day to get the right person to figure out the problem.
And trust me the people in this forum are nice and knowledgeable and will help you!

You could also post your problem here: 
[[COLOR=blue]_The Great Desktop Effects FAQ of 2010_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=809695")  This is also a great resource for many things related.

---

### Post by piratebill on 2010-09-24
I don't think a virtual machine can run compiz.....

---

### Post by endotherm on 2010-09-24
have you installed the VM guest tools with mouse integration? I shoudl have mentioned this before but I hadn't realized we were talking about a VM. Mouse integration is likely the issue, since ubuntu can only manage the mouse once you have clicked within the VM window (which contains the ubuntu windows). if the mouse is "ungrabbed" by your VM software, then moving the mouse over a nautilus window won't work, because the host os is managing the mouse, and the vm thinks it doesn't have one. 

you could test that by disabling mouse integration, setting gnome's window preferences, and testing again, but first click on the virtual desktop before moving your mouse over windows in the vm guest.

---

### Post by Hawkcode on 2010-09-25
> **endotherm said:**
> have you installed the VM guest tools with mouse integration? I shoudl have mentioned this before but I hadn't realized we were talking about a VM. Mouse integration is likely the issue, since ubuntu can only manage the mouse once you have clicked within the VM window (which contains the ubuntu windows). if the mouse is "ungrabbed" by your VM software, then moving the mouse over a nautilus window won't work, because the host os is managing the mouse, and the vm thinks it doesn't have one. 

you could test that by disabling mouse integration, setting gnome's window preferences, and testing again, but first click on the virtual desktop before moving your mouse over windows in the vm guest.

How do I disable MOUSE integration? I did a manual reinstall of of the VMWare tools. 

Stange thing is when I have the file browser open, if I park the mouse on top of a drive it keeps opening a new window, as if I was hitting the mouse button over and over.

---

