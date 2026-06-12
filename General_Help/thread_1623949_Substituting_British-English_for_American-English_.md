---
title: "Substituting British-English for American-English in spellcheck"
date: 2010-11-17
forum: General Help
---

### Post by t0p on 2010-11-17
Okay, this is something that has been mildly irritating me for quite some time.  I'm a Brit; and when I type words in my native tongue, Ubuntu tries to tell me I've spelt words wrong when the British-English spelling differs from the American-English version.  Eg *aluminium* instead of "aluminum", and *colour* instead of "color".

How do I go about telling my computers to use British-English spellings rather than their American-English counterparts.  And can this be done centrally, rather than having to tell each individual application to use my preferred spellings?

---

### Post by neanderslob on 2010-12-08
Hahahaha I'm looking for the solution to exactly the opposite problem.  Wanna just trade computers?  No really though, if you want to downgrade American English to UK english ;), it should work by going up to System>Administration>Language Support.  Then change from American to UK in both the language tab and the text tab.  I tried doing this for my problem but for some reason it just won't go.  Hope you have better luck across the pond; it should work. :guitar:

---

### Post by neanderslob on 2010-12-08
Hahahaha I'm looking for the solution to exactly the opposite problem.  Wanna just trade computers?  No really though, if you want to downgrade American English to UK english ;), it should work by going up to System>Administration>Language Support.  Then change from American to UK in both the language tab and the text tab.  I tried doing this for my problem but for some reason it just won't go.  Hope you have better luck across the pond; it should work. :guitar:

---

### Post by gandaran on 2010-12-08
> **neanderslob said:**
> Hahahaha I'm looking for the solution to exactly the opposite problem.  Wanna just trade computers?  No really though, if you want to downgrade American English to UK english ;), it should work by going up to System>Administration>Language Support.  Then change from American to UK in both the language tab and the text tab.  I tried doing this for my problem but for some reason it just won't go.  Hope you have better luck across the pond; it should work. :guitar:
did you install the full language support in  system > administration > language support? I did, and I can choose any English dictionary be it American, Canadian, British or South African and some others.

---

### Post by neanderslob on 2010-12-08
Hey man thanks for the suggestion but I think it's already taken care of.  It says American English is on the top of the list.  Here's a screen-shot of what I'm talking about.  American English is and always has been on top (in the technically pertinent sense, not in the nationalist sense) but for some reason the system just can't get it through its thick skull.  I assume it's working fine for you?  Maybe I'm missing something?  Thanks again for the reply, it's so moderately annoying to second guess my spelling of color in the middle of a chat.

---

### Post by dcstar on 2010-12-08
> **neanderslob said:**
> Hey man thanks for the suggestion but I think it's already taken care of.  It says American English is on the top of the list.  Here's a screen-shot of what I'm talking about.  American English is and always has been on top (in the technically pertinent sense, not in the nationalist sense) but for some reason the system just can't get it through its thick skull.  I assume it's working fine for you?  Maybe I'm missing something?  Thanks again for the reply, it's so moderately annoying to second guess my spelling of color in the middle of a chat.

Go into Synaptic and make sure all the correct dictionary versions are installed.

---

### Post by neanderslob on 2010-12-11
Well that was a good idea.  I uninstalled the south african myspell dictionaries and installed the us-english myspell package.  Thanks for doing my thinking for me!

---

### Post by bodhi.zazen on 2010-12-11
It sometimes varies by application as well. For example you can install various dictionaries in Firefox and Adobe PDF reader is language specific (to change the language you remove the old and install the new).

---

### Post by dcstar on 2010-12-11
> **bodhi.zazen said:**
> It sometimes varies by application as well. For example you can install various dictionaries in Firefox and Adobe PDF reader is language specific (to change the language you remove the old and install the new).

Also when you install new dictionaries you sometimes have to go into various apps and set them to use the news ones - Evolution is one of these where you have to select one in the Composer-Spell Checking preference.

---

