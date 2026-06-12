---
title: "Open Source Skype?"
date: 2012-09-07
forum: General Help
---

### Post by PremiumG on 2012-09-07
I recently just read this: [http://www.linuxbsdos.com/2012/08/01/one-more-reason-to-not-use-skype-for-linux/]("http://www.linuxbsdos.com/2012/08/01/one-more-reason-to-not-use-skype-for-linux/") and I was wondering if there were any open-source versions/alternatives to skype? Here is the kicker... the alternative must be able to video call others who are using skype on their pc. 

I am very new to linux (OH GOD! WHAT DO I DO IN TERMINAL?) and am using the latest 64-bit Lubuntu on my old dell craptop.

---

### Post by Kopkins on 2012-09-07
Currently there are no alternatives that can interact with skype video.

Also, that article is pretty bad. It is very unhelpful and the only purpose I see in it is to bash MicroSoft. It suggests using alternatives, but doesn't offer any. If you are making video calls then you have nothing to be worried about (probably in other cases too). There is no way that they will monitor video calls with people. It's not practical. 

The cool thing about open source is that it is free, and anyone can change it, you've heard the spiel. The downside is that there aren't always practical open-source alternatives to closed-source programs. 

As I see that you are new to Linux, I'm guessing that is to open-source as well. I'm sure you're all pumped up about using open-source only software. I know I was when I first started. But I've come to decide that it is worthwhile to use some closed-source programs, because practical alternatives aren't available. On my system I use Skype and Spotify. Those are the only closed-source programs that I am aware of. But good alternatives don't exist for them.

Best of luck with Linux. It's a great boat to be in. I can't see myself going back. But for now, I would say just use skype. 

Googletalk would work, but I've never used it, I'm not sure of it's capabilities.

Kopkins

---

### Post by kostkon on 2012-09-07
> **PremiumG said:**
> Here is the kicker... the alternative must be able to video call others who are using skype on their pc.
Not possible, sorry. 

Although, there was an effort to reverse engineer Skype, but according to Phoronix, it's now dead. Check [the article]("http://www.phoronix.com/scan.php?page=news_item&px=MTA2ODI").

Google talk is a good alternative though. Easy to setup in Ubuntu and Windows (or Mac).

---

### Post by Lars Noodén on 2012-09-07
There are good alternatives to Skype that use SIP instead of Skype's proprietary protocol.  Jitsi, Ekiga and Blink can all talk with each other since they all use the open standard, SIP.  Of those, only Ekiga is in the repository, but both Blink and Jitsi are available for Linux from their respective project sites.  You'll need an SIP account to use them but those are available for free from many sources.

---

### Post by TenPlus1 on 2012-09-07
If you are looking for a simple voice chat kinda like maknig an online phone call then Mutter is available on all platforms and is a really good program with some nifty features...

If you need video then google voice and video may be useful and since it's built into most open-source chat programs like Pidgin it's easy to setup and use also...

---

### Post by rockstarrem on 2012-09-07
> **Kopkins said:**
> Also, that article is pretty bad. It is very unhelpful and the only purpose I see in it is to bash MicroSoft. It suggests using alternatives, but doesn't offer any. If you are making video calls then you have nothing to be worried about (probably in other cases too). There is no way that they will monitor video calls with people. It's not practical. 

I went ahead and skimmed through the article and I have to disagree with you here. People use Skype to chat through IM all of the time. And, even on the extreme off chance they record every voice/video call, it's worrisome that they just hand these over, don't you think?

---

### Post by PremiumG on 2012-09-10
> **rockstarrem said:**
> I went ahead and skimmed through the article and I have to disagree with you here. People use Skype to chat through IM all of the time. And, even on the extreme off chance they record every voice/video call, it's worrisome that they just hand these over, don't you think?

Very true; however, as a philosophically driven visionary, I must have only open source options at my disposal. Ideally, and obviously circumstantially, a video-chat program that is open source, that can connect with people who do you skype.

---

### Post by d3v1150m471c on 2012-09-10
audio/video can be handled using pipes and correct tools
```

# examples of using the sox audio suite
# write audio input to stdout
rec -traw -r48000 -c2 -esigned-integer -b16 -

# play audio from stdin
play -traw -r48000 -c2 -esigned-integer -b16 -

```

using sox or similar tools, and some networking tools like ucspi-tcp, socat, netcat,
you should be able to come up with a clever wrapper for voip. if you're concerned about anonymity, you can try piping tcp through tor to a hidden service. also, exists options
of passing the data through an encryption.

```

#short sweet voip using socat

#server/recv
socat tcp4-listen:9876,bind=192.168.1.2, stdio |\
  play -traw -r48000 -c2 -esigned-integer -b16 -

#client/send
rec -traw -r48000 -c2 -esigned-integer -b16 - |\
  socat stdio, tcp4-connect:192.168.1.2:9876

```

---

