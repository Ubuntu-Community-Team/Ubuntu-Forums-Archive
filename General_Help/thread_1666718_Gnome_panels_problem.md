---
title: "Gnome panels problem"
date: 2011-01-14
forum: General Help
---

### Post by ogrishmania on 2011-01-14
So, a while ago I installed AWN and I wanted to get rid of the default panels. So after a quick browsing on google I found out just how to do that (modifying some time value). After a while I decided I want the default panels back so I entered these 3 commands: 
gconftool – -recursive-unset /apps/panel 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel 

It worked well but when I started adding applets to the panel, a line of icons appeared all over the panel (same icon, with some partition, with mount/unmount options). So I entered those 3 commands again but this time it set itself to a classical theme with black background. So I restarted the machine, after restart all was set to default (background, theme, panels) and all my files in home folder were gone (not in trash). 

So can I get them back or they're permanently deleted?

---

### Post by Pollox on 2011-01-14
If all the files that were in your home folder are gone, I suspect you may have accidentally entered
```
rm -rf ~/
```
at some point. I can't help you on undoing that, and I'm not even sure if that's possible. Maybe a post with a title like "undo rm -rf help" would generate more help with this.

I can offer some advice for the future. Rather than "rm" in terminal, delete things through nautilus so it gets sent to the trash. Or search for a terminal command that sends stuff to trash (I'm sure there's some out there).

---

