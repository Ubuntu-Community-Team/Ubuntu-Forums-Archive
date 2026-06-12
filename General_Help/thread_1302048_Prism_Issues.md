---
title: "Prism Issues"
date: 2009-10-26
forum: General Help
---

### Post by dazzler on 2009-10-26
I've had prism-google-reader installed for awhile, which i use all the time, out of curiosity i installed prism-twitter,

Now when i type prism-google-reader or start the shortcut it starts twitter app not reader ive uninstalled prism/twitter/reader and i cannot get it back.

Anyone know what i can do.

---

### Post by jason10 on 2009-11-05
im having the same problem with prism.  everything worked fine until i upgraded to 9.10, now my prism-gmail launches prism-facebook.  i uninstalled everything prism, then just reinstalled gmail, but its still launching as prism-facebook.  prism-facebook isnt even installed anymore..

lol.  i have a feeling i just need to clean out some prism config files somewhere but im not very good with ubuntu so im kind of afraid to go around deleting things i dont understand..

any help?
thanks

---

### Post by uweklosa on 2009-11-05
I have exactly the same problem on one of my computers. prism-google-calendar is working. prism-google-mail show facebook for me. I tried with removing ~/.prism, but there was no change.

On my laptop I do not have these problems. 

Uwe

---

### Post by albertomm on 2009-11-08
I have the same problem usign Xubuntu Karmic Koala.

First, Twitter fails to start if GMail is open. But if I close GMail and start Twitter, then the GMail prism will always open Twitter instead.

Workaround: delete the folder ~/.webapps/google.mail@developer.mozilla.org

This will reset the GMail web app configuration and you will be able to start it again. Its this bug reported?

---

### Post by jason10 on 2009-11-13
that was it.  i knew it was just a matter of deleting the right thing.  

thanks  :)

---

