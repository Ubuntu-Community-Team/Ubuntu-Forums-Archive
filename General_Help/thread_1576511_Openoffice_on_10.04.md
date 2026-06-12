---
title: "Openoffice on 10.04"
date: 2010-09-17
forum: General Help
---

### Post by dogdo on 2010-09-17
How do i install spell check and the thesaurus?-really annoying not having these by default...

---

### Post by Irony on 2010-09-17
They are in the repositories, look under openoffice in synaptic.

---

### Post by uRock on 2010-09-17
They should be installed already. You may just need to go to Tools> Options within Writer/Word Processor.

---

### Post by dogdo on 2010-09-17
> **uRock said:**
> They should be installed already. You may just need to go to Tools> Options within Writer/Word Processor.

Yes i checked and i have those enabled but spell check does not work...

whenever i run spell check it just goes spell check complete but it does not check spelling

---

### Post by uRock on 2010-09-17
hmm, that is odd. When I don an install I always use apt-get install openoffice.org, so maybe that adds the functionality you are missing.

---

### Post by Hagar Delest on 2010-09-17
Some hints here: [[Troubleshooting] Spell check in OOo 3.x](http://user.services.openoffice.org/en/forum/viewtopic.php?t=16512).

Make sure you see the blue check mark and that the dictionary is installed in the extension manager.

---

### Post by coffeecat on 2010-09-17
> **dogdo said:**
> Yes i checked and i have those enabled but spell check does not work...

whenever i run spell check it just goes spell check complete but it does not check spelling

Your screenshot shows no language in the text language box, which is odd. I'm in Maverisk atm and my OpenOffice is doing the same. I've never seen that before, I'm sure. I'll boot up 10.04 and see what I get and post back.

In the meantime, you don't say which language you need a thesaurus for. There's as irritating omission that's being plaguing Open Office for some time now: no British English Thesaurus, and we can't even use the American English one. 

If you are using UK English, the fix is in this link:

[http://www.weeklywhinge.com/?p=69](http://www.weeklywhinge.com/?p=69)

---

### Post by coffeecat on 2010-09-17
Well, this is curious. My 10.04 OpenOffice is showing the same. I can't do a spellcheck. I'd not noticed that before.

However, my Karmic OO is OK, even though it doesn't show a spellchecking dictionary in the Extension Manager the way Hagar de l'Est's link describes.

@dogdo, what language and which national variant are you using? It seems that UK English is being very badly served.

---

### Post by AlphaLexman on 2010-09-17
Go to -> Tools -> Options -> Language Settings -> Writing Aids ->

[LIST]
[*]_A_vailable language modules
[*]_U_ser-defined dictionaries
[*]_O_ptions
[/LIST]
And make sure all your necessary items are installed and check-marked.

---

### Post by coffeecat on 2010-09-17
> **AlphaLexman said:**
> Go to -> Tools -> Options -> Language Settings -> Writing Aids ->

[LIST]
[*]_A_vailable language modules
[*]_U_ser-defined dictionaries
[*]_O_ptions
[/LIST]
And make sure all your necessary items are installed and check-marked.

No. My writing aids are all checked. They appear exactly the same as uRock's screeshot in post #3. And my spellchecker window appears broken just as the OP's screenshot in post #4. Neither does Hagar de l'Est's link help if you are using British English - no British English dictionary to download in their extension list [here]("http://extensions.services.openoffice.org/en/dictionaries"). I even tried changing all my language settings to US English. It didn't help.

I'll be interested to see if any of the posted suggestions helps the OP.

---

### Post by Hagar Delest on 2010-09-17
According to that thread: [Real English]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=28484"), there is an extension here: [English dictionary (based on Oxford English Dictionary) 1.0.3]("http://extensions.services.openoffice.org/en/node/1890").

If there is no dictionary extension, I can't see how the spell checker could work. Have you tried to reinstall them?

NB: I only use the vanilla version of OOo (see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)), perhaps the Novell build used by Ubuntu is more tricky about the spell checking.

---

### Post by coffeecat on 2010-09-17
> **Hagar de l'Est said:**
> there is an extension here: [English dictionary (based on Oxford English Dictionary) 1.0.3]("http://extensions.services.openoffice.org/en/node/1890").

If there is no dictionary extension, I can't see how the spell checker could work. Have you tried to reinstall them?

That extension works in Maverick. Many thanks. I'll try it in Lucid tomorrow. Too late now - I must log off soon.

I had tried installing other extensions but with no luck. And in Karmic, no dictionary extension appears in the Extension Manager yet I can do a spellcheck. Ho hum. It does seem as though there is a problem with British English in recent versions of Open Office. Interesting what you say about the Novell build. I might try the Opensuse live CD tomorrow and see what that gets up to.

---

### Post by Hagar Delest on 2010-09-17
> **coffeecat said:**
> in Karmic, no dictionary extension appears in the Extension Manager yet I can do a spellcheck. Ho hum.
With Ubuntu, the OOo packages are exploded in multiple packages managed by Synaptic. So they may be installed that way without appearing in the extension manager

It's the kind of differences I don't like between vanilla and distros versions, rather puzzling for users.

---

### Post by coffeecat on 2010-09-18
> **Hagar de l'Est said:**
> With Ubuntu, the OOo packages are exploded in multiple packages managed by Synaptic. So they may be installed that way without appearing in the extension manager

Indeed, but in Lucid and Maverick the spellchecking packages are installed.

However, I've found something interesting this morning. In Lucid's OO, if I type in, or open, a document with no spelling errors, then I get the  spellchecking mini-window with "spell-check is complete" that the OP gets with the odd blank in the text language field. If, though, I type or load a document with spelling errors then the F7 spill-chucker works just fine.

This may be what happened when I seemed to be successful in Maverick last night with the English dictionary you kindly linked to. I'll do some experimenting with the live CDs for both Lucid and Maverick to be sure I'm getting the default behaviour. It would be interesting to see if people get the same with languages other than UK English.

This would appear to be a bug, but a usability bug rather than a functional one. It would be better if the F7 window showed the language. That blank language field simply looks wrong.

Perhaps the OP is a perfect speller. :)

