---
title: "what to use for Facebook Apps"
date: 2010-02-14
forum: General Help
---

### Post by demon148 on 2010-02-14
my gf has Ubuntu 9.10 instaled on her PC and she uses a lot of facebook apps, and no matter what she does the apps run slow, really slow, I have tried to install Google Chrome as that was supposed to be the best, but it runs very slow on there aswell, as for Mozilla it doesnt work on there even after a flash update. Although Facebook itself runs fine this doesnt so any help will be appreciated.

---

### Post by Swagman on 2010-02-14
I think it's more about your internet connection and graphics card.

I'm on an 8mb DSL connection (BT internet) using a nVidia GTX8800

I have no probs with Facebook apps

[**Screengrab**](http://www.upload3r.com/serve/130210/1266102384.jpeg) <--- Clicky

---

### Post by demon148 on 2010-02-14
Everything works to fine when using Windows, its only Linux, I am on a 8mb connection. is there anything I need to install other than flash player? is the Firefox browser thats on with Ubuntu 9.10 able to run the apps?

---

### Post by Swagman on 2010-02-14
My screengrab **IS** Firefox running Facebook apps.

I'm using the 32bit version of Ubuntu 9:10. Firefox version 3.5.7

You could try installing epiphany as that works ok with facebook as well ...and it's VERY fast. Just takes a bit of getting used to.

---

### Post by demon148 on 2010-02-14
so would I need to install flash? what about Java?

---

### Post by Swagman on 2010-02-14
open a terminal ( Applications-Accessories-Terminal) and copy & paste this into it

```
 sudo apt-get install ubuntu-restricted-extras
```

That will install various jubblies to make your ubuntu experience all the better.

---

### Post by sophicsage on 2010-02-14
> **demon148 said:**
> my gf has Ubuntu 9.10 instaled on her PC and she uses a lot of facebook apps, and no matter what she does the apps run slow, really slow, I have tried to install Google Chrome as that was supposed to be the best, but it runs very slow on there aswell, as for Mozilla it doesnt work on there even after a flash update. Although Facebook itself runs fine this doesnt so any help will be appreciated.


[COLOR=Navy][B]It sounds to me like you have maybe two minor issues.  I'm an Ubuntu newb...I've only had it since November.  I had the exact same flash issues.  I would suggest removing and reinstalling the non-free flash package via the Ubuntu Software Center.  That should help your Mozilla compatibility. 

Instead of updating...remove and reinstall the non-free flash package.  As to the speed of Chrome, I wouldn't even use that, personally.  Firefox has worked great since I got my non-free flash package installed correctly.

I also think you might have bandwidth / router issues, but only as it relates to Chrome, which as I stated I don't suggest at all.  

Is her PC on wired or wireless internet?  What kind of computer is it?   

I'm sure it's a simple issue for you....sounds to me like some simple settings need to be adjusted.  Once you get that little issue fixed like I did, your system will move FAST, trust me.
[/B][/COLOR]

---

### Post by demon148 on 2010-02-14
well let me try and what u suggested about the flash and I will get back to you

---

### Post by sophicsage on 2010-02-14
> **demon148 said:**
> so would I need to install flash? what about Java?



[COLOR=Navy][B]Very simple.  Go to the Ubuntu Software Center.  Type in Java in the search field.  You will see the search begin.  Select Ubuntu Restricted Extras.  It will install automatically when you click install.  This takes care of Java and some other codecs in Firefox.  If it's already installed, remove it and reinstall it.  I am betting this will work for you.

I know this is a headache.  You will be able to solve this.  You will get lots of support on here from people more qualified than me to answer...they sure helped me.
[/B][/COLOR]

---

### Post by demon148 on 2010-02-14
one thing, I am trying to find flash under the software center all I can find is flash block, but not options to install it.

---

### Post by demon148 on 2010-02-14
its saying not available in current data

---

### Post by sophicsage on 2010-02-14
> **demon148 said:**
> one thing, I am trying to find flash under the software center all I can find is flash block, but not options to install it.


[COLOR=Navy][B]Go to the Ubuntu Software Center, type in Java, it should be right there....ubuntu restricted extras.  You double click it and there should be an option to install on the screen.  It should install automatically.

Be patient if this doesn't work.  More people are going to log on today and will see your issue and some people are very technically competent and will know what to do.
[/B][/COLOR]

---

### Post by sophicsage on 2010-02-14
> **demon148 said:**
> its saying not available in current data


[COLOR=Navy]**OK, you need to update your ubuntu package list, in my opinion.  I don't know how to do that.  Can someone guide him to updating his package manager?**[/COLOR]

---

### Post by demon148 on 2010-02-14
doesnt matter got it done, the apps still run a little slow, there was no flash player in the software center

---

### Post by sophicsage on 2010-02-14
> **demon148 said:**
> doesnt matter got it done, the apps still run a little slow, there was no flash player in the software center

[COLOR=Navy][B]Yea, it's not a flash player.  It's just the codecs.  

So it's working now?  Good.  But slow, so it sounds like your last issue is your connectivity.  Since it's a common issue now between Chrome and Firefox, I think it's bandwidth.  What kind of computer is it and what type of service and router are you using?  Wireless or wired?

I think you would be having the speed issues even if you were running Windows.  Could be your ISP, your ethernet cable, your router, etc....don't worry it will work.
[/B][/COLOR]

---

### Post by demon148 on 2010-02-14
the computer is an old one, using a 1.7ghz Processor and 512mb ram the computer is connected to a netgear router and my ISP is through the Post Office its a 8mb service.

This Problem was not present under Windows

---

