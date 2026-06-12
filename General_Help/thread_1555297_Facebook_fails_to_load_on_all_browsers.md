---
title: "Facebook fails to load on all browsers"
date: 2010-08-17
forum: General Help
---

### Post by hapkidoman on 2010-08-17
Hi everyone!

Just installed Ubuntu 10.4 and almost all websites load properly except Facebook.  The problem is persistent with all browsers: opera, firefox, chrome.  If i use the same programs with Windows 7, Facebook loads properly.

Basically, the log in page comes up....howerver, once I sign on only the very top blue bar loads.  Youtube works perfectly - I have flash installed correctly.  I've never had this problem on Ubuntu before.

Thinking there was something wrong with Ubuntu 10.4 I installed 10.10.  The problem still persists.  Also, I can not load facebook with jolicloud.  I have an Asus 64 bit laptop.

Anyone have any suggestions?

Thanks in advance!

---

### Post by hapkidoman on 2010-08-17
I'm not sure what information you'll need from me so just ask : )

---

### Post by ercferret18 on 2010-08-17
Can you attach a screenshot?

---

### Post by hapkidoman on 2010-08-17
Here you go!

---

### Post by Mr_VeRiTy on 2010-08-17
Try clearing your firefox (and chrome and opera) cookies and cache (from the clear private data option in the tools menu), my laptop sometimes wont load pages till i have.

---

### Post by hapkidoman on 2010-08-17
No dice.  It still doesn't work : (

---

### Post by ercferret18 on 2010-08-17
Do you have javascript enabled?

---

### Post by Mr_VeRiTy on 2010-08-17
It might just be a facebook bug, try again in the morning if you don't find a solution on ubuntu forums.

---

### Post by hapkidoman on 2010-08-18
Thanks for the help everyone (and sorry for the late reply).  I installed Javascript on firefox but it still doesn't work.  I doubt it's a bug in Firefox cause I've tried several versions - none of which work (and Facebook hasn't been able to load since I've installed Ubuntu though it loads fine with a desktop I have that runs Ubuntu 9.10).  

Apparently I'm the only one with the problem since there doesn't seem to be too many similar cases out there on the forums.

I think at this point I'll just do a complete fresh install of Ubuntu 10.04.  Maybe I missed something when I installed from the repositories last time?

Thanks again for everyone's help!

---

### Post by mitb07 on 2010-08-23
hi, did you ever find a fix for this? because i am having the exact same problem and its driving me nuts

---

### Post by hapkidoman on 2010-08-25
I did not find a fix for it :(  

I went ahead and did a fresh install of Ubuntu 10.04 (64bit) and downloaded the ubuntu-restricted-extras and got flash up and working.  I'm able to view flash perfectly fine (youtube, etc) but still no facebook.  I'm curious as to what facebook is using that I can't view (perhaps it has something to do with .php? - I have no idea if that even matters, but its something i noticed that distinguishes it from most other websites I go to).  

Does anyone have any other ideas?  Is it because I have the 64bit version of Ubuntu 10.04?  I'm curious as to why we are having this problem.

---

### Post by julio_cortez on 2010-08-25
> **hapkidoman said:**
> Is it because I have the 64bit version of Ubuntu 10.04?I can say it's not due to the x64 version.
Works fine for me in Ubuntu 10.04 x64 with Firefox, and worked more or less fine in Kubuntu 9.10 and 10.04 x64 with Konqueror (despite it trying to access Facebook Mobile instead of the main page of FB).

I would've suggested you to try FB lite but it looks [like it's too late]("http://news.cnet.com/8301-13577_3-20002954-36.html").

---

