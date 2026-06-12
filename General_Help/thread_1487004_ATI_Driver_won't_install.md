---
title: "ATI Driver won't install"
date: 2010-05-18
forum: General Help
---

### Post by Vertigo134 on 2010-05-18
I am using Ubuntu 10.4 and i cant get ATI's driver(10.4) to install. i tryed to run it in termonal but it stops and says i need to run this install as a super-user. 

Help anyone?

---

### Post by cascade9 on 2010-05-18
Put 'sudo' in front of the command you were trying to run. 

You will be asked for your password, and then it should work.

---

### Post by clhsharky on 2010-05-18
HI Vertigo134

Does your card support fglrx?
Run
```
lspci
```

sudo will let you run as super-user.

Sharky

---

### Post by Vertigo134 on 2010-05-18
i tryed typing 'sudo <ati-driver-installer-10-4-x86.x86_64.run>' in the right dir but it didn't work...no clue if i am doing it right.

i dont know what fglrx is but the card is a HD 4890 so i think it should support it.

---

### Post by Vertigo134 on 2010-05-18
I was double clicking on the file before and selecting run in terminal. What is the command to start .run file in terminal?

---

### Post by cbrunhaver on 2010-05-18
Hello,

Normally, you would just go up to the Administration -> Hardware Drivers menu, but as you've noticed, ATI just released this driver with Lucid support.

By the way, I would recommend checking out page 4 of this document (showing the install process).

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat104-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat104-inst.pdf)

What you need to type in the terminal is:

```
sudo sh ./ati-driver-installer-10-4-x86.x86_64.run
```

and then enter your password and you should be good to go.

---

### Post by Vertigo134 on 2010-05-18
worked like a charm. ty

---

### Post by QIII on 2010-05-18
AMD/ATI made the 10.4 driver available in the Lucid repositories before  the final release as they have done for the last several versions of  Ubuntu.  They did not "just" release 10.4.
 
 That is, Ubuntu got the 10.4 driver before everyone else did.
 
 Install the driver via Hardware Drivers.
 
 When you are done, and before you reboot, run
 
 ```
sudo aticonfig --initial -f
``` Remember that the driver will not be active until you reboot.
 
 While you are at it, go to Synaptic and install the Catalyst Control  Center.

Edit:  Well, I see that worked.  However, as a general rule I would suggest using what is available in the repos since that is what they are for.

---

### Post by cbrunhaver on 2010-05-18
Got it.  My mistake.  I can edit my post if needed.

I'm not running ATI hardware and it sounded (by the release notes on the driver) that it wasn't in the repo.

-Chris

---

### Post by QIII on 2010-05-18
AMD/ATI seems to have a sweet spot for Ubuntu.

Phoronix is always making snide remarks like "More candy for Ubuntu" about the fact that they release the drivers to the Ubuntu repos before everyone else gets them.

When ATI was ATI (before AMD bought them in 2007), ATI's Linux support was legendarily poor.  That is not the case any longer.  AMD made Linux an imperative.  Took them about 18 months to catch up, but the are on top of it now and committed to Linux.

Much of the "ATI has bad Linux support" dialog is based on the bad old days and many don't realize the significant change under AMD.

---

