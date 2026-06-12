---
title: "Help! Think I have Virus and/or Spyware!"
date: 2009-08-19
forum: General Help
---

### Post by Kangaroo_Style on 2009-08-19
I know you're not supposed to be able to get a Virus or Spyware for Ubuntu; but I believe that I have one or the other. Here is what is happening:

1. When I click on a link, it takes forever for it to load. I sometimes have to click on it 2 or 3 times for it load up. This used to never happen before.

2. Occasionally, my browser will just take me a random website. Bookmarks.com being the most recent, when I just trying to browse the Ubuntu forum. 

3. Sometimes I will be browsing, and my browser will try and open up a new page. Today it went cannot connect to [www.-.com](www.-.com)

What gives? Anything I can do? Everything has been updated. This has been really frustrating, I appreciate any help!

---

### Post by admiralspark on 2009-08-19
First, lets get the usual questions out of the way:
1) What version of Ubuntu?
2) what's your computer setup?
3) did you use any special programs to run/install Ubuntu like Virtual Desktop or Wubi?
4) What sort of internet connection/setup do you have? Wireless/modem/is it secure?
5) Do you use Firestarter? If so, is there an inordinate amount of outgoing traffic? Unless I'm mistaken, programs can still be cracked even if they're on another operating system (like, for example, Microsoft Office on a Mac OSX computer).  Logically Firefox would still be susceptible, even though it is a very secure browser.
6) what programs have recently been installed, and what were you doing when you noticed it the first time?

As many have pointed out on here, it is almost pointless to create a virus for a GNU/Linux computer because of three things: their relatively small marketshare, the low benefit of gaining access to/torturing Linux users, and the fact that people all over the world review the code constantly. I would be willing to step out on a limb and say that it's probably not a virus/spyware infection but more likely something has upset how Firefox runs (e.g. a bad install/update). 

Just my $.02
-Admiralspark

---

### Post by aesis05401 on 2009-08-19
Consider disabling all browser plug-ins/add-ons to see if the behavior persists.

---

### Post by Kangaroo_Style on 2009-08-19
> **admiralspark said:**
> First, lets get the usual questions out of the way:
1) What version of Ubuntu?
2) what's your computer setup?
3) did you use any special programs to run/install Ubuntu like Virtual Desktop or Wubi?
4) What sort of internet connection/setup do you have? Wireless/modem/is it secure?
5) Do you use Firestarter? If so, is there an inordinate amount of outgoing traffic? Unless I'm mistaken, programs can still be cracked even if they're on another operating system (like, for example, Microsoft Office on a Mac OSX computer).  Logically Firefox would still be susceptible, even though it is a very secure browser.
6) what programs have recently been installed, and what were you doing when you noticed it the first time?

As many have pointed out on here, it is almost pointless to create a virus for a GNU/Linux computer because of three things: their relatively small marketshare, the low benefit of gaining access to/torturing Linux users, and the fact that people all over the world review the code constantly. I would be willing to step out on a limb and say that it's probably not a virus/spyware infection but more likely something has upset how Firefox runs (e.g. a bad install/update). 

Just my $.02
-Admiralspark


1. 9.04 Ubuntu 
2. Toshiba Satellite A135, Dual Core 1.73ghz, 1gb ram
3. None, it's the only OS on my system
4. Linksys wireless, it's secured. I hid my SSID as well
5. No I don't, I just have native linux programs installed. No Wine either
6. Most recent would be DeVeDe, and Firefox 3.5 (Shiretoko). Started noticing it after Shiretoko. I also have been downloading a few things off Frostwire, but I wouldn't imagine an accidental .wma file download would do anything to Ubuntu...

Thanks for any help. I appreciate it!

---

### Post by bodhi.zazen on 2009-08-19
Unlikely to be a virus or malware. Probably a java , java script, or flash hack.

Try creating a new (firefox) profile and see : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

I am willing to bet NoScript fixes the problem.

---

### Post by Kangaroo_Style on 2009-08-19
> **bodhi.zazen said:**
> Unlikely to be a virus or malware. Probably a java , java script, or flash hack.

