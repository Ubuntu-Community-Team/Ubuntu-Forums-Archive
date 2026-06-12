---
title: "How to upgrade gnome-settings-daemon?"
date: 2009-10-10
forum: General Help
---

### Post by tars_ac on 2009-10-10
First, a little background.  I've been having a problem on my Eee PC running UNR 9.04 where the mute button produces crackling sound instead of actually turning off the sound.  This issue seems to be well documented around the net.  Apparently the proper way to disable sound on these machines is to turn off the iSpeaker from the volume control.  There are scripts to do this out there, which integrate with the notification popups and work quite well.  Naturally I want to replace the mute button functionality with this.

However, I have stumbled across this bug in Gnome: [https://bugzilla.gnome.org/show_bug.cgi?id=580616](https://bugzilla.gnome.org/show_bug.cgi?id=580616).  I can work around the issue by entering some other key combination and then switching to the mute button once it's working, but on a restart it all goes away and I have to do it again (even though it's still showing up in the keyboard shortcuts applet).  I believe that the patch provided would fix my issue and make everything work perfectly, since it matches the exact problem that I've come across.

How do I get the version of gnome-settings-daemon with this fix?  I don't want to install some random .deb or do a make install, because I want to get further patches and keep up-to-date on it as time goes on.  I've added various PPAs in the past to do this, which seems to work ok, but I can't find one for more up-to-date gnome-settings-daemons.

Is there a good way around this, or this issue in general?  I know I could move to 9.10 beta, but I don't want my whole system to be unstable, just one small component.

(My current gnome-settings-daemon is 2.26.1-0ubuntu2)

Thanks.

(as an aside, if anyone comes across this post looking for the volume mute crackling issue fix - I've attached the two scripts needed.  eee-volume-mute.txt is not a text file but it wouldn't let me upload without changing the extension - get rid of the .txt, make them executable, and point your keyboard mute shortcut to eee-volume-mute [make a new custom one and disable the current one by pressing backspace].  I didn't write these scripts, although I did change the notification text.  I think there's attribution in the files themselves.)

---

### Post by tars_ac on 2009-10-11
Anyone have any idea?

---

### Post by barthel on 2009-10-11
You could comile your patched version, but instead of doing a `make install`, overwrite the executable from the package with your shiny new patched version.

Since you haven't removed the package, it should still update as new versions come along.

The only downside is that if the new version doesn't include the fix you need, you'll have to recompile and replace again.

---

