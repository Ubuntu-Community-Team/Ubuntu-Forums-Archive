---
title: "No hibernate in Ubuntu!"
date: 2012-08-11
forum: General Help
---

### Post by pyro.xyz on 2012-08-11
Hey, I used to have a hibernate option with Ubuntu, but now that I have upgraded to 12.04, there is no more hibernate option. I know that it doesn't come by default with Ubuntu, and the only reason that I had that button was because I had installed it as an add-on. However, I forgot how to do that. Please help!

---

### Post by Toz on 2012-08-11
See: [http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04]("http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04")

---

### Post by pyro.xyz on 2012-08-16
Hey, please respond to this thread. It's still not solved!

---

### Post by Toz on 2012-08-17
Did you have a look at the link I referenced? It gives instructions on how to re-enable the hibernate option.

---

### Post by Deepak J on 2012-08-17
I usually hibernate in Ubuntu from the command line using the command..

"sudo pm-hibernate"

And it serves ma task without any error. The only thing that I've gotta do more is press CTRL+ALT+T :lolflag:


Also I think think that the link posted by Toz is helpful... as the same advice is given in the Ubuntu site "https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html"

---

### Post by pyro.xyz on 2012-08-17
Sorry. I didn't see the link that you shared. All I saw was "please mark threads as 'solved'". Anyways, thanks!

---

### Post by pyro.xyz on 2012-08-17
Okay, so my laptop is actually able to hibernate. However, there is no hibernate option when I press the power option, neither in the option menu at the top-right of the screen. Also, there is another fairly large problem. I reinstalled Ubuntu from a USB drive, but now I can't boot my computer without the flash-drive being in the computer. I actually had to change the boot-order in BIOS to USB-drive being first. However, when the computer is booted, I no longer need that usb, and can just take it out. Not too much of a problem, until my flash-drive breaks or I lose it. Then, I'm pretty much screwed. Can you help with that?

---

### Post by 2F4U on 2012-08-17
Bug report

[https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394)

and solution

[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

Did you edit the policykit file as suggested in the second link?

---

### Post by Paddy Landau on 2012-08-17
Incidentally, if you have encrypted folders, hibernation must be disabled.

You can enable it with encrypted folders but there is a caveat; see point 6 in [Disclaimers and Warnings]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#Disclaimers_and_Warnings").

---

### Post by BitSmack on 2012-09-30
> **Paddy Landau said:**
> Incidentally, if you have encrypted folders, hibernation must be disabled.

You can enable it with encrypted folders but there is a caveat; see point 6 in [Disclaimers and Warnings]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#Disclaimers_and_Warnings").

Excellent, this was my problem.  Thanks for the heads-up :)

---

