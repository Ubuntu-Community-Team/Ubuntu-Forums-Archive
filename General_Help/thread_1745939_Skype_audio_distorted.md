---
title: "Skype audio distorted"
date: 2011-05-01
forum: General Help
---

### Post by Martin_sensei on 2011-05-01
Hello,

I have just upgraded (clean install) from Ubuntu 10.10, where Skype was working fine, to Ubuntu 11.04.  

I have installed Skype 2.2 from the Natty partner repository, but the audio is terrible, very crackly and distorted.  All other audio is fine.

Does anyone know how to fix this?  I tried messing with the alsa-mixer but nothing changed.

---

### Post by timgood on 2011-05-01
I've found that opening pulse audio mixer and adjusting mic input volume solves the problem, temporarily. But next boot may result in similar. This is a real pain.

---

### Post by Martin_sensei on 2011-05-01
Adjusting the microphone makes no difference on my system. Anyone else?

---

### Post by Martin_sensei on 2011-05-02
I just discovered that opening PulseAudio Volume control, then changing the System sounds slider on the playback tab to 0, then playing a skype sound, then moving it back to where it was and playing another skype test sound temporarily fixes the problem.

I agree though, it is most annoying...

---

### Post by dante6913 on 2011-05-03
Hi,
This worked for me on ubuntu 11.04 [http://www.nbuntu.cz.cc/2011/04/distortion-of-sound-in-skype-22.html]("http://www.nbuntu.cz.cc/2011/04/distortion-of-sound-in-skype-22.html:o")

---

### Post by Martin_sensei on 2011-05-03
Could you check the link  please?

I get...

Page not found
Sorry, the page you were looking for in the blog News &amp; Tips about does not exist.

Thanks

---

### Post by Martin_sensei on 2011-05-03
I found it [http://www.nbuntu.cz.cc/2011/04/distortion-of-sound-in-skype-22.html]("http://www.nbuntu.cz.cc/2011/04/distortion-of-sound-in-skype-22.html").

However I now get no sound at all in Skype.

The article does suggest this will fix Skype for those who got the problem since the upgrade to 2.2.  I was using Skype 2.2 fine on Ubuntu 10.10.  This problem has started since the upgrade (clean) to Natty.

---

### Post by Martin_sensei on 2011-05-03
Update:

It looks like a problem with my sound card, as I switched cards, and it works perfectly now!

The card which doesn't work is a Creative Labs Sound Blaster Audigy2 ZS.

I guess I could stick with the on-board sound for now...

Does anyone have a create labs sound card that works with Skype 2.2 on Ubuntu 11.04?  

Are there better drivers I can get from anywhere?

Cheers

---

### Post by dante6913 on 2011-05-03
I have skype working with a fresh installation of ubuntu 11.04 following the link guide.
update, when i restarted ubuntu i lost the sound so it doesn't work

---

### Post by Martin_sensei on 2011-05-03
You didn't try the fix in the post above did you?  That stopped my sound from working.

Have you checked your pulse audio settings all look OK, and maybe disallowed skype from adjusting the system sound?

---

### Post by dante6913 on 2011-05-03
well, if i do a test call, skype after that goes ok. This is getting more strange.

---

### Post by LucioC on 2011-05-05
I found the old version of skype (2.1.0.81) on the typical filehosters. The new version was hardly changed compared to its predecessor, so you won't even recognize it. I don't think Skype will work hard now on the little Linux version to fix this bug. Maybe in two years we have a new version with no "improved sound quality" anymore

---

### Post by Martin_sensei on 2011-05-05
It's strange that it was all working in Ubuntu 10.10 then stopped working on Ubuntu 11.04 though...

---

### Post by rwsmith61 on 2011-05-05
> **Martin_sensei said:**
> It's strange that it was all working in Ubuntu 10.10 then stopped working on Ubuntu 11.04 though...

Yes, something changed in 11.04 that breaks the audio in Skype. In my case I use the onboard audio (I have an ASUS P8P67) but use the mic in the Logitech Orb cam. There is also about a 1 sec delay in the audio and it is somewhat distorted. I can however run Skype in a VM XP Guest without any problems (Skype won't install under Wine).

Given how little development Skype does with Linux I don't expect them to release an update any time soon.

I'll try to de-install Skype and re-install it tonight to see if that helps and post backc my results.

Bob
--bs

---

### Post by Martin_sensei on 2011-05-07
Did you try any of the fixes mentioned earlier in this thread?  It seems some people have had success using the .asoundrc file for example.

I am almost certain my problem is a soundblaster problem though.

---

### Post by amanetta on 2011-05-09
me too...I've problem with skype's sound and problem in sending my voice...really orrible the combination skype/natty till now...

---

### Post by dante6913 on 2011-05-18
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/751265](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/751265) 
#23 solved my problem.
I think that will work on everyone that has a Intel hda

---

### Post by timgood on 2011-05-18
There is a bug in ia32libs causing distortion on 64bit systems. It can be fixed by: 
```
cd /usr/lib32
sudo chmod ugo-r libpulse.so.0.12.2
sudo chmod ugo-r libpulse-simple.so.0.0.3
```

Works for me and I hope it works for you.

---

### Post by BetaguyGZT on 2011-06-10
Martin_sensei, thanks for the link you fixed on the first page of this thread (and therefore, thanks dante6913 for finding the fix in the first place!). My Skype is working perfectly again on my Audigy 2 ZS Platinum.

I was getting worried, hehe.

---

### Post by ZeroFossilFuel on 2011-07-23
> **Martin_sensei said:**
> Did you try any of the fixes mentioned earlier in this thread?  It seems some people have had success using the .asoundrc file for example.

I am almost certain my problem is a soundblaster problem though.

The .asoundrc "fix" didn't. It killed my Skype audio altogether. Deleted the file from my home directory and my Skype audio is still broken. How do I get back to where I was with distorted audio?

Edit: Disregard. I reinstalled gnome-alsamixer and found the Digital output reenabled. Disabling it returns the Audigy back to normal. And, the launchpad fix #23 above worked for me also! Thanks a bunch to all.

Z

---

### Post by LuigiAntoniol on 2011-09-10
> **timgood said:**
> There is a bug in ia32libs causing distortion on 64bit systems. It can be fixed by: 
```
cd /usr/lib32
sudo chmod ugo-r libpulse.so.0.12.2
sudo chmod ugo-r libpulse-simple.so.0.0.3
```

Works for me and I hope it works for you.


After spending hours hacking other stuff, this worked beautifully for me.  Thanks for the post.:guitar:

---

### Post by crash9877 on 2011-09-26
works on my fresh installed natty too.

just a small change.  ;-)

cd /usr/lib32
sudo chmod ugo-r libpulse.so.0.12.3
sudo chmod ugo-r libpulse-simple.so.0.0.3

i could kiss you guys. this was getting me for quite some time. thx

---

### Post by as2277 on 2011-12-03
> **dante6913 said:**
> [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/751265](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/751265) 
#23 solved my problem.
I think that will work on everyone that has a Intel hda

Thank's a lot Dante. I had the same issue with Skype on Oneiric. I was looking for a workaround since more than a week. It works on my PC.
The workaround posted at #18 let Skype loss access to my webcam's microphone.
:cool:

---

### Post by dave0109 on 2012-01-29
Yep, comment #23 in the bug report worked for me too.  No more distortion in the audio on VLC and I think Skype (though I've a mic problem to sort out for that).

This is with Intel HD Audio on the Asus P8Z68-V mobo.

Thanks for posting.

[Edit: That didn't work in the end, I still had intermittent problems with the audio cutting out briefly and the notification icon showing up.  In the end I got it working by setting the second position fix, as detailed in [https://wiki.ubuntu.com/Audio/PositionReporting.]](https://wiki.ubuntu.com/Audio/PositionReporting.])

---

### Post by Belfry on 2012-04-13
Post #18 by timgood is the best thing since sliced bread. Perfectly resolves the Skype crackling on a 64-bit Lucid box.

---

### Post by valdasbc on 2012-11-17
> **as2277 said:**
> Thank's a lot Dante. I had the same issue with Skype on Oneiric. I was looking for a workaround since more than a week. It works on my PC.
The workaround posted at #18 let Skype loss access to my webcam's microphone.
:cool:

Yep, that's also worked on 64-bit Ubuntu 12.10. 

Thanks!

---

