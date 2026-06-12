---
title: "I screwed up.."
date: 2006-06-02
forum: General Help
---

### Post by nugglets on 2006-06-02
Ok, so my sound was working fine with a fresh dapper install. Then went through a long and tedious process of getting xgl/compiz working properly(which is awesome!), but now the sound doesnt work anymore. I have tried the alsa-project guide, and after alot of work and installing the proper packages, managed to get through all the steps error free.. but it still isnt working. I have looked in all the basic spots(system>pref>sound, alsamixer) and everything is kosher. What am I missing here? Its a laptop, on board audio ATI IXP. Also, sound is fine in XP so its not a hardware issue. 

Any help is greatly appreciated. I am pretty new to linux, but have learned quite a bit over the past few days. So far, other than the sound thing, I love it!

---

### Post by 2501 on 2006-06-02
I think I had a similar problem when I started using Fluxbox desktop environment. But I installed resolved the problem by installing Kmix. 

sudo apt-get install kmix

let me know if that works.

-2501

---

### Post by nugglets on 2006-06-02
Hmm, nope that didnt seem to work. Dunno when exactly this happened, but now under system>pref>sound there are no options for default sound card. Device manager shows the card, I just re-did all the steps on the alsa guide again.. and it still isnt showing in system panel. Im totally lost. 

Thank you for the suggestion though, I have no idea what I'm doing ](*,)

edit: Wait! It did work!! I just had to turn off the external amplifier switch in kMix! THANK YOU!!!! WEEEEEEEEEE!!!!!!!!!!

---

### Post by 2501 on 2006-06-03
awesome!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
-2501

---

