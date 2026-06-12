---
title: "Help!!! Last updates broke my system!"
date: 2006-06-17
forum: General Help
---

### Post by homersbrain on 2006-06-17
Where do I start?

1. Menus now have no icons next to them.

When I try to change theme I get:

> The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly.

2. The mouse moves about an inch on screen for every foot on the desk!

Going to mouse and changing things makes no difference.

3. Synaptic or anything that requires a password wont work.

[HTML]Failed to run /usr/sbin/synaptic as user root:
 Wrong password.[/HTML]

4. The terminal now looks really poor. Gone are the menus to configure it.

What on earth has happened!?!

---

### Post by homersbrain on 2006-06-17
bump!

---

### Post by homersbrain on 2006-06-17
Anyone?

---

### Post by purfier on 2006-06-17
My menu to change work spaces, and no menu to move apps to workspaces.

---

### Post by Nekrataal on 2006-06-17
Yeah, same here, not same problems, but my system is also broken since last update...What Happened?

---

### Post by homersbrain on 2006-06-18
I have no idea how to fix these problems. I have filed a bug report:

[https://launchpad.net/bugs/50133](https://launchpad.net/bugs/50133)

Please add to it to confirm.

---

### Post by gamerteck on 2006-06-18
This has happened to me as well. 

I installed **Automatix** and updated a few things, shutdown my PC to run some errands and when I booted back up I have the exact same issue as you.

---

### Post by homersbrain on 2006-06-18
The bug report has been merged to:

[https://launchpad.net/bugs/50150](https://launchpad.net/bugs/50150)

Please add your information to it as necessary to help speed up the fix as its still classed as unconfirmed.

I hope we do get a fix otherwise I see no option but a complete reinstall!

---

### Post by joe343 on 2006-06-18
Hi I'm having problems too since the last updates... (playing dvd movies)
Here's the thread:
[http://www.ubuntuforums.org/showthread.php?t=199089](http://www.ubuntuforums.org/showthread.php?t=199089)

---

### Post by gamerteck on 2006-06-18
I ran the 
```

sudo apt-get upgrade
```

Which seems to have fixed the issue regarding the desk panels where as before I minimized and the windows would disapear, now the properly dock.

I also notcied that my time format has reverted back to the correct display. Before it was shown just
**4:37 PM** and now it is shown **Sun Jun 18, 4:37 PM**
------------------
I still can't run any applications that require input of the root password

I still get the theme error.

My keboard is still messed up where I can't hold down a key to repeat it I have to tap it repeatedly.

Still can't open trash bin

All my menus are still missing all the icons next to the application name.
------------------

It's like my profile and security persmission where just wiped out.  Really funky, i'm a total newbie to Linux so i'm at a loss but still have been searching for hours for some sort of fix.

---

### Post by Haegin on 2006-06-21
I had this and for me at least it was linked to the schemas not being registered.
Solution:
1. ```
cd /usr/share/gconf/schemas
```
2. ```
sudo gconf-schemas --register *.schemas
```

That should register all the schemas again and for me it got the mouse working and the themes working and synaptic works ok. My menus seem fine but I don't know if they were broken as I fixed it pretty quick.

Hope this helps

EDIT:
I have attached a script for it. Just download it, rename it to .sh, make it executable and run it. It will ask you for your password to run the gconf-schemas command.

I haven't tested it so please report problems and fixes if possible.

---

### Post by homersbrain on 2006-06-21
Blast! I had just reinstalled my system! But it will be useful if it happens again.  Does it work for anyone else?

Many thanks HP!

---

### Post by driverkt on 2006-06-21
[QUOTE=homersbrain]Blast! I had just reinstalled my system! But it will be useful if it happens again.  Does it work for anyone else?

Many thanks HP![/QUOTE]

I can confirm that this works for me.

---

### Post by redyaky on 2006-07-20
> **Human Prototype said:**
> 
Solution:
1. ```
cd /usr/share/gconf/schemas
```
2. ```
sudo gconf-schemas --register *.schemas
```


You are the man! Many Thanks.

---

### Post by TopasPV on 2007-05-25
Great! It works.

Thanks a lot :)

---

