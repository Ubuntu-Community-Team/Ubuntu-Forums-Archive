---
title: "How to set google chrome to only use Droid Sans and no other fonts on all pages?"
date: 2012-05-08
forum: General Help
---

### Post by georgelappies on 2012-05-08
Hi all
Here is my specs, ubuntu 12.04 64 bit with chrome 18. Is there a way to set chrome to only use one type of font (those specified for serif, sans and mono) in the preferences and only use those fonts on all pages irrespective of what font the page actually uses?

Here is some info should it be needed:

georgelappies@devbox:~$ uname -a
Linux devbox 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
georgelappies@devbox:~$ which google-chrome 
/usr/bin/google-chrome
georgelappies@devbox:~$ /usr/bin/google-chrome --version
Google Chrome 18.0.1025.168

---

### Post by vasa1 on 2012-05-08
Have you looked at Wrench, Settings, Under the Hood, Web Content, Customize Fonts?

---

### Post by georgelappies on 2012-05-08
> **vasa1 said:**
> Have you looked at Wrench, Settings, Under the Hood, Web Content, Customize Fonts?

Hi Vasa, yip those settings I think only applies if the web page does not specify a default font to use. Firefox has a tick box where you can un tick the ability of websites to specify their own font and thus all sites use your font as set in the font settings tab.

So far it doesn't seem as if chrome supports this :(

---

### Post by vasa1 on 2012-05-08
> **georgelappies said:**
> ...
So far it doesn't seem as if chrome supports this :(

Got it. Well, in that case you may have to try the old-fashioned way of editing Custom.css. This is, by default, an empty file found in your default profile folder: /home/user/.config/google-chrome/Default/User StyleSheets/Custom.css.

I had been through this exercise a couple of years ago, but decided against it because some pages wouldn't display well. But I'll try to hunt down some relevant tips.

---

### Post by vasa1 on 2012-05-08
Here's one of my threads from way back:
http://productforums.google.com/forum/#!searchin/chrome/arial$20font$20custom.css/chrome/NNMAESmBxP4/aOreDxiRzZUJ

It uses arial as an example.

---

### Post by georgelappies on 2012-05-08
> **vasa1 said:**
> Here's one of my posts from way back:
http://productforums.google.com/forum/#!searchin/chrome/arial$20font$20custom.css/chrome/NNMAESmBxP4/aOreDxiRzZUJ

It uses arial as an example.

Thanks Vasa, much appreciated. Weird though that chrome basically makes it impossible to do this then.

---

### Post by vasa1 on 2012-05-09
> **georgelappies said:**
> Thanks Vasa, much appreciated. Weird though that chrome basically makes it impossible to do this then.

But that's what Custom.css is for. For users who want to do something that, maybe, not most people want to do.

In any case, it's well-known that Chrome is not as customizable as something like Firefox or Opera.

---

