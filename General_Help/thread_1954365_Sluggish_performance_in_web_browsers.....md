---
title: "Sluggish performance in web browsers...."
date: 2012-04-07
forum: General Help
---

### Post by Eirreann on 2012-04-07
Let me say first off that Ubuntu performs like a dream in every other area, thus far!  I absolutely love it!
However, in all of the web browsers I have used I've been experiencing some very sluggish performance.  The web pages load more than fast enough, the problem is that when I scroll up or down, always, no matter what page I have open or what I am watching/listening to/viewing, there is visible lag in the scroll speed.  When watching a YouTube video, scrolling caused the infamous "This webpage is no longer responding" error (thank you, Chrome).
So what's going on here?  Is there a fix?
The only other time that the computer lags, is when I'm download/installing/updating something, but that is acceptable because they are high-process operations...

---

### Post by Redblade20XX on 2012-04-07
Can we have the specs of your computer?

-Red

---

### Post by Eirreann on 2012-04-08
> **Redblade20XX said:**
> Can we have the specs of your computer?
 
-Red
 
Okay, I'm running a DELL Inspiron 8600 with these specs:
Intel Pentium M 1.50GHz processor
2GB of DDR 333MHz RAM
Nvidia GeForce FX Go5200 video card
and a 55GB hard drive...
 
Really the only limiting thing, I think, in my setup is possibly my video card.  However, when I'm running XP (I've got Ubuntu set up as a dual-boot) the web browsers run fine!  Is it possible that Ubuntu isn't using all of my RAM?  And would running Ubuntu 2D help?
Sorry it took so long to reply!

---

### Post by Eirreann on 2012-04-08
This is still a problem!  Anyone able to help me out?

---

### Post by cody1233 on 2012-04-08
So after the page is loaded and you scroll up/down it says that?

---

### Post by Eirreann on 2012-04-08
> **cody1233 said:**
> So after the page is loaded and you scroll up/down it says that?

When I scroll up/down it just lags like crazy!  Rather than scrolling smoothly like it should, it kind of glitches slowly, so if I quickly drag the scroll bar to the top, it will take a few seconds before the computer registers that I've done so and then it will glitch to the top of the page, if that makes sense.  It's incredibly annoying!

---

### Post by Eirreann on 2012-04-08
Still in need of assistance...

---

### Post by wildmanne39 on 2012-04-08
Hi, please try what is in this link it usually fixes that problem.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thanks

---

### Post by Eirreann on 2012-04-08
> **wildmanne39 said:**
> Hi, please try what is in this link it usually fixes that problem.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thanks

Thanks for the reply!  I've followed the steps, and it doesn't seem to have changed at all *yet*; I'll restart my computer and see if that has fixed it.  Thanks!

---

### Post by Eirreann on 2012-04-09
> **wildmanne39 said:**
> Hi, please try what is in this link it usually fixes that problem.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thanks

