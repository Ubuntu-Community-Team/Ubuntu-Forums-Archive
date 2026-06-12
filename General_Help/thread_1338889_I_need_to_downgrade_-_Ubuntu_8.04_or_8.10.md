---
title: "I need to downgrade - Ubuntu 8.04 or 8.10?"
date: 2009-11-26
forum: General Help
---

### Post by sam191 on 2009-11-26
Hey everyone,

My ATI 9600 card is giving me a lot of trouble with Karmic, so I think I will install an older version of Ubuntu as a temporary setup until I get my new laptop. 

AMD has drivers for the card on their site, but they only support distros that were released prior to Feb. 2009. 

My question is, should I go back to 8.10 or 8.04? The reason I ask is because, well while they are both old, 8.04 has LTS. So I guess it's supported until the 10.04 (by which time I will have my laptop, hopefully). Am I better off with the newer distro, or the LTS one? 

Also, I was wondering what I'm losing from downgrading my distro? (Anything crucial, that would not allow me to program?)

Thanks in advance!

---

### Post by cariboo on 2009-11-26
It is unfortunate that ATI decided to stop supporting older video cards. WHat sort of problems are you running into?

In order to downgrade to an older version you will need to do a clean install.

Backup all your important data before doing the install, you will of course have to reinstall all the programs you use.

---

### Post by DeMus on 2009-11-26
> **sam191 said:**
> Hey everyone,

My ATI 9600 card is giving me a lot of trouble with Karmic, so I think I will install an older version of Ubuntu as a temporary setup until I get my new laptop. 

AMD has drivers for the card on their site, but they only support distros that were released prior to Feb. 2009. 

My question is, should I go back to 8.10 or 8.04? The reason I ask is because, well while they are both old, 8.04 has LTS. So I guess it's supported until the 10.04 (by which time I will have my laptop, hopefully). Am I better off with the newer distro, or the LTS one? 

Also, I was wondering what I'm losing from downgrading my distro? (Anything crucial, that would not allow me to program?)

Thanks in advance!

In that case I would suggest 8.04 LTS. It's rock stable.
Make a complete backup of all your data first, make sure you've got it all.
Then start a new installation of Hardy (8.04), make a separate partition for /home and copy your data to it.

It's terrible you have to do that because of a company who is not interested in Linux and therefore does not make the right drivers for their products.
Success.

---

### Post by sam191 on 2009-11-26
Yeah, tell me about it. 

I have my hard drive partitioned 3 ways, so I'm always backed up :D It worked fine until my Nvidia card decided to die on me. But no worries. I'm downloading 8.04LTS right now.

I used to be a big AMD fan too. My current rig is from 2005, with an AMD proc and everything. I'm looking at System76 for my replacement, I've heard good things about them. 

And thanks for the help!

---

### Post by sam191 on 2009-11-26
> **cariboo907 said:**
> It is unfortunate that ATI decided to stop supporting older video cards. WHat sort of problems are you running into?


Well, everything from video playback to graphics. I'm currently developing games, and need full graphics support from my VGA with things such as OpenGL (And I don't want to work on windows!). 

Also, will I encounter problems if I'm working with other people on newer distros? I'm guessing not, but you never know.

---

### Post by DeMus on 2009-11-26
> **sam191 said:**
> Well, everything from video playback to graphics. I'm currently developing games, and need full graphics support from my VGA with things such as OpenGL (And I don't want to work on windows!). 

Also, will I encounter problems if I'm working with other people on newer distros? I'm guessing not, but you never know.

That depends more on the versions of the programs you are using, not on the OS. But it's something you have to find out, can't say that from here.

---

### Post by MelDJ on 2009-11-26
i would say 8.04 too. the word LTS says it all

---

### Post by Dennis N on 2009-11-27
8.04 LTS is supported until April 2011, so that would be until 11.04 comes around. 8.10 goes end of life in April 2010. So support wise, 8.04 is the best choice between the two.

Reference:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

