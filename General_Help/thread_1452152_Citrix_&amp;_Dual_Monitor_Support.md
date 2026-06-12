---
title: "Citrix &amp; Dual Monitor Support"
date: 2010-04-11
forum: General Help
---

### Post by cloud101120 on 2010-04-11
Hello,

I'm looking to setup Ubuntu Citrix Clients, and I am having a bit of difficultly getting the "desktop" view to span both screens.  I'm still pretty new to Ubuntu, so alot of what i have done has just been trial and error, and looking through forums.  

I'm currently using 10.04 LTS and have completed most steps in the process of getting citrix up and running.  The last and final step i seem to be having difficulty with.  I was following the Citrix 11.100 help guide and various online articles, but I'm stuck on the following:  

**To  make a session the spans multiple monitors from the command line**
  
[LIST=1]
[*]At a command prompt, type:  /usr/lib/ICAClient/wfica -span h A list of the numbers of the  monitors currently connected to the client workstation is printed to  stdout and wfica  exits.
[*]Make a note of these monitor numbers.
[*]At a command prompt, type: /usr/lib/ICAClient/wfica -span [w[,x[,y,z]]]  where w, x, y and z are monitor numbers obtained in step 1 above  and  the single value w, specifies a specific monitor, two values w and x  specify monitors at the top-left and bottom-right corners of the required area, and four values w, x, y and z specify monitors at the top, bottom,  left and right edges of the area. I**mportant:****  You must define the WFICA_OPTS variable before starting wfcmgr or  connecting to the Web interface through a browser. To do this, edit your  profile file, normally found at $HOME/.bash_profile or $HOME/.profile,  adding a line to define the WFICA_OPTS variable. For example:**
[*]** export WFICA_OPTS="-span a" ** Note that this change affects both XenApp and XenDesktop sessions.
[/LIST]

I've been able to use to get it to work using  /usr/lib/ICAClient/wfica -span o    , but i can't get the settings  to stick.  I'm stuck on the define wfica_opts variable ( export WFICA_OPTS="-span o" step. )

Any help on how to get this done would be greatly appreciated.

---

