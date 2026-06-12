---
title: "Please help me fix a weird java bug in chrome."
date: 2011-05-25
forum: General Help
---

### Post by jlp1528 on 2011-05-25
Hello. I'm new to these forums... I'm not sure where to put this... Maybe I'm already in the right place... Anyway, I am going to do a science project on a comparison of internet browsers on Windows 7 and Ubuntu, but I've sort of hit a road block with one of the first tests. You see, I want to find out if the browser you use has an effect on your internet speed and quality, so I want to use speedtest.net and pingtest.net to figure that out. But when I try to use pingtest.net on Google Chrome (not Chromium but I think the same thing would happen), the packet loss test doesn't work. I can do it on Firefox and Opera, but not Google Chrome. The test uses Java, so I have installed Sun Java (and removed anything icedtea or openjdk), but thought maybe Google Chrome wasn't recognizing it correctly.  But here's the kicker: as far as I can tell, anything else I try to do with Java in Google Chrome works. (I can play [www.flyordie.com](www.flyordie.com) games.) I've checked permissions for plugins to run so that's not the problem. I've tried everything I can think of and no dice. Can anyone help me out? Actually I don't think I've tried updating Java to 6 update 25 from 6 update 24, but that seems like it would be a tedious and maybe even risky process. I guess I could try it while I'm waiting for an answer... Other than that though I just don't know what to do here. Any ideas?

---

### Post by LordNeo on 2011-05-25
Try to run Google Chrome as root from console and see if that helps.
If not, you will at least get some kind of error or something.

---

### Post by jlp1528 on 2011-05-25
Got the following error:

Google Chrome can not be run as root.
Please start Google Chrome as a normal user. If you have previously run Google Chrome as root, you will need to change the ownership of your profile directory.

Okay, so how do I fix this? And how is running Chrome as root supposed to help exactly?

---

### Post by wildmanne39 on 2011-05-25
> **jlp1528 said:**
> Hello. I'm new to these forums... I'm not sure where to put this... Maybe I'm already in the right place... Anyway, I am going to do a science project on a comparison of internet browsers on Windows 7 and Ubuntu, but I've sort of hit a road block with one of the first tests. You see, I want to find out if the browser you use has an effect on your internet speed and quality, so I want to use speedtest.net and pingtest.net to figure that out. But when I try to use pingtest.net on Google Chrome (not Chromium but I think the same thing would happen), the packet loss test doesn't work. I can do it on Firefox and Opera, but not Google Chrome. The test uses Java, so I have installed Sun Java (and removed anything icedtea or openjdk), but thought maybe Google Chrome wasn't recognizing it correctly.  But here's the kicker: as far as I can tell, anything else I try to do with Java in Google Chrome works. (I can play [www.flyordie.com](www.flyordie.com) games.) I've checked permissions for plugins to run so that's not the problem. I've tried everything I can think of and no dice. Can anyone help me out? Actually I don't think I've tried updating Java to 6 update 25 from 6 update 24, but that seems like it would be a tedious and maybe even risky process. I guess I could try it while I'm waiting for an answer... Other than that though I just don't know what to do here. Any ideas?Hi,  I read on another forum that some forms of java do not work with all sites. Also you start removing java from the system and you will make it where firefox will not work when java is required. My understanding is that chrome comes with its own java and that if you want to reinstall it you reinstall chrome.
If you totally mess java up you can run this command to get rid of it completely so you can do a fresh install.
```
sudo apt-get --purge remove package name
```I do not think that will apply to java in chrome.

---

### Post by jlp1528 on 2011-05-26
Google Chrome has built in Flash but not Java. And as far as I can tell it's pulling Firefox's Java configuration, which, as I said, is obviously fine, even for the specific site. That is why this is so weird. And as I said, I just removed any openjdk and icedtea packages completely, not all Java, and I am still fine. Except for one site in one browser that happens to be the only one I really need Java for. Why!? So, any more suggestions? Anyone?

---

### Post by infallible on 2011-05-26
> **LordNeo said:**
> Try to run Google Chrome as root from console and see if that helps.
If not, you will at least get some kind of error or something.

No. Just.... No.

Unexpected behavior isn't a reason to use root permissions.  Ever.  Root is for system administration. 

