---
title: "Browser Issues"
date: 2009-10-25
forum: General Help
---

### Post by MrCanuck on 2009-10-25
The other day i finally installed Ubuntu on my laptop (yes i know its sad but i was so excited to finally run Linux).  

I love Ubuntu, the desktop is great, and i like the look/feel of it.

But....i don't spend a lot of time on my Desktop, most of my time is spent in my Browser (loving Firefox).  Facebook, Twitter, Blogging, Google Docs, Google Reader, almost every thing i do is in my browser.   

Sadly i find using the Browser in Ubuntu painful.  Most websites insist on using Flash to display content on their pages.....and it seems that Flash & Ubuntu are not best buddies yet (my personal opinion from my experiences over the past few days).  

Facebook is laggy, some flash games i play are laggy or just don't work at all.  I even installed the latest version of firefox and flash with no change.

So what i am wondering is, am i missing something? something i need to have to make my browser run smoother in Ubuntu.  Will the new Ubuntu coming out in 4 days help any?  

I am aware it could possibly be a Browser Issue and nothing to do with Ubuntu so please don't think im bashing Ubuntu because i am far from doing that.  

Any help would be greatly appreciated. 

Thanks.

---

### Post by shadow120 on 2009-10-25
have you installed "ubuntu-restricted-extras" if not that might fix some of your problems

---

### Post by MrCanuck on 2009-10-25
No i have not installed that yet, where do i go to install that? 

Thanks.

---

### Post by shadow120 on 2009-10-25
open a terminal and run
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by DeMus on 2009-10-25
> **shadow120 said:**
> open a terminal and run
```
sudo apt-get install ubuntu-restricted-extras
```

Open a terminal to do that:
Menu Applications -> Accessories -> Terminal
Then type
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by lovinglinux on 2009-10-25
> **MrCanuck said:**
> Will the new Ubuntu coming out in 4 days help any?

If you are still using Firefox 3.0.14 then yes, it will help, since Karmic comes with Firefox 3.5 by default, which is a lot faster than Firefox 3.0. Nevertheless, it won't be a miracle maker. If you want to really improve flash performance, then use Firefox 3.6.a1 or Chromium. They both are still alpha versions.

There are a few things you can do to improve flash tho. See the Flash Optimization section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). I also recommend reading other sections, because some optimizations helps flash indirectly, by increasing Firefox performance.

---

### Post by MrCanuck on 2009-10-25
Thanks for the help with installing the restricted extras.  I got it all installed, restarted (not sure if that was needed).  

It does not seem to have done a whole lot to improve my experience.

Facebook is still laggy when scrolling up and down, and sites with any flash on them are still very slow.  By slow i mean it seems like it takes the pointer on the screen a few seconds to catch up to where i moved it to with my mouse.


I do notice all the time that my cpu is at 42% (running dual core with 2gb of ram).  I have the CPU Monitor turned on in the bar across the top of Ubuntu.  Even with browser closed and nothing running its at 42%.  Not sure if that means any thing.

Any more ideas?  

Thanks.

---

### Post by P4man on 2009-10-25
open a terminal and run 

```
top
```

to see what is hogging your cpu. Something seems wrong, so its good to troubleshoot that, but you might want to try opera or google chrome as significantly faster browsers.

---

### Post by lovinglinux on 2009-10-25
> **MrCanuck said:**
> Thanks for the help with installing the restricted extras.  I got it all installed, restarted (not sure if that was needed).  

It does not seem to have done a whole lot to improve my experience.

Facebook is still laggy when scrolling up and down, and sites with any flash on them are still very slow.  By slow i mean it seems like it takes the pointer on the screen a few seconds to catch up to where i moved it to with my mouse.


I do notice all the time that my cpu is at 42% (running dual core with 2gb of ram).  I have the CPU Monitor turned on in the bar across the top of Ubuntu.  Even with browser closed and nothing running its at 42%.  Not sure if that means any thing.

Any more ideas?  

Thanks.

See my previous post.

---

### Post by MrCanuck on 2009-10-26
I tried that "top" command and it showed nothing taking up my cpu, so i think that thing in the top bar is not working correctly (disabled it).

I installed Chrome after messing with Firefox for over an hr to get it to install the new 3.5 version.......i shall just wait till the new Ubuntu comes out. 

Chrome works a lot better, its never been so smooth on Facebook before.  Still cant play poker on facebook but hey its working better now.

Must be a browser issue with Firefox i guess.

Thanks for all the help.

---

