---
title: "flash confusion in Ubuntu 10.10"
date: 2010-12-23
forum: General Help
---

### Post by 55tptag on 2010-12-23
Hello,

I'm confused with Adobe Flash. I'm using 32-bit Ubuntu 10.10.  Flash was working for me in Google Chrome 8.0.552.224 but not with Firefox 3.6.13.

So, I tried to troubleshoot it myself.  I searched for how to uninstall Flash and I found a link to a thread from 2008,   
[http://ubuntuforums.org/showthread.php?t=951441]("http://ubuntuforums.org/showthread.php?t=951441")

I quickly ran the code posted.  And, of course, only after running the code did I bother to read the date the post was posted which was 2008.  I did:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
```

Then I ran 
```
sudo apt-get install adobe-flashplugin 
```

Then Shockwave Flash 10.1 r102 was working for youtube in Firefox.  And was still working in Google Chrome.

My questions are: Is there a site that has explicit steps for removing Flash from 10.10?

And I had thought that the file named "libflashplayer.so" always had to be located in Firefox's directory named, /home/user/.mozilla/plugins/ for it to work in Firefox.  But, now the only place that file exists is 
```
# find / -name "libflashplayer.so"
/usr/lib/adobe-flashplugin/libflashplayer.so
```

So, I guess I was wrong with thinking that the file named "libflashplayer.so" always had to be located in Firefox's directory named, "/home/user/.mozilla/plugins/".

And I have no idea where it's suppose to go for Google Chrome 8.0.552.224.  How does Chrome find it?  Just curious.

So, in the end, Flash is working for me in both browsers and I have no idea why ;)

---

### Post by TBABill on 2010-12-23
It's built into Chrome from Google. Chromium uses the flash plugin. So does Firefox. If you want to just have it simple to keep it installed and up to date, just install Flash-Aid extension in Firefox and let it do it's thing. It keeps you always with the latest version and the correct version (32 or 64 bit). Get it here [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