Okay, just tried this method and it didn't work for me; the web browser is still choppy.  Also, I'm noticing that when I try to drag around a window on the desktop that too is a bit choppy.... why is this?  It works so much better on my XP (again, I'm dual-booting here) and I was under the impression that Ubuntu was supposed to be faster for older computers!

---

### Post by wildmanne39 on 2012-04-09
Hi, first when xp was made there was a lot less memory that could be installed so xp used much less, try running window 7 and you would have issues as well because it is a modern operating system not 10 or more years old.

From what I see your processor is most likely the issue it does not look very powerful.

You did not say what version of ubuntu you are using but I assumed it is 11.10 if that is the case log out and then into classic no effects that should help.

I recommend switching to lubuntu it is the most light on resources.

You can also type:
```
top
```
into the terminal and see what is using up the most resources.
Thanks

---

### Post by Cotopaxi on 2012-04-09
wildmanne

If the system itself is running like a dream, I suspect that is something related to the internet connection.

The only thing that comes to my mind is to disable IPV 6. Although there would be a contradiction with the fact that the pages load quite fast.

Eirreann

If you want give it a try disabling IPV 6, if you have firefox installed, you can go the following path:

> For example, in Firefox, type in the address bar: about:config
 then in "Search", type: ipv6
 You will see the variable network.dns.disableIPv6
 Change the value to true to disable IPv6 support in Firefox.

You can also double click on this line and it changes to true.

I got this hint from the following page:

[http://www.tipsandtutorials.net/disable-ipv6-will-speed-internet-connections.html]("http://www.tipsandtutorials.net/disable-ipv6-will-speed-internet-connections.html")

Give this a try and give us feedback.

Good luck.

---

### Post by wildmanne39 on 2012-04-09
Hi, this is what made me think what I do, because you said the web pages load fast if that is the case then it is not the IPV6.> The web pages load more than fast enough, the problem is that when I scroll up or down, always, no matter what page I have open or what I am watching/listening to/viewing, there is visible lag in the scroll speed.
If you are unsure if they load fast enough then you can set your settings to match the ones in the screenshots and that should make your speed faster.

Also you can post the output from:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Eirreann on 2012-04-09
> **wildmanne39 said:**
> 
From what I see your processor is most likely the issue it does not look very powerful.

You did not say what version of ubuntu you are using but I assumed it is 11.10 if that is the case log out and then into classic no effects that should help.


Yeah, my processor is old and slow, haha!  But it's well above the minimum (1GHz)...  So how do I switch to classic?  In the GUMP menu?

Also, I found a way to alleviate some of the lag.  I've been using a 1080p monitor with my laptop (which has a native res of 1200x800).  So now I'm using the laptop's monitor instead, and it runs quite a bit better (although there is still very noticeable glitchyness when scrolling/dragging).

But thanks again, guys, for responding!

---

### Post by idoitprone on 2012-04-10
> **Eirreann said:**
> Okay, I'm running a DELL Inspiron 8600 with these specs:
Intel Pentium M 1.50GHz processor
2GB of DDR 333MHz RAM
Nvidia GeForce FX Go5200 video card
and a 55GB hard drive...
 
Really the only limiting thing, I think, in my setup is possibly my video card.  However, when I'm running XP (I've got Ubuntu set up as a dual-boot) the web browsers run fine!  Is it possible that Ubuntu isn't using all of my RAM?  And would running Ubuntu 2D help?
Sorry it took so long to reply!

its not your processor because i believe it is faster than pentium 4. it your ram that sucks. Do not use chromium it is ram heavy. 

Please use an updated verion of midori or another light brower. Your experience will be better. Basically, any browser that uses less ram,
```
   sudo add-apt-repository ppa:midori
sudo add-apt-repository ppa:webkit-team
sudo apt-get update
sudo apt-get install midori
```

---

### Post by Eirreann on 2012-04-10
> **idoitprone said:**
> its not your processor because i believe it is faster than pentium 4. it your ram that sucks. Do not use chromium it is ram heavy. 

Please use an updated verion of midori or another light brower. Your experience will be better. Basically, any browser that uses less ram,
```
   sudo add-apt-repository ppa:midori
sudo add-apt-repository ppa:webkit-team
sudo apt-get update
sudo apt-get install midori
```

2GB of RAM isn't enough?  Or is it the frequency (which I can understand... 333MHz is pretty cruddy compared to today's standards...)
So would it help if I used Xubuntu instead?

---

### Post by idoitprone on 2012-04-10
> **Eirreann said:**
> 2GB of RAM isn't enough?  Or is it the frequency (which I can understand... 333MHz is pretty cruddy compared to today's standards...)
So would it help if I used Xubuntu instead?

2gb is enough ram, but i wonder how fast is your ram
Is your ram ddr1 or ddr2

I dont see the 333Mhz in the wiki standard

If it is ddr-333, then it is 2 time slower than my 1005ha atom 280 netbook.

Trust me, you feel the pain whenever the browers manage ram such in your case.

Xubuntu will not change much. It may help it boot faster. Programs that are not in use just stay in ram, it will not et away your resources, however your browser must allocate and mange ram, so using a lighter browser will make a difference

---

### Post by Eirreann on 2012-04-10
> **idoitprone said:**
> 2gb is enough ram, but i wonder how fast is your ram
Is your ram ddr1 or ddr2

I dont see the 333Mhz in the wiki standard

If it is ddr-333, then it is 2 time slower than my 1005ha atom 280 netbook.

Trust me, you feel the pain whenever the browers manage ram such in your case.

Xubuntu will not change much. It may help it boot faster. Programs that are not in use just stay in ram, it will not et away your resources, however your browser must allocate and mange ram, so using a lighter browser will make a difference

It's just DDR (or at least that's what Dell's website said when I ordered sticks to upgrade it from 512MB to 2GB...), no numbers.
Now I'm not sure that it is RAM, after all, because I have just finished installing Ubuntu from a live disk and now none of the browsers (not even Chromium) have any lag when scrolling or dragging around the windows!  I'm going to guess that the real problem was something to do with Wubi, rather, because now everything is working great!  (Not to mention, when using Chrome via Windows XP this computer never had any issues with lag at all)

P.S. I installed Midori and I like it!  It's a good browser!

---

