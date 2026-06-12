---
title: "I hate sudo"
date: 2006-04-12
forum: General Help
---

### Post by Sidk on 2006-04-12
Can someone walk me through removing sudo without breaking the desktop. I would much rather su and password then have to type sudo before I do everything. 

Besides that my Samsung printer utility will not validate the sudo account so I can not set up my printer correctly.

I have a user named root and i gave the user a password. I tried apt-get remove sudo and it broke the everything. I reinstalled it so I could continue on with setting this box up.

---

### Post by localzuk on 2006-04-12
You can use sudo -s in order to get to a root shell (su equivelant) or you can set a password for the standard root account simply by running sudo passwd root.

---

### Post by aysiu on 2006-04-12
Follow [these instructinos](https://wiki.ubuntu.com/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c).

---

### Post by Thiago on 2006-04-12
edit: bah... aysiu post first :P hehe

---

### Post by steve.horsley on 2006-04-12
There's no harm in giving the root account a (secure) password. 
**sudo passwd**
Then you can become root with **su** when you like. Trouble is, you don't know the command-line names of all the admin programs. 

One way round it is to use Alt-Ctrl-F1 to get a text console, log in as root, then start a second x session (on Alt-Ctrl-F8 ) with the command **startx -- :2**. 
I change root's background to fire-engine red to remind me. Logout ASAP when you've finished your work.

It is also possible to cnange sudo to ask for the root password rather than the user password, but I forget how.

---

### Post by Ramses de Norre on 2006-04-12
To make sudo ask root passwd: add "rootpw" to the defaults line in /etc/sudoers.

---

### Post by _linux_ on 2006-04-12
[QUOTE=Sidk]Can someone walk me through removing sudo without breaking the desktop. I would much rather su and password then have to type sudo before I do everything. 

Besides that my Samsung printer utility will not validate the sudo account so I can not set up my printer correctly.

I have a user named root and i gave the user a password. I tried apt-get remove sudo and it broke the everything. I reinstalled it so I could continue on with setting this box up.[/QUOTE]
The instructions are in the Ubuntu help files on the computer.

---

### Post by Sidk on 2006-04-12
Thanks all, I already had done that, thought I was missing something. Stupid Samsung printer configuration is still giving me fits but i found a work around.

---

### Post by Sidk on 2006-04-12
All the gnome applets won't take new root password. I have to use the old sudo one. Where or how do I change this?

---

### Post by kickaha on 2006-04-12
If you want  a spiffy new X session, you can enable root login through the gmd greeter (for gnome ubuntu), and then start a new login.

Go to System -> Administration -> Login Screen Setup
Clicking on that will open a tabbed dialog box that controls many aspects of the gdm greeter.
In the 'Security' tab, you will find a checkbox labeled, "Allow root to login with GDM". If you check that, you can login to a native gnome session as root.
I would suggest you NOT enable remote root login.

After you have enabled root login, and while you are still logged in as yourself, go to:
Applications -> System Tools -> New login.

Clicking on that will cause a new gdm login session to open up,
in which you can login as root.
If you are familiar with accessing multiple sessions via the <ctrl><alt>Fn key combo, the new session will be attached to <ctrl><alt>F8, and the 'first' session will be <ctrl><alt>F7.

If you want to get really sexy, apt-get install xnest. This will add a new  entry in the Applications -> System Tools menu called:

New Login in a Nested Window

which does exactly what it sounds like. Handy if you determine you need to do some admin chores when you already have a browser open to this forum with all the info neatly layed out.

I use xnested sessions when I want to browse synaptics.

---

