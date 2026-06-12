---
title: "HELP! User name and password forgotten"
date: 2009-09-27
forum: General Help
---

### Post by stressfactor03 on 2009-09-27
How do i uninstall UBUNTV, my oldest son loaded it on our computer and he doesnt remember his user name or password.............I am really ticked off. unless theres away to reset it if possible?? any help.........my daughter would like to use it now............
 
I'll leave it installed but user name and password is a no go, nor does he remember which email he used.................
 
 
[EMAIL="stressfactor03@epix.net"]stressfactor03@epix.net[/EMAIL]
 
Mike SR
 
THANKS FOR ANY HELP.............

---

### Post by geirha on 2009-09-27
During boot, there'll be a 3-second timer telling you you can hit Esc to see a boot menu. Hit Esc when you see it, then choose the second entry, with (recovery mode), to get to a «Root shell». Once at the root shell command prompt, type ```
ls /home
```
This lists the home folders of all users, and they'll have the same name as the usernames. To reset the password on a user, type:
```
passwd *username*
``` repacing *username* with an actual username of course.

Ubuntu is generally case-sensitive, so make sure you type in the commands using the right case; e.g. «ls /home» will work, «LS /HOME» will not

---

### Post by drs305 on 2009-09-27
Let's start with the simplest.

Do you get the Ubuntu/grub menu when you power up the computer? If not, as it boots, hit the ESC key to reveal the menu. 

From the menu, select the Recovery mode, then select the one that boots to a root prompt.

At the prompt, type "ls /home"  (lowercase L, no quotation symbols)

This will show you the username(s) on Ubuntu. Show your son the username and see if that jogs his memory as to what the password might be.

Edit: No point in continuing since geihra's got you covered.

---

### Post by stressfactor03 on 2009-09-27
> **geirha said:**
> During boot, there'll be a 3-second timer telling you you can hit Esc to see a boot menu. Hit Esc when you see it, then choose the second entry, with (recovery mode), to get to a «Root shell». Once at the root shell command prompt, type ```
ls /home
```
This lists the home folders of all users, and they'll have the same name as the usernames. To reset the password on a user, type:
```
passwd *username*
``` repacing *username* with an actual username of course.
 
Ubuntu is generally case-sensitive, so make sure you type in the commands using the right case; e.g. «ls /home» will work, «LS /HOME» will not
 
Ok i didnt get the 3sec stuff but i did manage to get to the root menu also got to were it says to enter new password BUT keyboard stopped working.......once i got it right anyway.............so now i cant add new password............. ACk!!!!!!!!!!!!!!!!
 
 
Mike

---

### Post by stressfactor03 on 2009-09-27
> **drs305 said:**
> Let's start with the simplest.
 
Do you get the Ubuntu/grub menu when you power up the computer? If not, as it boots, hit the ESC key to reveal the menu. 
 
From the menu, select the Recovery mode, then select the one that boots to a root prompt.
 
At the prompt, type "ls /home" (lowercase L, no quotation symbols)
 
This will show you the username(s) on Ubuntu. Show your son the username and see if that jogs his memory as to what the password might be.
 
 
Hes at work, tried to ask him if he remembers it and said sorry dad i dont........... not int he best of moods here...........

---

### Post by stressfactor03 on 2009-09-27
Ok heres what i get
enter new Unix Password:
Retype new password:
 
Passwd: authenication info cannot be recovered
Passwd: password unchanged
 
 
 
 
 
 
 
 
> **stressfactor03 said:**
> How do i uninstall UBUNTV, my oldest son loaded it on our computer and he doesnt remember his user name or password.............I am really ticked off. unless theres away to reset it if possible?? any help.........my daughter would like to use it now............
 
I'll leave it installed but user name and password is a no go, nor does he remember which email he used.................
 
 
[EMAIL="stressfactor03@epix.net"]stressfactor03@epix.net[/EMAIL]
 
Mike SR
 
THANKS FOR ANY HELP.............

---

### Post by stressfactor03 on 2009-09-27
WHEEEEEEEEEEEW!!!!!!!!!!!
 
You guys are the best!!!!!!!!!!!! 
 
I made it in finally!!!
 
now i hate to ask, how do i remove it? he said something about windows quit working and thats why he had to load this program............
 
or is it very user friendly?
 
Mike

---

### Post by geirha on 2009-09-28
Ubuntu is among the most user-friendly linux distributions around. If you're used to windows, it may be a little bit hard to adapt, as Ubuntu does things a bit differently than windows. For a person that is new to computers as a whole, Ubuntu is just as easy to learn as Windows.

The major upside of Ubuntu (and linux in general) is that there is no need for antivirus software. Viruses are nearly non-existant for linux, so you can browse the web without fear of getting a trojan or similar.

If you decide to give Ubuntu a try, I recommend reading through the docs for the release you have installed at [https://help.ubuntu.com/](https://help.ubuntu.com/). It should cover the most common tasks you'll need.

If you decide you rather want Windows, then just pop in the windows CD, boot and install. Windows will happily erase Ubuntu for you ;)

---

### Post by ErikEhlert on 2009-09-28
> **stressfactor03 said:**
>  my oldest son loaded it on our computer and he doesnt remember his user name or password.............I am really ticked off. unless theres away to reset it if possible?? any help.........my daughter would like to use it now............
 

How did your son manage to already forget his username and password? It seems like a bit of a weird thing if he just installed it, plus if its a family computer, not his own personal computer, he would have told the rest of the family the password on.

Edit: Yeah, I think your Q has been A'd, just pop in the DVD you used to install, or go back to Windows if you wish, wait, no, don't go back.... just re-load Ubuntu already...

---

