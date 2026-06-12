---
title: "Older version of Firefox 10?"
date: 2012-02-04
forum: General Help
---

### Post by Skara Brae on 2012-02-04
[I]I start this thread, because I cannot find this long (dozens of pages) thread about Firefox in which I posted a few minutes ago...

[http://ubuntuforums.org/newreply.php?do=postreply&t=1352580](http://ubuntuforums.org/newreply.php?do=postreply&t=1352580)[/I] - this link does not work.

The Update manager updated Firefox to version 10. I don't want it to do that (it broke a few add-ons). Firefox is starting to annoy me...a new/higher version every 5 feet...

How and where do I find a Firefox version-before-Ver.10 back?

-oo-

I found a tar.bz2 of Firefox 6 - but how do I install this?

(And what's more--how do I keep it from updating to version 10 before changing the update setting in Firefox preferences? Firefox 6, having started it from within a folder on my desktop, updated itself to version 10 before I could stop it... Firefox is starting to annoy me; in Windows too...)

* after several years (from 7.10) of using Ubuntu, I now experience my lack of Ubuntu knowledge. How do I install a "tar.bz2"?

(I better hurry and make a backup of my Bookmarks...)

---

### Post by oldos2er on 2012-02-04
Click Search, Find All Your Posts.

---

### Post by lovinglinux on 2012-02-04
First, is not recommended to keep using an old version of Firefox. If your extensions doesn't work, please let us know which extensions you use, so we can try to help. I use more than 60 extensions and they all work with FF 10.

For instance, have you tried to update your extensions through Firefox add-on manager?

You can change your Ubuntu update settings through the *Software Sources *application. Go to the *Updates* tab and set it to just warn instead of update automatically.

Keep in mind that Mozilla is about to release a long term support version of Firefox 10, which would solve your problems. However, I would check if the extensions are actually being developed. If they are compatible only with Firefox 3.6, then most likely they are abandoned. Then, using an old version of Firefox  is just delaying the inevitable. Firefox 3.6 will reach end-of-life in April 24th, so any extensions that works only with that version will be dead.

If you still want to install an old version of Firefox, which I discouraged, because of security reasons, then you can get it from [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/)

---

### Post by scheibenlosen on 2012-02-04
> **Skara Brae said:**
> [I]I start this thread, because I cannot find this long (dozens of pages) thread about Firefox in which I posted a few minutes ago...

[http://ubuntuforums.org/newreply.php?do=postreply&t=1352580](http://ubuntuforums.org/newreply.php?do=postreply&t=1352580)[/I] - this link does not work.

The Update manager updated Firefox to version 10. I don't want it to do that (it broke a few add-ons). Firefox is starting to annoy me...a new/higher version every 5 feet...

How and where do I find a Firefox version-before-Ver.10 back?

-oo-

I found a tar.bz2 of Firefox 6 - but how do I install this?

(And what's more--how do I keep it from updating to version 10 before changing the update setting in Firefox preferences? Firefox 6, having started it from within a folder on my desktop, updated itself to version 10 before I could stop it... Firefox is starting to annoy me; in Windows too...)

* after several years (from 7.10) of using Ubuntu, I now experience my lack of Ubuntu knowledge. How do I install a &quot;tar.bz2&quot;?

(I better hurry and make a backup of my Bookmarks...)

 That's strange. Firefox 10 seems to have "fixed" some incompatible addons for me.  As for the .tar.bz archive, move it to where you want to extract it, and then "tar jxvf filename.tar.bz" (no quotes) will extract it there. Afterwards, you can do a shortcut, or whatever, giving the full path to where you extracted it and away you go.

---

### Post by bsntech on 2012-02-04
Firefox 10 has screwed up my webmail.

I use Horde as a webmail system - and use the 'dynamic' version.

For some reason now, any e-mails with this encoding:

Content-Type: text/plain; charset="iso-8859-1"

Fail to show in the reading pane.  All I get is a white/empty reading pane.  If the encoding is not using the iso-8859-1 charset, the reading pane populates properly with the e-mail message.  I have to double-click on the e-mail to read it if it has the iso-8859-1 charset.

What is worse - is if I hit "Reply" on one of those e-mails, the entire e-mail is replaced with 'null' instead of the message I'm replying to.

I came across this post because of the upgrade - and am looking to downgrade as well.  Even on a Windows PC using the new Firefox 10, it does the same thing.  So it isn't the operating system.

IE8 / IE9 work just fine - and previous versions of Firefox work just fine as well.

---

### Post by bsntech on 2012-02-04
OK - I have 'downgraded' to Firefox 8.0.1.  Actually, I have both 10 and 8.0.1 installed.

First - download the file here:

[http://www.oldapps.com/linux/firefox.php?old_firefox=656?download](http://www.oldapps.com/linux/firefox.php?old_firefox=656?download)

Ensure to save it to a location.

Then open a terminal window and go to the location where it was downloaded (probably the Downloads folder).

Run this command:

sudo tar jxvf firefox-8.0.1.tar.bz2 -C /opt

Firefox 8.0.1 should now be installed.

You can run it immediately by typing in:

/opt/firefox/firefox

When it prompts you if you want to use it as the default browser, hit Yes.

After I did that, I had to update my launcher shorcut to point to the above path for 8.0.1.

Problem with Horde's dynamic webmail has now been fixed - and I can see any e-mail in the reading pane.

---

### Post by lovinglinux on 2012-02-05
> **scheibenlosen said:**
> That's strange. Firefox 10 seems to have "fixed" some incompatible addons for me. 

The reason for that is that Firefox 10 considers add-ons compatible by default. This is a big change in the process.

---

