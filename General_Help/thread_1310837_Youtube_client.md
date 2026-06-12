---
title: "Youtube client"
date: 2009-11-02
forum: General Help
---

### Post by JugglinPhil on 2009-11-02
Anybody know of any youtube clients like minitube, only for 64? From what I found out minitube is only 32.

---

### Post by loell on 2009-11-02
will totem do? it has a youtube viewer. both works on 32 and 64.

---

### Post by JugglinPhil on 2009-11-02
Thanks I'll try it

---

### Post by P4man on 2009-11-02
Minitube should work on 64 bit as well.
If you're using karmic get it from this ppa:
[https://launchpad.net/~neversfelde/+archive/ppa/+packages](https://launchpad.net/~neversfelde/+archive/ppa/+packages)

For jaunty its available on getdeb:
[http://www.getdeb.net/app/Minitube](http://www.getdeb.net/app/Minitube)

---

### Post by JugglinPhil on 2009-11-02
Okay now I know that totem is what's called Movie Player under apps, sound & video (getting some new insight everyday), but i'm not quite sure about how to watch youtube videos in there. The plugin is enabled. I need this because in 9.10 I've got some weird issues with flash, which makes watching youtube on the site itself a disaster.
Thanks :)

---

### Post by JugglinPhil on 2009-11-02
> **P4man said:**
> Minitube should work on 64 bit as well.
If you're using karmic get it from this ppa:
[https://launchpad.net/~neversfelde/+archive/ppa/+packages]("https://launchpad.net/%7Eneversfelde/+archive/ppa/+packages")

For jaunty its available on getdeb:
[http://www.getdeb.net/app/Minitube](http://www.getdeb.net/app/Minitube)
Thank you, looks like I got lost there.. ^^ Can you do me a favor and help me with that ppa thingy? I've tried it before and it was an epic fail... (not ppa, but my lack of knowledge)

---

### Post by JugglinPhil on 2009-11-02
Okay never mind I made it. :)
However Minitube doesn't let me watch anything, I get the video titles and everything but the only control I can use is stop, which brings me back to the search function again... Also on the screen where I believe the video is supposed to run it only shows the video description.

---

### Post by P4man on 2009-11-02
> **JugglinPhil said:**
> Okay never mind I made it. :)
However Minitube doesn't let me watch anything, I get the video titles and everything but the only control I can use is stop, which brings me back to the search function again... Also on the screen where I believe the video is supposed to run it only shows the video description.


try this:
```
sudo apt-get install phonon-backend-gstreamer
```

then try again. Worked for me.

---

### Post by kiking74 on 2009-11-02
Can anybody help me.... When I first installed ubuntu 9.04 Jackalone on my laptop, it was very annoying... first the graphic cards seems not compatible with the new OS. I tried to upgrade and everything went well... However, during the process, I got hold with "No Network found" and I panic. The network that used is a unsecured one. Plz help to fix the problem... Now I am running windows xp as I installed the ubuntu dual booting with xp.

Computer spec:
Acer Aspire 4530; AMD Turion X2; NVIDIA GeFoce 9100M G; 160GB HDD Sata; Atheros AR5007EG; ACPI Multiprocessor PC (but still using IDE):(:(:(

---

### Post by JugglinPhil on 2009-11-02
> **kiking74 said:**
> Can anybody help me.... When I first installed ubuntu 9.04 Jackalone on my laptop, it was very annoying... first the graphic cards seems not compatible with the new OS. I tried to upgrade and everything went well... However, during the process, I got hold with "No Network found" and I panic. The network that used is a unsecured one. Plz help to fix the problem... Now I am running windows xp as I installed the ubuntu dual booting with xp.

Computer spec:
Acer Aspire 4530; AMD Turion X2; NVIDIA GeFoce 9100M G; 160GB HDD Sata; Atheros AR5007EG; ACPI Multiprocessor PC (but still using IDE):(:(:(
Hi there, I think you should start a new thread with your question and I'm sure you'll get help there. :)

---

### Post by JugglinPhil on 2009-11-02
> **P4man said:**
> try this:
```
sudo apt-get install phonon-backend-gstreamer
```then try again. Worked for me.
Thanks, now it tells me: 'A required codec is missing. You need to install the following codec(s) to play this content: H.264'
How do I install it and what is it?

---

### Post by P4man on 2009-11-02
> **JugglinPhil said:**
> Thanks, now it tells me: 'A required codec is missing. You need to install the following codec(s) to play this content: H.264'
How do I install it and what is it?

Its a codec..:)
I guess you dont have the restricted extra's installed yet?
Go to system > administration > software sources. Make sure restricted and multiverse ("software restrcited by copyright etc..") are checked. Click close and let it reload the sources if it asks to.

Then install it with

```
 sudo apt-get install ubuntu-restricted-extras
```

Or through ubuntu software center or synaptic or whatever you prefer.

It think that should install all codecs needed.

---

### Post by JugglinPhil on 2009-11-02
Awesome thanks, works without any problems. :D

---

### Post by P4man on 2009-11-02
> **JugglinPhil said:**
> Awesome thanks, works without any problems. :D

great :)
dont forget to mark this thread SOLVED in thread tools.

---

### Post by JugglinPhil on 2009-11-02
> **P4man said:**
> great :)
dont forget to mark this thread SOLVED in thread tools.
done :)

---

