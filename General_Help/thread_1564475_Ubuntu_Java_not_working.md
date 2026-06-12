---
title: "Ubuntu Java not working"
date: 2010-08-30
forum: General Help
---

### Post by Jerriy on 2010-08-30
Here is an example: I go to [usopen.org]("http://usopen.org") click the menu option "fanzone" and three pictured links appear: 

1) Next contenders
2) Facebook
3) Twitter

The first option is working. And it apparently is a 'normal' html link.

The two other options on the other hand, are not working. I click on them but nothing happenes.

Both those facebook and Twitter links are java (I can see that by hovering on them and reading the status bar.

I have java installed (or so I thought) but there seem to be indications that my java is in some kind of a mess. The test page ([http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)) also acts funny
.

---

### Post by Jerriy on 2010-08-30
Oh and my quetion is: what is wrong with my Java and how can it be fixed ASAP?

Thank you in advance.

---

### Post by gandaran on 2010-08-30
that doesn't look like java, more like a flash problem! can you post the link?

---

### Post by Jerriy on 2010-08-30
Here is evidence that I have (what appears to be) Java installed:
.

---

### Post by Jerriy on 2010-08-30
> **gandaran said:**
> that doesn't look like java, more like a flash problem! can you post the link?I already did (usopen.org) 

I also found a third unclickable link elsewhere on the menu of the same site

Here's a copypaste of the three links:

```
javascript:openExternal('http://www.facebook.com/usopentennis',true);

javascript:openExternal('http://twitter.com/USOpen',true);

javascript:openExternal('http://seatviewer.usopen.org/?promo=PhotoInNav',true);
```

---

### Post by TheCosmicFrog on 2010-08-30
That's JavaScript, which is completely separate to Sun Java.

Yes, Sun.

---

### Post by spjackson on 2010-08-30
> **Jerriy said:**
> 
```
javascript:openExternal('http://www.facebook.com/usopentennis',true);

javascript:openExternal('http://twitter.com/USOpen',true);

javascript:openExternal('http://seatviewer.usopen.org/?promo=PhotoInNav',true);
```
Those 3 links are Javascript, nothing whatsoever to do with Java.

All 3 work for me in Firefox on Lucid.

---

### Post by Jerriy on 2010-08-30
> **TheCosmicFrog said:**
> That's JavaScript, which is completely separate to Sun Java.

Yes, Sun.I'm sure you're right.

But my knowledge goes only as far as knowing that both of those are completely different from yet another Java (Java, Indonesia)

---

### Post by Jerriy on 2010-08-30
> **spjackson said:**
> Those 3 links are Javascript, nothing whatsoever to do with Java.

All 3 work for me in Firefox on Lucid.OK then there is something wrong with my javascript (I've wondered if it was perhaps being blocked by something and checked my Firefox but I see that the "enable javascript" box in "preferences" is definitely ticked

---

### Post by Jerriy on 2010-09-05
Why am I not getting any help from Ubuntu?

I patiently wait for 5 days but no response to my request :(

I clearly have a problem with java(script)

---

### Post by Jerriy on 2010-09-05
Here is another website for which Ubuntu is completely uselss:

[http://twitterfall.com](http://twitterfall.com)

 I have windows so I can access the page and know that the website is working but in Ubuntu none of the buttons on the left and right are clickable and the website is permanently hang/stuck in this "loading" mode:
.

---

### Post by DandyDon on 2010-09-05
I installed Ubuntu 10.04 LTS yesterday, and both your websites load just fine for me. Two questions, have you run Update Manager, and have you tried Recovery Mode?.

---

### Post by Kenda on 2010-09-05
> **Jerriy said:**
> Here is another website for which Ubuntu is completely uselss:

[http://twitterfall.com](http://twitterfall.com)

 I have windows so I can access the page and know that the website is working but in Ubuntu none of the buttons on the left and right are clickable and the website is permanently hang/stuck in this "loading" mode:
.

Works fine for me on Lucid 64 bit.

---

### Post by lykeion on 2010-09-05
First of all Javascript has nothing to do with Java, so you shouldn't try to solve this by installing various flavors of Java.
Running in Recovery mode wouldn't help you either.
This is a browser-related problem.

I will give you some troubleshooting help.
You have a problem with opening Javascript links like this one:
```
javascript:openExternal('http://www.facebook.com/usopentennis',true);
```

You say you click them and nothing happens, although you've made sure Javascript is enabled.

Are you using Firefox or any other browser?
What version of Firefox are you running?
Do you use any script-blocking extensions like NoScript?
Do you use a proxy or a firewall?

You can view any Javascript errors in the Error Console.
Load the usopen page in Firefox
Tools > Error Console
Click Clear
Try the Fanzone > Facebook link
Do you see any errors?

Also see this:
[https://developer.mozilla.org/en/error_console](https://developer.mozilla.org/en/error_console)

---

### Post by Jerriy on 2010-09-05
> **lykeion said:**
> First of all Javascript has nothing to do with Java, so you shouldn't try to solve this by installing various flavors of Java.
Running in Recovery mode wouldn't help you either.
This is a browser-related problem.

I will give you some troubleshooting help.
You have a problem with opening Javascript links like this one:
```
javascript:openExternal('http://www.facebook.com/usopentennis',true);
```

You say you click them and nothing happens, although you've made sure Javascript is enabled.

Are you using Firefox or any other browser?
What version of Firefox are you running?
Do you use any script-blocking extensions like NoScript?
Do you use a proxy or a firewall?

You can view any Javascript errors in the Error Console.
Load the usopen page in Firefox
Tools > Error Console
Click Clear
Try the Fanzone > Facebook link
Do you see any errors?

Also see this:
[https://developer.mozilla.org/en/error_console](https://developer.mozilla.org/en/error_console)Yes I have noscript, is that what's causing something? I do get Error-Console messages when I click the two sites I mentioned (the usopen site menu link:```
Error: uncaught exception: [Exception... "Security error"  code: "1000" nsresult: "0x805303e8 (NS_ERROR_DOM_SECURITY_ERR)"  location: "http://www.usopen.org/s_code.js Line: 443"]
```And the twitterfall site:```
Warning: Unknown property 'border-top-right-radius'.  Declaration dropped.
Source File: http://twitterfall.com/core.css
Line: 37
```

---

### Post by Pascal-7 on 2010-09-05
Yep, it's totally browser related. If you have something that prevents your browser from running js, then it won't run.
You should get rid of the noscript extension, and allow java script to run.

---

### Post by Jerriy on 2010-09-05
> **Pascal-7 said:**
> Yep, it's totally browser related. If you have something that prevents your browser from running js, then it won't run.
You should get rid of the noscript extension, and allow java script to run.I've disabled Noscript in Firefox but no change in my problems

---

### Post by lykeion on 2010-09-05
You shouldn't need to get rid of NoScript.
I use it and can browse sites like usopen.org without any problems.
All you have to remember is to right-click NoScript and select "Allow all this page"

Also you should read on how to use NoScript on their homepage: [http://noscript.net](http://noscript.net)

EDIT:
Saw that you've already tried disabling NoScript.

Do you have any other extensions active?
Do you use a proxy like Privoxy?

---

### Post by Jerriy on 2010-09-05
Thank you
Thank you
Thank you all

It was indeed caused by one of the security extensions (or rather addons) that I have (but not noscrpt or any of the ones mentioned) i was able to pinpoint the culprit by disabling my long list of extensions/addons (disabling one at a time)

Problem solved/end of thread
bye!

---

### Post by waltclay on 2010-10-18
I just disabled the suspected add-ons in firefox and then enabled them one-by-one. The problem was adblock plus.

---

