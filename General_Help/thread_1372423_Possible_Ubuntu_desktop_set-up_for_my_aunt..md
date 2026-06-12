---
title: "Possible Ubuntu desktop set-up for my aunt."
date: 2010-01-04
forum: General Help
---

### Post by Jeremy_Tyrone_Jenkins on 2010-01-04
Looking at this set-up for my Aunt because she always destroys her windoze systems.
 
[http://configure.us.dell.com/dellstore/config.aspx?oc=ddcwrw1&c=us&l=en&s=dhs&cs=19&link_number=14218439&kc=desktop-inspiron-537s](http://configure.us.dell.com/dellstore/config.aspx?oc=ddcwrw1&c=us&l=en&s=dhs&cs=19&link_number=14218439&kc=desktop-inspiron-537s)
 
My question is will I be able to use a program like to connect to her PC remotely and get the regular Ubuntu updates? I don't want her to have the root password because then she would probably mess something up. 
 
So both of us would be using 9.04. From what I've seen if she has a Static IP I would be able to access it. 
 
She would be using the system for Internet, Photo editing and Office applications so I think it would be perfect. 
 
I'm almost SURE this has probably been posted before somewhere so I am sorry for dupicating someone elses post. If someone has seen it please send me the link and I would gladly read what was said. 
 
Thanks,
 
Jeremy

---

### Post by kyuubi777 on 2010-01-04
i believe with x11vnc you can set up a vnc server to run on the comp. and then u can use a vnc viewer on yor end... this will allow you full access of the machine so she will be able to see that someone is controlling her computer if she is using it at the time you decide to give her an update
i don't know of any other feature that might help you out, but then i am not the most experienced user.. just thought i'd toss you a thought

---

### Post by jamesisin on 2010-01-04
The easiest way to maintain your Aunt's system will be through ssh.  You'll have to turn ssh on so her machine will accept incoming connections; you'll have to ensure that she uses a strong password (something like a pleasant sentence "I love my nephew, John!" would be great); and you'll have to configure any router device to port-forward (port 22) (which means using a static IP address for her machine).

But once you have it set up you can ssh into her machine and enter a few small commands to run updates.  Then, when you are done, you can call her and ask her to reboot.  (You should be able to run updates even when she is logged in, though the machine will have to be turned on and connected at least.)

---

### Post by jamesisin on 2010-01-04
Oh, and you can ssh into her machine from a Mac, a Linux box, or a Windows machine (with Cygwin).

---

### Post by jamesisin on 2010-01-04
Also, no one will have a root password.  You will have your own account with admin privs from which you can run make system changes (via sudo) and she will have a limited user account.  I set machines up like this for friends and family all the time.

---

### Post by Jeremy_Tyrone_Jenkins on 2010-01-05
Thanks thats just what I needed to know.

---

### Post by audiomick on 2010-01-05
First of all, this is not intended to talk you out of admin via ssh. I need to learn how to do that myself...;)

As far as the password goes; as has been mentioned, the first user and any others with admin rights can do stuff using "sudo", or will be asked for a password for anything that needs root privileges.

I have a couple of people I help (including my mum), and simply tell them if they get asked for a password, cancel out of whatever it is. Unless they are really really sure about what they are doing.
or
If you really want to shut her out, set up a user for her that is not in the admin group.

As far as updating goes, in fact you should be able to show your aunt how to let that happen. It is not really complicated.
or
You can set the update manager to install security updates without asking. This will keep her secure, and let you do any other updates when you have time.

---

### Post by jamesisin on 2010-01-05
No problem.  (Please mark the thread as SOLVED in Thread Tools.)

---

