---
title: "Firefox support after Karmic EOS?"
date: 2011-05-13
forum: General Help
---

### Post by twogeo on 2011-05-13
Hi,
Suggestions of where to go for updates to mozilla stuff after Karmic support ends would be welcome.

Karmic is where I want to stop with this old portable, so it'd be great  if I could keep it running securely enough online.   For that I need the  Firefox/NoScript combo.

---

### Post by lithopsian on 2011-05-13
Presumably you have Firefox and NoScript already.  You don't have to change.

To install NoScript, you can go to the [Mozilla addons page]("https://addons.mozilla.org/en-US/firefox/addon/noscript/").  Clicking the "Add to Firefox" button will either install it, or update your installation to the current version.  Then you can set your addon manager to either upgrade automatically to any new versions, or can check it manually whenever you feel like it.

You can [download Firefox 4.0]("http://www.mozilla.com/en-US/firefox/fx/") and simply unpack the tarball wherever you like.  /opt is the standard location.  It is possible to update Firefox from the about dialog, but if Firefox was installed as root then you have to be running as root to do this.  Otherwise the dialog box will tell you there is an update but that you need administrator rights to install it.

You could also use a Firefox repository for a newer Ubuntu version.  Firefox should be the same binary for Karmic as for Natty.  You will need a little experience with repositories to set this up.

---

### Post by twogeo on 2011-05-13
> **lithopsian said:**
> Presumably you have Firefox and NoScript already.  You don't have to change.
You presumed right.
I'll stick with Fx 3.6.x and NS until it's no longer getting Mozilla support.

> It is possible to update Firefox from the about dialog, but if Firefox was installed as root then you have to be running as root to do this. Super!  That's the most straightforward method for a user who seldom gets a distraction-free system maintenance session.  I assume I'd uninstall the Ubufox package to give me full control of updating, but anyway I can play with that sort of thing now that I know that updates will run via the browser itself.
Thanks so much for an info-full response.

---

### Post by lithopsian on 2011-05-13
Yes, get rid of Ubufox, especially if you aren't going to get support from it any more.

BTW, Firefox is already on 3.6.17 ;)  Minor security updates and a few unusual crashes fixed.

---

