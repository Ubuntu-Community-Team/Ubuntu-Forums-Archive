---
title: "Removing current user and shutdown from toolbar"
date: 2012-05-28
forum: General Help
---

### Post by The-Master on 2012-05-28
Hi. I was wondering if there was any way that I could remove the part in the top bar in unity that has the person icon and then the username and also the red icon next to it that lets you log out and shut down?

I've done a lot of searching to try and find an answer but I'm stumped.

Thanks in advance.

---

### Post by Zukaro on 2012-05-28
Removing the guest user will remove the username from the toolbar (unless you have other users on your computer).  To remove the guest user, type "sudo gedit /etc/lightdm/lightd.conf" into the terminal (gedit can be replaced with the text editor of your choice).  Then once the file opens, at the bottom add "allow-guest=false" and then restart.

As for removing the power button, I don't know how to do that.  Also, my fix for the username only works if you're the only user on your computer.

---

### Post by MadmanRB on 2012-05-28
Ubuntu tweak offers most of what you are talking about, though no shutdown menu removal.

---

### Post by The-Master on 2012-05-29
Thanks very much guys. I don't think there is an easy way to remove the shutdown icon but I've used a dconf-editor to do what I think is the same as what Zukaro was suggesting only with a GUI. I tried ubuntu tweak but it didn't work for me. Thanks for the help though. Much appreciated!

---

