---
title: "Users and Groups EMPTY!"
date: 2010-03-05
forum: General Help
---

### Post by DedMoroz on 2010-03-05
When I go into System > Admin > User and Groups and then unlock and manage my list, it is completely empty. How can I fix this?? Ive never had this happen to me before.

Yet, if I go into a terminal and type groups, I can see my list of groups! Very frustrating!

Thanks for any help!

---

### Post by jmichelsen on 2010-03-05
I don't use the GUI much, but seeing as the groups and users show up on the command line, maybe try running the groups app as root.

in command line, type 

```
gksudo users-admin
```

I don't even recall if you are already prompted for root when opening that app from the menu, or if users-admin is still the application name, but give it a whirl and see if that helps.

---

### Post by DedMoroz on 2010-03-05
> **jmichelsen said:**
> I don't use the GUI much, but seeing as the groups and users show up on the command line, maybe try running the groups app as root.

in command line, type 

```
gksudo users-admin
```

I don't even recall if you are already prompted for root when opening that app from the menu, or if users-admin is still the application name, but give it a whirl and see if that helps.

Thanks for the reply. In the Users & Groups there in an unlock key to click and type in the password. Same as running root. But i did try in terminal and get the same outcome... nothing listed in the group.

---

### Post by DedMoroz on 2010-03-11
BUMP

I cannot use my USB scanner in Virtual Box now. I want to check my users and groups, but again, its BLANK. I also notice now that after typing in my password and clicking manage, the area where my groups should be listed is a light pink color.

Any tips? This is not good.

---

### Post by geirha on 2010-03-11
Hm. Could you show a screenshot of how the window looks? (Alt+PrintScreen takes a screenshot of the active window)

---

### Post by DedMoroz on 2010-03-11
> **geirha said:**
> Hm. Could you show a screenshot of how the window looks? (Alt+PrintScreen takes a screenshot of the active window)

Sure no prob. Here is what I am getting after inputing my pass and clicking manage...

[IMG]http://www.1916home.com/usersgroups.png[/IMG]

The groups list is blank. On my screen the whole area is pink, but in th image there is just a bit of pink at the bottom of the group box.

---

### Post by DedMoroz on 2010-03-11
Also, here is what I get when I type "groups" in a terminal. I can see my groups here... including usbusers which I wanted to look into and see if virtual box is enabled.

[IMG]http://www.1916home.com/terminalgroups.png[/IMG]

---

### Post by DedMoroz on 2010-03-11
I'm using 9.10 Karmic, which has been upgraded and upgraded and upgraded all the way from 8.04. All has worked fine, until a month or so ago when I installed Kubuntu on my system to check it out. Lots of error messages since then, so I did my best to uninstall it (following some tips in a thread I posted here).

---

### Post by geirha on 2010-03-11
I seem to remember a case where an app didn't work properly when using a different theme. Don't know if it was users-admin, but it's worth a shot to check it out. Close it, change to the default Ubuntu theme, then try running users-admin again.

---

### Post by DedMoroz on 2010-03-11
> **geirha said:**
> I seem to remember a case where an app didn't work properly when using a different theme. Don't know if it was users-admin, but it's worth a shot to check it out. Close it, change to the default Ubuntu theme, then try running users-admin again.

Thanks. No go on that for me. I turned off all visual effects, switched back to default theme and disabled screenlets. Rebooted and still no go.

---

### Post by geirha on 2010-03-11
I'm unable to reproduce it myself. It's showing groups as it should for me. If you run users-admin from a terminal, does it output anything (in the terminal) when you click the Manage groups button?

Also, verify the integrity of the group files with the grpck command in a terminal.
```
sudo grpck -r
```
No output == good.

---

### Post by DedMoroz on 2010-03-11
> **geirha said:**
> I'm unable to reproduce it myself. It's showing groups as it should for me. If you run users-admin from a terminal, does it output anything (in the terminal) when you click the Manage groups button?

Also, verify the integrity of the group files with the grpck command in a terminal.
```
sudo grpck -r
```
No output == good.

Nope. I get nothing interesting (nothing at all) by doing users-admin from the terminal.

When I do grpck command I get this:

> invalid group file entry
delete line 'none /proc/bus/usb usbfs devgid=124,devmode=664 0 0'? No
grpck: no changes


Google isnt pulling anything up on that one. I wonder how to edit my group file.

Would this work? 

> sudo gedit /etc/group

---

### Post by geirha on 2010-03-11
> **DedMoroz said:**
> 
When I do grpck command I get this:


Oh, now that sounds like a culprit. That line does not belong in /etc/group, it makes sense in /etc/fstab, but not /etc/group.

```
gksudo gedit /etc/group
```

Remove that line.

Or run ```
sudo grpck
``` (without the read-only option) and tell grpck to delete it for you.

---

### Post by DedMoroz on 2010-03-11
My Users & Groups WORKS AGAIN!! Woohooo! Thanks for guiding me!

---

