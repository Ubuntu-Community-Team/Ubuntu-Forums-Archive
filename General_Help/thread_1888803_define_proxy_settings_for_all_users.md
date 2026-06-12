---
title: "define proxy settings for all users"
date: 2011-11-30
forum: General Help
---

### Post by derek_mcgilvray on 2011-11-30
Hi, 

We're going to experiment with ubuntu in school.  We can connect to the internet when we point towards our proxy configuration script, but that only works for that user.  

As most of our 360 users will not be able to change their own proxy settings, is there a way to define proxy settings for all users?  

Thanks for any help.

---

### Post by Azdour on 2011-11-30
Hi,

I also faced something similar recently. We were using Firefox that went through a proxy but I found that I had to set it up for each user. Worse still was that the user could just simply go and change it.

The solution I have only works for Firefox, and started with me finding the following resource:

[http://ilias.ca/blog/2005/03/locking-mozilla-firefox-settings/](http://ilias.ca/blog/2005/03/locking-mozilla-firefox-settings/)

This lead me to finding the proxy preferences within Firefox that I needed to set. So I created a mozilla.txt file with the following:

```
lockPref("network.proxy.type", 1);
lockPref("network.proxy.http", "<insert your proxy url here>");
lockPref("network.proxy.http_port", <insert you proxy port here>);
lockPref("network.proxy.share_proxy_settings", true);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1");

```

I then used the link in the resource to encode it into mozilla.cfg.

The next thing was to find where Firefox lived in Ubuntu. I did this using through the terminal:

```
sudo updatedb
locate all.js
```

I found our Firefox lived in /usr/lib/firefox-3.6.13. I placed the mozilla.cfg file in /usr/lib/firefox-3.6.13. I then edited the all.js file located in /usr/lib/firefox-3.6.13/greprefs to add to the bottom:

```
pref("general.config.filename", "mozilla.cfg");
```

After I restarted Firefox I could see that the proxy was read-only. This was also true for the other users I logged in as.

The only problem with this solution comes when Firefox is updated. You'll need to go through the process again as there will be a new Firefox directory in /usr/lib.

---

### Post by derek_mcgilvray on 2011-11-30
Thanks for taking the time to help.  

Unfortunately, as a newbie to linux, I am finding it difficult to work with my version - Ubuntu 11.10, Firefox 7.0.1.  

Is there a way it will work with my current setup?

---

### Post by derek_mcgilvray on 2011-11-30
After playing around a bit, I've got a fix, at least until firefox updates!  

set proxy config for all users on all machines - type the following into usr/lib/firefox-7.0.1/defaults/pref/syspref.js: 
//
lockPref("network.proxy.http","proxy_address");
lockPref("network.proxy.http_port",3128);
lockPref("network.proxy.type",1);

Any other ideas please let me know.  

Thanks

---

