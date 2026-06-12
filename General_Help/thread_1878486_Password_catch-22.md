---
title: "Password catch-22"
date: 2011-11-09
forum: General Help
---

### Post by StarStrider on 2011-11-09
I apologize for posting about this issue, as I realize it's been discussed before; I was just reading a thread about it but now I can't find it again and at this point I'm just too frustrated/pissed off to spend another half hour grappling with it.

Because I'm not the only person who uses this computer (64-bit btw), and rather than opting for multiple log-ins or a simple password because I guess I'm an idiot, I decided to turn the password off. Not realizing, of course, that Ubuntu would ask me for the password when I went to install new programs. So, what do I do? I can't change the settings because it asks for a password I no longer have.

I tried using the "sudo password username" command someone mentioned in terminal, and it simply asked me for the password that doesn't exist. I tried the ctrl+alt+F1 but it insisted that sudo password username wasn't a command. I then tried it in the recovery console, but got the same problem.

Also, I am very new to Ubuntu. I am (still) a Win7 user, but my Win7 apparently forgot what a network adapter was and has all my malware and tech support lines stumped, so I turned to Ubuntu to use in the meantime (plus I was just using it on my laptop). Long story short, assume I don't know what you're talking about.

Thanks, and again, I'm sorry for zombiefying this topic. DX

---

### Post by Toafan on 2011-11-09
> **StarStrider said:**
> 
I tried using the "sudo password username" command someone mentioned in terminal, and it simply asked me for the password that doesn't exist. I tried the ctrl+alt+F1 but it insisted that sudo password username wasn't a command. I then tried it in the recovery console, but got the same problem.


For what it's worth, the terminal command to reset the password is:```
passwd
```Don't worry about it having thrown you of, that's the kind of thing that you have to know.

The guy behind [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) has a good tutorial to reset your password from the recovery mode, I haven't taken the time to find it and link you directly to it though (sorry 'bout that).
Basically, you go into recovery mode and do: ```
passwd *username*
``` and put in a new password at the prompts (though I bet you've found a tutorial on this already).

After this, I'd recommend setting up individual accounts.  They really do work better for multi-user computers, and that's the kind of thing Linux is designed for.

Just occured to me (sorry for the long post), if there is no password (as opposed to not needing the password to log in) then sudo should work without needing the current password.

---

### Post by WorMzy on 2011-11-09
Boot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode"), drop to root shell, and run:

```
passwd [COLOR="Red"]username[/COLOR]
```

Replacing [COLOR="Red"]username[/COLOR] with your actual username.

EDIT: As Toafan said, you can probably do it without recovery mode.

---

### Post by StarStrider on 2011-11-09
Thank you, Toafan! That tutorial was very helpful. For whatever reason when I initially tried the sudo command it did ask for my password, but maybe I just frelled it up anyway.

Haha, I very nearly lost the few marbles I had left. XD

---

