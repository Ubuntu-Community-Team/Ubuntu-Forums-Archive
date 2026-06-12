---
title: "Gnome-Do OpenSearch Plugin"
date: 2009-11-02
forum: General Help
---

### Post by letubenaiah on 2009-11-02
The gnome-do opensearch plugin quite working for me quite some time ago and I've not been able to find any information about why this is happening.  I have the problem on multiple machines.

One one machine I'm running ubuntu 9.10, with Firefox 3.5 and the only opensearch plugin that shows up in gnome-do is IMDB.  

The other machine is running ubuntu 9.04 with Firefox 3.5.4 and non of the installed opensearch plugins show up.

I have tried un-installing and purging gnome-do, but it had no affect. 

Any ideas on why this is happening?

Thanks!

---

### Post by terto on 2009-11-03
I am getting the same thing although the plugin I am stuck with is TorrentFind. 

Perhaps the problem resides on the place where Gnome-Do looks for plugins, but I have not yet been able to find whether there's a difference between firefox versions regarding this.

EDIT:
After looking for the search plugins I realized that gnome-do is looking in my ~/.mozilla/firefox/gs8secuv.default/searchplugins/ folder while firefox was keeping my opensearch plugins in /usr/lib/firefox-addons/searchplugins/en-US/

I fixed it with this command

<code> cp /usr/lib/firefox-addons/searchplugins/en-US/*.xml ~/.mozilla/firefox/gs8secuv.default/searchplugins/</code>

Note that you might have to change it to suit the actual place for searchplugins in the .mozilla folder in your home.

Also, I believe this solution is suboptimal for if you were to change your plugins from within firefox gnome-do wouldn't know it. Perhaps linking the folders should be a better option, or maybe editing some gnome-do setting as to where to look for the plugins.

---

### Post by letubenaiah on 2009-11-03
I've done some more digging and figured out what is happening but not really why.  

Gnome-Do is looking for plugins in the /home/<user>/.mozilla/firefox/<profile>/searchplugins/ directory.  However, all my opensearch plugins are in /usr/lib/firefox-addons/searchplugins/en-US/  When I install a new opensearch plugin in firefox it gets put in the ~/.mozilla/.../searchplugins directory and Gnome-Do can see it.  

Why are the current plugins in the /usr/.../en-US/ directory and newly installed ons in the ~/.mozilla/.../searchplugins directory?

My workaround for now was simply to copy the xml files to the .mozilla directory.

---

