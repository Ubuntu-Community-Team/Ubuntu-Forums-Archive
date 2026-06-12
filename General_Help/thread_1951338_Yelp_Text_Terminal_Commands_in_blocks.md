---
title: "Yelp Text: Terminal Commands in blocks"
date: 2012-04-02
forum: General Help
---

### Post by Oceola on 2012-04-02
Recent install of 10.04.04.
Yelp search and display of everything so far seems appropriate however when moving to Advanced Topics the Headings are missing for Terminal Commands and GNU info Pages are missing while the topics underneath, clicking on the boxes, reveals the topics but not the headings.
This from the Gnu Page:
·&#66652;&#66671;&#66687; &#66662;&#66671;&#66643;&#66676; &#66640;&#66673;&#66657;&#66663;&#66655;
&#66641;&#66670;&#66665;&#66651;&#66662;&#66646;&#66665;&#66671;&#66665;&#66660; &#66642;&#66665;&#66661;&#66669;&#66671;&#66651; &#66660;&#66674;&#66671; &#66659;&#66663;&#66660;&#66640; (&#66662;&#66671;&#66643;&#66676;)

This from the Terminal Commands page:
&#66661;&#66664;&#66671;&#66648;&#66667;&#66665;&#66660; &#66640;&#66673;&#66657;&#66663;&#66655;
&#66641;&#66670;&#66665;&#66651;&#66662;&#66646;&#66665;&#66671;&#66665;&#66660; &#66642;&#66665;&#66661;&#66669;&#66671;&#66651; &#66660;&#66674;&#66671; &#66659;&#66663;&#66660;&#66640; (&#66661;&#66664;&#66671;)

I've tried updating or changing about everything I can think of to remedy this with no change. Any thoughts or help appreciated.
Thanks

---

### Post by Oceola on 2012-04-02
Found out the blocks in the titles were Shavian an alphabet named after George Bernard Shaw. Found the ttf-MPH 2B Damase supports it.
It is a strictly phonetic sounding character set and has no value to me in Yelp since I can't read it, it's not being English.
Is this a bug?
Should it be reported as a bug?
or has some brigand left a slime trail in my computer?
Is this paybacks for removing Pulse, Ekiga, Erlang and Evolution?

---

### Post by Oceola on 2012-04-07
Fixed this by editing the /usr/share/yelp/*.xml files.
Edit consisted of doing a search in each of the xml files for "shaw."
There was one line which contained "en@shaw" which was completely removed.
The plain line above which contained the Shavian characters was edited and the characters replaced with the appropriate language character set, in my case English.
Also performed a general system wide search for en@shaw and found a folder in the locales section. This was deleted.
These changes worked with or without the system fonts toggled on or off.
For what it's worth.

---

