---
title: "session lasting less the 10 seconds?!?"
date: 2010-01-17
forum: General Help
---

### Post by funkyguy4000 on 2010-01-17
Okay so i'm having an issue,  I had an earlier thread but it kind of died.
I need some help here.

The earlier thread is here
[http://ubuntuforums.org/showthread.php?p=8682741#post8682741](http://ubuntuforums.org/showthread.php?p=8682741#post8682741)

basically what happens is when i log into a normal session it says:

Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try loggin in with one of the failsafe sessions to see if you can fix this problem.

and then the details (~/.xsession-errors file)

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for local=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir. permission denied.


I do have a live cd of the Ubuntu version i am running 9.04 although i am not an admin.

---

### Post by Kenno on 2010-01-21
Did you try this?
```

sudo mkdir -p /tmp
sudo chmod 1777 /tmp
```

---

### Post by funkyguy4000 on 2010-01-22
no i did not.  I can't do sudo commands since i'm not an admin

---

### Post by JiuJitsu500 on 2010-01-22
Are you on a network where you are not the admin? If it's your computer it's too easy to set a root password, and you are already the default admin... sudo isn't a permanent change, it's just telling the computer to act as a super user for one instance, you should always have sudo authority if it is your pc...

If it's not yours though I'll butt out :)

---

### Post by Kenno on 2010-01-22
> **funkyguy4000 said:**
> no i did not.  I can't do sudo commands since i'm not an admin
**Edit 1:** just to get this straight: when you get your login screen, instead of logging in, press CTRL-ALT-F1 for a textual terminal. There, you log in using your normal user name and password. Then you can type the above commands. When sudo asks you for a password, you have to give it *your normal* password, not the root or "admin" password. After you finish that, you can press CTRL-ALT-F7 to go back to your login screen.

**Edit 2:** also, it looks like [people have shown you another way to run commands as "admin" before...]("http://ubuntuforums.org/showthread.php?t=1370168#post8595816")](*,):lol:

**Edit 3:** on closer inspection of that earlier thread of yours, it's entirely possible that your disk is still detecting errors and mounting as read-only. If that's the case, the above commands won't help. But try them anyway.

---

