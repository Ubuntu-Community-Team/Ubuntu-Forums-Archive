---
title: "Market APK Downloader extension on Chromium"
date: 2012-03-01
forum: General Help
---

### Post by gandaran on 2012-03-01
[http://codekiem.com/2012/02/24/apk-downloader/](http://codekiem.com/2012/02/24/apk-downloader/)
any of you got this chrome extension working on chromium?
looks like it can work but how do I disable SSL error warnings on chromium? instructions on the website are only for windows.

---

### Post by jrussell88 on 2012-05-06
Copy Chromium Web Browser from /usr/share/applications to ~/.local/share/applications/chromium-browser.desktop. 

Open Properties and edit the Chromium Web Browser permissions to make it executable, and change the command to "/usr/bin/chromium-browser  --ignore-certificate-errors %U" which allows APK Downloader to run.

However in Chromium there is no APK Downloader icon on Chromium's address bar to click. I'll try rebooting again and see if that works.

---

### Post by jrussell88 on 2012-05-06
I've rebooted a number of times, and also installed it in Google Chrome. After some faffing around - the %U parameter seems to have to go at the end of the line - APK Downloader 'Options' shows it is working correctly.

However there is still no button on the address bar to download apks. 

I'm running Google Chrome 18.0.1025.168 on Ubuntu 11.10 and Chromium 18.0.1025.168 (Developer Build 134367 Linux) on Ubuntu 11.10. 

Let me know if you get any further than I have as it'd be very useful.

OK it appears to be working for FREE apps, but not so far for purchased apps, which rather misses the point for me. The download button appears inside the address box on the browser.

---

### Post by gandaran on 2012-05-06
> **jrussell88 said:**
> I've rebooted a number of times, and also installed it in Google Chrome. After some faffing around - the %U parameter seems to have to go at the end of the line - APK Downloader 'Options' shows it is working correctly.

However there is still no button on the address bar to download apks. 

I'm running Google Chrome 18.0.1025.168 on Ubuntu 11.10 and Chromium 18.0.1025.168 (Developer Build 134367 Linux) on Ubuntu 11.10. 

Let me know if you get any further than I have as it'd be very useful.

OK it appears to be working for FREE apps, but not so far for purchased apps, which rather misses the point for me. The download button appears inside the address box on the browser.
/usr/bin/chromium-browser %U --ignore-certificate-errors
running fine here on Chromium with this start command but will not work with purchased apps, I believe it's not supposed to download purchased apps!

---

