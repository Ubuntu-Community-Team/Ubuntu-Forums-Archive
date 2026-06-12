---
title: "No Javascript in 12.4LTS"
date: 2012-05-01
forum: General Help
---

### Post by mervynb on 2012-05-01
I've just updated from Ubuntu 11.10 to 12.4 and I now find that, using Opera 11.61, the javascript at [http://speedtest.mybroadband.co.za/](http://speedtest.mybroadband.co.za/) does not work.  I updated Opera to 11.62 but that made no difference.  I then tried to access the page using FireFox but also without success.

Opera 11.61 worked properly under Ubuntu 11.10 so, as two browsers have problems with the site under 12.4, it seems that Ubuntu is the problem rather than the browser.

Any suggestions?

---

### Post by kc1di on 2012-05-01
if you haven't already install ubuntu-restricted-addons and ubuntu-restricted-exatras 

you can do that in a terminal by typing the following.

```
sudo apt-get install ubuntu-restricted-addons ubuntu-restricted-extras
```

Then try the browser and that page again.

---

### Post by mervynb on 2012-05-01
> **kc1di said:**
> if you haven't already install ubuntu-restricted-addons and ubuntu-restricted-exatras 

you can do that in a terminal by typing the following.

```
sudo apt-get install ubuntu-restricted-addons ubuntu-restricted-extras
```

Then try the browser and that page again.


Thanks for the suggestion.  I've tried that but it doesen't seem to make a difference for either Opera or Firefox.

---

### Post by kc1di on 2012-05-01
Sorry that didn't work go to software center and do a search for icedtea and install the java plugin.

---

### Post by vasa1 on 2012-05-01
If "*it seems that Ubuntu is the problem rather than the browser*" were true there'd be a few more complaints.

I suggest you dig into your browser settings and enable javascript. If you've got some extensions, make sure that they're set properly.

---

### Post by mervynb on 2012-05-01
> **kc1di said:**
> Sorry that didn't work go to software center and do a search for icedtea and install the java plugin.

I actually had the icedtea plugin installed.  A bit more digging though and I realised I didn't have the Flashplayer plugin installed.  A quick visit to Adobe sorted that out and both Opera and Firefox are now happy to access the URL.

---

### Post by kc1di on 2012-05-01
> **mervynb said:**
> I actually had the icedtea plugin installed.  A bit more digging though and I realised I didn't have the Flashplayer plugin installed.  A quick visit to Adobe sorted that out and both Opera and Firefox are now happy to access the URL.

Glad it's working for you.  Flashplayer should have been installed with the Ubuntu-restricted so don't know why it was not working for you , in any event glad it is now 
Good Luck,
D ;)

---

