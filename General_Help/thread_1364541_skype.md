---
title: "skype"
date: 2009-12-26
forum: General Help
---

### Post by martinshort on 2009-12-26
just quickly...

skype's site has this 8.10 beta thing. can i use it on this 9.10 i just got? 

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

thanks...

---

### Post by lisati on 2009-12-26
> **martinshort said:**
> just quickly...

skype's site has this 8.10 beta thing. can i use it on this 9.10 i just got? 

thanks...

You might notice it says 8.10[COLOR="Red"]+[/COLOR],you should be fine, it works well with 9.04.

---

### Post by martinshort on 2009-12-26
installed. but the microphone is missing. i remember on gnome that had to do with mixer and record level?!

---

### Post by spiderbatdad on 2009-12-26
Did you consider we might like to know what kind of laptop you're using?

---

### Post by martinshort on 2009-12-26
i did. its called. hp mini 110 - 1150nr.
trying to figure out which one is the driver. it's some kind of "duplex" card?!

---

### Post by spiderbatdad on 2009-12-26
the following method I used to finally get 2.1.0.47 working on Acer Aspire One.
Install pavucontrol
```
sudo apt-get install pavucontrol

```
Open the program. Accessories>>Sound and Video>>Pulse Audio Control. Go to the input tab. Unlock it with the little lock icon near upper right corner. Move Left input to zero. Move right input to max. Close. Done. Try skype.

---

### Post by martinshort on 2009-12-26
thanks.  but it doesn't unlock the channels. it's a "stereo" card. still it should be doing it anyway. on the input sound control the microphone is also all the way up. doesn't register anything....;

---

### Post by spiderbatdad on 2009-12-26
you can't uncouple the channels with lock symbol?
also check alsamixer capture level. with command alsamixer then tab key to move and arrow to move to capture device and up arrow to raise it.

---

### Post by martinshort on 2009-12-26
no. it doesnt let me.

attached is what i see for the alsamixer. which one is the "capture device"? cause they are all up...

---

### Post by spiderbatdad on 2009-12-26
from that screen please press the Tab key.

---

### Post by martinshort on 2009-12-26
i see... thanks.
but still no input. new image attached.

---

### Post by martinshort on 2009-12-26
that's it?

---

### Post by spiderbatdad on 2009-12-26
It looks like you should turn front mic all the way down...leave capture up. Turn L-R capture down. Not sure, you'll have to experiment. I believe you can make it work.

---

### Post by martinshort on 2009-12-27
hi there spiderbatdad...

just wanted to let you know that somehow this thing works now. after a lot of tinkering all day yesterday i restarted the machine last night and i had the input working. that way ubuntu reminds me of that other system i was trying to avoid using, the one that you have to restart all the time to get settings to stick... anyway.

thanks for your help and tips.  cheers....

---

