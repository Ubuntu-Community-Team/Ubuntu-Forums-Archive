---
title: "Firefox - invisible bookmark adding window."
date: 2012-02-05
forum: General Help
---

### Post by mikewhatever on 2012-02-05
Ever since upgrading from Firefox 3.6 on this GMA500 netbook (10.04,Gnome, no Compiz), I've had a problem of "invisible bookmark adding window". Basically, when pressing ctrl+d, nothing appears most of the times, and rarely, I can see an artefact where the window is supposed to be. It looks something like this: [http://support.mozilla.org/media/uploads/images/2011-08-02-03-53-20-46aad6.jpg](http://support.mozilla.org/media/uploads/images/2011-08-02-03-53-20-46aad6.jpg)

Needless to say, I've tried the safe mode, a new firefox and ubuntu profile, removing all addons and plugins, using different themes - Gnome and Firefox, reinstalling Firefox and using Mozilla builds, none of which made any difference.

Bright ideas would be appreciated.

---

### Post by aasdfasdfg on 2012-02-05
You may very likely need to a file a bug [here]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable")

However, just to be safe ensure you are on the most recent version of Firefox (10) and verify whether the problems occurs with and without compiz (unity) window manager. For instance, does the issue persists after running ```
sudo metacity --replace &
```

edit:
I am sorry, I see now that you are not running compiz and you specified this. Can you tell us what version of Gtk you have installed?
In terms of a practical fix, try installing firefox-trunk builds; see [here]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

---

