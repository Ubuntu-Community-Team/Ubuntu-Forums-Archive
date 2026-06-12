---
title: "Triple screen - Intel + Nvidia?"
date: 2012-02-22
forum: General Help
---

### Post by Roasted on 2012-02-22
I just realized my onboard graphics card has Intel 3000 graphics. I'm running an Nvidia GT440. I began to wonder if I could power 2 monitors off of my 440 and use the onboard Intel for the 3rd monitor?

I also just now realized my main monitor also has HDMI input, and my graphics card has VGA, DVI, and HDMI. So at any rate, I could triple screen off of the Nvidia alone, right? Nonetheless, with Intel being open source drivers I began to wonder if I could use Intel + Nvidia to accomplish a seamless triple screen setup. Possible??

---

### Post by fcomstoc on 2012-02-22
Typically video cards share the HDMI and the DVI output so if you plug in monitors in the HDMI and DVI ports they will be the same output; so your card only supports 2 outputs VGA and HDMI/DVI. Most Mobos also disable integrated display ports if you have a video card installed. So I believe that if you want to have 3 displays you need another video card or replace the one you have with something that does support more than 2. I currently have 3 displays but I am running a MSI Frozr II HD 6950 OC that supports up to 4 monitors (1 DVI, 1 DVI/HDMI, 2 MDP)

---

### Post by Roasted on 2012-02-22
Thanks for your response. I do however have an Intel PCI graphics card. Could I mix and match Nvidia and Intel? Or would I be better off getting a low end Nvidia PCI? If I could use Intel though that would be great...

---

### Post by fcomstoc on 2012-02-22
To be honest with you I am not sure, I have never used different brand cards at the same time. My assumption is that I would work and allow you to have 2 on the Nvidia and one on the Intel but I am not sure. I think that getting another cheap Nvidia or a better one that supports 3 outputs would be better; but again I have never used mismatching brands so I am not 100% sure.

One thing I can tell you: don't buy an AMD(ATI)card their support on Linux SUCKS. I have spent many hours trying to get mine working right and I still have to boot Windows to run games on 3 monitors (3840x1024). I wish there was better support for Eyenfinity(AMD's monitor "extension" support) but that is not the case.

---

### Post by Roasted on 2012-02-22
Speaking of which, people have been telling me that chipsets like the AMD E-350 APU is awesome on Linux for HTPC setups and whatnot. People are citing that the open source drivers work great however avoid the proprietary drivers. Okay, fair enough. But I'm getting TERRIBLE playback with the open source driver... but that may be grounds for another thread...

---

### Post by fcomstoc on 2012-02-23
I personally have never used an open source driver, I have always been partial to the driver from the manufacturer. I figure if they made the card they should know how it works. 
I have never had real luck with any video card on Linux for that matter. They all pretty much work but anything beyond that is a crap-shoot. 
I have been a huge fan of Linux (esp Ubuntu) for a long time now, because there are issues with gaming, driver support, and other issues I have decided that all of my servers will run Linux and my Gaming machine has Windows and my Laptop has OSX Lion. That system just works better for me.

---

### Post by Roasted on 2012-02-23
I have very little issues with any of my systems, however I also run all Intel or Nvidia, which is definitely the safe ground as far as video cards go with Linux. AMD has been lacking substantially more as of lately which is a little disappointing. I'm just a little confused because a buddy told me he's running an HD 3200 with great 1080 playback, and here I am with an E350 APU which has an HD 6310 and it's terrible, yet we're both using the open source driver.

---

### Post by idoitprone on 2012-02-24
> **Roasted said:**
> I have very little issues with any of my systems, however I also run all Intel or Nvidia, which is definitely the safe ground as far as video cards go with Linux. AMD has been lacking substantially more as of lately which is a little disappointing. I'm just a little confused because a buddy told me he's running an HD 3200 with great 1080 playback, and here I am with an E350 APU which has an HD 6310 and it's terrible, yet we're both using the open source driver.

There is a simple rule with open source. Older cards are always better supported than newer cards. I belive HD 4000 and older are pretty decently well supported by now.

---

### Post by fcomstoc on 2012-02-24
> **Roasted said:**
> I have very little issues with any of my systems, however I also run all Intel or Nvidia, which is definitely the safe ground as far as video cards go with Linux. AMD has been lacking substantially more as of lately which is a little disappointing. I'm just a little confused because a buddy told me he's running an HD 3200 with great 1080 playback, and here I am with an E350 APU which has an HD 6310 and it's terrible, yet we're both using the open source driver.

Yeah, the only mistake I made when building this computer was putting a newer AMD (HD 6950) card in it. The support is terrible. The card somewhat works without the driver and when you install the driver and the program that runs with it it hardly works at all. The program (catalyst control center)  crashes constantly and the settings never get changed. Part of the issue is that I am running 3 screens but even with 1 it doesnt work right. I have pretty much given up on that as I use that computer for gaming. I wish that I could run Linux but I am not willing right now to spend $300+ on a new card just to do it. Plus gaming is just easier in Windows for the time being anyway.

---

### Post by Roasted on 2012-02-24
Well that's disappointing. All I was hearing was E-350 is great for HTPC and the open source driver does 1080 great etc etc... no, no no really at all... Gosh Nvidia and Intel are just so much more problem free... Maybe I'll have to return it and grab a mini ITX Intel board...

---

### Post by gordintoronto on 2012-02-24
> **idoitprone said:**
> There is a simple rule with open source. Older cards are always better supported than newer cards. I belive HD 4000 and older are pretty decently well supported by now.

It's true until the day they are no longer supported. In my experience, 10-year-old video cards are dicey.

---

### Post by gordintoronto on 2012-02-24
> **Roasted said:**
> I have very little issues with any of my systems, however I also run all Intel or Nvidia, which is definitely the safe ground as far as video cards go with Linux. AMD has been lacking substantially more as of lately which is a little disappointing. I'm just a little confused because a buddy told me he's running an HD 3200 with great 1080 playback, and here I am with an E350 APU which has an HD 6310 and it's terrible, yet we're both using the open source driver.

What version of Ubuntu? Have you tried Additional Drivers?

The E350 CPU is a little on the slow side, but it should be somewhat OK. Have you tried 720P?

---

