---
title: "Firefox think I'm British, I'm not"
date: 2009-12-10
forum: General Help
---

### Post by kafka201 on 2009-12-10
For some reason my firefox spell check thinks I'm a Brit, I'm an American that's never been across the pond as they say and I don't know why that setting is like that.  I have nothing against the British but because of the slightly different spelling of words I'm slowly starting to question my own sanity.  Where/how do I change this setting?

---

### Post by SteveDee on 2009-12-10
You can change the preferred language from Firefox menu: Edit > Preferences > Content > Languages Choose...

Firefox also thinks I am Britsh...and its right.

---

### Post by joes7 on 2009-12-10
You can also download it in your language (if you wish to update at the same time)

---

### Post by slumbergod on 2009-12-10
Hahahaha I get the same thing in reverse. I prefer the British/NZ spelling so when I visit a forum that assumes that my spelling is wrong and underlines it (e.g. IMDB) I deliberately use more words. Who can be bothered changing English preferences on every site and every application they use?

---

### Post by kafka201 on 2009-12-10
Bah, thanks SteveDee for the suggestion, I guess I missed that button.  I tried it though and now my only language installed/selected is us-en, American English, and it still tells me that color needs a u in it!  I've changed the setting and restarted firefox and still nada.  Any other suggestions?

---

### Post by SteveDee on 2009-12-11
> **kafka201 said:**
> Bah, thanks SteveDee for the suggestion, I guess I missed that button.  I tried it though and now my only language installed/selected is us-en, American English, and it still tells me that color needs a u in it!  I've changed the setting and restarted firefox and still nada.  Any other suggestions?

How strange! Thanks to 25 years of using & writing [US] software I now get confused as to the true spelling of colour/color and grey/gray.

Anyway try this. In Firefox address bar type:-

 about:config

Then (after acknowledging the "Dragons" message) type "spell" in the Filter.

On my system I see this:-
spellchecker.dictionary; user set  string  en_AU
...which is interesting because it thinks I'm an Ozzie (while in the US I've often been asked if I'm Australian).

Presumably yours shows en_GB. If so change it to en_US.

---

### Post by kafka201 on 2009-12-18
Ah, worked like a charm, thanks.

---

### Post by 5BallJuggler on 2009-12-18
> **kafka201 said:**
> Bah, thanks SteveDee for the suggestion, I guess I missed that button.  I tried it though and now my only language installed/selected is us-en, American English, and it still tells me that color needs a u in it!  I've changed the setting and restarted firefox and still nada.  Any other suggestions?

You could always spell colour with the "U" :)

---

### Post by nutznboltz on 2009-12-22
It may be easier to find a multi-line text box and right-click in it then choose "languages" off of the menu and set that to the proper locale.

This issue is a reported bug:

[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/320266](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/320266)

---

