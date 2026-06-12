---
title: "Firefox 4 beta 10 Flash plugin Ubuntu x64"
date: 2011-02-02
forum: General Help
---

### Post by balta on 2011-02-02
Hi there!
First of all sorry for this being the wrong section but I was unable to make a post in the x64 section.

Then, here it comes the problem:
I just installed Ubuntu 10.10 x64 on my machine (dual boot but I don't think that really can matter), everything seemed to be fine after the first hour of customizations\installs.
Then I realize I was using the "old" firefox and I think: 
"Hey let me try the new super badass firefox 4 beta 10, it works great in my netbook, it will work greater here!"
I get it from mozilla and it works just fine, addons and stuff.
Then on youtube, *BANG*: plugins needed > look for something > no results > go to mozilla official site > click adobe flash > get redirected > download it > try to intall > error: wrong architecture :s
No matter how I tried to get a x64 flash 10 plugin I failed but I really can't understand why only the new firefox is not working well. (please notice I didn't really installed it, I just start it from it's folder -as I do in my netbook- )
The strange part is that using the "old" firefox, youtube (and flash in general) works just fine.
Moreover firefox 4 works just fine in my x32 netbook (I'm using it right *now* ;)).
Therefore I'm quite convinced the problem is somewhat related to the fact that the OS is x64.

Can anyone give me a clue on what to do (besides reverting to the proper functioning version and wait for the official release OR install ubuntu x32)?

ThankyouThakyouThankyou

PS: I use firefox 4 also under windoze 7 x64, no problems there with flash o.O

---

### Post by balaknair on 2011-02-02
The problem is mainly due to the fact that the beta you downloaded is the x86-32 bit version of FF4(which is what you usually get from the default getfirefox beta download page).
It's to do with FF 32 bit version looking for the plugin in the wrong folder or something like that. Using the 64 bit version should fix this.

Get the 64 bit version here 
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b10/linux-x86_64/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b10/linux-x86_64/)

---

### Post by Nismine on 2011-02-02
I had the same issue some time ago and it was indeed because I was not using a 64-bit version of Firefox 4 (codenamed Minefield).
I got mine through PPA ([https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")) or you can also download the latest build of 64-bit Firefox here [http://nightly.mozilla.org/](http://nightly.mozilla.org/).

---

### Post by balta on 2011-02-03
Thankyou guys! I'll check it out as soon as I get home ^_^

---

### Post by balta on 2011-02-03
> **balaknair said:**
> The problem is mainly due to the fact that the beta you downloaded is the x86-32 bit version of FF4(which is what you usually get from the default getfirefox beta download page).
It's to do with FF 32 bit version looking for the plugin in the wrong folder or something like that. Using the 64 bit version should fix this.

Get the 64 bit version here 
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b10/linux-x86_64/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/4.0b10/linux-x86_64/)

Thanks man that worked just perfect! And now let's hunt some Java plugins and stuff lol!

---

