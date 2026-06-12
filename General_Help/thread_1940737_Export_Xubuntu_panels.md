---
title: "Export Xubuntu panels?"
date: 2012-03-14
forum: General Help
---

### Post by motorcity909 on 2012-03-14
Hi

I have Xubuntu 11.10 on my main machine and have the top & bottom panels set up just how I want (pretty much Gnome 2-esque).

I'm going to install Xubuntu 11.10 on an older netbook and will want my panels just the same.  Is there a way of exporting or copying my panel settings from my main machine onto the new install or will I have to manually recreate the panels?

Many thanks as always
Dave

---

### Post by raja.genupula on 2012-03-14
in your main system(what panel you want ) copy this file **.config/xfce4/[COLOR="Blue"]panel[/COLOR]** its a hidden file in your Home directory . 
then in the target system replace it with that file , then give restart . 

all the best and let us know what you got .

---

### Post by LewisTM on 2012-03-14
The .../panel directory only contains the configuration files for the panel items, not the overall layout of the panel.

This file needs to be transferred too:

~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

Cheers!

---

### Post by motorcity909 on 2012-03-14
Thanks for the quick replies!  I'll copy those files and folders and will come back once I've tried it over the next few days.

Cheers
Dave
:)

---

### Post by motorcity909 on 2012-03-21
Hi all

Quick update - it kind of worked.  The workplace switcher was increased to 4 squares but was still on the top panel whereas I've moved it to the bottom on my main machine.  

The bottom panel wasn't touched at all so I've manually removed those launchers.

None of the top panel launchers I'd set up were recreated so I'll need to do those manually on this second machine.

But the main thing is I've a second machine running my fav OS.  Also I secretly love the tinkering and configuration so don't really mind having to do this!

Cheers
Dave

---