---

### Post by Hagar Delest on 2010-09-18
> **coffeecat said:**
> if I type in, or open, a document with no spelling errors, then I get the  spellchecking mini-window with "spell-check is complete" that the OP gets with the odd blank in the text language field. If, though, I type or load a document with spelling errors then the F7 spill-chucker works just fine.
Very interesting... and I see the same with 3.2.1 on xubuntu 10.04 too! Had never noticed. I had had this blank dialog too (and I could see a language in the status bar) but couldn't spot what was the problem (can't remember if it was for small documents without spelling errors but will care about that next time). I think you've just found out. Thanks!!!

If OP could confirm that adding a spelling error triggers the spell check, that would settle this. And it's definitively a bug (even if minor, it's misleading, the user thinking that his install is wrong).

---

### Post by coffeecat on 2010-09-18
> **Hagar de l'Est said:**
> And it's definitively a bug (even if minor, it's misleading, the user thinking that his install is wrong).

Agreed. Just for the record I've confirmed this from the live CD. I let it boot up with the default US localisation (sorry, localization :wink:) to be sure this wasn't just a UK English issue. The two screenshots are fairly explanatory but you can see that with a correctly spelt text, the text language field is blank - just like the OP's - but when I misspell "sat" as "sta", things work properly.

I'll check Launchpad later and see if anyone's reported this yet.

But that does still leave the UK English thesaurus problem, a fix for which I posted earlier. As the OP hasn't yet told us what language variant they're using, we can't be sure whether this is affecting them.

---

### Post by Hagar Delest on 2010-09-18
I've filed a report on the OOo issue tracker since it comes from its main code: [Issue 114586 - No language in spell check field if no mistake]("http://qa.openoffice.org/issues/show_bug.cgi?id=114586").

Note that even if spell checking is blank in such case, it doesn't prevent the thesaurus from working.

---

### Post by coffeecat on 2010-09-18
> **Hagar de l'Est said:**
> Note that even if spell checking is blank in such case, it doesn't prevent the thesaurus from working.

...except in the UK. :(

**Edit:** Sorry, I should have elaborated. The UK thesaurus issue seems to affect the Novell OO build as stated in the link I posted earlier, here:

[http://www.weeklywhinge.com/?p=69](http://www.weeklywhinge.com/?p=69)

I can confirm that without that fix the UK thesaurus is non-functional in OO in Ubuntu and Opensuse, but works just fine in OO in Fedora, Windows and MacOS. Which seems to agree with what they say about the Novell build being faulty.

> **Hagar de l'Est said:**
> I've filed a report on the OOo issue tracker since it comes from its main code:

Thanks. Better there than on Launchpad. I can confirm I see the same spell-checker issue in Opensuse, Fedora, Windows and MacOS, so clearly an upstream bug.

---

### Post by jimmers on 2010-09-18
I use O.O.o in Lucid, I have never ecountered any problems with Spell Check,
even with Word Docs, which I have to use through my work, just a thought, have you tried installing said dictionary through Synaptic.

Luck 

Jim

---

### Post by Hagar Delest on 2010-09-18
I confirm that the thesaurus works fine with the Sun version (3.2.1 on xubuntu 10.04):

---

### Post by uRock on 2010-09-18
I was just using OpenOffice on the LiveCD and it works fine also. 

Have any of the people having issues tried reinstalling OpenOffice? I know this doesn't really fix the problem, but it may fix the symptoms.

---

### Post by coffeecat on 2010-09-18
> **uRock said:**
> I was just using OpenOffice on the LiveCD and it works fine also. 

Do you mean the spellchecker blank text language field, or the UK thesaurus issue? I can definitely confirm that I get what the OP sees with the spell-checker - but only with a correctly-spelt document - with the Lucid live CD. The UK thesaurus seems to be a separate issue and does only affect you if your OO is set up with UK localisation.

---

### Post by wilee-nilee on 2010-09-18
My OO in Lucid is doing a auto-check on the screen, strange that all the others wouldn't be. I only use the auto-check to check spelling.
[ATTACH]169894[/ATTACH]

---

### Post by uRock on 2010-09-18
Just the spell check. I never use the thesaurus.

Edit: This could be because I am using English(US).

---

### Post by Hagar Delest on 2010-09-18
> **wilee-nilee said:**
> My OO in Lucid is doing a auto-check on the screen, strange that all the others wouldn't be. I only use the auto-check to check spelling.
Spell check works fine as long as there is a mistake. See the other screenshots and the bug report.

Thesaurus is a separate issue it seems.

---

### Post by wheels666 on 2010-09-24
adding the nz english extension sorted out my spell checker - it's  unfortunate that people who use default usa english etc don't generally  think about that aspect, but for people in canada nz aus etc it's a  biggie

---