Try creating a new (firefox) profile and see : [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

I am willing to bet NoScript fixes the problem.


Don't know what to call this. This just occurred when browsing this thread. All of a sudden my browser changed to this webpage Echo Online. I didn't click on anything.  Needless to say I do not use Echo, or even know what it is. I have also uninstalled most add-ons for Firefox. Here is a screenshot of the page it directed me to. Hopefully this can help solve the problem.

---

### Post by pqwoerituytrueiwoq on 2009-08-19
likely an ad that changes the page with a frame breaker
noscript - [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

### Post by Kangaroo_Style on 2009-08-19
I just reinstalled noscript. I just get frustrated when I go to a new website and I have to figure out what to allow, wish there was just a universal whitelist that I could download

Edit: Wouldn't let me post/quote to this page unless I did temporary allow all on this page...!!!!

---

### Post by pqwoerituytrueiwoq on 2009-08-19
this site requires yahooapis.com

---

### Post by bodhi.zazen on 2009-08-19
> **Kangaroo_Style said:**
> I just reinstalled noscript. I just get frustrated when I go to a new website and I have to figure out what to allow, wish there was just a universal whitelist that I could download

Edit: Wouldn't let me post/quote to this page unless I did temporary allow all on this page...!!!!

It takes a few minutes. Go to all the pages you visit with any regularity and allow the primary site. Then allow others per session.

You will get the hang of it fast.

---

### Post by lykwydchykyn on 2009-08-19
By any chance... do the sites it's taking you to have anything to do with the contents of your clipboard?

And are you using the touchpad when it happens?

I noticed after putting 9.04 on my laptop, it had the annoying habit of plopping my clipboard contents into the URL bar of Firefox whenever it would hit the upper right corner.  Sounds suspiciously like what's happening to you.

---

### Post by Arand on 2009-08-19
This is by no means something that is just solved with noscript. Possibly the problem might have been evaded in the first place if noscript were used, but it hardly a solution at this stage, when the problem is already present.

By your description it sounds very much like some form of redirect adware, whether it's exploiting java, flash, or some other plugin doesn't really matter, it is still malware.

I feel forced to in this case take the other side and preach precaution, since claiming that cross-platform malware is no concern of ubuntu seems a very questionable point to maintain.

And in extreme precaution, I myself would immediately backup all necessary data and reinstall ubuntu, and then make sure to scan the data for malware before bringing it back.
(This may very well be overly precautious, but it will most definitely take care of the problem)
__________

If you do want to poke into and find the cause (at a risk, though probably rather small): 

You might try looking around for antivirus software for ubuntu, and see if possibly that might give any indications.

Also:
Provided the problem is contained to your firefox profile:
Try creating a new profile by using the command "firefox -P" (without quotes) in a terminal (Applications>Acessories>Terminal)

Provided the problem is contained to firefox:
You could test out another browser (e.g. epiphany-browser) and see if the same issues occur there.

If the problem is more global than that the issue should disappear if using a liveCD.

There might even be the chance that something outside the computer, your router, or even your ISP might hold the root of the problem. And if you do see a similar behaviour when booting a LiveCD, that would probably be the case (In those cases I guess replace/reset/update the router, or replace/contact/sue your ISP, would be appropriate steps).

- Arand

---

### Post by Compintuit on 2009-08-20
> **lykwydchykyn said:**
> By any chance... do the sites it's taking you to have anything to do with the contents of your clipboard?

And are you using the touchpad when it happens?

I noticed after putting 9.04 on my laptop, it had the annoying habit of plopping my clipboard contents into the URL bar of Firefox whenever it would hit the upper right corner.  Sounds suspiciously like what's happening to you.

Yeah, I have the same issue. But worse yet, you don't even have to copy the text. The problem is that a middle click pastes in linux, the upper right corner of a touchpad simulates a middle click, and if text is selected that will be pasted instead. Note that also hitting both touchpad buttons is a middle click. If you middle click in firefox, the text in the clipboard is taken to be an address. So it's OK - I'd bet one heck of a lot of money that is your only problem. But I wish the devs had said anything about this. There is no config I can find, but mapping touchpad corners to actions is highly useful and productive. Say, no one knows how to do this, do they?

---

