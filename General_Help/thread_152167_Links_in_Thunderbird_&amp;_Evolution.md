---
title: "Links in Thunderbird &amp; Evolution"
date: 2006-03-29
forum: General Help
---

### Post by smasterson on 2006-03-29
I'm sorry, I hate to ask this question again but I can't seem to find the answer on my own. Whenever I click on a link in either thunderbird or evolution it doesn't open firefox. I checked in preferred applications and in the custom settings under web browser I have mozilla-firefox %s. Is this right? Or is the problem in thunderbird & evolution? Any help would be GREATLY appreciated.

Thank You

---

### Post by AndrewCaul on 2006-03-29
What *does* it open in? Or does it not open at all?

---

### Post by smasterson on 2006-03-29
[QUOTE=AndrewCaul]What *does* it open in? Or does it not open at all?[/QUOTE]


It opens nothing at all.

---

### Post by Peter Randall on 2006-03-29
Hi
I have the self same problem with KDE. I have also tried the Thunderbird and Firefox Forums with no luck. I have tried playing around with various settings with no result. Any help to resolve this would be greatly appreciated.

---

### Post by siminone on 2006-03-29
I don't use thunderbird but I did have the problem when I used mandrake. I use evolution now and I have no problem with loading pages into firefox. 

To fix the problem with thunderbird, you will have to enter the following entry into your prefs.js file  that thunderbird uses for preferences.

user_pref("network.protocol-handler.app.http", "mozilla-firefox");
user_pref("network.protocol-handler.app.https", "mozilla-firefox"); 

To find the prefs.js file:
    Go into Places menu on Ubuntu toolbar.
    Click on Home Folder menu option
    Press Ctrl + H to view hidden files
   Click on .thunderbird folder (i think or .mozilla)
   Click on folder with xxxxx.default (where xxxx is random characters and numbers)
   edit the prefs.js and add above entries.

Hope this helps.

[http://forums.mozillazine.org/viewtopic.php?t=343905&highlight=mailto+prefs](http://forums.mozillazine.org/viewtopic.php?t=343905&highlight=mailto+prefs)

[http://kb.mozillazine.org/Default_browser](http://kb.mozillazine.org/Default_browser)

---

### Post by smasterson on 2006-03-30
Thanks for the help. I got evolution to work using the links to the mozillazine forums that you gave above. Thanks again for the help. It is GREATLY appreciated.

---

### Post by Peter Randall on 2006-03-30
Just received a reply from the Mozilla forum that works. The command line is slightly different to the one shown above:

user_pref("network.protocol-handler.app.http","/usr/bin/firefox");

Hope this is of help to others.

regards.

---

