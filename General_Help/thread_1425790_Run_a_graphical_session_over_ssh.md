---
title: "Run a graphical session over ssh"
date: 2010-03-09
forum: General Help
---

### Post by Dragonbite on 2010-03-09
I'm not even sure this is possible, but I've heard I can ssh into a remote computer and run an X session for de/gui possibilities?

Obviously would need a desktop or window environment for the gui aspect but what else?  And how do I start it?

Let's assume I have a Gnome Ubuntu which is acting like a LAMP server, how would I go about setting it up and running it?

---

### Post by Ilalmi on 2010-03-09
Does this help you?
[http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29](http://www.techotopia.com/index.php/Displaying_Ubuntu_Linux_Applications_Remotely_%28X11_Forwarding%29)

---

### Post by tgalati4 on 2010-03-09
Have one Ubuntu desktop running on your local network (at say IP 192.168.1.110).

sudo apt-get install openssh-server

Have another Ubuntu machine running; also on the same network.  

Open a terminal:

ssh -2 -Y dragonbite@192.168.1.110

gnome-panel &

See what happens.

---

### Post by doas777 on 2010-03-09
thats kewl. have to look at that tonight.;

---

### Post by geirha on 2010-03-09
Using just ssh with X11-forwarding does not require a desktop environment on the server. Just the necessary X libs and the app you want to run. 

If you do want to log into a gnome session on the server, [FreeNX](https://help.ubuntu.com/community/FreeNX) is a good option.

---

### Post by howlingmadhowie on 2010-03-09
> **Dragonbite said:**
> I'm not even sure this is possible, but I've heard I can ssh into a remote computer and run an X session for de/gui possibilities?

Obviously would need a desktop or window environment for the gui aspect but what else?  And how do I start it?

Let's assume I have a Gnome Ubuntu which is acting like a LAMP server, how would I go about setting it up and running it?

on the default ubuntu install you'll have to activate X11forwarding in /etc/ssh/ssh_config and /etc/ssh/sshd_config.

while you're about it, you can deactivate root login :)

---

