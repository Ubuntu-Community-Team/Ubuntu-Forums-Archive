---
title: "Auth window broken?"
date: 2011-02-13
forum: General Help
---

### Post by sshh on 2011-02-13
I can't do anything that requires root privileges. The window appears, shakes for 0.5 seconds, and disappears. It says "Authentication failure" at the bottom, but my pass was OK at logon and I didn't even have time to type it. 
It started after I made a second user administrator. Making him a normal user would solve everything (I think), but I can't do it because I have to AUTHENTICATE and that exactly what I can't do. sudo via command line works perfectly. I'm desperate.
How do I make this return to normal?

---

### Post by ajgreeny on 2011-02-13
The command ```
userdel username
``` will remove the user who seems to be causing the problem, but I am sure there must be a simple way to remove that user from the admin group rather than delete him or her completely, I just can't find it.

---

### Post by JKyleOKC on 2011-02-13
> **sshh said:**
> I can't do anything that requires root privileges. The window appears, shakes for 0.5 seconds, and disappears. It says "Authentication failure" at the bottom, but my pass was OK at logon and I didn't even have time to type it. ... sudo via command line works perfectly. I'm desperate.
How do I make this return to normal?I had a very similar problem a few days ago, except that the window stayed open, accepted my password, and then rejected it as incorrect. The same password was perfectly okay to sudo, though.

Mine turned out to be that I had unchecked PolicyKit from my list of autostart programs, so that it never actually did the password check from the GUI window. Putting PolicyKit back in the autostart list fixed it. Yours might be something similar.

---

### Post by ajgreeny on 2011-02-13
> **JKyleOKC said:**
> I had a very similar problem a few days ago, except that the window stayed open, accepted my password, and then rejected it as incorrect. The same password was perfectly okay to sudo, though.

Mine turned out to be that I had unchecked PolicyKit from my list of autostart programs, so that it never actually did the password check from the GUI window. Putting PolicyKit back in the autostart list fixed it. Yours might be something similar.
Interesting!

I don't even have policykit in my startup applications list in 10.04 so could not uncheck it if I wanted to, and I have never had a problem like this.

---

### Post by JKyleOKC on 2011-02-14
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1687274](http://ubuntuforums.org/showthread.php?t=1687274) 

It may help. I'm running Xubuntu, not Ubuntu, so everything about the window manager is a bit different. However the solution that CoffeeCat offered in that thread seems to be for standard Ubuntu!

---

### Post by sshh on 2011-02-14
****Thank you for your answers. 
Made the user a normal user by editing a file, but the problem continued. 
I looked around and found a way to launch Software center, it's
**gksu software-center**. And It works fine. But no progress anywhere else. 
 
Also, right now the window just stays open, with no text field to put the password, and I can't close it by pressing cancel or authenticate. 

Also with gksu software-center I get this:
> 
2011-02-14 16:28:07,803 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2011-02-14 16:28:07,803 - root - WARNING - failed to add sca db Couldn't detect type of database

But it works fine. I'm totally lost.

EDIT.
Now the window is back again as it was. Shakes for some moments and disappears. 
Also ,this is the output of **id:**
> 
uid=1000(sh) gid=1000(sh) groups=1000(sh),4(adm),7(lp),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)
 in case it helps.

Also I have too no policy kit in my Startup.

Also, sudo-mode IS checked, so that is not the problem. 
It's supposed to be checked, right?

---

### Post by JKyleOKC on 2011-02-14
Yes it IS supposed to be checked. I'm out of ideas. Hopefully someone else will chime in with some fresh thoughts!

---

### Post by sshh on 2011-02-16
I'm desperate.
So far the closest thing is editing the menu and adding gksudo at the beginning of everything that requires me to be root. But still, it does not always work ("Users" freezes, for example). Right now I'm learning the command line at a faster pace than before.
But still, if anyone has any suggestions, I will receive them very warmly. 

Also, before this started, I changed my password. It couldn't decrypt my Home Folder, and I had to change it back again. The problems started at the next boot. Maybe it's caused by this?
Also is there a way to reset Ubuntu without having to reinstall?

---

### Post by timjohn7 on 2011-04-06
I'm afraid that I can't help, but can offer empathy as I have exactly the same problem.

I have a new hard drive and installed 10.10 fresh.  I then tried to restore a snapshot of my old hard drive (also 10.10 updated) and fear that I have caused some serious devastation.  I have exactly the same symptoms.  sudo works fine in terminal, Authentication Panel shakes horizontally for 0.5 seconds and then disappears.  No install from Software Centre and no updates from the Update Manager.

Any help would be appreciated!

---

### Post by sshh on 2011-04-07
> **timjohn7 said:**
> I'm afraid that I can't help, but can offer empathy as I have exactly the same problem.

I have a new hard drive and installed 10.10 fresh.  I then tried to restore a snapshot of my old hard drive (also 10.10 updated) and fear that I have caused some serious devastation.  I have exactly the same symptoms.  sudo works fine in terminal, Authentication Panel shakes horizontally for 0.5 seconds and then disappears.  No install from Software Centre and no updates from the Update Manager.

Any help would be appreciated!
Hi. Right now I'm reinstalling Ubuntu on my hd. 
About software center, it works as
> gksudo software-center 
 in terminal, and some other commands do too.

---

