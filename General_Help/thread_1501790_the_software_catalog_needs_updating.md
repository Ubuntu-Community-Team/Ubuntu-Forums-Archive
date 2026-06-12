---
title: "the software catalog needs updating"
date: 2010-06-04
forum: General Help
---

### Post by pizza-is-good on 2010-06-04
Hi there. The bug has already been reported, but I can't seem to find a way to work around it.

Here is the problem:

The Ubuntu Software center will not allow me to install some applications. The install button is just gone. When I click 'more info' it says that the software catalog needs updating. See the screenshot.

I have looked around, and I have not been able to find how to update the software catalog. I made sure that I have all of of the software sources enabled (main, universe, restricted and multiverse) I also reloaded the package info in synaptic.

Running 10.04 64bit. (BTW, problem is also happening in 32bit PCs)

Any ideas?

---

### Post by James78 on 2010-06-04
If you can find the settings for that application in your $HOME, and delete them, it should reset it and it might work around the problem for now. I'd just use Synaptic though. :-)

---

### Post by wilee-nilee on 2010-06-04
The software center is pretty, but full of inherent problems. If you use synaptic or the terminal you will see dependencies that may be missing or that you are actually removing some core programs that will leave you in a desperate situation. I wouldn't touch that software center with a 100 foot pole and I'm experienced enough to know whats going on generally.

---

### Post by pizza-is-good on 2010-06-04
To James78:

Not sure what you mean, since the application is not installed, but rather, I am trying to install it.

---

### Post by James78 on 2010-06-04
I was saying, find the settings for the Ubuntu software catalog program in your $HOME, and delete them. It might work around the issue for you.

> **wilee-nilee said:**
> The software center is pretty, but full of inherent problems. If you use synaptic or the terminal you will see dependencies that may be missing or that you are actually removing some core programs that will leave you in a desperate situation. I wouldn't touch that software center with a 100 foot pole and I'm experienced enough to know whats going on generally.
Lol ya.

---

### Post by pizza-is-good on 2010-06-04
> **wilee-nilee said:**
> The software center is pretty, but full of inherent problems. If you use synaptic or the terminal you will see dependencies that may be missing or that you are actually removing some core programs that will leave you in a desperate situation. I wouldn't touch that software center with a 100 foot pole and I'm experienced enough to know whats going on generally.

OK, I'm not an expert, so please help me out here.

If I for example, want to intsall the Lighting Extentions for thunderbird from the screenshot in the original post, what would I do?

I looked for it in synaptic and can't find it, and Thunderbird won't find it either. So what now?

I imagine that ```
sudo apt-get install lighting-extensions-for-thunderbird
```won't do it, especially since I don't know what the package name is...

---

### Post by pizza-is-good on 2010-06-04
> **James78 said:**
> I was saying, find the settings for the Ubuntu software catalog program in your $HOME, and delete them. It might work around the issue for you.


Lol ya.

Ahh, now I get you...

---

### Post by James78 on 2010-06-04
> **pizza-is-good said:**
> OK, I'm not an expert, so please help me out here.

If I for example, want to intsall the Lighting Extentions for thunderbird from the screenshot in the original post, what would I do?

I looked for it in synaptic and can't find it, and Thunderbird won't find it either. So what now?

I imagine that ```
sudo apt-get install lighting-extensions-for-thunderbird
```won't do it, especially since I don't know what the package name is...

Only a few addons for Mozilla/Thunderbird are actually in the repositories. Anyways, I wouldn't trust installing the addons from there, because when the addons get updated in real life, and they do often, you'd have to wait for the repository to update them, but if you install them from the correct source (Thunderbird addons, you can Google it, or go [here]("https://addons.mozilla.org/en-US/thunderbird/")), they're updated whenever they need to be.

You can go there in your browser and download the xpi file, and install it in Thunderbird. I forgot the exact process for doing so, but you can probably just open the xpi with Thunderbird and it'll ask to install it. There might also be an inbuilt addon search in Thunderbird, like in Firefox, I'd look for that.

Bottom line, you should install it "officially", unless it's something like ubufox, which can only be found in the repository I think.

---

### Post by pizza-is-good on 2010-06-04
OK, thanks for that. Good point.

---

### Post by wilee-nilee on 2010-06-04
It seems james78 has you on the right track to get the software center working correctly. here is a link to the Mozilla project for reference.
[http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)

I would stick with the Ubuntu modified version if you using thunderbird from the software center.

Your correct it isn't in my synaptic in Lucid, for me that would along with it being a beta release would make me shy away from it, but it may be a fine setup.

---

### Post by zicoe on 2010-09-06
Hey, I'm trying to migrate from ms windows to ubuntu and facing the very same problem as pizza-is-good, but i still can't solve it, i'm using ubuntu 10.04  32-bit. can sombody help me please?

---

### Post by pizza-is-good on 2010-09-06
> **zicoe said:**
> Hey, I'm trying to migrate from ms windows to ubuntu and facing the very same problem as pizza-is-good, but i still can't solve it, i'm using ubuntu 10.04  32-bit. can sombody help me please?

Are you trying to install the same thunderbird extensions, or does your software catalog need updating?

---

