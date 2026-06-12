---
title: "Master Volume + PulseAudio"
date: 2009-11-23
forum: General Help
---

### Post by Tumpster on 2009-11-23
First off, lets count me as one of the folks who's not thrilled by pulse audio. I just recently had some hardware issues that forced me to whipe my hard drive and load up a fresh installation of 9.10 and I'm thrilled by all the advancements in the last 3 versions. However my problem is that PulseAudio doesn't provide true 5.1 to my surround sounds as I was able to do with Alsa in Hardy. What can I do to fix this and get 5.1 working properly. Second question is how can I have a master volume that controls everything instead of always having to open sound preferences and adjusting for the individual programs? Shouldn't master volume be just that? The master over all programs volume?

Also, I run a these Logitech Speakers
[http://www.amazon.com/Logitech-Z-640-Speaker-Surround-System/dp/B00006HYPD/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989913&sr=8-1](http://www.amazon.com/Logitech-Z-640-Speaker-Surround-System/dp/B00006HYPD/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989913&sr=8-1)

And this sound card:
[http://www.amazon.com/Creative-Sound-Blaster-Live-Digital/dp/B0000AKGPB/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989943&sr=1-1](http://www.amazon.com/Creative-Sound-Blaster-Live-Digital/dp/B0000AKGPB/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989943&sr=1-1)

---

### Post by Tumpster on 2009-11-23
Bump!

---

### Post by alexfish on 2009-11-23
> **Tumpster said:**
> First off, lets count me as one of the folks who's not thrilled by pulse audio. I just recently had some hardware issues that forced me to whipe my hard drive and load up a fresh installation of 9.10 and I'm thrilled by all the advancements in the last 3 versions. However my problem is that PulseAudio doesn't provide true 5.1 to my surround sounds as I was able to do with Alsa in Hardy. What can I do to fix this and get 5.1 working properly. Second question is how can I have a master volume that controls everything instead of always having to open sound preferences and adjusting for the individual programs? Shouldn't master volume be just that? The master over all programs volume?

Also, I run a these Logitech Speakers
[http://www.amazon.com/Logitech-Z-640-Speaker-Surround-System/dp/B00006HYPD/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989913&sr=8-1](http://www.amazon.com/Logitech-Z-640-Speaker-Surround-System/dp/B00006HYPD/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989913&sr=8-1)

And this sound card:
[http://www.amazon.com/Creative-Sound-Blaster-Live-Digital/dp/B0000AKGPB/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989943&sr=1-1](http://www.amazon.com/Creative-Sound-Blaster-Live-Digital/dp/B0000AKGPB/ref=sr_1_1?ie=UTF8&s=electronics&qid=1258989943&sr=1-1)

 pulse needs to be set 
  if you have aready done this please excuse

  link for setting up pulse take note of padevchooser

  this gives access to the info you may need

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

if pulse is set up 
sometimes the chanels have to be set in the


/etc/pulse/daemon.conf file

---

### Post by alexfish on 2009-11-24
also found link for info about the card have a look and see what you think

[http://www.mail-archive.com/linux-hardware@senator-bedfellow.mit.edu/msg04332.html](http://www.mail-archive.com/linux-hardware@senator-bedfellow.mit.edu/msg04332.html)

---

### Post by Tumpster on 2009-11-28
> **alexfish said:**
> also found link for info about the card have a look and see what you think

[http://www.mail-archive.com/linux-hardware@senator-bedfellow.mit.edu/msg04332.html](http://www.mail-archive.com/linux-hardware@senator-bedfellow.mit.edu/msg04332.html)


Thank you for the info, but this did not work, though it did point out for me to edit the dameon config file on my rig. Does anyone run 9.10 and have full 5.1 working through their speakers?

---

### Post by alexfish on 2009-12-01
> **Tumpster said:**
> Thank you for the info, but this did not work, though it did point out for me to edit the dameon config file on my rig. Does anyone run 9.10 and have full 5.1 working through their speakers? 

Hi 
  
 I will be back soon with links on how to do this

   in the mean time could you post  details of default player and your system 

     if you have not already done so     I  recomend  installing vlc   latest version
        
         best from synaptic 

       vlc will help to debug , from your desktop

thanks in advance

Regards
  
   alexfish

did a post here look at the basics and come back here
to go through the basics
  

[http://ubuntuforums.org/showthread.php?t=1327684&page=3](http://ubuntuforums.org/showthread.php?t=1327684&page=3)

---

