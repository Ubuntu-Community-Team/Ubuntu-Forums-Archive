---
title: "Anonymous Browsing Software"
date: 2012-09-11
forum: General Help
---

### Post by amir786_z on 2012-09-11
Hi there guys is there any software in Ubuntu for anonymous browsing?

---

### Post by critin on 2012-09-11
There is in Firefox.  Would that work?

I know nothing about these programs, but google has a few listed.   I posted your question.   Here's one.

[http://askubuntu.com/questions/175306/what-alternatives-are-there-to-fiddler-debugging-proxy](http://askubuntu.com/questions/175306/what-alternatives-are-there-to-fiddler-debugging-proxy)

---

### Post by neomorphix on 2012-09-11
You can setup TOR in Ubuntu fairly easily and configure Firefox to use it. But I would go to [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en) and download torbrowser and extract it some place in your home directory. It comes preconfigured for anonymous browsing. And having it self contained within a single directory like that makes clean it up afterwards nice n easy. Let me know if you need any help getting setup.

---

### Post by amir786_z on 2012-09-11
> **critin said:**
> There is in Firefox.  Would that work?

I know nothing about these programs, but google has a few listed.   I posted your question.   Here's one.

[http://askubuntu.com/questions/175306/what-alternatives-are-there-to-fiddler-debugging-proxy](http://askubuntu.com/questions/175306/what-alternatives-are-there-to-fiddler-debugging-proxy)

google addons for anonymous surfing sucks :( thanks for posting that question in ask ubuntu

---

### Post by amir786_z on 2012-09-11
> **neomorphix said:**
> You can setup TOR in Ubuntu fairly easily and configure Firefox to use it. But I would go to [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en) and download torbrowser and extract it some place in your home directory. It comes preconfigured for anonymous browsing. And having it self contained within a single directory like that makes clean it up afterwards nice n easy. Let me know if you need any help getting setup.

thanks i will check that out :)

---

### Post by numbrain2go on 2012-09-11
> **critin said:**
> There is in Firefox.  Would that work?

you can also use chrome's incognito window (Ctrl+Shift+N)

P.S.
tor is great once you set it up :)

---

### Post by greatsirkain on 2012-09-11
well usually I would install tor but looking through the firefox add-ons it seems once again the best add-ons are reserved for Microsoft...It makes me sick.
You could try anonymox 0.9.9, seems to be the best of the bunch for browsing in firefox.
One thing for certain I will not be updating firefox again, everytime I do they take something good out.

Edit:  I decided to have a mini rant and not read what the guy above me had said, of course you can install tor with its own browser :P
[https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

---

### Post by amir786_z on 2012-09-11
thanks guys really appreciate u r help.. anonymox 0.9.9 wont work for me. i will go with tor Browser :grin:

---

### Post by greatsirkain on 2012-09-11
sudo apt-get install tor :)

Edit: I went for the annoymex thing first, loaded it up "500mb per day limit" + adverts, no it didn't work for me either! Did the above install.

---

### Post by critin on 2012-09-11
> **amir786_z said:**
> google addons for anonymous surfing sucks :( thanks for posting that question in ask ubuntu

It isn't an addon, not even googles.   It's "Private Browsing" on the firefox browser.

---

### Post by varunendra on 2012-09-12
+1 to tor, the only drawback - it makes browsing way too slow, and that's because how it works (bouncing packets through multiple randomly selected nodes within tor network, before delivering it to the destination host).

Another word of caution: nothing can "guarantee" anonymity on internet, not even tor. Tor's own information pages describe it best.


> **numbrain2go said:**
> you can also use chrome's incognito window (Ctrl+Shift+N)
Incognito window or Private browsing in firefox do not make you anonymous on the internet, they just don't store your browsing history on 'your' computer. Read this note in the incognito window -"**Going incognito doesn't affect the behavior of other people, servers, or software...."** and the remaining stuff below that note.

---

