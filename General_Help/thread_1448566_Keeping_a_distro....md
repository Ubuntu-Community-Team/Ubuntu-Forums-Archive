---
title: "Keeping a distro..."
date: 2010-04-06
forum: General Help
---

### Post by ShadeS_07 on 2010-04-06
Is it a good idea to keep a distro even if it's been past its EOL?

I mean, for example, Kubuntu 10.04 LTS; If it gets released, I'm just thinking, if this distro will be stable and quite good for me, I might decide to keep it, even if it's reached its EOL...

Is that a good idea?

---

### Post by haddog on 2010-04-06
I guess it depends what you want to use it for. And for lack of a better example, lot's of people will still run win xp because their apps just work. I ran Ubuntu 5.10 on an old laptop until about a year ago, just because I could and had now probs with it. Actually the old hp laptop just died but it worked for me.

---

### Post by tekkidd on 2010-04-06
im running 9.04 and im not planning to upgrade to 10.04 after it releases

---

### Post by ShadeS_07 on 2010-04-06
So, it's not a bad idea? If I do such, I can still install, but I'll lose the capability of my distro to make automatic updates, if I keep it even to the point it has reached way past its EOL, right?

---

### Post by ubunterooster on 2010-04-06
If it ain't broke, wait 6 months to be safe before upgrading.

---

### Post by snowpine on 2010-04-06
> **ShadeS_07 said:**
> Is it a good idea to keep a distro even if it's been past its EOL?

I mean, for example, Kubuntu 10.04 LTS; If it gets released, I'm just thinking, if this distro will be stable and quite good for me, I might decide to keep it, even if it's reached its EOL...

Is that a good idea?

Kubuntu 10.04 will be fully supported through April 2013 (2015 for servers). How can you possibly know what your computing needs will be that far in the future? :)

Personally, I would not choose to use a distro past its EOL because it would no longer receive bug fixes and security patches. In the hypothetical situation that I was extremely attached to a particular distro (actually I am a horrible distro-hopper), I would rather use a rolling release distro or something like Red Hat that receives 10 years of support. ;)

---

### Post by Simian Man on 2010-04-06
I may be chastised for this but...unless you are using your computer as a public server it really doesn't matter that much whether you get the security updates or not.  We have some machines running *extremely* out of date Linux distros (including some with the original Red Hat still on them).  It's not that big of a deal.

---

### Post by ubunterooster on 2010-04-06
> **Simian Man said:**
> I may be chastised for this but...unless you are using your computer as a public server it really doesn't matter that much whether you get the security updates or not.  We have some machines running *extremely* out of date Linux distros (including some with the original Red Hat still on them).  It's not that big of a deal.
!#!$!&#8251;!¢!
You might as well leave them running as root for further convienience. You must keep a low profile or eventually script kiddies *will* have &#8220;fun&#8221;

---

### Post by waynefoutz on 2010-04-06
> **ShadeS_07 said:**
> Is it a good idea to keep a distro even if it's been past its EOL?

I mean, for example, Kubuntu 10.04 LTS; If it gets released, I'm just thinking, if this distro will be stable and quite good for me, I might decide to keep it, even if it's reached its EOL...

Is that a good idea?

you are going to have to change your sources so synaptic will continue working. In your /etc/apt/sources.list file, you are going to have to make these changes:


these lines need to be replaced:

```

deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

```

with these lines:

```

deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

```

The ones down at the bottom with the word "security" in them need to be commented out or removed. 

I took the liberty of putting "intrepid" in the code, since intrepid is the next version to go EOL in about 2-3 weeks. If it's an older version, you'd replace the word "intrepid" with the name, for instance "gutsy."

I plan on staying with Intrepid for a while myself. It was the last version ATI's drivers for my laptop's video card worked. The open source drivers are improving, but not where they need to be yet.

---

### Post by waynefoutz on 2010-04-06
> **ubunterooster said:**
> !#!$!&#8251;!¢!
You might as well leave them running as root for further convienience. You must keep a low profile or eventually script kiddies *will* have &#8220;fun&#8221;

A five year old Ubuntu install is still 1000 times more secure than a Windows machine.

You will still be able to get Firefox updates through Ubuntzilla, Chromium updates will still come in as well.

---

### Post by Simian Man on 2010-04-06
> **ubunterooster said:**
> !#!$!&#8251;!¢!
You might as well leave them running as root for further convienience. You must keep a low profile or eventually script kiddies *will* have “fun”

That's why I said "unless your computer is a public facing server".  For a typical home computer or private server you will be protected by a firewall anyway.

---

### Post by Chame_Wizard on 2010-04-07
You can safely upgrade the distro.:lolflag:

---

### Post by ShadeS_07 on 2010-04-07
Wow, thank you very much for all of you... ^^

