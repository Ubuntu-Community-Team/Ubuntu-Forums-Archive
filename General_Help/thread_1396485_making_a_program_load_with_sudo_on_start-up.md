---
title: "making a program load with sudo on start-up?"
date: 2010-02-02
forum: General Help
---

### Post by zozza on 2010-02-02
I cannot figure how to make a program start-up when Ubuntu boots.

I want the "sudo firestarter" command to run so the firestarter icon appears in the panel.

Thanks.

---

### Post by Leppie on 2010-02-02
you can add it to your /etc/gdm/PostLogin/Default script:
```
sudo cp /etc/gdm/PostLogin/Default.sample /etc/gdm/PostLogin/Default && gksudo gedit /etc/gdm/PostLogin/Default
```
at a line for firestarter at the end of the file (no need for sudo as this script is executed with root permissions), save and exit. log out and in to check.

---

### Post by 3rdalbum on 2010-02-02
Why do you want Firestarter open at login?

Firestarter is only an interface for setting up rules for the IPtables firewall that is inside the kernel. In other words, you only run Firestarter when you actually want to change the configuration.

In addition, Firestarter's logging system often scares new users - they see perfectly normal 'denied' connection attempts and think that the Russian mafia is owning their box. If you want to set up your personal firewall, I recommend using gUFW - unlike Firestarter, it's actually maintained and bugfixed.

---

### Post by zozza on 2010-02-03
Thank you both.

So now I have gUFW with the "actual status" enabled and "by default" set to deny.  

I hope that appears correct.

---

### Post by Leppie on 2010-02-03
> **zozza said:**
> Thank you both.

So now I have gUFW with the "actual status" enabled and "by default" set to deny.  

I hope that appears correct.
you're welcome.

is it working correctly *for you?*

---

### Post by zozza on 2010-02-04
Actually I am not convinced this is working.  

I have the gUFW icon load at startup because I have placed in in the panel as a launcher.  

However, the status as "enabled" is never checked when I log into Ubuntu.  

How can I tell that guFW or any program actually loads at start-up?  Under XP I just put the program information into msconfig.  

In this case I want the icon to load in the panel but also the actual program to be running on start-up.

---

### Post by marquinos on 2010-02-05
Hi!
Create a link (I think with drag and drop from menu) into your folder:
/home/your_user/.config/autostart
Best regards.

---

### Post by Leppie on 2010-02-05
> **zozza said:**
> How can I tell that guFW or any program actually loads at start-up?  Under XP I just put the program information into msconfig.
what else have you done to find out how to make this work? have you read the man pages for guFW?
you say that in XP you "just put the program information into msconfig", where did you obtain this knowledge and where did you get the program information?

> **zozza said:**
> In this case I want the icon to load in the panel but also the actual program to be running on start-up.
maybe if you tried searching, you'd find a solution: [http://ubuntuforums.org/showthread.php?t=960846](http://ubuntuforums.org/showthread.php?t=960846)

---

