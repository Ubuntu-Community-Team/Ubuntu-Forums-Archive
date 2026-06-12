---
title: "Alt text in firefox?"
date: 2009-09-28
forum: General Help
---

### Post by ninjapirate89 on 2009-09-28
I just realized that I can't read the alt text on images in Firefox :(
I miss xkcd's extra hidden humor. Can you help?

---

### Post by fluffman86 on 2009-09-28
working for me.  What's your firefox version? Click Help > About in Firefox.

---

### Post by ninjapirate89 on 2009-09-28
3.0.14

---

### Post by ninjapirate89 on 2009-09-28
Just found these with google that might explain why its not working for me.
[http://forums.mozillazine.org/viewtopic.php?f=38&t=249850&start=0&st=0&sk=t&sd=a]("http://forums.mozillazine.org/viewtopic.php?f=38&t=249850&start=0&st=0&sk=t&sd=a")
[http://gadgetopia.com/post/3206]("http://gadgetopia.com/post/3206")

I'm going to look for the firefox extension that they mention in the second one.

---

### Post by fluffman86 on 2009-09-28
what happens if you right-click > properties on the image?

---

### Post by ninjapirate89 on 2009-09-28
I can see alt text and title text! Thanks. At least now I can use that. I would prefer hovering though. It's much easier. I did find an extension but it doesn't work :(

---

### Post by iamaYs on 2009-09-28
Have you tried left clicking on the image first then hovering? Maybe you have to activate the image first. But in my firefox browser I get the alt tags fine by just hovering.

---

### Post by ninjapirate89 on 2009-09-28
> **iamaYs said:**
> Have you tried left clicking on the image first then hovering? Maybe you have to activate the image first. But in my firefox browser I get the alt tags fine by just hovering.

I hadn't tried it, but now I have, and it didn't work. :(

---

### Post by fluffman86 on 2009-09-28
I think I remember this happening the other day, but I'm not having the problem now.  Maybe a reboot fixed it?

Also, have you considered upgrading to firefox-3.5?  Follow the directions for adding the ppa on 
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
Then go to Applications > Accessories > Terminal and type:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install firefox-3.5
```
Note that this will replace firefox 3.0.  You should make a backup of your .mozilla folder (/home/username/.mozilla) as well.  Just in case. :)

---

### Post by ninjapirate89 on 2009-09-28
> **fluffman86 said:**
> I think I remember this happening the other day, but I'm not having the problem now.  Maybe a reboot fixed it?

Also, have you considered upgrading to firefox-3.5?  Follow the directions for adding the ppa on 
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
Then go to Applications > Accessories > Terminal and type:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install firefox-3.5
```
Note that this will replace firefox 3.0.  You should make a backup of your .mozilla folder (/home/username/.mozilla) as well.  Just in case. :)

Will that install Shiretoku (however its spelled) or will that actually install firefox?

---

### Post by fluffman86 on 2009-09-28
yes?

Shiretoko *IS* firefox.  Just an up-to-date version packaged by the mozilla-daily team.  Mine says Shiretoko in the title bar, but the "firefox" command and "firefox-3.5" are the same, and open shiretoko.  Hope that makes sense. :-\

---

### Post by ninjapirate89 on 2009-09-28
Yeah I've used shiretoku before. I don't know what it is about it but I don't really care for it. I just realized that I have karmic on my laptop so I'll see if alt text works on firefox there.

Edit -> Alt text works in Firefox 3.5.3 on Karmic.
Edit2 ->  </thread> I'll just deal with using right click -> properties on my desktop til Karmic is done.
Edit3 -> :lolflag: Thanks for the help.

---

### Post by fluffman86 on 2009-09-28
How long ago did you try shiretoko?  If it was still in beta, then yeah, maybe there were problems.  Anyway, you can upgrade to firefox-3.5 here instead, getting only the security updates:
[https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa)

---

### Post by ninjapirate89 on 2009-09-28
> **fluffman86 said:**
> How long ago did you try shiretoko?  If it was still in beta, then yeah, maybe there were problems.  Anyway, you can upgrade to firefox-3.5 here instead, getting only the security updates:
[https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa)

Thanks, I'll give that a try.

Edit -> Added the PPA and updated but still no alt text. I went ahead and installed Shiretoko to see if it would work and it doesn't either :( 
I also did a random search through about:config for anything related to alttext and only found one thing but changing it didn't fix it.
Looks like I'm stuck until Karmic whether I like it or not.

---

