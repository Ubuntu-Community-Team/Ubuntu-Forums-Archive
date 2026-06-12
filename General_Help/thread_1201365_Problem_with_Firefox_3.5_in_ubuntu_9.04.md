---
title: "Problem with Firefox 3.5 in ubuntu 9.04"
date: 2009-07-01
forum: General Help
---

### Post by abhi_69 on 2009-07-01
Hello,
firefox 3.5 is available for download. but, it still not in official ubuntu 9.04 repo. i came to know from an internet article that, ubuntu 9.04 repo will not update to firefox 3.5 & this version will be available in ubuntu 9.10. but, i want to install it in ubuntu 9.04...i don't like .tar.bz2 format file provided by mozilla for linux, becoz some of my plugins not working in this version (totem-mozilla-plugin, vlc-plugin etc.).
actually i want a native build (.deb) of firefox 3.5 for ubuntu 9.04 which support all of my plugins & i can easily install & uninstall it using apt-get or synaptic as i do for firefox 3 versions.
i know about ppa of launchpad called 'ubuntu-mozilla-daily'..but, i can't install from this repo, becoz it can't import the gpg-key sucessfully (even i do this via synaptic).
i think this version of firefox may be update in ubuntu 9.10 repo. is there any way to enable ubuntu 9.10 (pre-release) repo in 9.04? so that, i can install firefox 3.5 easily via apt-get (i mean something like Fedora rawhind, by enable this, user can get packages build for next release)
is there any other ppa for firefox 3.5? how can i get it fully working just like firefox 3 in ubuntu 9.04 with all plugins?
any help for me?
plz. someone inform me about it.
Regards.

---

### Post by phatcartoon on 2009-07-01
Sorry, I can't be any help for you, but I am looking for some what of the same.  This is what I got so far and it's driving me f-in nuts.  WTF!  I went to synaptic package manager and saw firefox 3.5 there tried that out.  Seems fine and all, but it's not the full release; it's the shiretoke pre-release.  Next I downloaded the 3.5 file directly from the Mozilla website, but this didn't really work out for me.  Firefox opend up, but I get the error "can not find server" for all websites.  The typical not connected to the internet page.....Though I am connected to the internet and all other browsers will work fine.  So, WTF!  Some one please help!  I can find pages on pages of how to install the beta release online, but I want the full release to work.  I agree with the person above; deb package sounds awesome!  Why is something that should be super simple being so F-in hard.

---

### Post by abhi_69 on 2009-07-01
> **phatcartoon said:**
> Sorry, I can't be any help for you, but I am looking for some what of the same.  This is what I got so far and it's driving me f-in nuts.  WTF!  I went to synaptic package manager and saw firefox 3.5 there tried that out.  Seems fine and all, but it's not the full release; it's the shiretoke pre-release.  Next I downloaded the 3.5 file directly from the Mozilla website, but this didn't really work out for me.  Firefox opend up, but I get the error "can not find server" for all websites.  The typical not connected to the internet page.....Though I am connected to the internet and all other browsers will work fine.  So, WTF!  Some one please help!  I can find pages on pages of how to install the beta release online, but I want the full release to work.  I agree with the person above; deb package sounds awesome!  Why is something that should be super simple being so F-in hard.agreed with him....plz someone help us......thanz in advance!

---

### Post by masux594 on 2009-07-01
Well, i want to talk about the troubles with the FF extensions-plugins [EP for next use].. The thing that you must think about is: is more important the EP backward-compatibility or the develop of the main application? I'm a developer, and in the app that i develop i must change something that doesen't work fine, something that is slow, that raise some error, some new feature etc.. Example: if i change a the call of a method because actually doesen't satisfy all the circumstance that it need, so, for apply the request, i must change the call of this method in the parts where this methods were called.. So, the question is.. Is more important the backward-compatibility or the new feature that the same method can satisfy with little changes? Obvious that in most cases i try to keep the backward-compatibility of the method, but, if not, is more important the main program! This is a stupid example but i think that this onveys the idea!

Sysc, A[I][B]
[/B][/I]

---

### Post by masux594 on 2009-07-01
For the "installing" or .deb question.. Hmm.. i havent installed yet, but, if i find some helpful guide i'll post here the link..

Sysc, A

---

### Post by abhi_69 on 2009-07-01
i just able to install firefox 3.5 from launchpad ppa (without key)....but, its not final version..its minefield 3.1pre (unbranded firefox version)...when we get final branded version with nice firefox logo (no more round blue logo!!!!!)?
waiting for it now..........

---

### Post by andreselsuave on 2009-07-01
I have downloaded 3.5 from mozilla website, unzipped it, and tried it for a while. But now the thing is firefox 3.0.11 crashes with the following terminal output 

```
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Éxito
```


Anyone knows what's happening? 
I hope someone posts a .deb package or something :/. If I find something related I'll post it here right away.

---

### Post by masux594 on 2009-07-01
have u ever tried with Ubuntuzilla?

Sysc, A

---

### Post by masux594 on 2009-07-01
Try with [this]("http://ubuntuzilla.wiki.sourceforge.net/").. I hope is will be helpful.. 

Sysc, A

---

### Post by ak331 on 2009-07-01
I tried to install firefox 3.5 using either add/remove and by synaptic package manager as this did not work. 

Then I used using command line installation and I lost my firefox 3.0 but Icon was still in the function bar. I checked the properties of the icon and browsed to the /user/home/firefox folder and pointed to firefox (/home/vijender/firefox/firefox) and long behold when I double clicked on it, the application was firefox 3.5. may be it was cheating but now I have fully functional firefox 3.5.

I hope this helps somebody.

---

### Post by abhi_69 on 2009-07-01
> **ak331 said:**
> I tried to install firefox 3.5 using either add/remove and by synaptic package manager as this did not work. 

Then I used using command line installation and I lost my firefox 3.0 but Icon was still in the function bar. I checked the properties of the icon and browsed to the /user/home/firefox folder and pointed to firefox (/home/vijender/firefox/firefox) and long behold when I double clicked on it, the application was firefox 3.5. may be it was cheating but now I have fully functional firefox 3.5.

I hope this helps somebody.
how do u get firefox 3.5? is it final version? which repository u use for this? i tried ppa launchpad repo (ubuntu-mozilla-daily) & try command line installation, but, it installs minefield 3.5 browser (sheirteko) not firefox 3.5 final version.
can u explain in details?
i will be greatful.

---

### Post by masux594 on 2009-07-02
Or check [this one]("http://gaarai.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/")

Sysc, A

---

