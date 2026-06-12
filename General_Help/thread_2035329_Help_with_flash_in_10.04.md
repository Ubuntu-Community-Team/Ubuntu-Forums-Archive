---
title: "Help with flash in 10.04"
date: 2012-07-30
forum: General Help
---

### Post by superbub112 on 2012-07-30
Hello, I am running 10.04 on an old computer (It won't let me update ubuntu) and I am having some problems running adobe flash player. Basically, it won't run any flash elements on any webpage. I have the same problem with Java runtime environment. I have tried everything I have found on the forums and other parts of the internet, and nothing works. I have downloaded different versions and changed repositories and so far, nothing.

Does any one have any ideas?
btw I'm running 32-bit, not 64-bit.

Thanks in advance.

---

### Post by albandy on 2012-07-30
Test it with a new user. Some times the error is in the browser profile.

Why you can't update ubuntu? 10.04 support finishes on April 2013

---

### Post by superbub112 on 2012-07-30
I can't update because 12.04 won't install on to my computer but 10.04 did. Also, I tried a new user, but still, nothing.

---

### Post by albandy on 2012-07-30
In Firefox, enter the url:  
```

about:plugins

```
then search for Shockwave Flash and upload an screenshot like this one:

---

### Post by claracc on 2012-07-31
I recommend you install firefox addon flash-aid. You can select the way you run it to install flash player for the browser.

If you have an old pc, probably flash player 11.2 and higher won't work, so you'll have to install flash player 11.1 release or a lower one: [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html), you can install it through flash-aid.

Remark security risks of installing old flash player releases

---

### Post by superbub112 on 2012-07-31
I can't seem to find the add-on for flash-aid. I was told it was removed by the author. If someone could give me a link to one that isn't removed, that would be great. Thanks.

---

### Post by superbub112 on 2012-07-31
This is what is in my plugins

---

### Post by claracc on 2012-08-01
yes, flash-aid addon has been removed by lovinglinux:

> webgapps
IMPORTANT NOTICE

 

We are currently unable to process any support requests at this moment.

    Due to the current state of NPAPI Flash Plugin on Linux, Flash-Aid development and distribution has been suspended until further notice.
    Due to changes in Google policy in regard to third-party YouTube apps, FlashVideoReplacer development and distribution has been suspended, until further notice.

 

We apologize for the inconvenience and also like to thank all the support we received over the years from our users, while developing those add-ons.

Regards

C. Gonçalves (a.k.a. lovinglinux) – Developer

So you can download and old flash player release : 11.1.102.63 or 10.3.183.20 (they all work in my old pentium III laptop) from [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html), note you download a large file including windows versions.

Then you can follow instructions given in this link:[http://tombuntu.com/index.php/2011/09/16/how-to-install-adobe-flash-player-11-beta/](http://tombuntu.com/index.php/2011/09/16/how-to-install-adobe-flash-player-11-beta/) (note, this is for 11 beta, you'll have to provide the correct name for the release you are installing) in order to install it.

---

### Post by houseworkshy on 2012-08-01
Gnash can cause problems when living alongside flash, you could try removing that.  
Not letting you update is curious.  Do you get error messages when you try?  Sort that one out first, then you could try installing the flash non free pluggins via the repositorties after removing gnash.

---

