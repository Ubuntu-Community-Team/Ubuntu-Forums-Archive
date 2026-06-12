---
title: "More Limitations with FireFox 3.0 in Ubuntu 9.10"
date: 2009-11-09
forum: General Help
---

### Post by oldefoxx on 2009-11-09
With Windows, you get a web browser not to like called Internet Explorer.  You get up to IE6 S1, which works, but they keep pushing you to move up to IE7 or even IE8.  But there are reasonable alternatives that can be downloaded and used instead.  With Ubuntu, you get just one web browser, which is FireFox.  While top rated with the Windows crowd, there are subtle differences in the Linux world version that can hinder sometimes.

I ran into a new one today with Ubuntu 9.10.  That is, that though FireFox will try to lauch twice when you double click the icon on the top toolbar, then second click will only bring a warning that FireFox has already been launched.  But that same message will come again and again if you try to launch a second instance of FireFox when one is already running.  Now this is different than Windows, where you can have multiple instances of FireFox or any other web browser running at the same time.

Now here is where the behavior of Ubuntu 9.10 throws me.  Without any instance of FireFox running, a single click on the icon gets me the warning message, and FireFox does not launch.  There is no visible evidence that FireFox is in fact running, though there are likely some ways to see if it is doing so in the background.  But if you cannot launch FireFox for real, how do you get on the Internet?  A reboot can be a real help, because this is not the normal behavior of FireFox under Ubuntu.  Not sure how it came abut, but it can mean that you are stuck.

There is something that can be done about it though.  For instance, the Ubuntu Software Center under Applications has its own way of getting to the Internet, and you can look under the Internet group for a different web browser to add to your system.  The one I found and installed was seamonkey navigator.  You get the 1.1 verson, and the seamonkey web site says you can download the 2.0 version to replace it, which I did.

Another good web browser that is available for both Windows and Linux is named Opera, but when I tried to do a  sudo apt-get install opera, it failed because oopera had a dependency on a file that was rejected.  No idea why it was refused, but with computers, you are often left in the dark on questins like that.

The thing is, it can be handy to have more than one web browser to call upon if you need to get to the Internet.  If can spare you a reboot and mere hope that the condition will have cleared when you get back up.

Too bad you can't just have multiple instances of FireFox up and running. That is an advantage that the Windows' version enjoys.

---

### Post by alphacrucis2 on 2009-11-09
> **oldefoxx said:**
> With Windows, you get a web browser not to like called Internet Explorer.  You get up to IE6 S1, which works, but they keep pushing you to move up to IE7 or even IE8.  But there are reasonable alternatives that can be downloaded and used instead.  With Ubuntu, you get just one web browser, which is FireFox.  While top rated with the Windows crowd, there are subtle differences in the Linux world version that can hinder sometimes.

I ran into a new one today with Ubuntu 9.10.  That is, that though FireFox will try to lauch twice when you double click the icon on the top toolbar, then second click will only bring a warning that FireFox has already been launched.  But that same message will come again and again if you try to launch a second instance of FireFox when one is already running.  Now this is different than Windows, where you can have multiple instances of FireFox or any other web browser running at the same time.

Now here is where the behavior of Ubuntu 9.10 throws me.  Without any instance of FireFox running, a single click on the icon gets me the warning message, and FireFox does not launch.  There is no visible evidence that FireFox is in fact running, though there are likely some ways to see if it is doing so in the background.  But if you cannot launch FireFox for real, how do you get on the Internet?  A reboot can be a real help, because this is not the normal behavior of FireFox under Ubuntu.  Not sure how it came abut, but it can mean that you are stuck.

There is something that can be done about it though.  For instance, the Ubuntu Software Center under Applications has its own way of getting to the Internet, and you can look under the Internet group for a different web browser to add to your system.  The one I found and installed was seamonkey navigator.  You get the 1.1 verson, and the seamonkey web site says you can download the 2.0 version to replace it, which I did.

Another good web browser that is available for both Windows and Linux is named Opera, but when I tried to do a  sudo apt-get install opera, it failed because oopera had a dependency on a file that was rejected.  No idea why it was refused, but with computers, you are often left in the dark on questins like that.

The thing is, it can be handy to have more than one web browser to call upon if you need to get to the Internet.  If can spare you a reboot and mere hope that the condition will have cleared when you get back up.

Too bad you can't just have multiple instances of FireFox up and running. That is an advantage that the Windows' version enjoys.

You can have multiple instances of Firefox. I had both 3.0 and 3.5 running when I was on Jaunty. When you install 3.5 it shows up as Shiretoko. Other browser options are Konquerer, and google chrome.

Edit. I misunderstood you multiple instance question. I run multiple instances of FF all the time. Each time I click on the FF panel icon it opens another instance so I don't know why you are having that problem.

