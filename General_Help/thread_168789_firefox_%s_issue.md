---
title: "firefox %s issue"
date: 2006-05-01
forum: General Help
---

### Post by kristof_v on 2006-05-01
eum i have a very weird problem with firefox 1.5.0.2

when i start the app with firefox %s it loads mcdonalds.com
when i start it with firefox it loads the homepage.

what the f*ck is going on?????

---

### Post by Stealth on 2006-05-01
Don't use %s then :lol:

---

### Post by kristof_v on 2006-05-01
what exactly do the %s en %u parameters mean? :-k

---

### Post by erik_boi on 2006-05-01
It is because firefox is searching for %s and returning the first site... mcdonalds.com

---

### Post by harisund on 2006-05-01
You might have realized by now that Firefox  can be started from the command line. Whatever  is passed to it become arguments to it. So if you were to do ```
firefox http://www.google.com
``` it would open google and depending on the way you have set up firefox up I believe ```
firefox http://www.ubuntu.com http://ubuntuforums.org/
``` would start the sites on multiple tabs.

Now, firefox also has by default the feature of returning Google's first search result if you type in something that is not a true URL. Just open firefox, and in the address bar type in ```
ubuntu forums
``` without any http, ':' or '//'. Firefox understands this is not a website, so does a Google search for it, and comes up with the first search result "Sort of a 'I'm feeling luck' in Google." 

Combining the above 2, you would be able to see why ```
 firefox %s
``` resutls in what you want. Go to Google and search for '%s' or use this url [http://www.google.com/search?hl=en&q=%25s](http://www.google.com/search?hl=en&q=%25s). Funny, I have no idea why %s would make Google return McDonalds. 

Now, generally %s is used to refer to a string. You would never have to do so yourself, but if you are clicking on an URL in another application (say you are on #ubuntu in xchat, and somebody sends a pasteboard link, or you are seeing someone's resume pdf that lists an online resource). When you click on a URL in another application, that application silenty calls firefox with that URL name, and the %s is substituted appropriately.

---