I appreciate all your tips and advises, I feel grateful for you who have helped... :popcorn:

Uhmmm, 6 months? What will happen if I upgrade my distro the moment that the official release of a newer distro has come? Exempli gratia, Kubuntu v10.04 LTS; Its release date will be on April 29, 2010... If I upgrade my distro on April 30, 2010 or maybe on May 2 or 3, 2010, what could be the difference actually? What do you mean "to be safe", **ubunterooster**?

Oh, and uhmmm, are you familiar with Knoppix? Will it be like using Knoppix on 2017 (way past the Lucid Lynx's EOL), if I'm still using Lucid Lynx on that time (2017)? No updates, just like, Knoppix?

---

### Post by ubunterooster on 2010-04-07
> **ShadeS_07 said:**
>  Uhmmm, 6 months? What will happen if I upgrade my distro the moment that the official release of a newer distro has come? Exepli gratia, Kubuntu v10.04 LTS; It's release date will be on April 29, 2010... If I upgrade my distro on April 30, 2010 or maybe on May 2 or 3, 2010, what could be the difference actually? What do you mean "to be safe", **ubunterooster**?  It is best to stick with LTSs, but wait six months after its release before upgrading to it so bugs can be worked out. 

>  Are you familiar with Knoppix? Will it be like using Knoppix on 2017 (way past the Lucid Lynx's EOL), if I'm still using Lucid Lynx on that time (2017)? No updates, just like Knoppix?

Knoppix was the first distro I liked. Yes, like Knoppix, end-of-life versions of Ubuntu do not give updates. (keep in mind that Knoppix is pretty much a one-man project of Knopper)

---

### Post by ShadeS_07 on 2010-04-07
> Knoppix was the first distro I liked. Yes, like Knoppix, end-of-life versions of Ubuntu do not give updates. (keep in mind that Knoppix is pretty much a one-man project of Knopper)

Cool, it's also the first distro I liked... I've been still using it for making system repairs, and the like... I also use SystemRescueCD, pretty handy too... ^^

And thanks again dude... By the way, when you upgrade your distro to Lucid Lynx, will you be sticking with this LTS distro? Or, you'd still upgrade when 10.10 comes out?

And uhmmm, is there a way to skip distro upgrades? Say, from 8.10 to 10.04?

Thanks again... God bless all...


~ShadeS_07,, -_+ :popcorn:

---

### Post by ubunterooster on 2010-04-07
I am not going to stay with regular releases. 6 months is way too often. LTSs or debian are coming to my computers.

Go to update manager. click settings. under the updates tab click the "release upgrades" drop-down menu. choose "long term support releases only"

 May God bless you also

---

### Post by wcutrombonekid on 2010-04-07
> **ubunterooster said:**
> !#!$!&#8251;!¢!
You might as well leave them running as root for further convienience. You must keep a low profile or eventually script kiddies *will* have “fun”

tee hee, that made me lol

---

### Post by ubunterooster on 2010-04-07
[quote=waynefoutz] a 5 yr old Ubuntu system... [/quote] not going to disagree, my father got himself hacked several times with MS's OS.

---

### Post by ShadeS_07 on 2010-04-07
[QUOTE=ubunterooster]I am not going to stay with regular releases. 6 months is way too often. LTSs or debian are coming to my computers.

Go to update manager. click settings. under the updates tab click the "release upgrades" drop-down menu. choose "long term support releases only"

May God bless you also[/QUOTE]

Okay dude, thanks again... I'll try it on my Adept Update Manager :popcorn:

---

### Post by TheKhaos24 on 2010-04-07
I would say I'm not to sure, because sometimes it is better to upgrade such as Windows7 for example. But I have to say 10.04 is worth it.

---

### Post by haddog on 2010-04-07
> **ubunterooster said:**
> I am not going to stay with regular releases. 6 months is way too often. LTSs or debian are coming to my computers.

Go to update manager. click settings. under the updates tab click the "release upgrades" drop-down menu. choose "long term support releases only"

 May God bless you also

6 months is too often if you are using as a production/work computer. I agree in using the LTS's for stability.

---

### Post by Ciarán McCann on 2010-04-07
> **tekkidd said:**
> im running 9.04 and im not planning to upgrade to 10.04 after it releases

Same, my 9.04 work perfectly for me. No risking an update and also don't like this new position of the window controls so not upgrading.

---

### Post by blueridgedog on 2010-04-07
There are two additional arguments for updating - that of getting new application releases and for moving on to newer kernels.  The updates you get are for security reasons, not functionality reasons.  Newer kernels also have better support for newer hardware. 

In the end it is your choice and there in no wrong choice.  Use what works, what satisfies you and what makes you happy.

---

