---
title: "Hyperlinks in Pidgin"
date: 2009-11-11
forum: General Help
---

### Post by groping_blindly on 2009-11-11
Hi all.

I've got an issue with hyperlinks posted by buddies in Pidgin IM conversations.  Basically, they don't work.  

When I hover over the hyperlink, the cursor turns into the little hand, but when I click, nothing happens, and the cursor turns back into the vertical text-editing bar.  I'm sure this used to automatically launch Firefox and go to the URL, but not any more.

According to the Pidgin online manual, I should have tab under preferences-> headed 'Browser', which allows the user to specify the various browser integration options.  This tab is absent from my version of Pidgin. 

Is this a Pidgin issue or a Firefox issue? (As a side question, why is FF such a cranky piece of crap these days and is it the case that 3.5 isn't yet in the repositories?  Or am I just stupid?)

Any ideas?

According to the update manager, my system is up to date.
I'm running Ubuntu Hardy 8.04 Kernel 2.6.24-24-generic; GNOME 2.22.3; FF 3.0.14; Pidgin 2.4.1

---

### Post by DFlame on 2009-11-11
You're using an LTS release, so you are a bit behind. I'm using FF 3.5.4 and Pidgin 2.5.5. The latter has the browser tab you are looking for.

You can get the latest version of Firefox by installing the ubuntuzilla package. You can download the deb for that right [here](http://sourceforge.net/projects/ubuntuzilla/files/). Once installed, just open a terminal window and enter "ubuntuzilla" to start the update process.

You'll be asked to choose a locale, give your password (to install) and pick whether you want update notifications. Once the script finishes its job, you should be running the latest version of FF :)

-

As for Pidgin, I'm not totally sure how to get the latest version running with Hardy. There are packages on the [legacy getdeb](http://old.getdeb.net/release/4937) website which may help. You would have to uninstall all Pidgin related packages in synaptic, download the later ones from the link, then install them. At a guess :P

Shout if there's any trouble

---

### Post by groping_blindly on 2009-11-15
Thanks for the tips!

It worked a bit.  I downloaded and installed the file with the deb installer, and that seemed to work alright.  But when I try to run ubuntuzilla at the command line, I get (copied and pasted from the terminal):

bash: ubuntuzilla: command not found

Maybe I need to cd to a particular directory?  (I really don't have much of an idea what I'm doing here).

I checked to see if FF had magically updated itself, but it's still the same.

---

### Post by DFlame on 2009-11-15
Try:

```
ubuntuzilla.py
```

in Terminal. My mistake there :P

---

### Post by groping_blindly on 2009-11-15
That did the trick :)  Thanks!

I've successfully updated Firefox and Pidgin now.  Still hasn't fixed the original issue, but now I've eliminated a lot of potential troubles.  I'll hunt around the Pidgin user forums:

[http://sourceforge.net/projects/pidgin/forums/forum/665/index/page/1](http://sourceforge.net/projects/pidgin/forums/forum/665/index/page/1)

And see how I go.

---

### Post by DFlame on 2009-11-16
Glad I could help, even if it was just a teensy bit :)

---

