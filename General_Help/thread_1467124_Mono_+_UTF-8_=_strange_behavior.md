---
title: "Mono + UTF-8 = strange behavior"
date: 2010-04-30
forum: General Help
---

### Post by bubulescu on 2010-04-30
Hello,

I did a quick search (here and Google) but I couldn't find anything relevant; on the other hand, the forum is a big place, so I didn't search thoroughly. Also, this section seemed good for asking for help so I posted here.

The problem is about running SMath Studio with mono. I used it in Karmic, upgraded (clean install) to Lucid, but I have the same behavior:

[img]http://i42.tinypic.com/efs8kk.png[/img]

The tooltip should show "Num**&#259;**r", just as in "Aritmetic**&#259;**" above. Special characters just won't show up in tooltips and dialogs. The main program, the menus and the help file are OK. 
Through the roadmap of fixes, I ended up installing mono-complete, but nothing was solved. This was in Karmic. Now I installed Lucid, clean; "/home" is on another partition, but I used a different username. I tried with and without ".fonts.conf", I changed the locale but everytime it complained about "LC_ALL" not being set up, I tried commenting it out, empty string "", eventually set to UTF-8 just so I wouldn't see the warnings. Nothing worked. This was done in Karmic, too.
I grabbed the sources from their web-page, compiled as the manual said, nothing. I ran the program from the console with "LC_ALL=C mono ...", even with "LC_ALL=ro_RO.UTF-8 ...", but it only complained about not supporting the codepage and falling back to "C"; the same happened for ISO-8859-2 and CP1250, even if I have them in locale. Also, running the bare command gave the warning: "Could not get Xim". I started iBus, made according settings, it stopped complaining but the result was the same. 
Right now, I'm a step away from making use of a crowbar. In the SMath's forum, I asked the developer about it but he showd me a screenshot and worked. He has openSuse which, as I understand, has 2.6 version of mono. That was what made me try to compile it myself (with the above result).

So, there you have it. If there's anyone who can help, please don't hesitate, you would spare a computer's life that way...


Regards,
Vlad.

---

### Post by bubulescu on 2010-05-01
...nobody?

---

### Post by bubulescu on 2010-05-03
"Bump" (?) to keep the thread alive.

---

### Post by Sam on 2010-05-03
Can you change the font used? Maybe it does not have the unicode blocks needed.

---

### Post by bubulescu on 2010-05-03
> **Sam said:**
> Can you change the font used? Maybe it does not have the unicode blocks needed.

It's the same font, that's the problem. Look, I've made another screenshot:

[IMG]http://i42.tinypic.com/34g0j0h.png[/IMG]

The missing character is the same as the one in "Editeaz**&#259;**". Also, "Fi**&#351;**ier" displays diacritics correctly. But the tooltip refuses to. Also, the dialogs:

[IMG]http://i40.tinypic.com/2ur4ahv.png[/IMG]

The title displays nicely, the rest doesn't. Can anyone try to get the program and try to change the language to one that uses diacritics? Does it work for you? Is it only my computer affected? What? Who? Where? ...? I have twice the gray hair I had before this. :(

---

### Post by bubulescu on 2010-05-03
Do all mono programs work with custom characters for you?

---

### Post by bubulescu on 2010-07-16
Among the many searches, it was suggested that I should add MS Sans Serif (micross.ttf) to my fonts. I did that (both in ~/.fonts and /usr/share/truetype/msttcorefonts), and now I get this:

[IMG]http://i27.tinypic.com/2hfmhed.png[/IMG]

The diacritics are shown in tooltips and dialogs, but the text is all garbled in the menus. It's like a reversed result, but worse.


I'm still hoping someone may know something...

---

### Post by zingo on 2010-07-16
I also see this problem (but with swedish chars like åäö)
I didn't have this problem before maybe it started around 9.04 or 9.10 don't remember

> it was suggested that I should add MS Sans Serif (micross.ttf) to my fonts. I did that (both in ~/.fonts and /usr/share/truetype/msttcorefonts)

How did you do that?

---

### Post by bubulescu on 2010-07-17
I googled for micross.ttf, downloaded it, copied it (at first) ~/.fonts, tested, then moved it in /usr/share/truetype/msttcorefonts, again tested, same result as in the last screenshot.

There was also a suggestion that one might only need to rename DejaVu via Fontforge (or similar programs) in "Microsoft Sans Serif" so that the font rendering engine would recognize it as the native one; a sort of a "free" alternative to the more costly one... Of course, I suspect some patent issues will still exist, but, eh...

I'm trying this method now, I'll let you know when I figure how to fiddle with Fontforge.


EDIT:
It doesn't work, in fact, it's worse: now there are no diacritics and the menus are garbled, too...


I'll just wait for other suggestions.

---

### Post by bubulescu on 2010-07-25
I found out the culprit: in my sources.list I had an update for libcairo2 which would result in the mess previously mentioned. I forced a re-installation with the official package and then I copied micross.ttf in ~/.fonts. 

Also, the trick with modifying a font works, too.

In short, the two solutions work.


Regards,
Vlad.

---

### Post by zingo on 2010-07-25
Worked for me also!

---

