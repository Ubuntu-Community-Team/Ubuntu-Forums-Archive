---
title: "size matters"
date: 2010-09-09
forum: General Help
---

### Post by Skriblinmatt on 2010-09-09
Although I have found similar issues, I have not found a solution to my exact problem.

I replaced Ubuntu with 10.4 and the sizes of everything got weird.  At first everything was small.  The icons and the fonts and the pointer.  So I searched the forum and found some adjustments that could be made like going into System>Preferences>Appearances>resolution or System>Preferences>Monitor resolution and some were I found a way to adjust my cursor size (although I have no idea where).  I also got another tip to use ctrl+scroll(mouse wheel) to zoom in and out on firefox.

Now EVERYTHING is a mess.  One thing will be huge and the next tiny. Like, the text I am typing now is so small I can hardly see it, if I zoom in the title window is too big to fit on the monitor.  It's not just the browser though, icons on my panels are like pin points.  It's as if my computer has no idea how big my monitor is.

What's up?

---

### Post by Skriblinmatt on 2010-09-10
Still ave not solved this problem or had any help or found the solution by searching the forums .  Can someone please help me out?

---

### Post by Rubi1200 on 2010-09-10
> **Skriblinmatt said:**
> Although I have found similar issues, I have not found a solution to my exact problem.

I replaced Ubuntu with 10.4 and the sizes of everything got weird.  At first everything was small.  The icons and the fonts and the pointer.  So I searched the forum and found some adjustments that could be made like going into System>Preferences>Appearances>resolution or System>Preferences>Monitor resolution and some were I found a way to adjust my cursor size (although I have no idea where).  I also got another tip to use ctrl+scroll(mouse wheel) to zoom in and out on firefox.

Now EVERYTHING is a mess.  One thing will be huge and the next tiny. Like, the text I am typing now is so small I can hardly see it, if I zoom in the title window is too big to fit on the monitor.  It's not just the browser though, icons on my panels are like pin points.  It's as if my computer has no idea how big my monitor is.

What's up?
>  I replaced Ubuntu with 10.4
From what? 
Did you have this issue with the previous version?
What graphics card do you have installed?
Do you have desktop effects turned on?

We need as much information as you think might be relevant about hardware etc.

---

### Post by earthpigg on 2010-09-10
is this problem present with other logins? if you need to, create another user account on the computer and log in. see if things are still messed up there.

the answer will help us narrow down the problem.

---

### Post by hudsonl on 2010-09-10
> **Skriblinmatt said:**
> Still ave not solved this problem or had any help or found the solution by searching the forums .  Can someone please help me out?

You might try a test ... try creating a new user and see if the defaults are good.

> adduser johndoe

Log out and then log in as your new user.

If it looks good ... then you can try re-creating gnome config for the original user.

While logged in as your new user (johndoe) ...

(If the username that is not working is "matt")

> sudo mv ~matt/.gconf ~matt/.gconf_sav

Log out as the new user (johndoe) ... and back in (matt)

---

### Post by Skriblinmatt on 2010-09-10
> **Rubi1200 said:**
> From what?
Did you have this issue with the previous version?
What graphics card do you have installed?
Do you have desktop effects turned on?

We need as much information as you think might be relevant about hardware etc.
1). From Ubuntu 9.something, I don't know what it was, it was brown.
2). Did NOT have this problem before.
3). It's an Nvidia EX845256L
4). Visual effects = none.

Created a new user account.  Everything is small in it.  Like tiny small. :(

---

### Post by borth92 on 2010-09-10
try installing the proprietary drivers through system>administration>hardware drivers

---

### Post by Skriblinmatt on 2010-09-10
THANK YOU BORTH  I think you're right.  I don't know why I didn't think of that.  I believe you are right because the recommended driver is not currently activated, however when I attempt to activate it I get this system error alert "SystemError: Failed to lock /var/cache/apt/archives/lock"

What does that mean?

---

### Post by Skriblinmatt on 2010-09-10
Just a little more info here, if it helps.  I ran 'who -r' and it showed the run level as level 2 so I used 'su -l' then 'init 5' to change it to 5 and it didn't change anything, so I rebooted and ran 'who -r' again and it was back at 2.

---

### Post by earthpigg on 2010-09-10
> **Skriblinmatt said:**
> THANK YOU BORTH  I think you're right.  I don't know why I didn't think of that.  I believe you are right because the recommended driver is not currently activated, however when I attempt to activate it I get this system error alert "SystemError: Failed to lock /var/cache/apt/archives/lock"

What does that mean?

it means that you already have a package manager going. make sure software center, synaptic, update manager, and any terminal that's running "apt-get" are all closed.

---

