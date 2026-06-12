---
title: "run commands on session logout?"
date: 2011-10-10
forum: General Help
---

### Post by Atamisk on 2011-10-10
Hello, 

How would i go about automatically running a command when the i log out of my session? I'm using lightDM now, so the idea of modifying /etc/X11/gdm/Postsession/Default won't work...

Any help is appreciated, 
--Aaron

---

### Post by hwttdz on 2011-10-11
How do you logout?

What about adding something to .bash_logout?

You can do some runlevel stuff if you want it to run when runlevels change.

---

### Post by grimmo on 2011-10-14
what if I want the script to only run when i logout from a graphical session but not when I am using the console?
Example:
I need procmail to process some email messages in a special way, not possible using just thunderbird filters, thus I need to get the mail using fetchmail have them processed by procmail and then pushed to the user mailbox spool file, from where they will be read by thunderbird. I want the mail to be fetched at specific intervals, so fetchmail needs to be started as a daemon when I login via X (simple, just add the script to startup applications) and to be killed as soon as I logout from X (using gdm/postsession worked flawlessy) this way I can also login on virtual consoles and avoid fetchmail daemon being started twice or killed when my X session is still active. 
This is the reason .bash_logout is the wrong tool.
Of couse I could write a complex shell script to check whether X is running before killing the fetchmail daemon.. but it's kludgy and ugly.

---

### Post by hwttdz on 2011-10-14
Looks like it's been fixed: [https://bugs.launchpad.net/lightdm/+bug/602505](https://bugs.launchpad.net/lightdm/+bug/602505) 

I suppose now you're waiting to get this version from the repos.

---

