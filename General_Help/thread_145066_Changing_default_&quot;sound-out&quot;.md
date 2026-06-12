---
title: "Changing default &quot;sound-out&quot;"
date: 2006-03-15
forum: General Help
---

### Post by b0nde on 2006-03-15
Hi.

I've just installed Ubuntu 5.10, and I really wanna have sound on my system, via my optical out / spdif. I'm running nvidia soundstorm on a Abit NF7-S. 
 So far I've got it in XMMS, by changing to ALSA and "hw:0,2". But, all other applications seems to be putting out the sound on the jacks, isnt it what they're called :) I hope some of you guys can help me with this matter! So far I've found help here for configuring my MX500 mouse properly, and loads of other stuff too! :-D  Thanks!

 - Jakob.

---

### Post by b0nde on 2006-03-16
*BUMP*

Please, isnt there anybody out there, that can help me ? :)
 Please!

---

### Post by Ivan Matveich on 2006-03-16
```
pcm.!default {
        type hw
        card 0
        device 0
        subdevice 2
}
```

---

### Post by Ivan Matveich on 2006-03-16
```
pcm.!default {
        type hw
        card 0
        device 2
}
```

I'm not sure.

---

### Post by b0nde on 2006-03-17
Thank you for your reply !! :)

 But where do I type those lines in ? I can see that you've wrote ~/.asoundrc , where is that ?

 Thank you!

---

### Post by jazzgossen on 2006-03-17
~ is short for your home directory, and all files starting with a dot (like .asoundrc) are normally invisible. You have to type "ls -a" to see them if you're in a terminal.

That said, there is no ~/.asoundrc by default, you have to create it yourself, with a text editor of your choice.

By the way, I have the same motherboard you do, and I managed to get SPDIF output with a .asoundrc file like this.

Oh, and I beleive you have to change to alsa under Preferences/Multimedia systems selector, too.

---

### Post by b0nde on 2006-03-18
[QUOTE=jazzgossen]~ is short for your home directory, and all files starting with a dot (like .asoundrc) are normally invisible. You have to type "ls -a" to see them if you're in a terminal.

That said, there is no ~/.asoundrc by default, you have to create it yourself, with a text editor of your choice.

By the way, I have the same motherboard you do, and I managed to get SPDIF output with a .asoundrc file like this.

Oh, and I beleive you have to change to alsa under Preferences/Multimedia systems selector, too.[/QUOTE]
 Okay, thank you for your guide! :) I will try this later, hope it works.

---

### Post by probablydrew on 2006-05-06
[QUOTE=Ivan Matveich]```
pcm.!default {
        type hw
        card 0
        device 2
}
```

I'm not sure.[/QUOTE]


thanks Ivan, this did the trick for me

---

