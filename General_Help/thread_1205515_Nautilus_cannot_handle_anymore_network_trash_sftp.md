---
title: "Nautilus cannot handle anymore network:/// trash:/// sftp:///"
date: 2009-07-06
forum: General Help
---

### Post by MicheleZ on 2009-07-06
Hello All,

Problem description: 
I cannot connect to any server from nautilus. When I select the option in the file menu all I get is a "custom location" in the
service type. If I try to type in the location bar I get a message saying that nautilus cannot handle "network" or "sftp" or "trash". 

System information:
I run Jaunty on a Dell 630 booting from a USB disk and keep the system up to date.

(failed) solution attempts:
- launched nautilus from the terminal to see if some error messages were popping up. No message appears on the terminal.
- launched nautilus as root to check if the problem was with my user, but the problem exists also for root.
- reinstalled nautilus, reinstalled ssh

Other info:
- I sent a message to the ubuntu mailing list. I hope this thread does not count as "double posting". If it does I apologise
- (not relevant?) I use awn and the places applet (which normally shows the "places" as in nautilus or in the panel) is out of synch and shows different "places".
- As the system has been built very recently, since the last time nautilus worked OK I installed several programs, so I cannot single out the one that may have caused the problem.

Any suggestion on what could have gone wrong and above all how to fix it? I will be happy to provide any information you may need, but as I am not an expert I may need to ask you how to gather the information you required.

TIA,

MicheleZ

---

### Post by fragos on 2009-07-06
Can't image what happened to your system trash:/// for example and network:/// works for me. Your example with sftp:/// doesn't include an ftp address which wouldn't work. I use ftp in Nautilus and it works when addressed properly for my hosting company.

---

### Post by MicheleZ on 2009-07-07
Hello fragos,

Thanks for the reply. I have digged a bit deeper and found out that I might have been affected by the following bug:
[http://bugzilla.gnome.org/show_bug.cgi?id=523039](http://bugzilla.gnome.org/show_bug.cgi?id=523039)

I have to confess that I have not understood the solution, but it seems that I mistakenly installed glib in the wrong place. 

Problem is that I am still clueless as to how to solve the issue.

Cheers,

Michele

---

### Post by fragos on 2009-07-07
> **MicheleZ said:**
> Hello fragos,

Thanks for the reply. I have digged a bit deeper and found out that I might have been affected by the following bug:
[http://bugzilla.gnome.org/show_bug.cgi?id=523039](http://bugzilla.gnome.org/show_bug.cgi?id=523039)

I have to confess that I have not understood the solution, but it seems that I mistakenly installed glib in the wrong place. 

Problem is that I am still clueless as to how to solve the issue.

Cheers,

Michele

I install from an Ubuntu supplied .iso and have used the Update Manager to upgrade to new distro releases. Everything goes where it's supposed to. You might try symlinks from where these libraries are expected to where you placed them.

---

