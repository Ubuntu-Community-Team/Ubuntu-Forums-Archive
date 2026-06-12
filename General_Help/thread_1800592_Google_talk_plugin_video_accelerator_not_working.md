---
title: "Google talk plugin video accelerator not working"
date: 2011-07-09
forum: General Help
---

### Post by knutschr on 2011-07-09
I have installed Google talk plugin video accelerator using
```
 sudo dpkg -i google-talkplugin_current_i386

``` as Software center can't install it.
Installation was fine,but when I open it (Hangout in Google+), it tries to start (Messaging Just a minute) but after a couple of seconds I get the yellow line in top of browser telling that the plugin has stopped working.
This happens in Chrome as well as in Firefox. 
Is there a way I can fix this?

---

### Post by pqwoerituytrueiwoq on 2011-07-09
just to make you are using 32bit ubuntu (the package you installed was 32 bit)
what does [FONT=Courier New]uname -m[/FONT] give you

---

### Post by mikewhatever on 2011-07-09
Google-talk plugin has never worked on my netbook with the built in webcam. Probably never will. Oddly enough, it works with a crappy old external USB cam.

---

### Post by knutschr on 2011-07-09
```
knuts@knuts-Aspire-5810T:~$  uname -m 
i686

```

---

### Post by pqwoerituytrueiwoq on 2011-07-09
> **knutschr said:**
> ```
knuts@knuts-Aspire-5810T:~$  uname -m 
i686

```
you have the correct version
i have never used the video since i don't have a web cam or fast enough Internet to use it
hell i can even do voice worth a crap with my internet's sh** upload 160 Kbps
but my voice breaks up on the other end

---

### Post by knutschr on 2011-07-10
[bump]

---

### Post by knutschr on 2011-07-10
I dualbooted to Windows and tried there.
Same resault, so it must be the plugin not recognising my inbuilt webcam (CNF113)
Cheese and guvcview (in linux) have no problems!

---

### Post by edm1 on 2011-07-12
> **pqwoerituytrueiwoq said:**
> hell i can even do voice worth a crap with my internet's sh** upload 160 Kbps

despite having a fairly fast connection google audio chat only uses about 10 kbps upload for me. having said that, video chat rarely works for me. i just get a black screen.

---

### Post by embrodak on 2011-07-20
I'm having the same issue and it's driving me absolutely nuts every time my friends hang out and I can't. Normal gtalk works fine (through gchat). I'm suffering so much I can't stop eating random electronics. Please help before I die from an impacted bowel.

---

### Post by no2498 on 2011-07-21
look in system, preferences, sound
see if the mic has a tic mark 
mine was blank

---

### Post by embrodak on 2011-07-27
If this helps, ~/.config/google-googletalkplugin/gtbplugin.log :

> 
[000:010] Warning(clientchannel.cc:560): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:011] Warning(clientchannel.cc:403): Could not initiate GoogleTalkPlugin connection
[000:011] Warning(optionsfile.cc:22): Load: Could not open file
[000:011] Warning(clientchannel.cc:530): Failed to get GoogleTalkPlugin path. Trying default.


Whenever I try to start a hangout or verify settings the camera shows a sad dead puzzle piece and the yellow strip saying the google talk video accelerator plugin crashed appears at the top of the browser.

Out of stress, I have already consumed two power supplies, an FTIR spectrometer, and a 30-foot powered USB cable. Please help before the tesla coil I'm currently gnawing on kills me.

---

### Post by balduin on 2012-01-15
Using [FONT="Courier New"]google-talkplugin_amd64[/FONT] on oneiric failed for me, although it worked in the past. I tried several browsers, among them Google Chrome, Chromium, Firefox and Opera. When I started [FONT="Courier New"]chromium-browser[/FONT] via a terminal window, I got the following error message every few seconds once I tried to start a Hangout in Google+ or a video based chat session in Google Mail: 

```
[476:069] Waiting for GoogleTalkPlugin to start...
[477:071] Warning(clientchannel.cc:525): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[477:072] Warning(clientchannel.cc:380): Could not initiate GoogleTalkPlugin connection
[477:072] Waiting for GoogleTalkPlugin to start...
[478:074] Warning(clientchannel.cc:525): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[478:075] Warning(clientchannel.cc:380): Could not initiate GoogleTalkPlugin connection
[478:075] Waiting for GoogleTalkPlugin to start...
[479:076] Warning(clientchannel.cc:525): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[479:077] Warning(clientchannel.cc:380): Could not initiate GoogleTalkPlugin connection
[479:077] Waiting for GoogleTalkPlugin to start...
[480:079] Warning(clientchannel.cc:525): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[480:079] Warning(clientchannel.cc:380): Could not initiate GoogleTalkPlugin connection
[480:079] Waiting for GoogleTalkPlugin to start...
[481:081] Warning(clientchannel.cc:525): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[481:082] Warning(clientchannel.cc:380): Could not initiate GoogleTalkPlugin connection

```

The solution was to install a missing package: [FONT="Courier New"]libv4l-0:i386[/FONT] Everything went smoothly from there on.

---