---

### Post by rygar on 2009-11-09
i'm not sure why you are having problems, but i can run many instances of firefox on my computer (ubuntu 9.10)

if you think there may be an instance of firefox running in the background that prevents you from starting firefox, type 

```
ps x | grep firefox
```

in a terminal winndow, you get something like this:

```
jeff@jeff-laptop:~$ ps x | grep firefox
17999 ?        Sl     0:01 /usr/lib/firefox-3.5.4/firefox
18052 pts/0    R+     0:00 grep firefox

```

now you can kill that instance of firefox by doing this

```
kill -9 17999
```

where 17999 is the process id of firefox found from the previous step.

---

### Post by howefield on 2009-11-09
> **oldefoxx said:**
> Too bad you can't just have multiple instances of FireFox up and running. That is an advantage that the Windows' version enjoys.

You reckon ? 

I reckon it is more to do with a lack of knowledge on your part. Firefox can open multiple windows easily on Ubuntu.

What does ctrl + N do when you have Firefox running ?

---

### Post by winotree on 2009-11-09
Does this [or will this] [http://support.mozilla.com/en-US/kb/Firefox+is+already+running+but+is+not+responding?s=firefox%20already%20running](http://support.mozilla.com/en-US/kb/Firefox+is+already+running+but+is+not+responding?s=firefox%20already%20running) solve your Firefox problem?

---

### Post by oldefoxx on 2009-11-09
Hmmm.  The problem with 9.10 and FireFox is worse than I thoght.  I've tried five times to uninstall FireFox, even doing restarts before trying to get it installed ang going again, and each time I just get the message that it is already running.  Fact is, I even found that Ubuntu Software Center shows a FireFox Launcher, and instance of just FireFox, and another of FireFox 3.0.  I've tried each way to install FireFox, and on uninstalls, even went into Synaptic Package Manager and did an uninstall that way. 

Interesting thing is that the single instance problem of FireFox was first found with Ubuntu 7.10, and seems to reoccur with each one since.  I just took it for granted that was an aspect of the Linux version of FireFox.  Your apparent freedom from this and remarks to the effect that somehow I'm creating my own havoc here or misreading things seems so out of touch with what I am dealing with that I won't comment on those remarks any further.  However, I will take a shot at trying to see if there is a locked thread and try to kill it as suggested.  But it is all very strange and unsettling anyway.  I want an OS that works with me, not crosses me at every turn.

---

### Post by oldefoxx on 2009-11-09
Okay I tried the px method, but found no instance of FireFox running.  It only showed up the the grep instruction.  Then I followed the link suggestion, which wanted me to check several things related to FireFox.
These proved negative as well, but one took me to .mozilla/firefox, which should not even have been there since I had uninstalled FireFox.

So I just moved .mozilla to the trach, then used Synaptic Package Manager to reinstall FireFox, and now it starts up.  So I right-clicked the FireFox Icon and added back to the panel where it had been before.

Just to be sure of things, I tried clicking on the FireFox icon several times, slowly, and each time another instance of FireFox opened up.  Never had that experience under Ubuntu before, and it can be very handy.

Oh, incidently, just as a reward to anyone keeping up with this talking on my part, three of my favorite online shopping sites are [www.eBay.com](www.eBay.com), [www.TigerDirect.com](www.TigerDirect.com), and [www.geeks.com](www.geeks.com).  The computer stuff being sold cheaply and shipped from Hong Kong or China in general has really improved in quality in the last few years, and on eBay you can find some excellent prices and low shipping rates if it comes from there.  TigerDirect has been pretty good as well, especially for specials, but sometimes you have to fight the rebate war if you end up going that way.

Geeks has been really great lately, coming through with unbelievable deals on refurbished thiings like notebooks, desktops, even hard drives, and I ended up ordering two 17" Toshiba notebooks with extras, a flat price, no taxes and no S/H.  Think of a 17" name brand notebook for just $389.99 flat.  Or a 500 GB SATA hard drive for just $37.50, plus shipping.  This is a great time for deals as the economy is down and slow, and retailers are trying to move stock one way or another.

Not twisting anyone's arm, but after telling some family and friends about my great deal, I just wanted to share the opportunity with others while it still lasts.  Assuming it does.  Even Christmas shoppers are getting super deals early this year, something that likely won't be there in future years if jobs begin to come back.

---

### Post by winotree on 2009-11-09
> ....but one took me to .mozilla/firefox, which should not even have been there since I had uninstalled FireFox...Ah -- seems I'm as guilty as anyone in assuming you'd know that removing Firefox does not remove its configuration files, which you've found in /home/user/.mozilla/firefox    

The /random.default is the actual file -- the profile -- where you'd make any changes in the future.  Hope things are a bit easier for you now.

---

