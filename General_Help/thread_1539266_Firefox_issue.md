---
title: "Firefox issue"
date: 2010-07-26
forum: General Help
---

### Post by Rodd_Roddy on 2010-07-26
My recent issue is that when i start firefox 3.6.7 OS 9.10 is that the terminal will pop up and have this error:

(firefox-bin:2690): GLib-WARNING **: g_set_prgname() called multiple times

I can only have firefox running when the terminal is running.If I close the terminal firefox will close as well

any suggestion would be great to fix it 

thanks in advance

---

### Post by corncob on 2010-07-26
> **Rodd_Roddy said:**
> My recent issue is that when i start firefox 3.6.7 OS 9.10 is that the terminal will pop up and have this error:

(firefox-bin:2690): GLib-WARNING **: g_set_prgname() called multiple times

I can only have firefox running when the terminal is running.If I close the terminal firefox will close as well

any suggestion would be great to fix it 

thanks in advance

Sounds like you're running firefox from the terminal in which case the process will be killed when you close the terminal.  If you're running it from a launcher right-click on the launcher and select "properties".  See what the command line says.  I think there might be an argument or option that will have it run in the terminal.  On my system it says "firefox %u".  If someone can tell me what %u means I'd be grateful for the knowledge but since everything is working I've left it alone.

---

### Post by lovinglinux on 2010-07-26
See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Also please vote at [http://ubuntuforums.org/showthread.php?t=1539100](http://ubuntuforums.org/showthread.php?t=1539100)

---

