---
title: "How to install Internet Explorer (IE) 8.0 on Ubuntu"
date: 2010-04-05
forum: General Help
---

### Post by badaveil on 2010-04-05
I am very happy surfing the Internet with **Chromium** my regular browser, it's really fast but alas, for work, I need to access some applications that require IE. I've tried to install IE7 using PlayonLinux but it takes ages to load and also hangs. I need one that loads reasonably fast and functions well. Believe me, if not for those IE-biased applications, I wouldn't even look at IE but what to do?!

Any SIMPLE advise on how to install IE on Ubuntu? Thanks

---

### Post by claracc on 2010-04-05
Perhaps this link [http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html) can help you to install IE8 in wine.

Regards

---

### Post by wilee-nilee on 2010-04-05
There is a firefox addon that emulates other browsers so to speak called user agent switcher, I use it to access my college's blackboard system.

I don't think you can get above IE7 with wine. I would just install XP in a virtual and use it that way if you have the ram.

---

### Post by asmoore82 on 2010-04-05
I say VirtualBox OSE(OpenSource Edition).

The Wine method linked above requires native dll's so either way you technically
need a valid Windows license, because of course IE is **_NOT_** free.

---

### Post by badaveil on 2010-04-05
I was overjoyed when claracc provided a link for me to investigate but what asmoore82 says is true. The object in Open Source is not to rely on any licence software, I also want to prove to some sceptic managers how powerful Open Source is. I understand what wilee-nilee is saying because I know and tried to use Chrome to emulates IE by installing an IE something, however I found out that the IE application I need to open doesn't respond to it so I'm back to square 1.

Keep the suggestions coming folks. You see, if I can make this idea workable,I can prove to the government how they can save much money by merely relying on Ubuntu as the operating system and here, I'm talking in terms of millions of Ringgit and if that happens people will look towards Ubuntu as the better OS, Yeah!!!!

---

### Post by cong06 on 2010-04-05
Here's a addon for Firefox that can be used to tell websites that you're running Internet Explorer:
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Then there's IEs4Linux which is the same thing as running IE in wine.
[Legal notice]("http://www.tatanka.com.br/ies4linux/page/Legal_notices").
[Main]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

I'm curious if the Firefox extension works.

---

### Post by ozPATT on 2010-05-14
Firefox extension doesn't really do what it should. It definitely changes the user agent but I have a website in development that looks different in IE6, 7 and 8. Using this user agent addon, the site looks great in IE6 7 and 8! So can't be working, or if it is working, it isn't suitable for development testing.

---

### Post by cong06 on 2010-05-15
> **ozPATT said:**
> Firefox extension doesn't really do what it should. It definitely changes the user agent but I have a website in development that looks different in IE6, 7 and 8.

Well, That depends. If you expected Firefox to act exactly like IE (with all it's faults and everything) there's no way thats going to happen without using IE itself.

If you wanted Firefox to pretend that it is IE in order to view sites that "require Internet explorer" then the previously mentioned plugin may work.

---

### Post by TeoBigusGeekus on 2010-05-15
A thing you can try in Opera:
Go to the web site that demands IE, right click and choose edit site preferences. Go to Network tab and choose Identify as Internet Explorer.

---

### Post by alexthunder on 2010-05-27
I wasn't able to install IE8 using a tutorial from wine reviews. Well it was installed, but I can't enter any URL because there is no address bar and I can't open a dialog for entering URL either.

I was able to install IE7 though
[http://stream-recorder.com/forum/install-internet-explorer-7-ie7-ubuntu-10-t6721.html](http://stream-recorder.com/forum/install-internet-explorer-7-ie7-ubuntu-10-t6721.html)
It works OK, but I don't know how to make HTTPS work. Any ideas?

---

### Post by irv on 2010-06-15
I have been playing around with "PlayOnLinux" with is for games, but you can load many other things like IE7. I have it running on My Ubuntu desktop take a look at the screen shot.
[ATTACH]160559[/ATTACH]
The only problem I have is getting logon to websites. I get a funky error.

---

### Post by badaveil on 2010-06-15
Mmm...I gave up the idea of installing IE on Ubuntu because it seems that the sites I want to visit that are dependent on IE are also dependent on Active-X. Anyway, thanks forumers for the feedbacks.

---