### Post by sydbat on 2010-08-25
> **hapkidoman said:**
> I did not find a fix for it :(  

I went ahead and did a fresh install of Ubuntu 10.04 (64bit) and downloaded the ubuntu-restricted-extras and got flash up and working.  I'm able to view flash perfectly fine (youtube, etc) but still no facebook.  I'm curious as to what facebook is using that I can't view (perhaps it has something to do with .php? - I have no idea if that even matters, but its something i noticed that distinguishes it from most other websites I go to).  

Does anyone have any other ideas?  Is it because I have the 64bit version of Ubuntu 10.04?  I'm curious as to why we are having this problem.A very strange problem indeed. I'm on FB right now with no issues (except for the fact that I am on FB in the first place :p). And I am using 10.04 64bit on a couple of boxen.

I wonder if there is some repository you need to activate that has some file/whatever required for FB. 

Have you done Medibuntu?
Universe?
Multiverse?
Backports?

---

### Post by hapkidoman on 2010-08-25
Well that sucks :(  Good to know that its not a 64bit problem though.  I'm curious, is there a program that can track what a website loads and what it gets stuck on?  

When I tried to get on facebook the page just continuously loads - it never stops 'transferring data from facebook'.  I've tried firebug, but couldn't really figure out what i needed to do to actually track where the errors were.

Perhaps if I could do that I could narrow down what is and isn't working.

What version of Java do you have installed?  I'm wondering if that is my problem as well.

---

### Post by hapkidoman on 2010-08-25
> **sydbat said:**
> A very strange problem indeed. I'm on FB right now with no issues (except for the fact that I am on FB in the first place :p). And I am using 10.04 64bit on a couple of boxen.

I wonder if there is some repository you need to activate that has some file/whatever required for FB. 

Have you done Medibuntu?
Universe?
Multiverse?
Backports?

Mmmm....well, i know I got Universe as well as multiverse.  Not sure about Medibuntu (now that you mention it - I'll really need to check on that) and I'm not sure what you mean by backports.

Unfortunately, I'm at work right now so I won't be able to test any idea that comes my way (just wanted to get some ideas while at work so as soon as I'm done I can test them out at home).

Could you elaborate on 'backports'?

---

### Post by sydbat on 2010-08-25
> **hapkidoman said:**
> Mmmm....well, i know I got Universe as well as multiverse.  Not sure about Medibuntu (now that you mention it - I'll really need to check on that) and I'm not sure what you mean by backports.

Unfortunately, I'm at work right now so I won't be able to test any idea that comes my way (just wanted to get some ideas while at work so as soon as I'm done I can test them out at home).

Could you elaborate on 'backports'?Backports is in Software Sources under the Updates tab. They are "Unsupported Updates", but can include certain functionality for some applications.

---

### Post by hapkidoman on 2010-08-25
> **sydbat said:**
> Backports is in Software Sources under the Updates tab. They are "Unsupported Updates", but can include certain functionality for some applications.

Awesome!  Thanks for explaining that to me.  I will check that out as soon as I get home.  Hopefully its something as simple as doing that :)

Here's to hoping!

---

### Post by hawkeye2777 on 2010-08-25
Try one of these links:

[http://touch.facebook.com/](http://touch.facebook.com/)
[http://m.facebook.com/](http://m.facebook.com/)

Also, I don't think Facebook uses flash at all (except maybe for some applications or games). Most of the site does need AJAX though... maybe that is part of the problem.

---

### Post by hapkidoman on 2010-08-25
> **hawkeye2777 said:**
> Try one of these links:

[http://touch.facebook.com/](http://touch.facebook.com/)
[http://m.facebook.com/](http://m.facebook.com/)

Also, I don't think Facebook uses flash at all (except maybe for some applications or games). Most of the site does need AJAX though... maybe that is part of the problem.

Thank you for suggesting those as well.  As soon as I get home I will give them a shot and see what's up.  Now, in terms of AJAX....is there something I can download to Ubuntu that would help with that?

---

### Post by hawkeye2777 on 2010-08-25
> **hapkidoman said:**
> Thank you for suggesting those as well.  As soon as I get home I will give them a shot and see what's up.  Now, in terms of AJAX....is there something I can download to Ubuntu that would help with that?

Nope; if it was a problem with AJAX it would probably be either the implementation (in other words, Facebook's problem) or it's a issue with Javascript on your side. I could be wrong too; it might not have anything to do with AJAX.

One other thing: it could be an external script that is failing to load. I've had pages refuse to load because they are waiting on one particular external script.

---

### Post by hapkidoman on 2010-08-25
> **hawkeye2777 said:**
> Try one of these links:

[http://touch.facebook.com/](http://touch.facebook.com/)
[http://m.facebook.com/](http://m.facebook.com/)

Also, I don't think Facebook uses flash at all (except maybe for some applications or games). Most of the site does need AJAX though... maybe that is part of the problem.

I could only load touch.facebook.com/.  It worked - kind of.  The main page never came up but I was able to get my profile to pop up.  The info and friends tab would never load it would just hang.

I've included a pic of the loading bar (all the blue bars) that will 'load' indefinitely but never actually load anything.  Does anyone know what script it might be trying to load?

---

### Post by hapkidoman on 2010-08-26
Last night I installed most of the medibuntu packages and to no avail!  Facebook still won't load properly.  I'm beginning to wonder if it has anything to do with the laptop I'm using it on.  For instance, my parent's desktop had the same version of Ubuntu and is running Facebook flawlessly.

Jolicloud, which I have installed on my laptop - which was based off of Ubuntu 9.04? (not sure which version) also does not load facebook.

I'm beginning to think I should triple boot Windows 7, Ubuntu 10.04, and Fedora 13 to see if it will work on a different OS.

Any thoughts?

---

### Post by drewbub on 2010-08-26
Install the firefox extension Firebug.

Open the firebug panel and enable all tracking (js,etc)  

Recreate the problem and see if firebug shows any errors.

---

### Post by b827530@lhsdv.com on 2010-10-05
Try to switch to Open DNS (set DNS servers to 208.67.222.222,208.67.220.220 in your network settings). I had the same problem and it helped me.

---

### Post by besneatte on 2011-05-26
I am having the same issue. All browsers. However, it is only an issue on certain connections. Perhaps a proxy? I have this issue not only with facebook but also with paypal. It's really weird because if I use a windows computer on this network it works fine ( however some people here are experiencing the issue with Chrome on windows )

Could it perhaps have something to do with security settings?

Tried switching DNS servers to no avail.

---

