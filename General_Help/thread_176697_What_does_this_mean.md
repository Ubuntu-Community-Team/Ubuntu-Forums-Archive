---
title: "What does this mean?"
date: 2006-05-15
forum: General Help
---

### Post by Russty of Oz on 2006-05-15
Hello!:) 

I have Firestarter installed and everytime I start Ubuntu, I am asked for my password for Firestarter then I get this error message everytime.

[B]Failed to run  /usr/sbin/Firestarter as     user root:
child terminated with 1 status
[/B]

Although this happens everytime, Firestarter still seems to be working, as I have to stop it to be able to access other computers on my network.  :-? 

So, does anyone know why I am getting this, and what does it mean?  I have seen a few messages with the term "child terminated with 1 status".  I would like to know what that is all about too.:confused: 

Russty.

---

### Post by iball on 2006-05-15
How are you starting Firestarter on boot: with Sudo?

Although Ubuntu does not enable a root account by default, the init.d scripts are still run with root privilleges.  You do not need to use sudo.  The error may be that Sudo is expecting the root password (which doesn't exist) and not your user password.

I hope this helps
--Ian

---

### Post by Russty of Oz on 2006-05-15
Hi iball!

All I do is boot and Ubuntu loads in then I put in my user name and password then a box appears and asks for my password for Firestarter, so I put in my password. It is just a normal little box, not a terminal.   There is nothing about Sudo.  

It still works so I guess there is no real problem, it's just that an error message usually means that something needs attention.  

Russty

---

### Post by seth0x2b on 2006-05-15
I have the exact same problem.
A quick look at System > Preferences > Sessions > Startup Programs shows me that Firestarter is started with
```
gksudo /usr/sbin/firestarter
```
When gnome boots up Firestarter asks for the root pass, I enter it and it gives the same error. I can then run Firestarter manually.
Anyone found a solution yet?!

Cheers

---

### Post by aureliofake on 2006-05-15
Each time i start Ubuntu firestarter ask for root password, after i type it, then it display the following message 

Failed to run /usr/sbin/Firestarter as user root:
child terminated with 1 status

i have uninstalled firestarter with synaptic but i get the same messages...
Then, the questions are

1. Firestarter is only a Gui frontend to configure iptables?
2. where i can delete the scripts that  call usr/bin/Firestarter on start up?

---

### Post by cgjones on 2006-05-15
Check [this](http://www.fs-security.com/docs/faq.php#trayicon) out for information on loading Firestarter when you login. It's been working great for me.

---

### Post by iball on 2006-05-15
From memory, you don't need to have firestarter running for the firewall to be active.  Firestarter is just a graphical frontend to IPTables, so the script can be run as a startup service.  

What is the output of "ls -l /etc/init.d" and "ls -l /etc/rc2.d" ?

If firestarter is in there, it is being started as a startup service, so you don't need to start it when you log in to Gnome.  The reason it is asking you for your users password is the "gksudo" part, because the Firstarter GUI needs root privilleges to run.  Firestarter can be safely removed from the Gnome Startup Programs.

To check if Firestarter is running, run "sudo iptables -L" in a terminal.  You should see all your firewall rules.

I hope this helps
--Ian

---

### Post by aureliofake on 2006-05-15
In the output for ls -l /etc/init.d" and "ls -l /etc/rc2.d   i get  this line

lrwxrwxrwx  1 root root 21 2006-05-14 02:32 S20firestarter -> ../init.d/firestar ter
this line it is marked in a different color in my system (this is after removing the firestarter package with synaptic)

also i have Deleted  gksudo /usr/sbin/firestarter from  System > Preferences > Sessions > Startup Programs 

i have restarted the computer and...
there are no more firestarter messages!

Now.. how i can test if the firewall is protecting me from the command line? 
the output from sudo iptables -L is
 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

thanks

---

