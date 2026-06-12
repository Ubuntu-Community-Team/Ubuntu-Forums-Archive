---
title: "How to eliminate constant password logins?"
date: 2011-02-19
forum: General Help
---

### Post by jiminoregon on 2011-02-19
Very often I have to leave my computer for a few minutes while in the process of downloading files, or just to get a cup of coffee, and when I come back, I have to re-enter my password to continue.  This level of security is unnecessary since I am the only one here, and there is no danger of anyone ever messing with my PC. How can I eliminate these annoying login requests?  One reason I am trying to get away form Windows is to have the computer do what I want, and not what other people think I want. I have been experimenting with various Linux OSs and several versions of Ubuntu, and this is an annoyance in every one I try.

---

### Post by janthonywj on 2011-02-19
I agree, however I think it's easy to disable the password login from resuming the screen. I think unchecking the "lock screen when screensaver is active" option under screensaver preferences will take care of that one. 

I would like not to have to enter a password with every app install or anytime I need root privileges, but this isn't a huge deal. I like knowing Ubuntu cares about security anyway. And this feature helps me keep people in check when I install Ubuntu for them on their machines when they come to me with problems. I suspect they would find ways of screwing up the OS quickly if I couldn't keep them from touching most things. But, as for my computer, I'm the only one that touches it.

---

### Post by gerowen on 2011-02-19
**To disable password protected screensaver:**

System -> Preference -> Screensaver
Uncheck "Lock screen when screensaver is active".

**To disable password protected login:**
System -> Administration -> Login Screen
"Unlock" the window, then select the user you want to log in as automatically.

OR
System -> Administration -> Users and Groups
Click "Advanced Settings", highlight your user account, next to password click "Change".  Check the box that says, "Don't ask for password on login".

This may cause issues with your encrypted passwords so you may have to go clear the password or set up unencrypted storage of passwords.

**To disable password protection for executing administrative tasks: (NOT RECOMMENDED)**
Edit /etc/sudoers with:
```

sudo gedit /etc/sudoers

```

Scroll down until you see:
root	ALL=(ALL) ALL

Enter a new line below that and enter the following:
*username*    ALL = NOPASSWD: ALL

Where *username* is your username.  Reboot your computer and you should be able to execute root commands without prompting.  However please note that this is VERY dangerous, as in Windows XP virus dangerous.  If you happen to contract some funky malware it would have full rights to execute any command as root without prompting you.  There are other ways to make it a little easier, you can google sudoers for more information.

---

### Post by jwbrase on 2011-02-19
Is this a laptop or a desktop? If it's a desktop I'd say you're fine disabling locking the screen when the screensaver comes up (even on my laptop I have a delay between screensaver activation and locking), and even possibly setting up an autologin at boot-up, but on a laptop I'd recommend you have it lock the screen if left unattended and require manual login at boot up.

---

### Post by jiminoregon on 2011-02-19
Thank you all. So simple; why didn't I think of that. Special thanks to Gerowen for the info about the eliminating the password request for admin tasks.  As I said, I am the only one who uses/has access to this PC, so it will not be a problem.

---

### Post by Krytarik on 2011-02-19
> **jiminoregon said:**
> ...eliminating the password request for admin tasks.  As I said, I am the only one who uses/has access to this PC, so it will not be a problem.
LOL :p  I hope it remains that way!

Having the default password query active for administrative tasks not at least also keeps yourself aware to what you are about to do.

---

### Post by tgm4883 on 2011-02-19
> **jiminoregon said:**
> Thank you all. So simple; why didn't I think of that. Special thanks to Gerowen for the info about the eliminating the password request for admin tasks.  As I said, I am the only one who uses/has access to this PC,** so it will not be a problem.**

Until you get hit with some form of malware.

---

### Post by Anakunda on 2011-12-20
> **gerowen said:**
> There are other ways to make it a little easier, you can google sudoers for more information.

HI!! I would be very thankful if you can give some guide how to "make it little easier" as I'm constantly something installing, uninstalling, or just making some system changes, and EVERY time I'm prompted to reenter my (quite long) password. This is making me mad. If granting a superuser privilegues to my account is so dangerous as you say, which is the compromise way?

---

