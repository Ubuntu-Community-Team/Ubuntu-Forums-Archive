---
title: "How to install an application from tar.gz"
date: 2011-12-03
forum: General Help
---

### Post by fredand44 on 2011-12-03
Hello!

I'm new to Ubuntu (recently stopped using Mandriva).

I try to figure out the concept off installing (and starting) applications from a tar.gz file.

I would like to have an application menu (like in mandriva) where you can add short cuts to applications inside downloaded and unpacked tar.gz.

Right now I have downloaded Eclipse for Java EE development.

Of course I can use the file manager and start it from where it is unpacked but I bet that is not the correct way to start it each time?

Do Ubuntu users always use the "Dash Home" or "Ubuntu Software center" and find the app you would like to start that way? (I guess not)

Best regards
Fredrik

---

### Post by MG&amp;TL on 2011-12-03
Unless you need bleeding edge software for whatever reason, install eclipse from the software centre and everything will be set up for you.

If you do need it (and very often you won't) , I am assuming it's precompiled as you say you can run the executable already.

There are two ways into this:

1. Use the 'install' rule of whatever build system they use to install stuff in relevant places. Not reccomended, IMO, far too many things can go wrong, and removing is a pain.

2. Make a .desktop file pointing to the executable file and copy it to /usr/share/applications/ . Probably easier and definitely easier to remove.

If you need help with either of those, post again. :)

---

### Post by BC59 on 2011-12-03
You can open manually the tar and export the file to a folder. Then depends what type of file is inside.

---

### Post by oldtimer7777 on 2011-12-03
Here is a nice walkthrough to install everything you are going to probably want on that Ubuntu 11.10 system.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Just do it step by step..

As for installing software, I prefer to use Synaptic Package Manager.

sudo apt-get install synaptic
sudo synaptic

I use it to search and find what I am looking for, but I also research what I need with google search engine first to help save some time by being more precise on what I need to install on my Ubuntu system. 

Eclipse is a great program for that you want to do too.

> **fredand44 said:**
> Hello!

I'm new to Ubuntu (recently stopped using Mandriva).

I try to figure out the concept off installing (and starting) applications from a tar.gz file.

I would like to have an application menu (like in mandriva) where you can add short cuts to applications inside downloaded and unpacked tar.gz.

Right now I have downloaded Eclipse for Java EE development.

Of course I can use the file manager and start it from where it is unpacked but I bet that is not the correct way to start it each time?

Do Ubuntu users always use the "Dash Home" or "Ubuntu Software center" and find the app you would like to start that way? (I guess not)

Best regards
Fredrik

---

### Post by fredand44 on 2011-12-04
Hello Guys!

Thanks for all replies.
I just wonder if installing Gnome is the most common (and only) way to get an menu with your applications if you are a Ubuntu-user?

Best regards
Fredrik

---

### Post by oldtimer7777 on 2011-12-04
I really like Fallback Ubuntu session for that kind of menu.  

> **fredand44 said:**
> Hello Guys!

Thanks for all replies.
I just wonder if installing Gnome is the most common (and only) way to get an menu with your applications if you are a Ubuntu-user?

Best regards
Fredrik

---

### Post by fredand44 on 2011-12-09
Thanks for all help!

Now I use Gnome and I got my link to Eclipse!

Great site btw, with the steps!!!

/Fredrik

---

