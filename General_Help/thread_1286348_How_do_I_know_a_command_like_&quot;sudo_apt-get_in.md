---
title: "How do I know a command like &quot;sudo apt-get install ubuntu-desktop&quot; is not a hacker?"
date: 2009-10-08
forum: General Help
---

### Post by Linuxwho? on 2009-10-08
I am using 8.04 but the question applies to any version really.  So I am watching all this stuff download and install..How do I know that when doing an update or getting some sort of package using this command, it is not a hacker intercepting at setting up stuff on my computer?  Thanks.

---

### Post by OpenGuard on 2009-10-08
He'll better install some of his rootkits, not ubuntu-desktop :D Seriously, everything that starts with apt-get ( except custom repos ), comes directly from Ubuntu servers and there are no way someone could spread malicious code, just for fun/profit.

---

### Post by CharlesA on 2009-10-08
It even says where it's being downloaded from.

---

### Post by cariboo on 2009-10-09
The code for all packages gets reviewed before it is accepted in the repositories.

If you write a program and want it included in the repositories, you have to have a sponsor, an ubuntu developer usually, before it will even be accepted for code review.

---

### Post by OpenGuard on 2009-10-09
> **cariboo907 said:**
> 
If you write a program and want it included in the repositories, you have to have a sponsor, an ubuntu developer usually, before it will even be accepted for code review.

Why so big restrictions ? I mean, if I'm developing applications just as a hobby and don't know anyone from Ubuntu developers, I should not even think about a chance to see my application ( no matter how good it is ) being reviewed and uploaded to repositories ?

---

### Post by cariboo on 2009-10-09
It is more a matter of security than anything else, the way it is set up we are assured that the code is safe and there will no sort of malware in the package.

Have a look [here]("https://wiki.ubuntu.com/UbuntuDevelopers") for what it takes to be able to contribute a package.

---

### Post by OpenGuard on 2009-10-09
> **cariboo907 said:**
> It is more a matter of security than anything else, the way it is set up we are assured that the code is safe and there will no sort of malware in the package.

Have a look [here]("https://wiki.ubuntu.com/UbuntuDevelopers") for what it takes to be able to contribute a package.

Security doesn't always mean 5 doors, made from steel, isn't it ? Anyway, thank you for the link - will definitely check it out.

---

### Post by sopadeajo on 2009-10-09
> **OpenGuard said:**
> Why so big restrictions ? I mean, if I'm developing applications just as a hobby and don't know anyone from Ubuntu developers, I should not even think about a chance to see my application ( no matter how good it is ) being reviewed and uploaded to repositories ?

Since it is open source code you just post the code (or a part of it) in a forum like this one and other developers will see if your application is good.

---

### Post by dcstar on 2009-10-09
> **cariboo907 said:**
> The code for all packages gets reviewed before it is accepted in the repositories.

If you write a program and want it included in the repositories, you have to have a sponsor, an ubuntu developer usually, before it will even be accepted for code review.

What about any other of the "unofficial" repositories that people are urged to add to their systems constantly? These can easily install any piece of code simply by having a package version higher than the official one.

Half the "advice" in these forums seems to compromise the security of Ubuntu setups in one way or the other.

Any advice about Ubuntu being a "safe" environment must have the caveat of a system with no unofficial repositories as well as not have been compromised by the multitude of "help" that is around.

---

### Post by Linuxwho? on 2009-10-11
This is good to know.  For the most part I feel much better that "corporate" america does not have the hold on security and we can rely on Ubuntu instead of Microsoft so much.  You guys rock.  :guitar:

---

### Post by t0p on 2009-10-11
> **dcstar said:**
> What about any other of the "unofficial" repositories that people are urged to add to their systems constantly? These can easily install any piece of code simply by having a package version higher than the official one.

Half the "advice" in these forums seems to compromise the security of Ubuntu setups in one way or the other.

Any advice about Ubuntu being a "safe" environment must have the caveat of a system with no unofficial repositories as well as not have been compromised by the multitude of "help" that is around.

There are clear notices all over the place warning about accepting software from third parties and exhorting you to only install software from trusted sources.  It's up to you what you install to your system.  And it would be silly to start claiming Linux is insecure because the administrator of a system can cause it to be screwed up!  Security is the administrator's responsibility at the end of the day.

If security is uber-important to you set-up, then don't install any third party software.  If you choose to install software from untrusted sources, do so and accept the possible consequences.  But don't blame anyone else if doing this b0rks your system.  You have been warned!

---

### Post by Snatcher on 2009-10-11
Since, this is Linux we're talking about.  A hacker is more then likely going to fix a hole then take control of someones system . However with Microsoft they would post it all over then internet.  But its good to know Ubuntu is taking steps to prevent any bad code getting in to our systems with their updates.

---

### Post by jpmelos on 2009-10-11
Thanks for the explanation of this point... I didn't know about all that procedure to get your application in the official repositories, nor did I know about the problems of setting up third-party repositories could cause...

Now, I guess I'm not going to set up repositories of third-parties, but I guess I can download an application and install them myself, instead of relying on the apt-get. That is much safer!

Thanks!

---

### Post by CatKiller on 2009-10-11
> **dcstar said:**
> What about any other of the "unofficial" repositories that people are urged to add to their systems constantly? These can easily install any piece of code simply by having a package version higher than the official one.

It's been [done]("http://ubuntuforums.org/showthread.php?t=297814") [already]("http://www.flickr.com/photos/trevi55/296804891/").

(No harm from that particular case, but I think the community as a whole learned a sharp lesson at that point. Possibly it's time for a refresher...)

---

