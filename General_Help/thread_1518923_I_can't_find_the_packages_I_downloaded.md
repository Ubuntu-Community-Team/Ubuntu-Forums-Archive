---
title: "I can't find the packages I downloaded"
date: 2010-06-27
forum: General Help
---

### Post by getsumsucka on 2010-06-27
I recently decided that I wanted to set up a firewall. The firewall I chose was Ebox, which can be found in the Ubuntu software center, so i downloaded the package. But, after doing so I can not find the Ebox application. Any help would be greatly appreciated

---

### Post by dino99 on 2010-06-27
what Ebox is:

*** eBox Platform is an open source small business server that can act as
a Gateway, a Unified Threat Manager, an Office Server, an Infrastructure
Manager, a Unified Communications Server or a combination of them. One
single, easy-to-use platform to manage all your network services. ***

you should find it into menu: (dont know as i've not installed it) either apps/system, or system/admin/

If you want a firewall: kernel already deal with iptable, and ufw easily take care of rules, gufw is the gui. You might be pleased too with denyhosts, ipblock, moblock.

---

### Post by TRoe on 2010-06-27
In a terminal: whereis ebox (although it may be eBox)

As an executable, it'll either be in /usr/bin, /bin, or /sbin.

---

### Post by WorMzy on 2010-06-27
Never used it myself, but the config files will probably be in /etc, rather than ~, since it'll most likely be run as a daemon.

---

### Post by dino99 on 2010-06-27
into a console: locate yourpackage (need to install locate with synaptic first)

---

### Post by coldraven on 2010-06-27
I sometimes have this problem and this is what I do.

Run Synaptic, (In System/Administration)
Type "yourpackagename" in the search box
Once it shows up right click it and select "Properties"
Then open the "Installed Files" tab

This can often reveal that there are HTML help docs as well as the text or man files.
Some applications show up in the drop down menus immediately and some appear after a couple of minutes, why I cannot say.
It would be helpful if the software centre was more explicit about whether an application has a GUI or not.

---

