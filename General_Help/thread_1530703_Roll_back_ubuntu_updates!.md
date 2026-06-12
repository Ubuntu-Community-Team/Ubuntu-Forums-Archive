---
title: "Roll back ubuntu updates!"
date: 2010-07-14
forum: General Help
---

### Post by samuelrock on 2010-07-14
Ok

So I updated this afternoon and once my updates were done i went to connect a usb to my vmware xp box. I got a usb error that windows could not use the usb. So i rebooted vmware and got the same thing...

I then shut down vmware and rebooted my machine..  once i logged into the machine and launched vmware i no longer can see any of my usb devices.

I would like to just rollback the updates so that i can use my vmware again..  as i must transfer cad files to the pc with usb. Autodesk only works in windows so vmware has been a blessing as i dont have to reboot every time i need to work on drawings!

HOST: lucid 10.04
guest: XP PRO sp3
VM ver: 7.1.0 build-261024

Thanks
Sam

---

### Post by bodhi.zazen on 2010-07-14
Did you install a new kernel ? That is most likely the problem.

If so, did you update vmware ?

If so, boot the old kernel. As you boot hold the Shift key and select an older kernel.

In the long run, consider migrating to Virtualbox or KVM, less hassles then VMWare. KVM and Virtualbox offer most features available on VMWare, but there may be a vmware feature you can not live without.

---

### Post by iponeverything on 2010-07-14
I agree that booting an earlier kernel will probably solve your problem. 

On the update roll-back - it would be nice if there an automated tool for this - this how you do it:

find the corresponding log for the update in:

 ~root/.synaptic/log

then find the previous version of the package in:

 /var/cache/apt/archives/

reinstall them just by clicking on them or by using dpkg.

---

