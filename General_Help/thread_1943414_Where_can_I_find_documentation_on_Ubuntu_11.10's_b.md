---
title: "Where can I find documentation on Ubuntu 11.10's boot process?"
date: 2012-03-19
forum: General Help
---

### Post by Curious00 on 2012-03-19
Which files are run out of /etc and then is there an .xinitrc configuration file which is run?

I'd like to see a layout of the whole daisy chain of events.

Is the process different when using the Unity Compiz Desktop as opposed to the others?

---

### Post by raja.genupula on 2012-03-19
[http://www.debianadmin.com/the-lniux-boot-process-explained.html](http://www.debianadmin.com/the-lniux-boot-process-explained.html)

---

### Post by Curious00 on 2012-03-23
Thanks for the answer. There's a lot of good information on that page. I can basically figure most of it out from there. What seems to be lacking, however, is an explanation of how Ubuntu goes on to boot into X Windows. Is there an .xinitrc somewhere?

---

### Post by Curious00 on 2012-04-10
I've discovered that the information linked above is out of date. It took me a few weeks to stumble upon all the various bits of information here and there on the internet.

Ubuntu 11.10 does not use the standard runlevel boot process. Instead, it uses something called "Upstart." This innovative system is described [here]("http://upstart.ubuntu.com/cookbook/").

Upstart calls [LightDM]("https://wiki.ubuntu.com/LightDM") (the logon screen). LightDM has configuration options listed in the form of standard Freedesktop .desktop files which can be found in the /usr/share/xsessions/ folder. You'll see there that the standard Ubuntu 3D session calls "gnome-session --session=ubuntu."

Ocelot does not use ~/.xinitrc or ~/.xsessions at all. Instead you have to open the dash and search for "startup." This tool (whose command line name is: gnome-session-properties) will let you  add links to custom scripts which run after X starts.

---

