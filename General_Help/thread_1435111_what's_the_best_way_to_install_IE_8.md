---
title: "what's the best way to install IE 8 ?"
date: 2010-03-21
forum: General Help
---

### Post by unpresedented on 2010-03-21
I searched a lot on google for installing IE8  ( Microsoft Internet Explorer )  on ubuntu, but every tutorial I read produced errors with various users after I read comments too, my question is : is [this tutorial]("http://zytzagoo.net/blog/2009/03/20/howto-running-ie6-ie7-and-ie8-on-ubuntu-intrepid-810-using-virtualbox/") the best one to install IE8 on ubuntu ?
 
thank you so much in advance ...

---

### Post by Swagman on 2010-03-21
Why in the name of all that's holy would you or anyone else want to install that abomination ?

---

### Post by MelDJ on 2010-03-21
yes. but that means you have to install windows in virtualbox

---

### Post by unpresedented on 2010-03-21
> **Swagman said:**
> Why in the name of all that's holy would you or anyone else want to install that abomination ?
 
I need I.E. 8 to test my web pages on it along with firefox ...
and yes, it sounds that I have to install windows on virtual box ...
 
is there a better lighter method ?

---

### Post by s.fox on 2010-03-21
> **Swagman said:**
> Why in the name of all that's holy would you or anyone else want to install that abomination ?

I run many browsers for testing webpages I have built.  

-Silver Fox

---

### Post by unpresedented on 2010-03-21
> **Silver_fox_ said:**
> I run many browsers for testing webpages I have built. 
 
-Silver Fox
 
Hi Silver,
what's the method you've followed to install I.E. 8 on your ubuntu ?

---

### Post by waynefoutz on 2010-03-21
If you install PlayonLinux, it's in the Ubuntu Software Center in Karmic or later, or you can download it directly from their site, it will install IE7, not IE8,  and put the launcher right on your desktop. It runs pretty slow, but then any windows browser running under WINE usually does. I have it installed on mine, but I can't think of any instance where I've had to use it.

---

### Post by unpresedented on 2010-03-21
> **waynefoutz said:**
> If you install PlayonLinux, it's in the Ubuntu Software Center in Karmic or later, or you can download it directly from their site, it will install IE7, not IE8, and put the launcher right on your desktop. It runs pretty slow, but then any windows browser running under WINE usually does. I have it installed on mine, but I can't think of any instance where I've had to use it.
 
so basically, you advise me to use wine as the simplest WORKING method to install internet explorer 8 (i don't want version 7) ?

---

### Post by unpresedented on 2010-03-21
any ideas regarding this issue would be highly appreciated !

---

### Post by mike555 on 2010-03-21
I have seen websites that let you test different browsers (on their website) just Google and you should find one.........

 for instance;
[http://ipinfo.info/netrenderer/index.php](http://ipinfo.info/netrenderer/index.php)

---

### Post by zaphod777 on 2010-03-21
> **unpresedented said:**
> any ideas regarding this issue would be highly appreciated !

I think you have only 2 choices run it in a VM (I like virtualbox)or run it in Wine here  is a link to run it wine.
[http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html](http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html)

personally I just run a VM for that rare occasion wen I need IE ushually just around tax time. I would rather not clutter up my system with all of the wine stuff but I might need to when portal2 comes out.

---

### Post by s.fox on 2010-03-21
> **zaphod777 said:**
> I think you have only 2 choices run it in a VM (I like virtualbox)or run it in Wine here  is a link to run it wine.
[http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html](http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html)

personally I just run a VM for that rare occasion wen I need IE ushually just around tax time. I would rather not clutter up my system with all of the wine stuff but I might need to when portal2 comes out.

Hello, 

I agree.  I had it running in WINE for a shortwhile but just found it too buggy.  I run it in a VM when needed.

-Silver Fox

---

### Post by unpresedented on 2010-03-22
too buggy ???
mmmmm ... I need to use it frequently ... running VM on a laptop would kill the RAM

---

### Post by unpresedented on 2010-03-22
> **zaphod777 said:**
> I think you have only 2 choices run it in a VM (I like virtualbox)or run it in Wine here  is a link to run it wine.
[http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html](http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html)

personally I just run a VM for that rare occasion wen I need IE ushually just around tax time. I would rather not clutter up my system with all of the wine stuff but I might need to when portal2 comes out.

thank you Zaphod for this cool tutorial ..
however, because i'm new to ubuntu, i didn't understand this phrase : 
**DLL Overrides can be set in winecfg, just run winecfg from your favorite terminal and then go to Libraries and set the above DLL's as shown above**.

what's the command that I should type in terminal to set those dll overrides, and is there another way to set those overrides other than terminal ?
and should I press on Add Application button before all of the steps in this tutorial or not ?
thanks so much in advance.

---

### Post by Mark Phelps on 2010-03-22
> **unpresedented said:**
> too buggy ???
mmmmm ... I need to use it frequently ... running VM on a laptop would kill the RAM

There are some things that Wine simply will not run well.  IE is one of them.

Look at the following WineHQ page for IE:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=25")

Of the versions of IE8, two are rated Garbages (meaning, they will NOT run, regardless of what you do), and the third is Bronze -- one step up from Garbage.  Also, the only version that WILL run is for XP -- and I would wager that MOST IE8 users are running Vista or Win7.

So, you won't even be able to install a version of IE8 that represents the environment you want to test!

If you're not willing to use a VM of some sort, you've run out of options.

---

