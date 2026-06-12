---
title: "Broadcom STA Driver Activated But Not In Use"
date: 2010-05-11
forum: General Help
---

### Post by jschille on 2010-05-11
System-->Admin-->Hardware Drivers
States my STA driver is activated, but not in use... ug. having so many wireless issues with 10.04 i've been pulling my hair out for a week now.

I assume this is why it says my network UNCLAIMED as well.
Any one else having this issue and maybe have fixed it?

---

### Post by mike555 on 2010-05-11
did you connect to internet and download drivers ....... that's what I had to do (and restart) before the drivers were working ...

---

### Post by jschille on 2010-05-11
> **mike555 said:**
> did you connect to internet and download drivers ....... that's what I had to do (and restart) before the drivers were working ...

even though the drivers worked pre 10.04 i need to d/l and install them again? - is this a dumb question? :P

edit: is this what you are referring to? [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
if so any chance you could help me through it, i find it a little confusing

edit 2: some people say removing and then re-activating the driver fixes the problem for them.  This does not solve my problem, after i reboot it still it NOT IN USE

---

### Post by efflandt on 2010-05-11
If you activate Broadcom STA on bootable USB iso with persistent data, it gives that error (activated, but not in use).  That is because the module does not load automatically on that.  It should load automatically on a regular install.  But for the fun of it, try:

**sudo modprobe -v wl** (that is small L as in **w**ire**l**ess)

Normally to activate Broadcom STA, you either have to be temporarily connected to a network, or you have to insert an install CD and add that to the Synaptic repository temporarily (if it does not ask when you insert CD, there is a checkbox in Synaptic).  But you have to close Synaptic when deactivating or reactivating the driver.

I have used Broadcom STA in 9.10 on an older Dell.  But it has always had a weak signal.  So when I tried activating it in 10.04 and could not seem to connect, I used a Linksys USB54GSC instead (supported automatically) and deactivated Broadcom STA.  So I don't know how well it actually works in 10.04.

---

### Post by jschille on 2010-05-11
> **efflandt said:**
> If you activate Broadcom STA on bootable USB iso with persistent data, it gives that error (activated, but not in use).  That is because the module does not load automatically on that.  It should load automatically on a regular install.  But for the fun of it, try:

**sudo modprobe -v wl** (that is small L as in **w**ire**l**ess)

Normally to activate Broadcom STA, you either have to be temporarily connected to a network, or you have to insert an install CD and add that to the Synaptic repository temporarily (if it does not ask when you insert CD, there is a checkbox in Synaptic).  But you have to close Synaptic when deactivating or reactivating the driver.

I have used Broadcom STA in 9.10 on an older Dell.  But it has always had a weak signal.  So when I tried activating it in 10.04 and could not seem to connect, I used a Linksys USB54GSC instead (supported automatically) and deactivated Broadcom STA.  So I don't know how well it actually works in 10.04.

haha, forgive me, but i am so confused :)

I entered in 
[B]sudo modprobe -v wl
[/B]and got
```

insmod /lib/modules/2.6.32-22-generic/updates/dkms/wl.ko 
FATAL: Error inserting wl (/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

I am connected to the internet, but through the ethernet cable.
I also noticed that no wlan is showing when i type in 
**iwconfig**
i get
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

Thank you for the reply.

---

### Post by mcooke1 on 2010-05-11
I use the Broadcom STA Driver with BCM4328 802.11a/b/g/n card and I find that the default Network Managers in both Kubuntu and Ubuntu do not work for me. So after a fresh install I install the driver reboot install wicd reboot and it works. (In 10.04 installing wicd does not remove Network Manager)

---

### Post by efflandt on 2010-05-12
Have you rebooted since you activated Broadcom STA?  Sometimes it tells you to do that.

Maybe dependencies for the other related module didn't take place.

Try **sudo depmod -v** and then the modprobe.  If you are able to get wl module to load, then try **sudo iwlist scan** (that is IWLIST in small letters) which should find any wireless APs in range.

Note that it will show up as an eth# instead of wlan#, but I have had no problems with Network Connections recognizing it as Wireless (at least not in 9.10), other than initially having to enter security settings once more before it connects.

---

### Post by dmitryabat on 2010-05-13
I have same problem, Do you find solution?

---

### Post by jschille on 2010-05-14
> **dmitryabat said:**
> I have same problem, Do you find solution?

Yes, I did.  I hope this works for you to.
Open up the terminal and enter
```

sudo apt-get remove  --purge linux-backports-modules-*

```

Once that is done go to System --> Admin --> Hardware Drivers
Click on the STA Driver and "Remove" it.
Once it is Removed click Activate.
Restart the Computer after and hopefully you are good to go.

If that doesn't work I'd open a new thread and hopefully Chili can help you out. He knows all.

---

### Post by dmitryabat on 2010-05-19
Thanks a lot. It's working now!

---

### Post by Alex_W on 2010-05-23
hmm... with all that, wireless works only until reboot. then it's back to "activated but not used", and the cycle repeats itself...

---

### Post by ravana_ravana on 2011-02-06
> **jschille said:**
> Yes, I did.  I hope this works for you to.
Open up the terminal and enter
```

sudo apt-get remove  --purge linux-backports-modules-*

```

Once that is done go to System --> Admin --> Hardware Drivers
Click on the STA Driver and "Remove" it.
Once it is Removed click Activate.
Restart the Computer after and hopefully you are good to go.

If that doesn't work I'd open a new thread and hopefully Chili can help you out. He knows all.

Thanks dude.
This really worked for me ..

---

### Post by roger3000 on 2011-02-08
> **Alex_W said:**
> hmm... with all that, wireless works only until reboot. then it's back to "activated but not used", and the cycle repeats itself...

I am facing the exact same issue. 
None of the other solutions proposed below were of any help to me...
[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

---

