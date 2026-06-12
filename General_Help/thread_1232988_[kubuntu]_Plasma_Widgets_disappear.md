---
title: "[kubuntu] Plasma Widgets disappear"
date: 2009-08-06
forum: General Help
---

### Post by rkoma on 2009-08-06
Hi All,

I have a Kubuntu 9.04 and while I was playing around with Plasma Widgets, suddenly all widgets from desktop disappeared. It is interesting that widgets were present but not visible - in the Add Widgets windows it was possible to remove non-visible widgets. Adding and removing new widgets was possible without problems, but the old one could not be shown.

The solution was to edit plasma applets configuration file, located in $HOME/.kde/share/config/plasma-appletsrc. In the [Containments][1] section, value of screen attribute was somehow set to -1. After setting this attribute value to 0 and restarting plasma, everything returned to normal :)

I am not sure what is the meaning of screen attribute and how it was set to value -1. Also, check all your [Containments] sections, each of them has screen attribute and can contain some widgets.

---

