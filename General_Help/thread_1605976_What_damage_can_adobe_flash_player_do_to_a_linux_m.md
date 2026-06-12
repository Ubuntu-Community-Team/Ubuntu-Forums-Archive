---
title: "What damage can adobe flash player do to a linux machine?"
date: 2010-10-26
forum: General Help
---

### Post by aloprot on 2010-10-26
Hi, I hope I posted in the right section, if not I kindly ask a moderator to move it where it belongs(I didn't find the section). Like the title says I would like to know what damage can adobe flash player can actually do to a linux machine. Right now I am running ubuntu 10.10 and flash player. I have read adobe system security buletin and saw a lot of vulnerabilities cross platform and linux is affected too. But I'm curious, what can this vulnerabilities do to your linux machine. I don't like it but unfortunately I have to use it because I go to a lot of websites with flash content and gnash can't help me, yet. 
Thank you very much!

---

### Post by lovinglinux on 2010-10-26
Most of the last security alerts I read about flash stated that a specially crafted malicious flash content could crash the player and allow full control of your machine.

Besides that, if you use flash all the time I suspect it could diminish hardware life expectancy, because it uses a lot of CPU. This is just a guess, because I have no data about how long you can use your machine in such conditions and how it would affect your hardware.

---

### Post by dcstar on 2010-10-26
> **lovinglinux said:**
> Most of the last security alerts I read about flash stated that a specially crafted malicious flash content could crash the player and allow full control of your machine.
..........

And if you read them carefully, most of them refer to Windows and the references to Unix/Linux seem very (**very**) difficult to determine.

I haven't read **one** example of Flash content damaging or compromising a Linux install since I started using Ubuntu at version 4.10.

If you happen to stumble onto some web site with malicious Flash content and - at worst - it mucks up your browsing session then I don't consider that much to justify the amount of fear people seem to have.

There might be a risk, but it seems that in the Linux world it is a tiny risk.

---

### Post by HermanAB on 2010-10-26
Howdy,

In my experience, the worst thing it does is make Firefox freeze, so you got to restart it.  I would not classify that as a security problem.

---

### Post by aloprot on 2010-10-26
Thank you!

@lovinglinux: Were you ironic?:)

---

### Post by lovinglinux on 2010-10-26
> **aloprot said:**
> @lovinglinux: Were you ironic?:)

Maybe :)

---

### Post by nacho32 on 2010-10-26
It could cause your computer to explode blowing every window out of your house. 
[IMG]http://www.mopo.ca/uploaded_images/computerbomb-737749.jpg[/IMG]

---

### Post by aloprot on 2010-10-27
I don't understand, why so much irony? I just asked a simple question, I'm not an expert, I do not know. nacho32,either you give me a relevant answer or you can stop posting pictures like that. What do you want to prove?

---

### Post by NoBugs! on 2010-10-27
> **lovinglinux said:**
> Most of the last security alerts I read about flash stated that a specially crafted malicious flash content could crash the player and allow full control of your machine.

It shouldn't be possible for a malicious script to "take over" your computer, unless you run your browser as root. By default Firefox and other browsers only have user's privileges, so a malicious script would at worst have same privilege as normal user.

---

### Post by dcstar on 2010-10-27
> **NoBugs! said:**
> It shouldn't be possible for a malicious script to "take over" your computer, unless you run your browser as root. By default Firefox and other browsers only have user's privileges, so a malicious script would at worst have same privilege as normal user.

Will you people pay attention?, **all** of those articles actually refer to versions of Windows where it **is** possible for malicious code to run with full privileges.

How do you think all of the millions of zombie machines that spam the world right now got compromised?, it wasn't by running a modern version of Linux.

---

### Post by aloprot on 2010-10-27
'A [critical]("http://www.adobe.com/support/security/severity_ratings.html")  vulnerability exists in Adobe Flash Player 10.1.82.76 and earlier  versions for  Windows, Macintosh, Linux, and Solaris, and Adobe Flash  Player 10.1.92.10 for  Android. This vulnerability also affects Adobe  Reader 9.3.4 and earlier versions for Windows,  Macintosh and UNIX, and  Adobe Acrobat 9.3.4 and earlier versions for Windows and  Macintosh.  This vulnerability (CVE-2010-2884) could cause a crash and  potentially  allow an attacker to take control of the affected system.'

