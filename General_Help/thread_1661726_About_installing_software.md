---
title: "About installing software"
date: 2011-01-07
forum: General Help
---

### Post by GrahamLabdon on 2011-01-07
Hello
I am not certain that this is the correct place to pose my question, if not please forgive me!

I have developed a suite of software apps that I want to distribute in the form of a .deb file.
I want to add to the Applications menu when the installation takes place - 
Applications
    My Apps
        App 1
        App 2
I think i will need a script to do this but dont really know where to start.

If anyone could give me some pointers I would be grateful

Thanks for your time

Graham

---

### Post by gandaran on 2011-01-07
> **GrahamLabdon said:**
> Hello
I am not certain that this is the correct place to pose my question, if not please forgive me!

I have developed a suite of software apps that I want to distribute in the form of a .deb file.
I want to add to the Applications menu when the installation takes place - 
Applications
    My Apps
        App 1
        App 2
I think i will need a script to do this but dont really know where to start.

If anyone could give me some pointers I would be grateful

Thanks for your time

Graham
you need to put a .desktop file for your app in /usr/share/applications, look in the same directory for examples, open any of them in gedit text editor.

---

### Post by GrahamLabdon on 2011-01-07
Hi Gandaran
Thanks for your reply
How do I create a new menu entry under the Applications main menu?
What I would like it to look like is
Applications
    My Apps
        App1
        App2

TIA

Graham

---

