---
title: "Firefox bookmarks ubuntu 11.04"
date: 2011-10-06
forum: General Help
---

### Post by Azrael84 on 2011-10-06
Hi,

Anyone else had issues with firefox books in 11.04? firstly any click on a bookmark is treated as a left click (making it impossible to right click and bring up properties to rename a bookmark for example), and bookmarks cannot be reorganised by dragging them into different folders or up or down.

The usual bookmark button in firefox (normally just under the google search bar in the top right hand corner) allows the bookmarks when accessed through it to behave as usual, but the problem is this bookmark button only appears sporadically.

Anyone else experiencing these issues? I'm using firefox 7.01. Is there a work around?

---

### Post by dino99 on 2011-10-06
sudo dpkg-reconfigure firefox

---

### Post by Frogs Hair on 2011-10-06
I have been using only nightly builds and this has been the norm on all of them . I have to rename the bookmarks when added  or use the unsorted bookmarks option to enter properties . I thought it was default behavior in the newer versions .

---

### Post by Krytarik on 2011-10-06
> **Azrael84 said:**
> Anyone else had issues with firefox books in 11.04? firstly any click on a bookmark is treated as a left click (making it impossible to right click and bring up properties to rename a bookmark for example), and bookmarks cannot be reorganised by dragging them into different folders or up or down.
Is this via Unity's Global Menu in the top panel?
If so, yes, every click is handled like a left-click; afaik, as I didn't exactly use Unity myself so far.

Regards.

---

### Post by Azrael84 on 2011-10-06
> **dino99 said:**
> sudo dpkg-reconfigure firefox

I tried this and got >  Please restart all running instances of firefox, or you will experience problems. 

I then did a restart and didn't run any firefox upon logging in and tried again, still the same message. I then tried ps auxwww | grep firefox and kill [process num], still same message. Also just tried killall -9 firefox, still same msg.

I then found this website [http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/](http://www.mattcutts.com/blog/how-to-fix-firefox-is-already-running-error/) and delelted the lock and .parentlock files as suggested but still I get the same message....any ideas?

---

### Post by Azrael84 on 2011-10-06
> **Krytarik said:**
> Is this via Unity's Global Menu in the top panel?
If so, yes, every click is handled like a left-click; afaik, as I didn't exactly use Unity myself so far.

Regards.

Yes, it is. When I do things via built in bookmark button all is good, but as I say this appears and disappears on my firefox, so sometimes I'm forced to use the global unity bar...

---

### Post by Azrael84 on 2011-10-07
I've ended up just removing the unity addon and the firefox built in bookmarks now work fine at least.

Still wondering why I couldn't seem to kill all instances of firefox to do that dkpg reconfigure..hmm..

---

### Post by Krytarik on 2011-10-07
> **Azrael84 said:**
> Still wondering why I couldn't seem to kill all instances of firefox to do that dkpg reconfigure..hmm..
Those message is *always* generated, regardless if there are instances of Firefox running at that time or not; and in fact *after* 'dpkg' did its job.

---

### Post by Frogs Hair on 2011-10-07
Properties in bookmarks appear as usual after disabling global menu integration .:o

---

### Post by Krytarik on 2011-10-07
> **Frogs Hair said:**
> Properties in bookmarks appear as usual after disabling global menu integration .:o
Of course! ;-)

---

