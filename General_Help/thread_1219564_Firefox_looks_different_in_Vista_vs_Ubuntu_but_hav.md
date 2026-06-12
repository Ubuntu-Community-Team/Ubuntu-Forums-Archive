---
title: "Firefox looks different in Vista vs Ubuntu but have same fonts.  Any ideas?"
date: 2009-07-21
forum: General Help
---

### Post by sois on 2009-07-21
Hi guys,

I am running Ubuntu 90% of the time vs Vista.  So far so good.  One thing is bugging me.  Fonts look different in Vista vs Ubuntu.  Take a look at these screens:

[IMG]http://www.sois.com/misc/Ubuntu.png[/IMG]

and Vista:
[IMG]http://www.sois.com/misc/Vista.JPG[/IMG]

Here is the font information for the site:
```

**[http://goallineblitz.com/game/home.pl](http://goallineblitz.com/game/home.pl)**

**[http://goallineblitz.com/css/main.css?6](http://goallineblitz.com/css/main.css?6)**

html, body {

	height: 100%;

	font-size: 12px;

	font-family: arial;

	text-align: center;

	background-color: #DDE3DD;

	margin: 0px;

	padding: 0px;


}

```

I verified I have Arial installed.  I opened Word Processor and checked.  Everything looks good.  Any reason for this discrepancy?

---

### Post by adamant715 on 2009-07-21
Of course they're going to look different. They both do everything different.

Not to be a douche or anything, but why does it matter really? They look very close to the fonts in vista.

---

### Post by kostkon on 2009-07-22
I can see in both cases the same fonts are used in *Firefox*. Thus, you indeed have the same fonts.

The only difference I can see is that it seems that in Windows the fonts don't have any (or have low) antialiasing/hinting applied to them.

You could try disabling or lowering the antialing/hinting in Ubuntu. You can do it in *System &#8594; Preferences &#8594; Appearance*.

---

### Post by sois on 2009-07-22
> **adamant715 said:**
> Of course they're going to look different. They both do everything different.

Not to be a douche or anything, but why does it matter really? They look very close to the fonts in vista.

As a web designer, it matters a lot.  I figured Firefox was Firefox across the board.  Notice how the "Next Game" under Graham Harrell moves to the next line in Ubuntu.  This is really annoying.

Arial should be Arial no matter how I look at it.  Thanks for the hinting advice, but that didn't work.

---

### Post by Vaphell on 2009-07-22
different rendering engines - different results

isn't the whole point of HTML/CSS separation of content and presentation?
You won't ever get pixel perfect results so design pages with some error margin. Cramming as much content as physically possible is doomed to fail in a lot of scenarios. Things look different on different OSes/browsers/engines/resolutions, people with sight problems can force minimum font size in browser preferences or override font settings in general, etc.

---

### Post by Finalfantasykid on 2009-07-22
Arial font is proprietary is it not?  Therefore Ubuntu does not natively support it(however you can still download it).
You might have to specify a default font which looks very similar to arial, and is supported by many/all distributions.

EDIT:  Oh you said you have Arial installed, well then disregard what I said earlier.

But, even though Firefox is Firefox, the fond rendering features comes from the OS, so stuff like hinting/anti aliasing.  Different algorithms(better IMO) are used for linux to AA text compared to in Windows.

---

