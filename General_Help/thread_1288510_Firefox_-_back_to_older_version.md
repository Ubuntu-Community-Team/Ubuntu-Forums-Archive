---
title: "Firefox - back to older version"
date: 2009-10-11
forum: General Help
---

### Post by KarenAK on 2009-10-11
I usually update whenever I see the icon on the panel - turns out to be a big mistake.
With the Firefox update of 3 days ago I now cannot use my StumbleUpon extension properly anymore. No more Discoveries ! I had hoped that they'd fix it in one of the following updates but it doesn't look like it. 

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.5pre) Gecko/20091009 Ubuntu/8.10 (intrepid) Shiretoko/3.5.5pre

So I have decided to go back to an older version if at all possible and to hell with the canonical (or whose ever) updates they offer every day.


Anybody here who can tell me where to get an older version ? Synaptics only has the current one.

Any help is much appreciated.
thanks in advance.

---

### Post by lovinglinux on 2009-10-11
> **KarenAK said:**
> I usually update whenever I see the icon on the panel - turns out to be a big mistake.
With the Firefox update of 3 days ago I now cannot use my StumbleUpon extension properly anymore. No more Discoveries ! I had hoped that they'd fix it in one of the following updates but it doesn't look like it. 

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.5pre) Gecko/20091009 Ubuntu/8.10 (intrepid) Shiretoko/3.5.5pre

Looks like you are using an extra repository for Firefox, like *ubuntu-mozilla-daily* or backports, because version **3.5.5pre** is not a stable one. It's an development release, due to the *pre* suffix. Running unstable development releases usually result in such issues.

Most likely that you can still run StumbleUpon extension, by overriding the compatibility check. See [https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)

> **KarenAK said:**
> So I have decided to go back to an older version if at all possible and to hell with the canonical (or whose ever) updates they offer every day.

You should not ignore Canonical updates. What you should do is to be more careful and understand the consequences of installing additional repositories, before doing it.

> **KarenAK said:**
> Anybody here who can tell me where to get an older version ? Synaptics only has the current one.

To stick with the stable version of Firefox 3.5, you should uninstall it, then disable the extra Mozilla/Firefox repository you have in the Software Sources, then update and then install Firefox again. This should put the stable version back, which is 3.5.2.

BTW, I recommend reading the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by KarenAK on 2009-10-11
thank you for your reply.

You are right of course - when firefox 3 took such a long time I installed the Shiretoko version. However, I thought they'd eventually replace it with the official one. 

My mistake.

Thank you for your help :-)

---

### Post by 98cwitr on 2009-10-12
go Chromium, I don't use Firefox any more since they got flash working properly:

[http://nixbasics.com/component/content/article/47-linux/125-help-articles-linux-installing-google-chrome-in-ubuntu-kinda?directory=115](http://nixbasics.com/component/content/article/47-linux/125-help-articles-linux-installing-google-chrome-in-ubuntu-kinda?directory=115)

---

### Post by DeMus on 2009-10-12
> **KarenAK said:**
> thank you for your reply.

I was not aware that I am using a developers version of firefox. Nor was I aware of using such a repository.

In order to be able to deactivate the right one, here's my list of repositories that Synaptics lists:

Ubuntu Software
canonical-supported Open Source software (main)
Community-maintained Open Source software (universe)
Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues (multiverse)
Source Code

Third-Party Software
cdrom:[Kubuntu 8.10_Intrepid Ibex_ - Release i386 (20081029.1)]/intrepid main restricted
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
[http://archive](http://archive) canonical.com/ubuntu intrepid partner (Source code)
[http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) intrepid main
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) intrepid main
[http://ppa.launchpad.net/ubuntu-mozilla.daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla.daily/ppa/ubuntu) intrepid main (Source Code)
Medibuntu - Ubuntu 8.10 "Intrepid Ibex" free non-free
Medibuntu (source) - Ubuntu 8.10 "Intrepid Ibex" free non-free (Source Code)


--> which is it ?


Thank you for your help :-)

.

To find out which repository delivers the pre version of FF do this:
Open Synaptic
At the bottom left click on Origin.
Then further up you see the repositories. Click them one by one. With every click you see on the right which packages originate from that repo. Do this until you find the FF pre version.

---

### Post by lovinglinux on 2009-10-12
Remove Firefox 3.5, then remove these sources below, then update, then install Firefox 3.5 again.

```
http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu intrepid main
http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu intrepid main (Source Code)
```

---

### Post by KarenAK on 2009-10-12
@98cwitr - as far as I know StumbleUpon doesn't work on Chromium. And having a working StumbleUpon again is the reason for opening this thread in the first place  - but thank you for your suggestion.

@demus - sorry, I thought I had edited the post quickly enough to hide my rashness. It was a bit early for me this morning and I replied before properly reading through lovinglinux's post, then edited the post - obviusly too late. After all he did say *ubuntu-mozilla-daily...* still that tip about the Origin button is very useful - Thank You :-)

@lovinglinux - sorry for the confusion. Your explanation was perfectly ok - once I was awake enough and my brain working again...  Thank you :-)

---

