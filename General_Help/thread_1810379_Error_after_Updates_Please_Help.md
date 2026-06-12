---
title: "Error after Updates Please Help"
date: 2011-07-22
forum: General Help
---

### Post by mattw421 on 2011-07-22
Hi after I ran update through the terminal and rebooted i get this error message on start up and again after I log in Please Help!! I'm running Ubuntu 11.04 using unity 2d and the latest version of Gnome 2 on  a Dell Inspiron 5150 laptop

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 32512)

---

### Post by Roopertt on 2011-07-25
I had the same issue found in another forum if you delete gconf-sanity-check-2 the error will go away, but I did lose all of my preferences

---

### Post by mattw421 on 2011-07-26
I would hate to lose all my preferences were you able to reset them. I also get this error when I do updates from terminal W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1773AF13B1510FD

---

### Post by domi84 on 2011-08-23
I too have the same problem, any other solution?

---

### Post by ncohea on 2011-09-17
Try to get to a console (Alt+F1 through Alt+F6). From there, type /usr/lib/libgconf2-4/gconf-sanity-check-2 and tell us what you get.

When I tried to upgrade to 11.10 development branch, I got that libgtk3.so.0 does not exist. If this is your issue as well, you will need to install Gtk version 3.

---

### Post by Desktop_n00b on 2011-09-28
I found this in some ubuntu Indonesian website. I hope it works for you. I used google translate so sry if some of the stuff is a bit off. 

Just make sure you read the last part BEFORE YOU REBOOT! I didn't and it messed the whole thing up for me and I just had to reinstall. It wouldn't log me in anymore and I couldn't figure out what to do abt that.

YOU HAVE BEEN WARNED!

Here is original site if you want to look at whole thread [http://ubuntu-indonesia.com/forums/ubbthreads.php/ubb/showflat/Number/66495](http://ubuntu-indonesia.com/forums/ubbthreads.php/ubb/showflat/Number/66495)


"updates through what? terminal or the update manager??. Partial upgrade their voting would ya?? .. and if install gnome terminal 3 of the initial use, the result would also not perfect, because who upgraded only partial upgrade later. do not choose a partial upgrade. try again n diremove wrote all just follow the way below ......... 


3 gnome installation shell: 

> Into Ubuntu tweak> source center> gnome 3 checked> refresh. wait smp update process is complete, and will appear long for the updated list, not first upgraded tp. close aja box updates. 

> Tetep diubuntu tweak> moved under the source center, which is updated manager, then check all the lists would be updated / upgraded. smp wait for the process is complete. ente ask if the device is restarted, restart aja yaa, but before you restart make sure first paket2 below already installed / diremove. lakuin longer updated, but if ente n updated to use the terminal for the second time wrote: 


sudo apt-get update & & sudo apt-get upgrade & & sudo apt-get dist-upgrade (regardless of the outcome of the second update is not updated / upgraded). 

sudo apt-get install gnome-shell 


sudo apt-get remove gnome-accessibility-themes 


sudo apt-get remove gnome-accessibility-themes-extra 


sudo apt-get install gnome-themes-standard 


sudo apt-get install gnome-tweak-tool 


sudo reboot 


>> Before rebooted, press alt + f2 and type gnome-tweak-tool-and-run. then reboot. 

>> Not have a tweaked Ubuntu?? .. just install first: 

[http://ubuntu-indonesia.com/forums/ubbth..._seti](http://ubuntu-indonesia.com/forums/ubbth..._seti) # Post65653 


Edited by Honeycomb (June 28, 11 22:21)"

---

