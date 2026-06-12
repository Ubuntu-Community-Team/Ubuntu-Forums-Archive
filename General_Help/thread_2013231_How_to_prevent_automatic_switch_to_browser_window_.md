---
title: "How to prevent automatic switch to browser window when clicking on a hyperlink?"
date: 2012-06-30
forum: General Help
---

### Post by tellapu on 2012-06-30
How to prevent the automatic switch from e.g. an email in evolution/thunderbird to firefox when clicking on a hyperlink in the email?

When I click on a **hyperlink** in an email (Ubuntu 12.04,  Evolution 3.2.3 or thunderbird 13, although it happened in previous  versions as well), the program window (Evolution) in focus changes to  Firefox (default internet browser) to open the webpage. I would like  that it does **NOT** switch automatically from Evolution to  Firefox with every clicked hyperlink as I would prefer to read the  whole email first and then "manually" go to the Firefox with the opened  webpages.
I know that it is possible to prevent this **automatic change of program window** (email client to internet browser) as in Ubuntu 11.10 I had this preferred behaviour (before I now installed Ubuntu 12.04).
Does anybody know where I can change the preferences for this issue?
Thanks for any help, it bothers me daily. 
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by tellapu on 2012-07-23
Mlacunza posted an answer on another webpage and it works for me:

Open config window in Firefox: about:config
there find: browser.tabs.loadDivertedInBackground
and change to True.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

