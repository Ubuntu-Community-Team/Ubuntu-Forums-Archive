---
title: "CouchDB in evo contacts... URI issue"
date: 2010-01-24
forum: General Help
---

### Post by JiuJitsu500 on 2010-01-24
Howdy and what not!

Figured out another way to make a mistake... this time finally setting up evolution and such. The original problem was being unable to sync contacts to the CouchDB address book, but I definately went above and beyond with this one.

Thinking I was cool, I went into the "passwords and Encryption keys" app, and found two entries of the same title, so being an idiot somewhere in the fiddling I guess I deleted one of the couchdb entries form this (even though I noticed the two had seperate passwords in them). I'm almost positive recovery cannot be done.... but anyone got a tip on how I can replace this? Or at least stop getting this "incorrect URI" message when trying to open CouchDB address book in Evolution?

BTW evolution is great, and I wish I bothered with it a LOT sooner than I have (KMail trapped me).... and I would put this in ubuntu one.... but I think when this is fixed I'll get a new thread over there for this syncing issue :) thanks! arigato! danke! che-che! gracias! gratzi! merci! all in advance of course...

---

### Post by duanedesign on 2010-01-24
Was the entry in 'Passwords and Encryptions' under the Passwords tab and called 'Desktop Couch user authentication'?

These keys most likely hold information regarding your username, password, and other login details

---

### Post by JiuJitsu500 on 2010-01-24
Yes it was, but I found a site in the launchpad bug reports that helped (re-started desktop couch from scratch)...

Now both keys are still there, but I get the same message when trying to open the ubuntu one address book in Evolution...

---

### Post by JiuJitsu500 on 2010-01-24
I lied! turns out the .ini file was screwed when I deleted the entry, so I had to delete the whole file, wait for it to reset, and reboot the computer (probably not necessary, bu I did it to be sure) and viola!!!

Even the things that weren't working before are now. Don't know how, but screw it It works!

---

