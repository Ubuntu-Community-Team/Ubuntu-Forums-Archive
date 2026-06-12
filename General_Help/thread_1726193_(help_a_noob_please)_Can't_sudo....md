---
title: "(help a noob please) Can't sudo...?"
date: 2011-04-10
forum: General Help
---

### Post by chromium48 on 2011-04-10
I recently installed Ubuntu on my CR-48 and everything has been working fine, until I tired to use the terminal to install something. I tried to do the sudo thing and I typed in my password correctly, and I got this error: 
[IMG]http://f.cl.ly/items/250J13031G1j0K103i1p/Screenshot-westin@cr-48:%20~.png[/IMG]

Anything else you suggest me trying? I know I have entered my password correctly each time I've done this, but I get the same error!

Thanks in advance for the help!

-westin

---

### Post by Quackers on 2011-04-10
Try something simple like ```
sudo apt-get update
``` then enter your password, making sure that no shift lock or number loack is switched on at the keyboard.
What happens?

---

### Post by linuxman94 on 2011-04-10
Use sudo su no just su.  Su expects the root password, whereas sudo su expects the user password.  If you just need to run one command, just type sudo followed by the command.

Example:
```
sudo apt-get install <application>
```

---

### Post by ~Plue on 2011-04-10
su is a little different then sudo..
su is used to change to the shell of another user, and when used without any other options, it defaults to the root account which does not have a password set by default in ubuntu. so you cannot use it directly

but if sudo is working, you can use *sudo su *or* sudo -i - *using *your* password to get to a root shell

---

### Post by KegHead on 2011-04-10
Hi!

Make sure all your letters are lowercase.

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

KegHead

---

### Post by chromium48 on 2011-04-10
Thanks guys! **sudo su** works :D

---

### Post by KegHead on 2011-04-10
Hi!

congrats and welcome to the group!

Next time try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

Enjoy!

Make sure you close out this thread!

KegHead

---

### Post by Quackers on 2011-04-10
Good. Just sudo should be good though :-)
Please mark the thread as solved using the Thread Tools near the top of the page.

---

### Post by chromium48 on 2011-04-10
> **Quackers said:**
> Good. Just sudo should be good though :-)
Please mark the thread as solved using the Thread Tools near the top of the page.

done, thanks again!

---

