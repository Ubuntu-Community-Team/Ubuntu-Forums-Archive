---
title: "Firefox find and search bars &quot;skipping&quot; letters when typing"
date: 2009-07-07
forum: General Help
---

### Post by chezzo on 2009-07-07
I've recently started having a really strange problem in Firefox - when I type in the find or search bars, or alternative search bars such as Hyperwords, some letters are occasionally missed out. This doesn't happen when I type in the location bar, or anywhere on a webpage, or in any other application!

Strangely, the letters most affected seem to be n, i, r and s. They are not missed out all of the time, but often enough to be annoying - I can often fix the problem by backspacing and re-typing the letter, but this requires that I constantly watch what I'm typing if I don't want to search for the wrong thing.

The problem started for me on Firefox 3.1, and has not been solved by updating to 3.5. Any ideas?!

---

### Post by danwood76 on 2009-07-07
It is probably caused by a plugin/setting.

If you start firefox in safemode do you get the same issues?

From a terminal:
```

firefox --safe-mode

```

---

### Post by chezzo on 2009-07-07
You're right - it's being caused by Hyperwords. I seem to remember there being an update at the time that the problem started too, so that explains it. Weird that I can't find any references to anyone else with the problem, but I've emailed the developer.
Thanks.

---

### Post by lovinglinux on 2009-07-07
> **chezzo said:**
> You're right - it's being caused by Hyperwords. I seem to remember there being an update at the time that the problem started too, so that explains it. Weird that I can't find any references to anyone else with the problem, but I've emailed the developer.
Thanks.

I remember installing that extension some time ago, but it didn't last 30 minutes on my profile :)

---

### Post by chezzo on 2009-07-07
> **lovinglinux said:**
> I remember installing that extension some time ago, but it didn't last 30 minutes on my profile :)

you should really give it another go - if you take the time to customise it to your purposes you can do pretty much anything with it - you can use it to search any site with a few quick keyboard shortcuts (e.g. for google images type the query, hit enter, then s for search, i for images, g for google), translate, convert units, digg pages, and even tweet!

---

### Post by lovinglinux on 2009-07-07
> **chezzo said:**
> you should really give it another go - if you take the time to customise it to your purposes you can do pretty much anything with it - you can use it to search any site with a few quick keyboard shortcuts (e.g. for google images type the query, hit enter, then s for search, i for images, g for google), translate, convert units, digg pages, and even tweet!

I guess I made a confusion. The extension I'm talking about is actually Hyper-Anchor. The idea is great, but the implementation not so good ;)

I'm currently using [CyberSearch](https://addons.mozilla.org/en-US/firefox/addon/7931), which integrates search capabilities with keywords in the awesome bar and display them along with my bookmarks and history results ;)

For translation I use Nice Translator, which is pretty cool. I also use [Define](https://addons.mozilla.org/en-US/firefox/addon/3428).

---

