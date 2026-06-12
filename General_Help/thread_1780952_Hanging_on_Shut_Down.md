---
title: "Hanging on Shut Down"
date: 2011-06-12
forum: General Help
---

### Post by Leaky on 2011-06-12
Whenever I try and shut down my Ubuntu Machine, it just hangs at the desktop (no icons, mouse) and then after a couple of seconds hangs at either a purple screen permanently until hard power off or a black screen displaying 'Disconnected from Plymouth' permanently until hard power off...

I'm not going to be the primary user of this machine and so if you could help me get it shutting down / rebooting smoothly then thatbe great. Below is a link to the syslog containing a reboot procees.

[http://pastebin.com/raw.php?i=T56bLeqE](http://pastebin.com/raw.php?i=T56bLeqE)

ps. I'm an Ubuntu Newbie.

---

### Post by mörgæs on 2011-06-12
Hi, welcome to the fora.

In which releases of Ubuntu does this happen?

---

### Post by JohnBonne on 2011-06-12
try updating the system and rebooting.

Enter recovery console on bootup.

---

### Post by Leaky on 2011-06-13
It's the latest version. 11.04? I've tried both 32/64 bit versions and the same problem occurs

---

### Post by mörgæs on 2011-06-13
If you haven't tried 10.10 it will be good to do that for comparison.

---

### Post by Leaky on 2011-06-13
I've just downgraded to 10.10 and I can reboot flawlessly. However, I now have a problem where the wireless doesn't work? I can connect to the internet via ethernet, but it needs to be wireless. Under WIreless Networks it says 'disconnected'.

---

### Post by mörgæs on 2011-06-13
Which wireless card do you have?

---

### Post by Leaky on 2011-06-13
The machine is an eMachine ER1401 and it has built in wireless. I'm trying to get working smoothly as I've got another 8 to configure yet... :(

---

### Post by mörgæs on 2011-06-13
Please post the output of 

```
hwinfo --netcard
```

---

### Post by Leaky on 2011-06-14
I have the wireless sorted now, I had to add a PPA to update manager to get te bugfix. However, now I'm back to square 1 with the hanging on shutdown?! It's one problem after another :/

---

### Post by matt_symes on 2011-06-14
Hi

What happens if you try to shutdown from the terminal. Open a terminal amd type

```
sudo shutdown -h now
```

Enter your password. It will not be echoed to the screen.

Does it shut down ?

Kind regards

---

### Post by Leaky on 2011-06-14
No, it would still hang

---

### Post by matt_symes on 2011-06-15
Hi

> **Leaky said:**
> I have the wireless sorted now, I had to add a PPA to update manager to get te bugfix. However, now I'm back to square 1 with the hanging on shutdown?! It's one problem after another :/

You added a bug fix for your wireless to 10.10 and then immediately after that you could not shutdown ?

If this is the case, can you supply details of the PPA and bug fix and exactly what you did.

Kind regards

---

### Post by xGryph on 2011-07-30
Hi,

I'm also trying to install Ubuntu 11.04 on an eMachine ER1401 computer. 

I can confirm the same issue. A purple screen of death when shutting down. The purple screen can also be replicated by clicking on the network icon on the system tray and disabling wireless.

It appears when wireless is deactivated which presumably happens on shutdown a purple screen of death occurs.

I'm not too concerned about wireless functionality so I'm wondering if I can prevent the wireless drivers from being loaded on startup?

Thanks.

---

### Post by Guinch on 2011-08-11
This worked for me:

[http://www.harley-jones.co.uk/?p=135](http://www.harley-jones.co.uk/?p=135)


Thanks to Mr Harley Jones.

---

