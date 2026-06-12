---
title: "Newb needs some major help"
date: 2006-03-21
forum: General Help
---

### Post by captainjy on 2006-03-21
Hello everyone.  New to Ubuntu and need some help.  I haven't used Linux is years and am just wondering where to begin.  I just installed 5.10 and did a server install.  Just trying to figure out a couple things- for one, how do I get into the graphical interface?  Also, I would like to configure this server as a DNS server and could use some help changing the IP configuration.  Basically, I know nothing and any help would be greatly appreciated!  Thanks!

---

### Post by fatsamurai on 2006-03-21
In the meantime, before someone comes and rescues you check out the documentation Wiki. It's bound to answer some of your questions.

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Try 'sudo gdm' to get into a gui.. though I don't know if the gui is installed or not on a server install.

---

### Post by captainjy on 2006-03-22
Thanks for the reply.  I did manage to get to the GUI.  I am stuck on how to login as root.  Is there a default root password that is created?

---

### Post by captainjy on 2006-03-22
[QUOTE=captainjy]Thanks for the reply.  I did manage to get to the GUI.  I am stuck on how to login as root.  Is there a default root password that is created?[/QUOTE]

Ok, I managed to change the root password, but is there any way to login to GNOME as root?

---

### Post by rhomsy on 2006-03-22
[QUOTE=captainjy]Ok, I managed to change the root password, but is there any way to login to GNOME as root?[/QUOTE]

Ubuntu does not allow for root login by default.  However, to make most configurations, you don't need it.  Use the sudo command at the command line, and the GUI configs just ask for your password, which is an added safeguard.  If you've ever used MacOS X, it handles root in the same way.

---

### Post by gabruo on 2006-03-22
In Gnome

    *

      Open System --> Administration --> Login Screen Setup
    *

      Click on the security tab
    *

      Check Allow root login

In KDE

    *

      Open Konqueror and open the /etc/kde3/kdm/ folder
    *

      Right click the kdmrc file and then Actions --> 'Edit as root'
    *

      On line 246 should be AllowRootLogin=false change it to 'true'
    *

      Save and exit.

---

### Post by NetMatrix on 2006-03-22
Ubuntu is kinda tricky when it comes to the root user.  The root user is disabled and the sudo command is used.  So when you are trying to make changes in the GUI and it asks for a password, just put in your user password.  The sudo command allows you to 'act' as the root user.  The same goes for the command line. i.e.

$ apt-get install package1

This will give you an error because you don't have the right permissions so:

$ sudo apt-get install package1
password: kladjflkadjsfl

Here you enter YOUR password and then you can install the package.

Good Luck.

---

### Post by halitech on 2006-03-22
the first user created is root, ubuntu doesn't actually have a "root" or "superuser" account.

---

### Post by captainjy on 2006-03-22
Sweet!  I tried what Gabruo suggested and it worked great.  Thanks everyone!  One last question- how do I install a DNS server?  I would  like to make this server a backup DNS server.  I am going to do some more looking and see if I can find this myself, but if anyone has suggestions, I would appreciate them!  Thanks!

---

