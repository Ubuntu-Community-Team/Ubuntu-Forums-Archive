---
title: "Programs fail to redirect firefox to webpages"
date: 2011-04-19
forum: General Help
---

### Post by Bujiraso on 2011-04-19
Hi there.

Since upgrading to Ubuntu 11.04 Natty Narwhal, I have this problem where  programs to redirect me to webpages. 
It just loads up  my home page and acts like it's finished. Even if I have Firefox  previously open, nothing happens.

Programs this happens with are Apport (when I try to file bug-reports), Tomboy (if I click "get add-ins"), and Liferea until I edited a setting telling it not to use the default gnome browser but to use Firefox.

I know the first thing you'd think hearing that is that my web browser isn't set in my gnome default applications, but it is. 

When I open firefox in terminal this error pops up[FONT=monospace]
[/FONT]```
LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
```Any help would be greatly appreciated, as I don't even know where to start troubleshooting.

**If **you think **you have any idea at all**, please [U]say something.
[/U]Thanks

---

### Post by Baumbart on 2011-04-20
Hi Bujiraso,

I'm an absolute beginner with Ubuntu (1 week) who started with a beta just because I have troubleshooting as a hobby.
So I probably won't be very helpful.

I stumbled across your post because I get the same error-message from Firefox.
As far as I can say, it seems to be a minor bug with Firefox trying to set an invalid keyboard acceleration key somewhere in its menu.

I tried to reproduce the error you first described following links from thunderbir and tomboy but everything works well, no matter if i choose Firefox or Opera as default browser.

So I don't think that both errors are related.

What is your default gnome-browser if not firefox?

---

### Post by Bujiraso on 2011-04-22
Actually, Baumbart, that's brilliant help. Knowing the error message is nothing relevant is good to know. 
 My gnome default browser IS firefox. It just acts as if it isn't. 

New information on the situation, when firefox crashes, it can't even load the "Oops, something went wrong" page. It immediately redirects to google as if something is forcing it hardcore.

To anyone who is tempted to ask, I have indeed purged it entirely including the .firefox folder and reinstalled.  Still very lost. 

Still very disappointed with how little anyone has to say on it (minus you of course, Baumbart.)

---

### Post by clhsharky on 2011-04-22
Bujiraso


> Still very disappointed with how little anyone has to say on it (minus you of course, Baumbart.) 
General help section is for final releases, so many may not know.

Might have been better asked in Natty sub forum.

Development & Programming>Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)


Sharky

---

### Post by Bujiraso on 2011-04-22
Again, brilliant. Thanks. Will search anew there. 

(Clarity on my disappointment: there's another version of this thread floating somewhere, both this and that I waited a week for any response on, when all it takes is somebody saying I'm in the wrong spot even :P)

Marking as solved since I'm in the wrong spot.
Thread also avail for deletion if mods are around.

---

