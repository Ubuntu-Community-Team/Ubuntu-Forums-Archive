---
title: "Web browser default"
date: 2012-03-10
forum: General Help
---

### Post by rhchia on 2012-03-10
I have Chromium and firefox installed in my Ubuntu 11.10 and Chromium as the default system Web application. When I use firefox to surf net, it always opens up chromium when i click a link in a page. What can i do to fix this issue? I wan the link in firefox to be opened using firefox itself and visa versa

---

### Post by codemaniac on 2012-03-10
To change the default or re-confirm the default browser drop the line of code in the terminal  , use the update-alternatives command.

```
sudo update-alternatives --config x-www-browser
```

You can also check the manual pages of update-alternatives to get an detailed overview .

---

### Post by rhchia on 2012-03-10
i used the command and selected chrome. Tested on both browser and shows no problem on chrome side. Links are all open within the chrome browser. But firefox is giving me problem.i tried to login to this forum, it opens another tab firefox. not within the same tab. On top of that, i'm not logged in despite keying in the right credential.

[IMG]http://i5.photobucket.com/albums/y199/rhchia/Screenshotat2012-03-10144258.png[/IMG]

---

### Post by codemaniac on 2012-03-10
here is a parameter in the Firefox configuration that allows Firefox users to force the web browser to open links in the same tab unless one of the previously mentioned ways of opening links in new tabs or windows is selected.

type in [about:config] in a tab in the Firefox web browser. This should open the Firefox configuration. First time users need to accept a disclaimer. They then need to filter for the term [browser.link.open_newwindow]. The default value of that entry is [3] which opens links that would normally open in a new window in a new tab.



To force Firefox to open links (no matter if they have been designed to open in a new tab or window) in the same tab one would need to change the value to [1] which will open all links that would normally open in a new window in the same tab. Changing the value to [2] would open new windows in a new window (duh).

---

### Post by rhchia on 2012-03-10
it loading within the page now i'm still not able to login. the page refreshes but i'm not logged in. Could it be a chance my firefox is corrupted?

---

### Post by codemaniac on 2012-03-10
have you checked the remember me checkbox while logging in ?

---

### Post by rhchia on 2012-03-10
yes but to no avail. The page just refreshes itself

---

### Post by codemaniac on 2012-03-10
> **rhchia said:**
> yes but to no avail. The page just refreshes itself

Seems like there is no problem with firefox setup .
All i needed to ensure that if you are remembered by your browser , you log in next time .

---

### Post by rhchia on 2012-03-10
hmm... what could be the problem then? I can't login. If I change the default application via System Info to chrome, i use firefox to login, a new tab is opened using in chrome

---

### Post by codemaniac on 2012-03-10
Checking your cookies might help .Make sure your browser is accepting cookies from ubuntuforms.org .
You can force your browser to accept cookies if it is not currently accepting .
Something like below 
Tools->Options->Privacy->Use custom settings for history->Accept cookies from sites .

---

