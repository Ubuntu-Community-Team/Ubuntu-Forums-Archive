---
title: "Gnome/KDE Logout Screen Garbled"
date: 2011-11-08
forum: General Help
---

### Post by zcacogp on 2011-11-08
Chaps, 

I've put KDE on top of Ubuntu (11.10 Oneiric) and am getting used to it. (And liking it, I'll add!) In the process, I now have the KDE login screen (rather than the Ubuntu one.) 

I have discovered that when I logout, the login screen that is supposed to be displayed is garbled. I don't know how to take a screenshot so have a photo instead. 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/DSC_2751.jpg[/IMG]

As this screen is unusable I can only use the power off button to turn off and re-start - whereupon everything is fine, and the login screen is displayed as it should. 

My gut feeling is that this is screen driver related, but am not 100% sure. This problem has appeared since putting KDE on the system, and it worked fine before. It's probably worth saying that if I choose to boot into Unity from the boot screen then I get into Unity fine, but if I try to logout then the same problem appears. 

This isn't a biggie (it doesn't stop me using the machine), but it is a nuisance. 

All help welcomed - thanks. 


Oli.

ETA: I have an ATI on-board graphics card, and it's an AMD 64-bit installation. I am using the proprietary ATI drivers.

---

### Post by sanderd17 on 2011-11-08
can you press CTRL+ALT+F1, log in and execute
```

sudo rc.d restart kdm

```

Then (if the login manager doesn't display automatically) press CTRL+ALT+F7 or F8.

---

### Post by zcacogp on 2011-11-08
Sanderd17, 

Hello again and thank you again - you helped on my previous thread as well! 

It went into TTY fine, but didn't recognise the command rc.d However, typing that line without the rc.d (i.e. 'sudo restart kdm') killed the TTY session and took me back to the normal login screen. Which was good and meant I didn't need to re-start (again!) 

At a guess, this means that kde isn't restarting properly when I logout. Can this be changed? (Or am I barking up the wrong tree?) 

Thanks again for your help. 


Oli.

---

### Post by sanderd17 on 2011-11-08
> **zcacogp said:**
> Sanderd17, 

Hello again and thank you again - you helped on my previous thread as well! 

It went into TTY fine, but didn't recognise the command rc.d However, typing that line without the rc.d (i.e. 'sudo restart kdm') killed the TTY session and took me back to the normal login screen. Which was good and meant I didn't need to re-start (again!) 

At a guess, this means that kde isn't restarting properly when I logout. Can this be changed? (Or am I barking up the wrong tree?) 

Thanks again for your help. 


Oli.

Hmm, I wonder why rc.d isn't used in Ubuntu.

Anyway, I don't know enough of KDE to know what's the problem is, but maybe you can execute the command at logout. I'm gonna look into this.

---

### Post by zcacogp on 2011-11-08
Executing the command at logout would seem to be an answer. I'll see what I can find out about doing this. Let me know if you come across anything when you look into it - thanks. 

Anyone else have any ideas? Do chip in - thanks!


Oli.

---

### Post by sanderd17 on 2011-11-08
Apparently this isn't so easy. I've found a post about logging out of shells: [http://www.cyberciti.biz/faq/linux-unix-run-commands-when-you-log-out/](http://www.cyberciti.biz/faq/linux-unix-run-commands-when-you-log-out/)

Maybe you can try the .logout file, or the .profile thing.

But for graphical interfaces it's difficult: [http://askubuntu.com/questions/5200/how-can-i-automatically-run-a-command-when-i-log-out](http://askubuntu.com/questions/5200/how-can-i-automatically-run-a-command-when-i-log-out)

The above is an explanation for Gnome, but one for KDE could also be made.

And an extra problem is that the command has to be run with a "sudo" which means you will have to enter your password.

---

### Post by zcacogp on 2011-11-08
Hmmm. I can't be the first person to have had this problem - I wonder whether I have broken something, necessitating this extra work.

In fact, it worked originally (before I had kde) and therefore I **DO **seem to have broken it! 

Thanks for the links you posted. I'll have a play around and see what I can make work. 


Oli.

---

### Post by Seb71 on 2011-11-08
I have a similar garbled screen at starting and at shutdown (in my case, it looks like some zebra stripes - vertical black and white stripes). Using Ubuntu 11.10.

---