### Post by mikewhatever on 2012-02-05
The libgtk installed is 2.20.1-0ubuntu2.1:
[http://packages.ubuntu.com/search?suite=lucid&searchon=names&keywords=libgtk](http://packages.ubuntu.com/search?suite=lucid&searchon=names&keywords=libgtk)

As mentioned above, all the latest versions of Firefox are affected, from 4 through 10, but not Firefox 3.6.26.

---

### Post by mikewhatever on 2012-03-01
...up

---

### Post by Dragynbane on 2012-03-01
This could be due to a failure in updating the setting to where the Bookmark manager just bookmarks a page without a separate window, have you tried the star button in the address bar (the bookmark button)?

---

### Post by lovinglinux on 2012-03-01
That looks like a video driver issue to me.

Have you tried to create a new Ubuntu user, just for testing? If it works, then you will know is some configuration in your /home.

---

### Post by mikewhatever on 2012-03-01
> **Dragynbane said:**
> This could be due to a failure in updating the setting to where the Bookmark manager just bookmarks a page without a separate window, have you tried the star button in the address bar (the bookmark button)?

Yes, I've tried the star, and the results were the same - invisible dialogue window.


> **lovinglinux said:**
> That looks like a video driver issue to me.

Have you tried to create a new Ubuntu user, just for testing? If it works, then you will know is some configuration in your /home.

Yes, I've tried creating a new Ubuntu user, the dialogue window was still invisible. The driver could be a problem, but it worked for Firefox 3.6.26 and earlier.

---

### Post by lovinglinux on 2012-03-02
> **mikewhatever said:**
> Yes, I've tried creating a new Ubuntu user, the dialogue window was still invisible. The driver could be a problem, but it worked for Firefox 3.6.26 and earlier.

This could be a problem that only occurs with your particular card and Firefox version.

---

### Post by mikewhatever on 2012-03-02
Yea, that would be unfortunate.

---

### Post by lovinglinux on 2012-03-02
Try to disable hardware acceleration. To do that open Firefox preferences, click the advanced tab, and untick the option "Use hardware acceleration when available". Close Firefox and start it again.

---

### Post by mikewhatever on 2012-03-02
Interesting idea, but no, that didn't fix it.
I am gonna ask the gma500 crowd to provide some feedback.

---

### Post by bodhi.zazen on 2012-03-02
I have been using the psb_gfx for quite some time, and not seen this problem.

What kernel are you using ? 10.04 and firefox 3.6 are quite long in the tooth.

I doubt you will get any support with an old kernel and old version of firefox, everyone will tell you to update to a more recent kernel and version of firefox.

I suggest you update your version of firefox first. If that fails, use the highest kernel you can (I am using kernel 3.2.2 + firefox 10 on gentoo with no problems).

---

### Post by mikewhatever on 2012-03-02
I use Firefox 10 and the generic kernel that Lucid provides, currently 2.6.32-38. Note, Firefox 3.6.x is the one that does not have the problem, it started with Firefox 4 and later.

---

### Post by bodhi.zazen on 2012-03-02
Do you use the pab_gfx with that kernel ? Did you compile it yourself ?

---

### Post by mikewhatever on 2012-03-02
No, I use the old psb driver. Precise with psb_gfx doesn't have that problem, but then, too many things have changed apart from the driver to be helpful in solving this.

---

### Post by mikewhatever on 2012-03-20
...up

---

### Post by lovinglinux on 2012-03-20
> **mikewhatever said:**
> ...up

I'm out of ideas.

---

### Post by mikewhatever on 2012-03-21
Yea, looks like I'm the only one having this problem. Thanks for trying.

---

### Post by nogasbiker on 2012-06-12
You're not the only one  :(


Similar symptoms for me as for you.  Just did an update moments ago, and now up to Firefox 13 and the problem persists.  Did all the stuff other threads have suggested- disabling extensions, addons, starting in safe mode, new profile, etc.  The problem persists.

I can sometimes see the outline of the bookmark dialog.  Once, I could see only one field of the dialog.  So it looks like a graphics / rendering problem?

Enough people had the problem that someone wrote an AddOn to address it.  There are only 5,000 users for it though, a little thin for my taste.

I'll be trying out Chrome now.  Loss of bookmark editing and cataloging on the fly is a big enough problem to make me look elsewhere.

---

### Post by Frogs Hair on 2012-06-12
This problem occurred with Unity 2D and 3D when Nightly 16 was released. I have reported it via report a problem option in the menu. I have not checked the Gnome Shell for the same problem yet. This does not happen all the time.

---

### Post by nogasbiker on 2012-06-12
Are you running somewhat old hardware by any chance?  Wonder if it is a legacy graphics support problem.

---

### Post by Frogs Hair on 2012-06-14
I am not running old hardware but,I don't know about the OP . The problem was corrected on the 16 nightly build update. What ever caused  this did not affect the Nightly 15 build. :confused:

---

### Post by Church on 2012-09-02
12.04 x64
No add bookmark dialog on FF15. Plugins: BitTorrent WebUI+ 0.2.2.3 / Classic Compact Options 10.0.2 / Flashblock 1.5.15.1 / Global Menu Bar integration 3.4 / Second Search 0.7.2012031101 / Tab Mix Plus 0.4.0.3 / Xmarks 4.1.2
Somewhat doubt issue being related to version seeing this problem reported with different versions. Also official package is used widely enough for it to be reported and fixed soon, so probably others are using without this issue. Maybe some fsckup in profile/settings?

---

### Post by SantaFe on 2012-09-02
Hmmm... never noticed this before, probably because whenever I save a bookmark I usually click on the bookmarks button up top & when the sidebar opens, just drag the URL where I want it.

Checked though (on Firefox 15, as well as Aurora & Nightly) and I get the same things you mentioned.  I DID notice if I click on the star, the bookmark pops up in the Unsorted Bookmarks folder or if I Ctrl-d, it gets added to the bottom of the bookmark list.;)

Tried getting rid of Ubufox, disabled Tab Mix Plus & Classic Compact Options, disabling Hardware Acceleration, nada.

Forgot to mention, this is on a Dell Laptop running Xubuntu 12.04 and the default video drivers.

---

### Post by mikewhatever on 2012-09-04
Hi SantaFe. What kind of a Dell notebook do you use? Can you post the output of **lspci**. It's an obscure bug, and Firefox 15 has not fix it for me too.

---

