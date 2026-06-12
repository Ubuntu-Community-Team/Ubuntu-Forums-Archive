---
title: "Flash in Ubunto  FireFox?"
date: 2009-09-08
forum: General Help
---

### Post by Irvine_himself on 2009-09-08
In Windows, I am a bit of a security geek and having just installed Ubuntu for the first time, I was setting up my browser security features  when I noticed there did not seem to be a Flash application directory.  Is this because Flash applications are not supported, or do they have to be installed separately?

---

### Post by wojox on 2009-09-08
You're best installing ubuntu-restricted-extras:

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by P4man on 2009-09-08
Welcome to  **u**b**u**nt**u** (no o's)
:)

Im not entirely sure what you mean, but did you install flash already? It doesn't come installed by default, but it should prompt you to install adobe flash when browsing to a page with flash content. (do install the nonfree adobe flash plugin though, and not the free alternatives, which aren't quite up to the task yet).

---

### Post by manuelgsc on 2009-09-08
To install the flash plugin in jaunty:

1.- Enable the multiverse repository.
2.- Install flashplugin-installer

---

### Post by Irvine_himself on 2009-09-08
I installed the Flash plug-in for Ubuntu direct from the Adobe website. It fixes a new security hole, though I don't suppose Ubuntu users should worry?   The particular problem I was worried about is so called Flash cookies where both  goodies and baddies  use Flash to gather and store large amount's of personal data, use ping backs to track your habits and generally annoy people who are concerned about privacy. That problem is now solved since Adobe created the required directory and I can take the required steps.  Though, on the subject of privacy, in my Ubuntu Firefox installation I can't find the options tab where I can set default actions like: cookie permissions,  blacklist in-line images... etc.  Am I yet again missing something?

---

### Post by ackanao on 2009-09-08
To get rid of Flash cookies just send them to **/dev/null** and they're gone for good:

1. Delete "**~/.macromedia**" folder;

2. Create a symbolic link to /dev/null:

```
ln -s /dev/null .macromedia
```

Just to be sure that it's set up correctly use this command:

```
ls -ald .macromedia
```

You should see something like this:

```
lrwxrwxrwx 1 Irvine_himself Irvine_himself 9 2009-03-30 09:56 .macromedia -> /dev/null
```

