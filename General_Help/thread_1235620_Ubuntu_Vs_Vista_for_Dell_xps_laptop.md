---
title: "Ubuntu Vs Vista for Dell xps laptop"
date: 2009-08-09
forum: General Help
---

### Post by elect82 on 2009-08-09
I have been using ubuntu since last six month dual boot with vista and i love ubuntu :). I only use vista for skype and yahoo messanger :(.

I am using Dell XPS 1330 laptop with nVidia graphic card (GeForce 8400M GS). I had two times problem with graphic cards (Well known problem in dell laptop) and replaced GPU and motherboard twice.

I have monitored both GPU and CPU temperature in both vista and ubuntu and noticed that GPU temperature averaged around 48 deg in vista compared to 58 deg in ubuntu (may be due to better graphic card driver support in vista?) and cpu temp around 55 deg in vista compared to 48 deg in ubuntu.

**On an average, GPU temperature is 10 deg higher in ubuntu than vista.** Is there any way to reduce the GPU temperature? I have installed Gkrellm and always runs fan on fast speed. I am using latest nvidia driver (180.?)in ubuntu. 

Thanks in advance...

---

### Post by Arup on 2009-08-09
Are you using latest nvidia 185 series drivers with powermizer enabled, in that case the temps should be close to your Windows temps. Skype works reliably in Ubutu as well with both video and audio having same quality as its Win counterpart. For Yahoo messenger consider Gyachi which gives Webcam and sound support.

---

### Post by elect82 on 2009-08-09
Thanks for your reply Arup..

I am using nvidia 180 series driver. When I looked System < administration < Hardware sources, It shows 180 series driver and gives only option for 173 series. Not sure how to get and install 185 series nvidia driver. Also I have installed both GYachi and skype in ubuntu, but mic is not working in ubuntu and that is the only reason i need to boot window.... ( i hve tried virtual box as well but no luck yet..)

---

### Post by mordecai83 on 2009-08-09
I have an xps too, although a m1530 im sure it has the same type of mic, which is a built in one. If you right click on the volume icon on the panel and go to "volume control" and then click on "preferences" you should be able to enable the "digital input source". That should make your mic work. If your recording volume is too low, which mine was in distributions before jaunty you should search this forum for a fix ( i remember there being a fix, just didn't store the link). As for the GPU, the 180 drivers work fine for me albeit at a higher temperature than in vista. You could upgrade to the latest, and again if you search this forum I'm sure you'll find out how, but i dont think its worth the hassle just for the temperature.

Hope this helps,
Mordecai

---

### Post by elect82 on 2009-08-09
I have installed latest stable nvidia driver 185.18.31 as per wonderful guide given in the forum [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978).
Though I haven't noticed any difference in the GPU temperature. However, I hope it includes few bug fixes and new features.

(Thanks Mordecai83 for your reply. It's too late here and I have to go to sleep. But I will definitely do a first thing tomorrow to find a forum to solve mic issue in ubuntu. :) and i will get back to let u know if i have corrected it or not.)

---

