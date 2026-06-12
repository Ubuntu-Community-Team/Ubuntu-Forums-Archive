---
title: "Fix for Firefox address bar search?"
date: 2009-09-26
forum: General Help
---

### Post by Xzallion on 2009-09-26
Firefox's address bar searches in yahoo instead of google, and I want to change it back.  I tried about:config and checking the keyword.URL string but that says google and it still searches in yahoo.  I'm on Karmic Koala, and using firefox 3.5.3 if that helps.

---

### Post by rreese6 on 2009-09-26
if you click the Yahoo logo it will drop-down a menu so you can pick Google.
in the new window type "about:config"
promise to be nice
then search for this line
"browser.search.defaultenginename"
Make sure it says "Google"

---

### Post by Xzallion on 2009-09-26
The search bar (the one on the top right) is google, thanks for checking though.

In about:config searching for browser.search.defaultenginename shows Google.

I'm trying to get it where if I type a search in the address bar (location bar?) to search Google.  Any ideas?

---

### Post by rreese6 on 2009-09-26
Maybe it is this one:


search in about:config for keyword.URL

mine says this :keyword.URL;[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=)

---

### Post by Xzallion on 2009-09-26
Heres what my about:config keyword.URL shows
keyword.URL;[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=)

---

### Post by wojox on 2009-09-26
You mean the navigation bar?

---

### Post by Xzallion on 2009-09-26
Yeah thats probably it.  I have always heard it referred to as the address bar, the one you type the website name in like [www.website.com](www.website.com) or [http://www.anothersite.com](http://www.anothersite.com)

---

### Post by lovinglinux on 2009-09-26
Looks like a profile issue. Start a new profile and see if it works. You could also try **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

On a side note, I guess you will like the [CyberSearch](https://addons.mozilla.org/en-US/firefox/addon/7931) extension.

---

### Post by tlwolf on 2009-12-05
I'm having the same problem. keyword.URL is set to google's lucky search and it is enabled. browser.search.defaultenginename is set for google. I even tried a new profile, with the same results. Figuring it was a profile deal I reinstalled firefox, but no love there either. On top of all that, all the options in about:config that were not default, didn't have anything to do with the search. I was wondering if anyone might have found a solution.

---

