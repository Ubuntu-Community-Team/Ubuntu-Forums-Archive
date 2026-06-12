---
title: "Firefox Hijacked??"
date: 2005-03-13
forum: General Help
---

### Post by pixel80r on 2005-03-13
I upgraded to hoary last night and began using firefox to browse Slashdot. from slashdot, I followed a couple links to external sites related to whirlwind activity on Mars...blah blah blah...

This morning I opened Firefox and it loads [www.whatyouseek.com](www.whatyouseek.com) search page.
My home page is set to Google and when I click the home icon in the toolbar, it loads Google. I have no idea where firefox is getting the instruction to load whatyouseek.com
Being the moron that I am, I forgot to check the preferences in firefox to make sure that java was disabled and that javascript was limited etc... oops.
Could this be a hijack in firefox??

I unstalled firefox, and installed it again. that didn't work. Still loading whatyouseek.

Any Idea how to get firefox back to a "default" state?  :-(

---

### Post by bored2k on 2005-03-13
[QUOTE=pixel80r]I upgraded to hoary last night and began using firefox to browse Slashdot. from slashdot, I followed a couple links to external sites related to whirlwind activity on Mars...blah blah blah...

This morning I opened Firefox and it loads [www.whatyouseek.com](www.whatyouseek.com) search page.
My home page is set to Google and when I click the home icon in the toolbar, it loads Google. I have no idea where firefox is getting the instruction to load whatyouseek.com
Being the moron that I am, I forgot to check the preferences in firefox to make sure that java was disabled and that javascript was limited etc... oops.
Could this be a hijack in firefox??

I unstalled firefox, and installed it again. that didn't work. Still loading whatyouseek.

Any Idea how to get firefox back to a "default" state?  :-([/QUOTE]
 It could be related to a certain extension/theme/plugin you installed on Firefox.

Here I have:
gmail notifier
tab browser pref
adblck
Qute3 theme

And I havent had any problems.

---

### Post by ssam on 2005-03-14
Your personal settings are stored in ~/.mozilla/firefox deleting that should fix it (you'll need to tell nautulis to show hiden files).

You probably should tell a mozilla person, have a look at [http://www.mozilla.org/projects/security/security-bugs-policy.html](http://www.mozilla.org/projects/security/security-bugs-policy.html) . you should probably keep a copy of the hijacked profile, incase they need to look at it.

---

### Post by DanN on 2005-03-14
Hmmm,
Same thing happened to me when I installed hoary to take a look, the same page comes up.
I'd be interested to know why too.

---

### Post by DanN on 2005-03-14
I just noticed as well, that it is only when I open firefox using the gdesklets startbar that it goes to whatyouseek, the applications menu item doesn't.

---

### Post by jdong on 2005-03-14
I'm unfamiliar with gdesklets. Can you please check the properties of that launcher button, copy-and-paste the exact command used by it to launch firefox, and let us take a look?

---

### Post by mike998 on 2005-03-14
Check out the shortcut's properties - You will find that it is something like "firefox %u" or something similar.  This is Firefox taking the first search result for "u" and sending it to the google "I'm feeling lucky" result.

Remove the %u and you should be okay.

---

### Post by jdong on 2005-03-14
You've hit the jackpot! Type in "%u" into Firefox's address bar. It'll redirect you to WhatUSeek.

---