However, launching from a terminal window could give you some revealing output.

This might be helpful as well, as there is  Sun Java, and the OpenJDK; usually compatible but not always equal.

[http://ubuntuforums.org/showthread.php?t=295718](http://ubuntuforums.org/showthread.php?t=295718)

---

### Post by fdrake on 2011-05-26
in the terminal :```

chrome www.site.com
```
or 
```
sudo chrome www.site
```

post here the output when chrome fails

---

### Post by jlp1528 on 2011-05-26
No dice on either of your suggestions. No output if I launch Google Chrome from terminal. It just runs. And BTW the command is google-chrome not just chrome and no I don't need sudo. In fact, if I try sudo, it says Google Chrome can not be run as root. So, any further ideas? Also, I think some of you are misunderstanding the problem. I'm just trying to get Java to work on pingtest.net. The packet loss test uses Java. Again, I think I have my permissions right, and it almost seems like Java is trying to do its job, but it doesn't. Both lines are blank for a while (they both immediately say 0 at first when it works), and then it just says that it was unable to test. I think I'll try resetting my permissions for plugins to run. Also, should I check the permissions for the Java files themselves? Maybe Ubuntu is not allowing Google Chrome to use the files. But that would be strange considering that I don't have this problem in Firefox or Opera... Then again, it can't hurt to try. I guess I'll try while you guys brainstorm some more.

---

### Post by jlp1528 on 2011-05-26
fdrake, the link in your signature does not work. Just letting you know.

---

### Post by infallible on 2011-05-26
[QUOTE=fdrake;10863827]
or 
```
sudo chrome www.site
```

No.  How can I say it so you understand?  Do not run a browser as root.  This is a security issue. This kind of help is counterproductive and should be kept to oneself.

The OP is evaluating browsers. In my opinion, this kind of evaluation calls for assessment as-is.  Note the failure and move on to other assessment criteria, including other bandwidth testing methods.  I've run across sites that assess compliance with standards for HTML, HTML5 and CSS, these may be more pertinent.

---

### Post by fdrake on 2011-05-26
> **infallible said:**
> [QUOTE=fdrake;10863827]
or 
```
sudo chrome www.site
```

No.  How can I say it so you understand?  Do not run a browser as root.  This is a security issue. This kind of help is counterproductive and should be kept to oneself.
you are NOT running as ROOT!!!! doh. You are just extending the permissions of you user account.. To run chrome as root u'd need to do:gksudo. by using sudo u use your config files, with gksudo u use roots conf file!  different story.

that's why he has an error when he runs chrome as root since he is probabl using the conf files of another user, not of root!

---

### Post by jlp1528 on 2011-05-26
fdrake, either way it says Google Chrome can not be run as root. So like infallible said, stop telling me to run stuff as root because not only am I unable to do so in this case, but it probably wouldn't work anyway. Infallible, I don't really want to give up on this, but yes, maybe I should just note the failure and move on. BTW I have a list of the stuff I'm going to do. I will go find it and post it here. At that point, if you can think of any more completely unbiased tests or even just tell me which ones on my list are likely to be the most relevant, I'd appreciate the help. Maybe you could PM me on that stuff since I doubt that a lot of other people would care. Or email works too. While I'm here, I also have another question, one that's probably going to make me sound like a total n00b, but I'll ask it anyway: What's with the beans and coffee jokes everywhere about Ubuntu? Beans seem like ranks, but why beans? And why do people say that they saw a problem so they drank a huge cup of coffee and wrote something to solve it? I do not understand...

---

### Post by fdrake on 2011-05-26
see here [http://ubuntuforums.org/showthread.php?t=239560](http://ubuntuforums.org/showthread.php?t=239560)

maybe to fix this problem it will take more time then using another website nohh?  and by that, we are assuming that the website is fully supporting chrome, thing that we are not sure about. Does chrome works on win7 . Why don't you just try a different site or that maybe doesn't use java, but ajax or something else instead.

---

### Post by infallible on 2011-05-26
> **fdrake said:**
> [QUOTE=infallible;10865556]
you are NOT running as ROOT!!!! doh. You are just extending the permissions of you user account.. To run chrome as root u'd need to do:gksudo. by using sudo u use your config files, with gksudo u use roots conf file!  different story.
that's why he has an error when he runs chrome as root since he is probabl using the conf files of another user, not of root!

Sudo gives your user account root permissions (but not root's $PATH.)
gksudo is sudo for GUI applications.   When you use either, you give that application root permissions. Semantics aside, this is a bad idea.

 [http://linux.die.net/man/1/gksudo](http://linux.die.net/man/1/gksudo)
 [http://linux.die.net/man/8/sudo](http://linux.die.net/man/8/sudo)

---

### Post by jlp1528 on 2011-05-27
Fdrake, stop telling me to mess around with sudo crap or get off this thread. And yes the site does fully support Google Chrome because it works perfectly on Windoes 7. Infallible, I will find my list. When I do would you like a PM or do you want me to post it here? I don't mean to be pessimistic but it doesn't look like this very minor problem is going to get fixed so I'm probably going to stop using this thread. Perhaps the problem doesn't even need to be fixed. I mean, if packet loss is 0%, it's 0% regardless of browser right? In fact, the entire test may not even be pertinent to my project. What I really want is to compare compliance with the latest and greatest of web technologies and standards and browser speed (not internet speed) across the browsers. By speed I primarily mean basic page loading speed. I've heard JavaScript tests are good to determine that. Is that true? Really whatever browser I'm on in Ubuntu tends to be a bit slow at loading pages, but download speed is great (4.2 Mbps). Then again, I'm using Ubuntu as my primary OS now so it could be the same story on Windows 7... Also, ever since Qwest "upgraded" our Internet when we complained about being very misinformed about pricing, it's been weird. Ping isn't as good as it was before (55 ms... from A to B on pingtest.net... disappointing...), and whenever my sister gets on Facebook, our modem/router combo thing crashes and I have to give it a hard reset by unplugging it and plugging it back in. Yet I still can't convince my dad to have another chat with Qwest. Maybe I should update our 5-year-old modem/router's firmware that hasn't been updated ever before? Do you think that would help? Yes I know I'm really rabbit-trailing off the original point of this thread so yes I think this would be the time for some PMs. If you can help, infallible, that would be great. I'd be sure to credit you in my project somehow if you end up helping. It would be great if you could do the same tests as me to help validate my results, even if I can't put your results in the project. Anyway, shoot me a PM. Let's talk. Is there a chat feature on this site? If not there's always gmail chat...

---

### Post by infallible on 2011-05-27
There, finally at my desk, maybe I can help a little.

When I go to pingtest.net on my machine (or speedtest.net, or speedtest.qwest.net)  I get a notification that I need to install Flash.  Adobe's support for Linux has been mostly an afterthought, so I'm not surprised that a flash app was having problems.  <speculation> It could be Chrome's 'sandboxing' or maybe something else...</speculation>

That aside, you're looking for render speed, not download speed. Javascript is good for this because it's 'client-side' code, downloaded from a remote server to be executed locally.  The download time should be negligible across browsers, since it's a common denominator.  You're looking for the time that it takes to actually skim the html, apply CSS styles, run the javascript, and draw the page to your screen.  

There's plenty of benchmark sites out there for you to discover. [http://clients.futuremark.com/peacekeeper/index.action](http://clients.futuremark.com/peacekeeper/index.action) was pretty interesting.

[http://html5test.com](http://html5test.com) is a good way to see how browsers are keeping pace with html5 development.  Keep in mind that at this stage, the score isn't really a 'score' - some support is left out for business reasons, some for security reasons.

I found this while searching for CSS compliance, not a benchmark but informative:
[http://clients.futuremark.com/peacekeeper](http://clients.futuremark.com/peacekeeper)

So, keep looking around the internet with this context in mind. Post your list, maybe I, or someone else, will have more feedback.  If I'm reading correctly, you're comparing browsers across platforms to see if each runs differently?  I would expect similar results from like *versions* of firefox or chrome, but I wouldn't actually expect like versions to be installed for each.  You'd get more info on this browsing bug reports than running benchmarks or speed tests.

---

### Post by jlp1528 on 2011-05-27
I already knew about Peacekeeper and [www.html5test.com](www.html5test.com). I'll get the list in a bit, but I started this on my iPod and need to copy the list from an email. To clarify, I'm comparing browsers to each other, not platforms with the same browser because yes, the results there would probably be about the same. Running for list now...

---

### Post by jlp1528 on 2011-05-27
Finally found it in that old email. So, this is what I have so far.
[http://clients.futuremark.com/peacekeeper/index.action](http://clients.futuremark.com/peacekeeper/index.action) (Peacekeeper)
[http://acid3.acidtests.org/](http://acid3.acidtests.org/) (The Acid3 Test)
[http://html5test.com/](http://html5test.com/) (an HTML5 test similar to the Acid3 Test, but with, well, HTML5)
[https://clubcompy.com/rwBench.jsp](https://clubcompy.com/rwBench.jsp) (ClubComply HTML5 and Javascript benchmark)
[http://www.craftymind.com/guimark2/](http://www.craftymind.com/guimark2/) (yet more HTML5 and Flash benchmarks/comparisons)
[http://www.lecrabe.net/labs/benchmark/ps3/test7.html](http://www.lecrabe.net/labs/benchmark/ps3/test7.html) (LeCrabe Flash benchmark)
[http://www.this-play.nl/tools/flashmark/](http://www.this-play.nl/tools/flashmark/) (another Flash benchmark)
I'm really not sure if I want Flash benchmarks though. A lot of games are made in Flash still so I thought it might be a good idea, but do most games even use enough computer power for it to even make a difference? Also, you mentioned CSS. Can you find any unbiased CSS benchmarks out there? I'll also go hunting and report back. But I also can't have too many benchmarks. Also, something to note: Peacekeeper calculates final score out of mean of subscores. This may seem good at first, until you look at the fact that Google Chrome absolutely blows away the data test with a whopping 30000 points or more. That throws off the average quite a bit. But then again, maybe it doesn't matter. Isn't that one of the most important aspects of browser performance? I looked at that test's details and it seems like it's mostly JavaScript...

---

### Post by jlp1528 on 2011-05-27
[http://selectors.turnwheel.com/slickspeed.php](http://selectors.turnwheel.com/slickspeed.php) (CSS benchmark)
Does that look like a good one to you?

---

### Post by infallible on 2011-05-28
Looks like you've got a good handle on benchmarks. I brought up CSS because some browsers are notorious for doing their own thing - IE especially.

Good luck with your project!

---

### Post by jlp1528 on 2011-05-28
What do you mean by some browsers do their own thing? And IE has a pretty good set of demos itself, including benchmarks, but wouldn't they be biased and work best on IE? Or should I try some anyway and see if other browsers can still kick IE's butt in its own benchmarks?

---

### Post by infallible on 2011-05-28
In the early days of the internet, IE had absolute dominance over the browser market (they still do, but to a lesser extent.) HTML and CSS are standardized for public consumption by the World Wide Web Consortium.  Newer browsers like Chrome and Firefox start with the specs for these markup languages and work up to build the browser; Internet Explorer has taken a different approach.  The languages are treated as a feature of the browser, and not only rendered as the IE sees fit, but adding tags unused by other browsers, and not implementing others.  

The end result is that a web designer must design for both IE and other browsers, instead of simply adhering to the standards.  Conditional statements directing IE to it's very own stylesheet are the norm. This might give you some insight, and there are plenty of articles out there describing 'workarounds' for IE's implementation.

[http://en.wikipedia.org/wiki/Comparison_of_layout_engines_%28Non-standard_HTML%29](http://en.wikipedia.org/wiki/Comparison_of_layout_engines_%28Non-standard_HTML%29)

---

### Post by jlp1528 on 2011-05-28
Interesting. So that probably means that yes, IE9 demos will either not work or completely suck on other browsers. Dang, and people still wonder why I hate Microsoft. Yet I still probably have to buy and use Windows for just a few things just because the most of the world is still making stuff for Windows and Windows only. I'm really trying to use Ubuntu as my main OS though now. So far it seems to be working for everything I need it to, if there is a bug here or there. But if I ever want to do any serious gaming, I'll be stuck with Windows because games are made for Windows. Yes, I know, wine, blah blah blah. But wine simply doesn't work all the time. Seems like we're David stuck in a futile, chicken-or-egg fight/scenario against Goliath, and we just haven't found the right stone yet. Then again, David did kick Goliath's butt in the end...

---