[http://www.adobe.com/support/security/bulletins/apsb10-22.html](http://www.adobe.com/support/security/bulletins/apsb10-22.html)


From here I draw the conclusion that this can happen to linux too. So why the irony?

---

### Post by tomtiger40 on 2010-10-27
> **aloprot said:**
> Hi, I hope I posted in the right section, if not I kindly ask a moderator to move it where it belongs(I didn't find the section). Like the title says I would like to know what damage can adobe flash player can actually do to a linux machine. Right now I am running ubuntu 10.10 and flash player. I have read adobe system security buletin and saw a lot of vulnerabilities cross platform and linux is affected too. But I'm curious, what can this vulnerabilities do to your linux machine. I don't like it but unfortunately I have to use it because I go to a lot of websites with flash content and gnash can't help me, yet. 
Thank you very much!
i didn't think that flash damaged any computer:)

---

### Post by matt_symes on 2010-10-27
Hi,

dcstar is correct. Remember Linux is not windows. To answer your question, _any_ computer can be infected with a virus. _However_, running Linux without root privilages is going to make it next to _impossible_ to get a virus unless you install it yourself. One cannot make computers idiot proof. One can only put enough safe guards in place to help a user protect them self. As for the picture, Maybe the poster was trying to make you laugh. It made me chuckle.

Kind regards

---

### Post by nerdy_kid on 2010-10-27
I suppose a security flaw could allow *his* account to be compromised though?  I think that you are safe there as well if you use chrome with all its process isolation and all that.  But, I really wouldn't be worried.  Like everyone else said, it is basically impossible to get a virus from flash on linux unless you are running it as root.

---

### Post by maureenc on 2010-12-18
I am a very new Ubuntu user.... 

I decided to load Ubuntu after  my main hard drive was corrupted following a download of an Adobe Acrobat update o Windows XP...

This week my OH's Vista laptop has also "died" after he downloaded an update of Adobe Acrobat...

I've come to this thread because I wanted to find out if I am safe to load the latest (?) Flash player so that I can make full use of the BBC sports section.....

Can I assume that I will be about as safe as possible loading Adobe to Linux?

Thanks for your help...... Mo

---

### Post by nerdy_kid on 2010-12-18
> **maureenc said:**
> I am a very new Ubuntu user.... 

I decided to load Ubuntu after  my main hard drive was corrupted following a download of an Adobe Acrobat update o Windows XP...

This week my OH's Vista laptop has also "died" after he downloaded an update of Adobe Acrobat...

I've come to this thread because I wanted to find out if I am safe to load the latest (?) Flash player so that I can make full use of the BBC sports section.....

Can I assume that I will be about as safe as possible loading Adobe to Linux?

Thanks for your help...... Mo

your as safe as you can get :)  If you are really worried, then use google chrome as your browser.  It is basically impossible for a linux system to be destroyed by adobe flash.  Just don't run your browser as root (if you don't know what I am talking about then you are not running it as root so dont worry).

---

### Post by uRock on 2010-12-18
There are quite a few flash vulnerabilities. Use [NoScript]("http://noscript.net/") add-on in Firefox. Please read this very informative thread to learn more about Ubuntu's security and how to properly implement it. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by dcstar on 2010-12-18
> **nerdy_kid said:**
> 
.......
Like everyone else said, it is basically impossible to get a virus from flash on Linux unless you are running it as root.

**And** the "virus" is **specifically** written to execute on a Linux platform.

This is the whole point people seem to miss when getting hysterical about media reports of all these threats, any code that gets run by these vulnerabilities usually has to be OS specific - and guess what OS has the overwhelming mass of attacks because it is so inherently insecure?

Yes, Flash can have some common vulnerabilities across platforms but that only opens a crack in door that OS specific code might be able to run in, and what do you all think the percentage of Linux to Windows code hacks will be written and put out in the wild?

---

### Post by maureenc on 2010-12-19
Thank you Nerdy_kid, Urock and dcstar for you replies, much appreciated.

Urock - I've bookmarked that thread and will read it ASAP..... Thank you.....
 
Should I load Flash before I install the "No Script" or won't it make any difference?

Cheers,
Mo

---

### Post by nerdy_kid on 2010-12-19
> **maureenc said:**
> Thank you Nerdy_kid, Urock and dcstar for you replies, much appreciated.

Urock - I've bookmarked that thread and will read it ASAP..... Thank you.....
 
Should I load Flash before I install the "No Script" or won't it make any difference?

Cheers,
Mo

noscript will just kill flash, so if you want to use flash you have to disable noscript temporarily anyway.  I saw just install it.  If you get a virus, post here and you'll be famous :lol:

---

### Post by uRock on 2010-12-19
> **nerdy_kid said:**
> noscript will just kill flash, so if you want to use flash you have to disable noscript temporarily anyway.  I saw just install it.  If you get a virus, post here and you'll be famous :lol:
You don't get viruses via flash attacks. And you don't temporarily allow flash. You select the things you trust such as the video frame on youtube, while the other unknowns from the site are blocked.

---

### Post by tgalati4 on 2010-12-20
Flash may not shorten the life of your computer but it does shorten your life expectancy.  Frustrations with flash on linux cause an increase in stress hormones which has been shown to shorten life.

So, yes, flash is dangerous to your health.

---

### Post by lovinglinux on 2010-12-20
> **tgalati4 said:**
> Flash may not shorten the life of your computer but it does shorten your life expectancy.  Frustrations with flash on linux cause an increase in stress hormones which has been shown to shorten life.

So, yes, flash is dangerous to your health.

:lolflag:

Indeed.

---

### Post by maureenc on 2010-12-21
Got enough stress already! Is it flakey on Ubuntu then? 

But what alternative is there to Flash if, like me you are not a Linux expert? I don't want anything flash (?) just something that will let me view the videos on News sites etc..

Mo

---

