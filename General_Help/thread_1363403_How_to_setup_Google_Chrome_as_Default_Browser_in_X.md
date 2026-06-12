---
title: "How to setup Google Chrome as Default Browser in Xubuntu"
date: 2009-12-24
forum: General Help
---

### Post by shanali4 on 2009-12-24
All in title. I m currently using LXDE desktop environment. Plz help. currently firefox is default browser

---

### Post by Atzu on 2009-12-24
I believe that if you go options and then basics there's a button that sets Google Chrome as default browser.

---

### Post by maxrpowell on 2009-12-24
Google Chrome also periodicly asks for you to set it as the defualt browser. If you keep using it for a while it will end up asking you somtime or another.

---

### Post by onyxwolf on 2009-12-24
Just hit the wrench button and open options on the bottom of the Basics tab it says default browser and if its not already set to it, there should be a button that says "Make Google Chrome my default browser." Just hit that and Chrome should do the heavy work for you; however you can also go to Application > Preferences > Preferred Applications and set it there under the Internet Tab > Web Browser.

---

### Post by shanali4 on 2009-12-25
> **onyxwolf said:**
> Just hit the wrench button and open options on the bottom of the Basics tab it says default browser and if its not already set to it, there should be a button that says "Make Google Chrome my default browser." Just hit that and Chrome should do the heavy work for you; however you can also go to Application > Preferences > Preferred Applications and set it there under the Internet Tab > Web Browser.

Thanks problem solved

---

### Post by bodhi.zazen on 2009-12-25
As an alternate option, from the command line :

```
sudo update-alternatives --config x-www-browser
```

---

### Post by oubiwann on 2010-08-01
> **bodhi.zazen said:**
> As an alternate option, from the command line :

```
sudo update-alternatives --config x-www-browser
```

I've been having a similar problem as the OP, but nothing seems to work. When I click on an HTTP link in Evolution, the page is opened by Firefox. When I open Firefox preferences, it shows that it's the default browser.

Application -> Settings -> Preferred Applications -> Web Browser is set to chromium-browser and Chromium's preferences indicate that *it's* the preferred browser.

Running update-alternatives as indicated above also shows that Chromium is the preferred browser. 

My guess is that there's some bit of gnome plumbing that needs to be tweaked, so that Evolution gets the clue, since it doesn't seem to be using the system preferences to get the default browser.

Why Firefox itself thinks that *it's* the default browser befuddles me, though. And this may indicate that the culprit is not a gnome setting...

---

### Post by oubiwann on 2010-08-01
> **oubiwann said:**
> I've been having a similar problem as the OP, but nothing seems to work. When I click on an HTTP link in Evolution, the page is opened by Firefox. When I open Firefox preferences, it shows that it's the default browser.

Application -> Settings -> Preferred Applications -> Web Browser is set to chromium-browser and Chromium's preferences indicate that *it's* the preferred browser.

Running update-alternatives as indicated above also shows that Chromium is the preferred browser. 

My guess is that there's some bit of gnome plumbing that needs to be tweaked, so that Evolution gets the clue, since it doesn't seem to be using the system preferences to get the default browser.

Why Firefox itself thinks that *it's* the default browser befuddles me, though. And this may indicate that the culprit is not a gnome setting...

Ah-ha! It *was* gnome plumbing. I managed to find the answer here:
  [http://www.google.com/support/forum/p/Chrome/thread?tid=479e566824181986&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=479e566824181986&hl=en)

In short, just do this:
```

  gconftool-2 --type string \
  -s /desktop/gnome/url-handlers/http/command "chromium-browser %s"

```

---

### Post by misterspider on 2010-11-08
> **oubiwann said:**
> Ah-ha! It *was* gnome plumbing. I managed to find the answer here:
  [http://www.google.com/support/forum/p/Chrome/thread?tid=479e566824181986&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=479e566824181986&hl=en)

In short, just do this:
```

  gconftool-2 --type string \
  -s /desktop/gnome/url-handlers/http/command "chromium-browser %s"

```

Finally, an answer to this! It's been plaguing me too. Thanks oubiwann.

---

### Post by maphmu on 2012-05-26
Although this is a very old thread, but maybe for someone like me would be glad to know, that the fix works with Xubuntu 12.04! 

Thanks a lot for that fix!

---

### Post by maphmu on 2012-05-26
> **maphmu said:**
> Although this is a very old thread, but maybe for someone like me would be glad to know, that the fix works with Xubuntu 12.04! 

Thanks a lot for that fix!

doesn´t work... :mad:
I also tried galternatives and the "default app" under settings under Xubuntu 12.04 /64bit with Chrome 19.0xx and no firefox or any other browser installed.

Maybe someone has an idea how to fix this problem, to set Chrome as default browser in Xubuntu.

Best regards
maphmu

---

### Post by oldos2er on 2012-05-26
Old thread closed. Please start a new thread for your question.

---

