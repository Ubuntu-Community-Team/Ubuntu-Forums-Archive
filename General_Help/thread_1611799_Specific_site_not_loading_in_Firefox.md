---
title: "Specific site not loading in Firefox"
date: 2010-11-02
forum: General Help
---

### Post by mikembm on 2010-11-02
[http://www.newegg.com](http://www.newegg.com) does not load for me in Firefox. It works fine in Chromium and in Windows. I have tried disabling IPv6, Firefox in safe mode, and also typing the IP address in directly but still doesn't work. Also, I cannot ping the site (I can ping other sites) and yet somehow it still loads fine in Chromium.

---

### Post by cpmman on 2010-11-02
Do you have noscript add-on?
Check white and black lists there and in any other (parental control etc.) you may have.

---

### Post by mikembm on 2010-11-02
No, I don't.
And I don't think it's an addon either because I have disabled all of them.

---

### Post by abrianb on 2010-11-07
I have the same problem, I don't use no script and I disabled adblock plus. No joy. Chrome opens this page without fail. Midori works as well. I tried upgrading to 4.0b8pre and still no newegg.

---

### Post by mikembm on 2010-11-07
> **abrianb said:**
> I have the same problem, I don't use no script and I disabled adblock plus. No joy. Chrome opens this page without fail. Midori works as well. I tried upgrading to 4.0b8pre and still no newegg.

I still don't know what caused it, but I was able to fix it by completely uninstalling firefox, deleting my config directory, and then reinstalling it. However, be warned that this will remove all of your firefox settings/addons/cookies/etc...

```

sudo apt-get purge firefox
rm -rf ~/.mozilla
sudo apt-get install firefox

```

And after doing the above, I was able to reinstall all of my previous addons and reset all my settings and it continued to work just fine.

---

### Post by sidzen on 2010-11-07
It looks like installing adblock then uninstalling it may be common to your problem.  After dist-upgrade (actually, an aptitude safe-upgrade) firefox 3.6.12, *et al*, resulted in more functionality in my case.

Cheers!

---

### Post by abrianb on 2010-11-07
Ipurged ./mozilla and unistalled firefox. Then reinstalled firefox. I went to [www.newegg.com](www.newegg.com) . The site loaded no problem. I went to my home page, installed firefox sync. I tried to go to [www.newegg.com](www.newegg.com), failed to load. I tried to disable sync then go to [www.newegg.com](www.newegg.com) but still no success . Sync will cause the problem. Any ideas other than purge and unistall without sync?

---

### Post by dino99 on 2010-11-07
you might email to newegg admin about that issue (check logs for usefull errors)

---

### Post by pheonix7117 on 2010-12-26
A less-invasive (possible) fix at: [http://support.mozilla.com/ak/questions/762363](http://support.mozilla.com/ak/questions/762363)

Essentially, it says:
> Try:

   1. Navigating to about:config
   2. Searching for "intl.accept_languages"
   3. Right click on the matching result and click "Reset". 

Newegg doesn't respond if you send a malformed Accept-Language header. There is some plugin that is changing the default value for that header (I'm pretty sure it is, or was, Firefox Sync)


---

### Post by abrianb on 2010-12-28
**@**[pheonix7117]("http://ubuntuforums.org/member.php?u=454377") , Thanks this works great. I really appreciate the help.

---

