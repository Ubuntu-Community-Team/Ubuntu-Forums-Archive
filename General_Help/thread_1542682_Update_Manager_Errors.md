---
title: "Update Manager Errors"
date: 2010-07-30
forum: General Help
---

### Post by golfnut324 on 2010-07-30
Sort of new to Ubuntu here. When Update Manager runs, it gets to the end (63rd or 64th download package) and then I get the error messages attached. Is there anything I can do to eliminate these messages?

Thanks for any help.


[ATTACH]165038[/ATTACH]

---

### Post by Adola on 2010-07-30
Hi, for the first error, it means you've a key error, keys are used to validate software.  

This link might be able to help with your specific error: [http://www.forgenet.tamilbot.com/?p=57832](http://www.forgenet.tamilbot.com/?p=57832)

The next two _might_ be resolved with: 
```
sudo apt-get update --fix-missing
```

If that still doesn't fix it, you can remove it by commenting out the lines in your sources.list file:
```
sudo gedit /etc/apt/sources.list
```
You can comment by adding '##' infront of the line that contains the error.  Mind you, that'll disable you from getting updates, but if you're really that worried, just remove it, and come back to it when you're ready to tackle it again.

---

### Post by golfnut324 on 2010-07-31
> **Adola said:**
> If that still doesn't fix it, you can remove it by commenting out the lines in your sources.list file:
```
sudo gedit /etc/apt/sources.list
```You can comment by adding '##' infront of the line that contains the error.  Mind you, that'll disable you from getting updates, but if you're really that worried, just remove it, and come back to it when you're ready to tackle it again.


Thanks, I commented it out and now it doesn't bother me anymore. I will either upgrade to 10.04 (maybe that'll clear it up) or I'll dig into it deeper later.

Thanks again!

---

