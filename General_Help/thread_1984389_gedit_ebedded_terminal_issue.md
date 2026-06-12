---
title: "gedit ebedded terminal issue"
date: 2012-05-21
forum: General Help
---

### Post by wolfdart on 2012-05-21
Hi folks. I  installed gedit-plugins package and turn on the Embedded Terminal plugin.

But I'm having a issue with that. Look this screen below:
[IMG]http://s8.postimage.org/5fwsmwu77/gedit.png[/IMG]

The Gedit color scheme don't work on Embedded Terminal. I tried to change the Gedit color scheme and the Terminal color scheme, but nothing happened!

Can I solve this issue? :confused:

Thanks in advance.

---

### Post by wolfdart on 2012-05-21
Hi folks. I tried some help on #Ubuntu and the user undecim helped me.

How fix that:
install dconf-tools
> sudo apt-get install dconf-tools
open dconf-tools and go to "org.gnome.gedit.plugins.terminal.forgound-color"
Uncheck "use-theme-color"
Restart Gedit
\o/

:guitar:

---

