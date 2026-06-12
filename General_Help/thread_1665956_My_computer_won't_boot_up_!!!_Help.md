---
title: "My computer won't boot up !!! Help"
date: 2011-01-13
forum: General Help
---

### Post by q8_legend on 2011-01-13
Hi
My computer was working before perfectly. But today, when i tried  to powering it on. It stucks and freeze after "ubuntu 10.10" logo, and nothing happen after. I can't access to the os(gui) anymore. I don't know why !!!

Is there is a way to make it return to a previouse working day(system restore, like windows) or a command line that i can fix it from the booting error ?? Because, i don't know what causes this problem to raise !!

Thanks alot ;)

---

### Post by oly on 2011-01-13
dont know if it will help, but do you have an ati card using fglrx i hit a similar problem using recovery and failsafex has got me in for now.

not figured out the cause i do not know what packages changed last night and weather to wait or try reinstalling graphics drivers not got time to experiment now.

---

### Post by Rubi1200 on 2011-01-13
In order to help you, please provide us with more information.

what graphics card do you have, how much RAM, which version of Ubuntu, any other operating systems etc.

The more you tell us, the better we can help you troubleshoot this.

Thanks.

---

### Post by oly on 2011-01-13
well i can tell you i have an ati card of this model.
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
and around 4gb of ram, i am also using the latest fglrx drivers from the ati website.

no idea if this is the same as the other guy, but as this has not had more posts could be the same.

also using 10.11 and i do have win 7 on the same machine but i have never booted it since i got the laptop :p

---

### Post by q8_legend on 2011-01-13
> **oly said:**
> dont know if it will help, but do you have an ati card using fglrx i hit a similar problem using recovery and failsafex has got me in for now.

not figured out the cause i do not know what packages changed last night and weather to wait or try reinstalling graphics drivers not got time to experiment now.

Thanks alot oly

It does help me to fix my problem... As what you siad, I have an ati card, and it seems the problem from the driver i don't know why...  but, i did what you said and it works for me prefectly without any problem(like what it was before the problem ;), Thanks God ) ...

Do that, if you still facing the problem :

I went to the recovery mode and choose "failsafex", then when i entered the os in the low resolution mode.. choose restart the card to the default resolution( i think its in the display configration menu select)... after choosing the default setting, try to restart the computer using the restart option in the menu.. and then the computer should start normally(don't enter the recovery mode in this time), but the ati card configuration is not working now... So, you have to go to "System-->Administration-->Additional drivers" and activate the card from here...

finally, restart your computer and I hope it will works without problem now...

If you ask me what cause the problem, it don't really know why.. I think it's from the driver .. but, why it does happen.. I don't know.. If any one know please let us know.. 

Please, give me a feedback with your job... and, tell me if it does work or not...

Thanks alot "oly" for your help :)

---

### Post by oly on 2011-01-13
where you using the driver from the ati website or the one ubuntu selected for you ?

my only thought is that an update was incompatible with the fglrx driver from ati.

by going into failsafex i am guessing it reset the driver in use so at next boot it defaulted to the opensource driver which is why the control center no longer works so you had to re-install from the repo which most likely has been tested with the update.

anyway good to know i can fix it quite easy tonight, i just got to the desktop and wanted to work as i had inspiration rather than fix the issue :)

---

### Post by q8_legend on 2011-01-13
> **oly said:**
> where you using the driver from the ati website or the one ubuntu selected for you ?

my only thought is that an update was incompatible with the fglrx driver from ati.

by going into failsafex i am guessing it reset the driver in use so at next boot it defaulted to the opensource driver which is why the control center no longer works so you had to re-install from the repo which most likely has been tested with the update.

anyway good to know i can fix it quite easy tonight, i just got to the desktop and wanted to work as i had inspiration rather than fix the issue :)


Before, i get it from the ati website... but when i faced the problem today... i get it from the additional driver in the ubuntu... but, i think its only setting it up... 

anyway... The good thing that its working now... Thats what we want ;)

---

### Post by West201 on 2011-01-13
Something happened similar when I installed the ATI video drivers on my Vaio. The default worked alot more decent. 

I fixed it by switching back to the default one. Try booting with live CD

---

