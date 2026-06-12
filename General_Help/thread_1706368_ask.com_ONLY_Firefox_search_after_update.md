---
title: "ask.com ONLY Firefox search after update"
date: 2011-03-13
forum: General Help
---

### Post by madtom1999 on 2011-03-13
In firefox a recent update has forced Ask.com into the search toolbar - possibly via the Ubuntu Modifications pack 0.9rc2 as disabling this removes even ask from the search engine list.
This is on several machines I have and exists on a fresh user with no addons other than those provided by ubuntu.

---

### Post by lithopsian on 2011-03-13
The package that does this (in recent Ubuntu releases) is xul-ext-ubufox.  It provides a plugin to enable access to Firefox addons through repositories rather than having to go direct to Mozilla or other locations., but as you have seen it also makes nasty tweaks to your configuration.  My advice would be to get rid of it completely, but that's me.  It get my Firefox from Mozilla or another trusted build.  If Ubuntu can't resist changing Firefox then I don't want that version.[I][B]
[/B][/I]

---

### Post by Krytarik on 2011-03-13
Simply purge the mentioned package, "xul-ext-ubufox", or at least disable the resulting add-on via Firefox' options: "Tools -> Add-ons -> Extensions -> Ubuntu Firefox Modifications".

---

### Post by madtom1999 on 2011-03-14
I've found the problem:
[https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768](https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768)

---

### Post by Krytarik on 2011-03-14
> **madtom1999 said:**
> I've found the problem:
[https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768](https://bugs.launchpad.net/ubuntu/+source/language-pack-zh-hans-base/+bug/732768)
Ah, interesting, thanks for pointing out!

Is it correct then, that if you remove the package "xul-ext-ubufox", you end up with having no search engines at all?

I'd like to add that I took part in this thread earlier regarding the same issue:
[http://ubuntuforums.org/showthread.php?t=1704788](http://ubuntuforums.org/showthread.php?t=1704788)

Do you have a different locale than "en-US" then? Did you try the workaround described in the bug report, the second one?

---

### Post by madtom1999 on 2011-03-20
I deleted /usr/lib/firefox-addons/searchplugins/en-GB/ (as per Chris Coulson).
 And, yes, removing the package xul-ext-ubufox leaves no search engines

---

### Post by Krytarik on 2011-03-20
> **madtom1999 said:**
> I deleted /usr/lib/firefox-addons/searchplugins/en-GB/ (as per Chris Coulson).
 And, yes, removing the package xul-ext-ubufox leaves no search engines
Thanks!

---

### Post by 3vi1 on 2011-09-25
Looks like they've managed to recreate this problem in Oneiric with today's FF update.  :/

I'm trying to search launchpad to see if anyone's reported it, but it keeps timing out.

---

### Post by darkhole on 2011-09-25
> **3vi1 said:**
> Looks like they've managed to recreate this problem in Oneiric with today's FF update.  :/

I'm trying to search launchpad to see if anyone's reported it, but it keeps timing out.

The same happend to me... Weeeird, because works fine on Firefox, not in Nightly.
Edit: Also happend onf FIrefox 7... With today update.. Seems to be a Firefox bug, because Ubufox only add ask.com engine, but the others engines found here: /usr/lib/firefox-addons/searchplugins/ Should appear.

---

### Post by clvx on 2011-09-25
I'm having the same issue. Last night I left my system doing the latest updates and today I realized firefox only had ask.com as default engine, and thunderbird didn't show images  as simple html; it only shows  plain text or original html. If someone opens a bug in launchpad please post the link here.

---

### Post by bkratz on 2011-09-25
> **clvx said:**
> I'm having the same issue. Last night I left my system doing the latest updates and today I realized firefox only had ask.com as default engine, and thunderbird didn't show images  as simple html; it only shows  plain text or original html. If someone opens a bug in launchpad please post the link here.



here is another thread about the ask.com thing, with some possible answers.

[http://ubuntuforums.org/showthread.php?t=1849721](http://ubuntuforums.org/showthread.php?t=1849721)

---

