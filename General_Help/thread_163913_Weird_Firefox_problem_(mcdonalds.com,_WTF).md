---
title: "Weird Firefox problem (mcdonalds.com, WTF?)"
date: 2006-04-21
forum: General Help
---

### Post by asusrules on 2006-04-21
hello,
every time i hit firefox icon, it loads up **mcdonalds.com**. i set the homepage location to google but it still loads mcdonalds. can someone please help me????


thanks a bunch!

---

### Post by moon_dog on 2006-04-21
well if setting the homepage doesn't work, you can always erase the .mozilla folder found in /home/*profile*/  it's a hidden folder, so you'll have to enable hidden folders (i think it's CTRL + H).  once you erase the .mozilla folder, everything will be set to default on firefox.  however, this erases everything, bookmarks, cookies, etc.

---

### Post by towsonu2003 on 2006-04-21
moving the folder might be a good idea (see below), but I would first try to understand why that happened. 

try putting this instead of a web address in firefox and hit enter:
about:config
in the coming screen, there will be a box you can write into, called "filter". put url (as keyword, keyword is "url") in there and see whether you see anything related to mcdonalds. 

to move the profile:
```
mv ~/.mozilla/firefox ~/Desktop/firefox.mcdonalds
```now your bookmarks will be on your desktop for you to browse and to import to a new firefox profile ("manage bookmarks" > Import).

---

### Post by astoltz on 2006-04-21
Right click on the icon, then select properties.  Get rid of the "%u" in the command. That is, change the command 
FROM: firefox %u
TO: firefox

I don't remember specifics but it seems like this is a firefox bug that it does an "i'm feeling lucky" search when started with that %u option.  Then again, I could be all wrong.

---

### Post by Harold P on 2006-04-21
Is your homepage "s"?

If you just type s in the toolbar, it takes you to McDonalds.

---

### Post by Kevinator on 2006-04-22
Yeah, it could very well be that the shortcut is messed up. Try running from a terminal by just typing "firefox" at the prompt. If that works properly then you need to edit the launcher to remove whatever extra stuff is causing the problem.

---

### Post by asusrules on 2006-04-22
its fixed by the shortcut problem,

thanks for all of your guys help!

---

### Post by elamericano on 2006-04-22
I'm Lovin' It! :mrgreen:

---

### Post by PriceChild on 2006-04-22
[quote=Harold P]Is your homepage "s"?

If you just type s in the toolbar, it takes you to McDonalds.[/quote]

OMG he's right!!!

What's going on here? :O

---

### Post by astoltz on 2006-04-22
It's just an "I'm feeling lucky" result when you do a google search for 's'.

---

### Post by Kevinator on 2006-04-22
Firefox has a feature that causes it to do a Google "I'm feeling lucky" search if you enter something that's not a web address. Personally I think this feature is far too confusing to be enabled by default. It tends to get triggered unintentionally and the user has no explanation for what has happened. Often people interpret it as some form of virus or browser hijack. I wish they would disable it by default.

---

### Post by aysiu on 2006-04-22
You can change that if you type ```
about:config
``` in the address field and search for ```
keyword.URL
``` The default is ```
http://www.google.com/search?btnI=I%27m+Feeling+Lucky&ie=UTF-8&oe=UTF-8&q=
``` I'm not sure what to change it to, though, if you want something else or to just turn it off completely.

---

