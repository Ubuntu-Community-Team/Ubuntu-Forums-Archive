---
title: "Light blue screen of death after loading Gnome desktop"
date: 2012-08-15
forum: General Help
---

### Post by TideMan on 2012-08-15
I recently upgraded from 10.04 to 12.04 Ubuntu, but I cannot get used to the Unity desktop, so I decided to use Gnome instead, which I loaded from the Software Center (or whatever it's called).

BUT, now when I logon, I get a light blue screen with a few letters here and there, but nothing else.

Fortunately, I can run headless using puTTY.
So now the question is: how do I revert to the Unity desktop?
Can anyone help?

---

### Post by electricmaster on 2012-08-15
On the login screen next to your name, click on the little Gnome "foot" icon and select Ubuntu  from the list

---

### Post by TideMan on 2012-08-15
I don't get a login screen.
It jumps straight to the blue window.

---

### Post by TideMan on 2012-08-15
I've solved my problem, but just in case someone else goes down this path, I'll document what happened.
1.  I downloaded the Gnome desktop from the Software Center
2.  My system was on auto login and when I re-booted, I ended up with a light blue screen with a few odd letters scattered about and no mouse.
3.  I was able to get a terminal using Ctl-Alt-F2 and edit:
sudo nano /etc/lightdm/lightdm.conf
to remove the autologin.
4.  Now, when I reboot I get a login panel and clicking the ubuntu symbol in the top right corner gives me a list of possible desktops.  Choosing Gnome returns me to the light blue screen, but all other desktops work OK.

Why the Gnome desktop doesn't work, beats me.

---

