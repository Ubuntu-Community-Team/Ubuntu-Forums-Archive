---
title: "Browser display in Mozilla (Ubuntu 11.04)"
date: 2011-09-29
forum: General Help
---

### Post by You Buntoo on 2011-09-29
I am new to Ubuntu (11.04), and web pages which contain Flash only display in small size, in middle of display window. There are large borders to the left and right of the browser display. I have tried mozilla zoom settings and different screen resolutions. Anyone know what's up?

---

### Post by lovinglinux on 2011-09-29
Are you referring to fullscreen video or the page itself? 
Are you using a dual monitor setup? 
Can you post a screenshot?
What version of Flash you are using?

---

### Post by paul_in_london on 2011-10-02
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1851070](http://ubuntuforums.org/showthread.php?t=1851070)

11.10 is due out in a little under 2 weeks. You may have more luck with that.

Also, try burning an 11.04 live cd. Boot from the cd, select try Ubuntu without installing and see if that works as it should:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

In the live environment, you may need to do:

```
sudo aptitude install flashplugin-downloader
```

Sorry - in 11.04 I think it's still called **flashplugin-nonfree**, not flashplugin-downloader.

---

### Post by You Buntoo on 2011-10-02
this is my screenshoot, fullscreen not an issue, dual monitor not an issues, flashes is 10.2.159

---

### Post by paul_in_london on 2011-10-02
Another thought - see what you get with this:

[https://www.youtube.com/html5](https://www.youtube.com/html5)

(i.e. join the HTML5 trial).

---

### Post by holycow131415 on 2011-10-02
what is your screen resolution. it looks like its a high resolution and that is why the site is centered like that.

---

### Post by paul_in_london on 2011-10-02
The attached screenshot from tvcatchup.com is without full screen in 11.10. Full screen is fine though.

Maybe you can post the equivalent Windows screenshot (i.e. same page).

---

### Post by You Buntoo on 2011-10-03
Lovinglinux: thanks for your reply, fullscreen is not an issue, have played youtube videos on fulscreen.. it's fine

holycow: thanks, but I have tried all the screen resolutions and none of them help

paul in london: thanks but I don't think you are seeing the bigger picture ( as am I not)

---

### Post by paul_in_london on 2011-10-03
Not sure why the page is displayed like that. Here are 2 screenshots from my virtual machine @ work (11.10) - one of which is the same web page.

What resolution does your "Displays" page show (see my 3rd attachment)? With my physical machine it's 1920x1600.

---

### Post by You Buntoo on 2011-10-03
[attach]203467[/attach]

---

### Post by paul_in_london on 2011-10-03
For comparison, what does bbc.co.uk look like?

---

### Post by lovinglinux on 2011-10-03
I don't see the problem. The sites you provided look the same on my machine. The pics you provided from your virtual machine are different, because the VM resolution is 1024x768.

Those sites are not dynamically adapted to your screen width. This is not a problem with your browser, monitor or OS. Is the web site that is designed like that, so they don't look bad on low resolution monitors.

---

### Post by paul_in_london on 2011-10-03
Yes, I understand why the VM screenshots look different compared with my widescreen monitor at home. I was trying to say (in a roundabout way) that I don't see the problem either!

---

### Post by You Buntoo on 2011-10-03
Ubuntu, XP

[ATTACH]203479[/ATTACH][ATTACH]203480[/ATTACH]

---

### Post by lovinglinux on 2011-10-04
> **You Buntoo said:**
> Ubuntu, XP

[ATTACH]203479[/ATTACH][ATTACH]203480[/ATTACH]

Resolutions are not the same.

> **paul_in_london said:**
> Yes, I understand why the VM screenshots look different compared with my widescreen monitor at home. I was trying to say (in a roundabout way) that I don't see the problem either!

Sorry, I mixed up the replies and thought you was the OP.

---

