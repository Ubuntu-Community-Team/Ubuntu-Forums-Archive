---
title: "Confused about my processor!! Is it 64 bit or 32 bit? A little help please!"
date: 2012-03-27
forum: General Help
---

### Post by neo1691 on 2012-03-27
Hey folks. I purchased my laptop three years back, HP dv6 1111au.
It came preloaded with windows vista 32 bit.
The details about my laptop are given here 
[http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx]("http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx")

I am facing acute heating problems since then. Now i did some googling and found that 64 bits can be run on this processor that i am on. 

Can somebody please tell me what could be the best option for me??

Here is the processor..

[CENTER][IMG]http://www.inter-kom.ru/components/com_virtuemart/shop_image/product/1304148462.jpg[/IMG][/CENTER]

---

### Post by Bucky Ball on 2012-03-27
Yep, 64bit will utilise that processor better but might not fix your heating problems. Which Ubuntu release are you using?

---

### Post by neo1691 on 2012-03-27
> **Bucky Ball said:**
> Yep, 64bit will utilise that processor better but might not fix your heating problems. Which Ubuntu release are you using?
I am using 32 bit 10.04 LTS.. But then why i was given a 32 bit version of windows in the first place by HP?? Damn.. Anyways thanks!!  I think i will reformat everything next month for the installation of next LTS

---

### Post by 2F4U on 2012-03-27
The HP website says that the computer can run either 32 or 64 bit (in the question about upgrade to 64 bit Windows):

[http://www.google.de/url?sa=t&rct=j&q=hp%20pavilion%20dv6-1111au%2064%20bit&source=web&cd=2&ved=0CC4QFjAB&url=http%3A%2F%2Fh10025.www1.hp.com%2Fewfrf%2Fwc%2Fdocument%3Fdocname%3Dc01883653%26cc%3Dus%26dlc%3Den%26lc%3Den%26product%3D3962766&ei=2uxxT5CkJoHOtAb4m9ziDQ&usg=AFQjCNFH7nDUSPYvXaEloG4IPUbyRaQo-Q&cad=rja]("http://www.google.de/url?sa=t&rct=j&q=hp%20pavilion%20dv6-1111au%2064%20bit&source=web&cd=2&ved=0CC4QFjAB&url=http%3A%2F%2Fh10025.www1.hp.com%2Fewfrf%2Fwc%2Fdocument%3Fdocname%3Dc01883653%26cc%3Dus%26dlc%3Den%26lc%3Den%26product%3D3962766&ei=2uxxT5CkJoHOtAb4m9ziDQ&usg=AFQjCNFH7nDUSPYvXaEloG4IPUbyRaQo-Q&cad=rja")

So you can run either 32 or 64 bit Ubuntu. However, I doubt that this will solve the heating issues. Since this laptop has an ATI card, what graphics driver are you using, open source or proprietary?

---

### Post by Bucky Ball on 2012-03-27
> **2F4U said:**
> Since this laptop has an ATI card, what graphics driver are you using, open source or proprietary?

+1. Check 'Additional Drivers' and see if there is a disabled ATI driver in there ...

PS: I'd wait a little after 12.04 release for the dust to settle and the OS to stabilise.

---

### Post by mastablasta on 2012-03-27
> **neo1691 said:**
> I am using 32 bit 10.04 LTS.. But then why i was given a 32 bit version of windows in the first place by HP?? Damn.. Anyways thanks!!  I think i will reformat everything next month for the installation of next LTS


use the latest Ubuntu version (11.10) instead for a better drivers support for your GPU.


You dont' ahve to have 64 bit os on it. many programms at the tiem of vista didn't even work on 64 bit system. i too have (though single core) athlon that is 64 bit yet i chose to use 32 bit WinXP at the time due to compatibility reasons.

for linux you cna use 64bit easilly (well windows too), but the heating issue really porbably has to do with graphics chip.

---

### Post by neo1691 on 2012-03-27
> **2F4U said:**
> The HP website says that the computer can run either 32 or 64 bit (in the question about upgrade to 64 bit Windows):

[http://www.google.de/url?sa=t&rct=j&q=hp%20pavilion%20dv6-1111au%2064%20bit&source=web&cd=2&ved=0CC4QFjAB&url=http%3A%2F%2Fh10025.www1.hp.com%2Fewfrf%2Fwc%2Fdocument%3Fdocname%3Dc01883653%26cc%3Dus%26dlc%3Den%26lc%3Den%26product%3D3962766&ei=2uxxT5CkJoHOtAb4m9ziDQ&usg=AFQjCNFH7nDUSPYvXaEloG4IPUbyRaQo-Q&cad=rja]("http://www.google.de/url?sa=t&rct=j&q=hp%20pavilion%20dv6-1111au%2064%20bit&source=web&cd=2&ved=0CC4QFjAB&url=http%3A%2F%2Fh10025.www1.hp.com%2Fewfrf%2Fwc%2Fdocument%3Fdocname%3Dc01883653%26cc%3Dus%26dlc%3Den%26lc%3Den%26product%3D3962766&ei=2uxxT5CkJoHOtAb4m9ziDQ&usg=AFQjCNFH7nDUSPYvXaEloG4IPUbyRaQo-Q&cad=rja")

So you can run either 32 or 64 bit Ubuntu. However, I doubt that this will solve the heating issues. Since this laptop has an ATI card, what graphics driver are you using, open source or proprietary?

I am using proprietary fglrx drivers.

> **Bucky Ball said:**
> +1. Check 'Additional Drivers' and see if there is a disabled ATI driver in there ...

PS: I'd wait a little after 12.04 release for the dust to settle and the OS to stabilise.

I have activated the drivers. It has improved


> **mastablasta said:**
> use the latest Ubuntu version (11.10) instead for a better drivers support for your GPU.


You dont' ahve to have 64 bit os on it. many programms at the tiem of vista didn't even work on 64 bit system. i too have (though single core) athlon that is 64 bit yet i chose to use 32 bit WinXP at the time due to compatibility reasons.

for linux you cna use 64bit easilly (well windows too), but the heating issue really porbably has to do with graphics chip.

Well i have tried every version of ubuntu from 10.04. But 10.04 was the most less noisy for me.. In 11.10 the new gnome shell (or whatever as i dont know the name of the latest version of gnome) caused lags and stuttering.

also in 10.04 i installed docky and then there was constant heating, as soon as i installed it the system was again silent. 

Its very sad for me. I cannot use those features which i want to!!

---

