---
title: "Firefox and ScotiaBank online banking website"
date: 2006-03-18
forum: General Help
---

### Post by FIONEX on 2006-03-18
Hey,

I realised that the Scotiabank Online banking website won't load my account under firefox.  However, it will load it in IE (server is up).  Funny thing is, it'll load almost everything, except for pages that access account information like "Pay bills, Account balance".  I tried using the UserAgen Switcher plugin with no success.  Then I realised that when I switched UserAgent to MSIE6, even this website acts wierd -> the search drop down menu stopped working.  When i switched it back to default, the search drop down menu works.  So i'm thinking that the wrong UserAgent line is being used 'Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)'.  What do you think?

---

### Post by SoggyCornflake on 2006-03-18
Have you tried using Konqueror?  I've had pretty good luck with its spoofing abilities.:p

---

### Post by FIONEX on 2006-03-18
Actually, it just viewed the page TEMPORAIRLY.  I don't know why the server only sends this browser the first half of the page :S.

---

### Post by FIONEX on 2006-03-18
Ok so I've realised it has to do with the way the page loads.  For some reason, the server doesn't load the page evenly.  Like it sends the header of the page and the menu, but the account information is sent after a second or something.  So firefox doesn't load it.  Any ideas what might be causing this, or how would I get firefox to wait for the rest of the page?

---

### Post by Tayra on 2006-04-21
Hello. My mother's new Ubuntu install is behaving the same way. I have attempted to have her use Mozilla, Opera, Epiphany, and Firefox, all to the same effect.  With Opera she can press stop and Reload several times to eventually load the first account page. But this is NOT good for doing any money transfers   etc.... (repeat it several times?!)


I'm wondering if this may be a problem with Ubuntu, were you ever able to resolve this problem? Or does anyone else have any ideas other than returning to *shudders* Microsoft?

Thanks in advance!

---

### Post by Joel B on 2006-04-27
I am also having this problem and it is extremely annoying.  I have 2 ubuntu computers that refuse to load the ScotiaBank web page.  I have also tried running Win2k in VMware and that doesnt even work.  This leads me to believe that this is a problem with networking in the OS itself.

