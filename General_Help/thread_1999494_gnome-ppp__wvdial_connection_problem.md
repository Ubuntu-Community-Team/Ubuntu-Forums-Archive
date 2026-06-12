---
title: "gnome-ppp / wvdial connection problem"
date: 2012-06-08
forum: General Help
---

### Post by rdh61 on 2012-06-08
Hi,

I am running Lubuntu 12.04 and connecting to the Internet with a USB modem. 
In order to connect, I prefer to use a GUI rather than typing commands in the terminal. I am trying to use gnome-ppp, a front end for wvdial. However, wvdial will only work if I open it as sudo, therefore gnome-ppp will not work unless I do likewise. So my objective of not messing about with command lines is defeated. If I try to connect as myself (not root), either with gnome-ppp or directly with wvdial, I get the following repetitive error message in the log / terminal:

"Unable to run /usr/sbin/pppd. 
Check permissions, or specify a "PPPD Path" option in wvdial.conf."

I'd appreciate help to sort this, assuming it can be sorted. Otherwise, what is the point of gnome-ppp?

Many thanks.

---

### Post by rdh61 on 2012-06-08
The answer is here: [https://wiki.archlinux.org/index.php/Wvdial](https://wiki.archlinux.org/index.php/Wvdial)
[I]
sudo arguably offers the most secure option to allow regular users to establish dial-up connections using wvdial. It can be used to give permission both on a per-user and group basis. Another benefit of using sudo is that it is only needed to do the setup once; both previous solutions will be "undone" when a new package of wvdial is installed.
Use visudo to edit the file /etc/sudoers:
# visudo
To give a specific user permission to run wvdial as root, add the following line (changing the username):
username localhost = /usr/bin/wvdial  [/I]

I would add that you have to give the command sudo visudo to edit /etc/sudoers. Also, when you're done, log out and log in again.

This has wasted hours of my time. So much for things working "out of the box". Could do better.

---

### Post by mbuell on 2012-06-26
I'm messing about with getting a Thinkpad T60 modem working. I agree - could be better. Modems seem to have fallen through the cracks, but that is perhaps understandable. After all, for most people they have become obsolete. I don't find it today, but somehow in my explorations of fixes, I found a Ubuntu page discussing modems. It was quite clear that the developers agree with us - this is too much fuss to get something working. However, they also noted that most modem mfrs don't have any non-proprietary driver solutions, and other issues. Combine that with the fact that modem use is dieing out - and you have what we see, I think. 

Still, I am not whining. Ubuntu otherwise does a marvelous job of producing the finest Linux desktop/laptop available. This is the only hardware issue I have had in the last couple of years. Given where hardware used to be, this is a pretty marvelous thing.

---

