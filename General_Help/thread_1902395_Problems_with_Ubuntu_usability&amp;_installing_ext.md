---
title: "Problems with Ubuntu usability&amp; installing external software"
date: 2011-12-30
forum: General Help
---

### Post by 0011235813 on 2011-12-30
Hello forum, I am a recent Ubuntu convert. I have been greatly pleased by Ubuntu speed,security,looks,software etc. etc. BUT, I do have one problem.  THE OBSCURITIES OF THE PENGUIN Yes, I can't seem to be able to install downloaded applications. The only thing I managed to get to work was TrueCrypt. I have tried to install storybox, teamspeak and Avast! In all cases, I was unable to do so. I'm quite certain the applications are compatible with Ubuntu 11.10 64-bit. I have tried to open them with mono runtime and openJDK Java Runtime Environment. I always get something along the lines of this: [see first attachment]. OpenJDK doesn't even startup. Is there anything I'm doing wrong? Or are the applications just bull$hit?

---

### Post by MG&amp;TL on 2011-12-30
Teamspeak I have working perfectly, it's just a bit weird install, if you want the latest.

Why do you need avast?

Sorry, never heard of storybox.

You can get teamspeak in the repos, 

```
sudo apt-get install teamspeak-client
```

---

### Post by 0011235813 on 2011-12-30
> **MG&TL said:**
> Teamspeak I have working perfectly, it's just a bit weird install, if you want the latest.

Why do you need avast?

Sorry, never heard of storybox.

You can get teamspeak in the repos, 

```
sudo apt-get install teamspeak-client
```

I don't really need Avast! But then, I'm paranoid as hell, that's why I have NoScript,Adblock Plus,WOT,BetterPrivacy,Spamavert,URL checker,FoxyProxy (though I'm not sure if I need it with tor running in the background), and the add-ons for thunderbird, and firewall, and clamscan, and ```
sudo visudo
```.... Storybox is supposed to be some sort of novel writing software. I honestly didn't know that! Thanks! Though it's strange, why is it so difficult to install software outside the repos? We're not like closed-garden Apple now are we??

---

### Post by MG&amp;TL on 2011-12-30
> **0011235813 said:**
> Though it's strange, why is it so difficult to install software outside the repos? We're not like closed-garden Apple now are we??

nope, but software installation is a pain in itself. Read up on debian packaging and you'll find out why. And nobody cares about linux. I take it you've never had to do an autoconf install?

---

### Post by 0011235813 on 2011-12-31
> **MG&TL said:**
> nope, but software installation is a pain in itself. Read up on debian packaging and you'll find out why. And nobody cares about linux. I take it you've never had to do an autoconf install?

No I never had to do an autoconf install.  I'm thankful we have the repositories though, I don't think Linux would be much use without them LOL.

---

### Post by Paqman on 2011-12-31
> **0011235813 said:**
> Thanks! Though it's strange, why is it so difficult to install software outside the repos? We're not like closed-garden Apple now are we??

It's only difficult for software that nobody can be bothered to package properly.

Some software is available through PPAs (Personal Package Archives). A PPA can be added to your system, and will provide access to all the software in it through the normal tools like Software Centre. Some companies like Google and Oracle also provide their own repos for packages like Chrome and Virtualbox.

Apart from all that, what you want to find is a .deb package, which can be downloaded and installed with a click. Anything else is IMO too much of a hassle. You can pretty much always find a proper Ubuntu package for most types of software without messing about with nasty tarballs.

---

### Post by 0011235813 on 2011-12-31
> **Paqman said:**
> It's only difficult for software that nobody can be bothered to package properly.

Some software is available through PPAs (Personal Package Archives). A PPA can be added to your system, and will provide access to all the software in it through the normal tools like Software Centre. Some companies like Google and Oracle also provide their own repos for packages like Chrome and Virtualbox.

Apart from all that, what you want to find is a .deb package, which can be downloaded and installed with a click. Anything else is IMO too much of a hassle. You can pretty much always find a proper Ubuntu package for most types of software without messing about with nasty tarballs.

I agree, I hate having to go through half a dozen steps or more for a simple software installation. Well, I guess I just have to pay more attention to the file type I'm downloading.

---