Could someone please look into this?  The website to try is [http://www.scotiaonline.scotiabank.com](http://www.scotiaonline.scotiabank.com)

Thanks

---

### Post by Jagot on 2006-04-27
I have installed Firefox 1.5.0.2 as per this wiki:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

The page you posted loads perfectly for me.

If that doesn't work for you then you could always install Internet Explorer in WINE as a last resort.  This is the easiest way to do that:

[http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)

---

### Post by Sef on 2006-04-27
Works fine for me with Opera and firefox 1.5.0.1.

---

### Post by az on 2006-04-27
[QUOTE=Joel B]I am also having this problem and it is extremely annoying.  I have 2 ubuntu computers that refuse to load the ScotiaBank web page.  I have also tried running Win2k in VMware and that doesnt even work.  This leads me to believe that this is a problem with networking in the OS itself.

Could someone please look into this?  The website to try is [http://www.scotiaonline.scotiabank.com](http://www.scotiaonline.scotiabank.com)

Thanks[/QUOTE]
Are you able to run the Dapper live cd?  Yo ucould log in to see if it work. It seems to load fine for me, but I don't log in since I am not a customer...

---

### Post by saultpastor on 2006-05-17
[QUOTE=Jagot]I have installed Firefox 1.5.0.2 as per this wiki:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

The page you posted loads perfectly for me.

If that doesn't work for you then you could always install Internet Explorer in WINE as a last resort.  This is the easiest way to do that:

[http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)[/QUOTE]

The main page is no problem it is the account information after you log in.  This has been broken for a long time in Linux.  I don't remember when it started, but the only solution is boot windows.  I hate it.  I have tried many distros and every browser I've ever heard of.  

It must be a problem with the basic way Linux configures networking. It is worth noting that this started showing up occassionally arount Aug 05  I think Scotia Bank signed a agreement with Microsoft around Feb 05.  I'm sure this has nothing to do with it. :-?  I have an old laptop with win 98 on my network just for my banking and it works fine behind the same router.  Yes I have tried IE under wine on several platforms.

I would be so grateful if some braniac Linux Guru brought forth some ideas.  Here are some of the things I have tried.

[http://www.oclug.on.ca/archives/linux/2005-August/000232.html](http://www.oclug.on.ca/archives/linux/2005-August/000232.html)

I would also add that this problem has gotten worse with newer kernels.  6 months ago I could refresh several time and get the page to eventually load.  Just ried again today on a 2.6.15 kernel and I can't get it to load at all.  I also remember getting it to load nicely on a P1 120mhz under STX with Mozilla.  But the same livecd on a P3 1ghz required the same reload dance.

fwiw

---

### Post by Madpilot on 2006-05-18
I'm a Scotia customer too, and haven't had any troubles with Ubuntu in a while, mostly using Opera but sometimes Firefox.

Currently with Opera 9beta Scotia Online works just fine, with no spoofing required - I always run Opera identified as Opera... Opera 8 up to 8.54 was just fine too... the standard Firefox in Breezy (1.0.x) has always worked, the few times I've used it instead of Opera...

---

### Post by saultpastor on 2006-05-18
[QUOTE=Madpilot]I'm a Scotia customer too, and haven't had any troubles with Ubuntu in a while, mostly using Opera but sometimes Firefox.

Currently with Opera 9beta Scotia Online works just fine, with no spoofing required - I always run Opera identified as Opera... Opera 8 up to 8.54 was just fine too... the standard Firefox in Breezy (1.0.x) has always worked, the few times I've used it instead of Opera...[/QUOTE]

Hmm.  I always assumed it was a Linux thing since it always has worked on the same network with windows (both XP and 98)  I have seen others complain about the same problem but I have wondered why more people don't have this problem.  I have the same problem from work.  At home I have a Dlink router, and at work a Linksys.  The one thing that is common is Shawcable.  I have experimented with different MTU's and no success.

Are you on shawcable?

---

### Post by Tayra on 2006-06-30
Unfortunately the end result was mom reverting first back to Puppy Linux (for some reason it still loads the website) - and then she switched back into XP. 
We are on shawcable. I removed ubuntu from the computers I had it on - but would reinstall most definately if we could get this issue worked out. I find that I can load the main page, but when logging in to do any account-related stuff, it wont load. Any solution for this yet?

---

### Post by UphillSkier on 2006-07-27
> **saultpastor said:**
> 

<snip> 
I would be so grateful if some braniac Linux Guru brought forth some ideas.  Here are some of the things I have tried.

[http://www.oclug.on.ca/archives/linux/2005-August/000232.html](http://www.oclug.on.ca/archives/linux/2005-August/000232.html)

I would also add that this problem has gotten worse with newer kernels.  6 months ago I could refresh several time and get the page to eventually load.  Just ried again today on a 2.6.15 kernel and I can't get it to load at all.  I also remember getting it to load nicely on a P1 120mhz under STX with Mozilla.  But the same livecd on a P3 1ghz required the same reload dance.

fwiw

I, too, would be eternally grateful to someone who could solve this.  I was having no problem under Breezy but when I upgraded to Dapper loading the "On-line Banking Sign-on" link just stalls right out. 

Has anyone had the same problem at any other Canadian Bank? My investment accounts at Bank of Montreal work fine.

---

### Post by Cooked_Electron on 2006-08-02
Okay...I found this forum by googling "Scotiabank won't load" cuz I too am experiencing the same wierd partially loaded pages as posted here.  The only thing is, I'm not using Ubuntu...but Vista Beta 2...

Either way the fact that two completely different o/s' are experiencing the same wierd symptoms leads me to beleive it's a Scotiabank problem.  The fact that some people have it working is baffling to me...

When I contacted Scotabank about the problem I got a reply that basically said "That's unfortunate, It should work, beta or not"...then in a totally unrelated, unhelpful addition to their reply, they offered me to sign up for the Scotia Star Network Rewards Program(tm)...stupid canned answers.

Hope somebody figures something out.  Maybe if enought people send them a message they'll work it out.

---

### Post by punkass on 2006-09-10
Just thought I would leave a note to, problem still exists even in Edgy knot2

---

### Post by ReelExterminator on 2006-10-03
I'm having trouble figuring this out as well. Firefox under Windows loads the page fine, while failing to do so both under Gentoo and Ubuntu. Also using shawcable.

---

### Post by Kyouzame on 2006-10-06
Here's a quick workaround that may assist you folks.  It has worked for my banking site, which was having similar problems (e.g. site logon problems, nonloading of account pages, etc.) under Firefox 1.5.0.3.   Uncheck SSL 2.0, but leave SSL 3.0 and TLS 1.0 checked, in Firefox's security settings.    

My thought is that the browser is trying to connect securely using both SSL 2.0 and SSL 3.0, and my bank's servers just won't have any of that.  Perhaps this or similar is causing problems for Scotiabank users.

---