Here's the link that explains things better:
[http://www.linuxplanet.com/linuxplanet/reports/6711/2/]("http://www.linuxplanet.com/linuxplanet/reports/6711/2/")

Alternatively, there are two Firefox extensions you can use to delete Flash cookies: BetterPrivacy and Objection.

EDIT:
> I can't find the options tab where I can set default actions like: cookie permissions, blacklist in-line images... etc. Am I yet again missing something?

For more control over your cookies and history select "Use custom settings for history" option in "Privacy" tab;

Sorry, but what do you mean by "blacklist in-line images" - do you want to block 3rd party images and/or IFRAMEs?

"**for originating web site only**" option for images is long gone from GUI but still available through **about:config**; Alternatively you could use **HOSTS** file, **userContent.css** file and AdBlock Plus to block adservers or you could use a local proxy like Privoxy for filtering.

If you want to block IFRAMEs just put this in your **userContent.css** file:

```
/* Disable launching programs and files in an IFRAME */

IFRAME {display: none !important;}
```

Or you could use NoScript extension.

---

### Post by Irvine_himself on 2009-09-08
Thanks ackanao,

That is pretty interesting about linking the folder to a null file, (I assume that's roughly what in effect the line is doing?)and could imagine lots more uses. I uses "Better Privacy" myself since it is easier and blocks "ping backs". As with traditional cookies, holding the Flash cookies for a short time can useful.

I did not realise this about the Firefox GUI... In Windows it is still pretty much as before, (a few niggling changes, but nothing radical.)

Okay, "blacklist in-line images" was probably badly phrased. As you are no-doubt aware, off-site images can be used to track your movements and Iframes can be used to launch attacks. 

I was recently reading an article, (sorry I cant remember details, it could have been the New York Times?)  which said that off-site images can be used to launch an attack similar to an Iframe attack.

In general I do use Noscript! since, with all these things, there are times when both Iframes and JS are useful.

Thanks again, that was a good informative answer.

---

### Post by ackanao on 2009-09-08
> **Irvine_himself said:**
> ...I did not realise this about the Firefox GUI... In Windows it is still pretty much as before, (a few niggling changes, but nothing radical.)...

...Okay, "blacklist in-line images" was probably badly phrased. As you are no-doubt aware, off-site images can be used to track your movements and Iframes can be used to launch attacks... 

OK. now I understand what are you talking about; In earlier versions of Firefox (prior to 2.x) there was an option for images "for originating web sites only" that effectively blocked almost all web-tracking beacons. Now it's really cumbersome to have about:config always open in one tab just to turn this option on/off. 

Because of that, I use mvps.org Hosts file available from here:
[http://www.mvps.org/winhelp2002/hosts.htm]("http://www.mvps.org/winhelp2002/hosts.htm")

I have my own set of rules in userContent.css file - if you want to use userContent.css to block ads, this one is excellent:
[http://www.gozer.org/mozilla/ad_blocking/]("http://www.gozer.org/mozilla/ad_blocking/")

I don't use AdBlock Plus because I just don't like it and I think that more than 90% of ads, web-bugs, etc. are blocked with my own setup so it's useless for me.

But I do like NoScript; I have a great respect for Giorgio Maone and I think that NoScript is one of the best security solutions for any web browser - but I must admit that I'm glad that it's only available for mozilla-based browsers...

---

### Post by Irvine_himself on 2009-09-08
Thanks again, that is also a useful and though provoking reply.

I cant check out the full details, since the box I am installing Ubuntu on is currently at a friends house, (I am using his high speed internet connection for installation purposes.) My other machine, the one I am using at the moment runs XP and it was this one from which I was going to import my Hosts file into Ubuntu. 


As a browser, I am using Firefox 3.5.2 and if I goto: 

Tools >> Options >> Content >> Allow Images >> Exceptions

This lists  sites from which images are blocked, usually by anti-malware, but individual sites can be entered by hand. This list, plus a list of known bad cookies, is stored in "permisssions.sqlite" in  Firefox profiles and can be exported to another Firefox installation by copy and paste. I take it from what you are saying that there is no compatibility between Firefox for Windows and Firefox for Ubuntu?


PS

In fact I have the full Tor/Privoxy setup installed; though, (noting the current direction of UK government,) it is mainly for the political statement that the proposed new legislation is un-enforceable. I find that Google does not really like Tor and Privoxy is too hard-core for general use. Generally I use Adblock-Plus which is much lighter than Privoxy and better suited for the normal user.

---

### Post by ackanao on 2009-09-08
> **Irvine_himself said:**
> Thanks again, that is also a useful and though provoking reply.

I cant check out the full details, since the box I am installing Ubuntu on is currently at a friends house, (I am using his high speed internet connection for installation purposes.) My other machine, the one I am using at the moment runs XP and it was this one from which I was going to import my Hosts file into Ubuntu.


As a browser, I am using Firefox 3.5.2 and if I goto:

Tools >> Options >> Content >> Allow Images >> Exceptions

This lists sites from which images are blocked, usually by anti-malware, but individual sites can be entered by hand. This list, plus a list of known bad cookies, is stored in "permisssions.sqlite" in Firefox profiles and can be exported to another Firefox installation by copy and paste. I take it from what you are saying that there is no compatibility between Firefox for Windows and Firefox for Ubuntu?


PS

In fact I have the full Tor/Privoxy setup installed; though, (noting the current direction of UK government,) it is mainly for the political statement that the proposed new legislation is un-enforceable. I find that Google does not really like Tor and Privoxy is too hard-core for general use. Generally I use Adblock-Plus which is much lighter than Privoxy and better suited for the normal user.

They should be perfectly compatible with each other you don't have to worry about that - sorry for misunderstandings but english is not my native language.

Yes, you can block images with "Exceptions" option but I think you may experience slowdowns of Firefox UI if you use large blocklist; If Firefox UI become less responsive then you could use HOSTS file and AdBlock instead. 

About cookies: Maybe it's better idea to just block all cookies by default and then you just define the White-list of websites that are allowed to store cookies - I think this is a better solution because the "white list" will be much shorter (couple of lines long); You could use CS Lite extension to temporarily enable cookies for websites that are not on a "white list" (when needed).

I didn't mean to post a provoking reply and I'm sorry about that; I just wanted to point out (for any other Firefox user) that NoScript offers protection from various attacks and not just from web-tracking beacons like ads or web-bugs.

---

### Post by Irvine_himself on 2009-09-08
No apology is needed, it is my bad spelling: 

While I wrote "though provoking", I meant to write "thought provoking"

That is a complement, it means your reply was stimulating and well written and brought new ideas to my attention.

---

### Post by ackanao on 2009-09-08
OK. thank you for that. :KS

And thanks to our discussion i decided to give another chance to AdBlock and I must admit that it's far more easier and faster to block ads with AdBlock then creating your own rules in userContent.css; I really like "**AdBlock Plus: Element Hiding Helper**" because with just a few clicks I can block any element on the webpage that annoys me - I used to do this "by hand", looking at the source code of a page and creating the css rules in userContent.css file for "unwanted" html elements.

So I stand corrected - AdBlock Plus is much better and much easier solution for adblocking than userContent.css file. For some stupid reason (or lack of better judgment) I avoided it for years... :confused:

---

