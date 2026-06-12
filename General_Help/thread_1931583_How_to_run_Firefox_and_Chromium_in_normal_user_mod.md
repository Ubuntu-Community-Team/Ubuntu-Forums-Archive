---
title: "How to run Firefox and Chromium in normal user mode?"
date: 2012-02-25
forum: General Help
---

### Post by kaplis on 2012-02-25
Hei!

Today made reinstall of 10.4.4LTS (because 11.10 is a big crap, but thats another story:).

After reinstall I did update and I cant use Firefox and Chromium to access web as a normal user anymore. Have to run *sudo firefox* in terminal. So any downloaded file I have to save in *root* folder, which I dont want to do, especially, to surf the web.

How it is possible to get back to normal user access mode?

Thank You

---

### Post by mikodo on 2012-02-25
Follow the links (Webgapps one) suggested in this thread by LovingLinux, and it shows how to do this for Mozilla Firefox. You can see if you can tailor it for chromium, also.

[http://ubuntuforums.org/showthread.php?p=10941116](http://ubuntuforums.org/showthread.php?p=10941116)

[http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions)

Basically, this is what is suggested:

Check the ownership of **~/.mozilla/** and **~/.mozilla/firefox/** folders.  If these folders are owned by root, then it could prevent Firefox from  saving settings or even running.
 To change the ownership back to you, close Firefox and run this command (do not replace $USER):
 ```
sudo chown -R $USER:$USER ~/.mozilla
```

Good Luck!

---

### Post by 3Miro on 2012-02-25
The simplest thing that I can think of is to open Nautilus (Places->Home) then hit Ctr+H to see the "hidden files". Look for .mozilla and either delete it or rename it to .mozilla_mybackup. Then try running firefox again. This will delete all settings along with your bookmarks.

BTW you should never run a browser as root, it is not a good idea.

---

### Post by kaplis on 2012-02-26
Hei,

none of your advices helped. I can change the ownership with *sudo chown -R $USER:$USER ~/.mozilla* , but still internet can be accessed only in root mode:/

And Webgapps page doesnt run:)

Any advice?

---

### Post by kaplis on 2012-02-26
Btw, this thing appears in fresh 10.04.4LTS install.

Could it be a bug?

---

### Post by mikodo on 2012-02-26
> **kaplis said:**
> Hei,

none of your advices helped. I can change the ownership with *sudo chown -R $USER:$USER ~/.mozilla* , but still internet can be accessed only in root mode:/

And Webgapps page doesnt run:)

Any advice?

I know that you said that you couldn't open the links I provided, but there is a section to continue with, to follow along for more options to correct what is wrong, if that first command didn't work. Just in case you can reach it, from another computer, or a friends', here it is:

[http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting)

Did you do what 3Miro suggested? You should be able to do that, don't you think?

---

