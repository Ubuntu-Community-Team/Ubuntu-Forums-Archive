---
title: "iPhone custom ringtone using Ubuntu"
date: 2011-05-17
forum: General Help
---

### Post by cymbaline42 on 2011-05-17
This is a tutorial (and a note to myself) on how to put a custom ringtone without length limitation on your iPhone using Ubuntu.

All credits go to this site: [http://www.control-d.com/?p=60](http://www.control-d.com/?p=60)

I'm posting this here since I wanted to put a custom ringtone on my iPhone and did not want to use the bloatware called iTunes to convert the mp3 to m4r.

This tutorial works only on jailbroken iPhones.


[LIST=1]
[*]Download the mp3 file of your choice that you want as your ringtone
[*]Navigate to wherever the mp3 file is stored on your computer and use the following commands to convert the mp3 to wav, and the wav to m4a
[*]mplayer -vo null -vc null -ao pcm:fast: file=file.wav (your filename).mp3
[*]faac -b 128 -c 44100 -w (the converted wav filename).wav
[*]Rename the converted file to m4r
[*]Connect the iPhone to the computer.  If you have SSH enabled on iFile, you can navigate your phone folders using your computer's browser.
[*]Alternatively, copy the m4r file to iPhone-Downloads.
[*]Open iFile, copy the file and paste it into /Library/Ringtones/ folder in your iPhone
[*]Close iFile, open Settings - Sounds - Ringtone - and voila, choose your custom ringtone.
[/LIST]

---

### Post by masali on 2011-05-17
Out of curiosity, What do u gain with this way as opposed to using itunes?


Q: What do you mean by jail broken iphone? Can I improve on the security of the phone. 

Thanks

---

### Post by cymbaline42 on 2011-05-17
This is a guide for people using Ubuntu, if you have Windows and iTunes, by all means, use it.  I believe that there is a ringtone length limit of about thirty seconds using iTunes though.

Jail-breaking is a process of installing an 'unofficial' repository called Cydia, which provides additional functionality.  It also unlocks the phone to be used with your choice of sim cards.  There are advantages and disadvantages to jailbreaking.  Do an internet search for more detailed information.

I'm not sure what you mean by improving the security of the phone.

---

