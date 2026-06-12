---
title: "Why doesn't any Ubuntu browser have Flash on it?"
date: 2012-03-13
forum: General Help
---

### Post by trifi34 on 2012-03-13
I noticed with Linux Mint (which is based off Ubuntu) has Flash already installed on any browser you download, but on Ubuntu (say, Google Chrome) it doesn't have Flash already on it. I'm sure it can't be that difficult to install, but it's better when it's already there. :confused:

---

### Post by PhantomTurtle on 2012-03-13
Thats because Linux Mint comes with the restricted extra's installed, Ubuntu does not due to legal reasons. In Ubuntu you have to install the restricted extra's package, which contains flash and other codecs. Then it will be available for all your browsers.

---

### Post by TBABill on 2012-03-13
If you install Google Chrome, flash is included in the browser. Firefox and Chromium uses flash installed into the OS, but Chrome carries its own. As stated above, Ubuntu does not include for legal reasons.

---

### Post by squilookle on 2012-03-13
It's not just Flash, there are several formats that are affected, included mp3 and encrypted DVD. Also, while a few distros (Mint, Crunchbang) include the restricted codecs, most of the mainstream distributions (Suse, Fedora, Ubuntu) do not. 

It has been an issue with Lunux for a long time, but most of the distributions have made it much easier to get the formats installed and working. 

More information [here]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by TBABill on 2012-03-13
> **trifi34 said:**
> I'm sure it can't be that difficult to install, but it's better when it's already there. :confused:It's as simple as opening a terminal and typing ```
sudo apt-get install ubuntu-restricted-extras
``` Or you can open Ubuntu software center and search for and install it.

---

### Post by 3Miro on 2012-03-13
In some countries, downloading Mint is illegal. Ubuntu is always legal.

Since Canonical is more susceptible to lawsuits (compared to a small community of people), Ubuntu pays more by the rules.

Install the restricted extras package from the software center and you will get flash and codecs.

---

### Post by grahammechanical on 2012-03-13
Canonical - that is its owner and its employees, believe in Open Source  programming.

So, they produce a distribution that is entirely open source but they also believe in Ubuntu being for Humans.

So, they make it easy for us to install non-open source (proprietary) software such as video card drivers and codecs. But only if it can be done legally.

Ubuntu is about to release a Ubuntu business remix. It will contain some proprietary software that is useful in the business environment. This is done so that there is no need for the user to install these programs after the installation of Ubuntu. But the user has to accept the End User License Agreement (EULA).

We have to do the same if we use the Software Centre to install Microsoft core fonts.

Some distributions do not offer proprietary software at all. So, if someone has ethical reasons for not using closed source progerams then they can still use Ubuntu but without the codecs.

This is why Ubuntu does not install these things as standard.

See this quote:

> Ubuntu makes a point of openness to heterogeneous environments. We celebrate the point that the Ubuntu desktop can be highly useful, beautiful, functional and complete **without any proprietary applications at all**, _while recognising that some people need to work with proprietary software on occasion_, making sure that software is available and certified for Ubuntu, and making it easy to install. Remixes can include non-free software and still retain the Ubuntu name, as long as they can be brought back to the standard Ubuntu experience with straightforward package management tools and no risk of divergence on the hardware and security front.

From here:

[http://www.markshuttleworth.com/archives/date/2012/02]("http://www.markshuttleworth.com/archives/date/2012/02")

See Remixing Ubuntu for the Enterprise Desktop

Regards.

---

### Post by trifi34 on 2012-03-13
Thanks for clearing that up guys :KS

---

