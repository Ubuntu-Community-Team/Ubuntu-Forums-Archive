---
title: "Minecraft Help"
date: 2011-06-14
forum: General Help
---

### Post by parkerskouson on 2011-06-14
Ok. I have installed minecraft on Natty. I just wiped and reinstalled to Maverik and now i cannot get Java to install, which i have to have to play minecraft. Are there other programs or codes to install Java??

Any help needed

Parker

---

### Post by Pax-Man on 2011-06-14
I'm also having problems running Minecraft on Ubuntu 11.04. 
How did you install Java?

---

### Post by parkerskouson on 2011-06-14
I used this Java install code.. But it did not work. Sadly

[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR] openjdk-[COLOR=#000000]6[/COLOR]-jre openjdk-[COLOR=#000000]6[/COLOR]-jre-headless

---

### Post by jim_deadlock on 2011-06-14
Remove openjdk-6-jre, openjdk-6-jre-headless and all icedtea apps via software center, then make sure in your software center -> software source -> other software  -> canonical partners is enabled, then install sun-java6-plugin (it should auto-install sun-java6-jre and sun-java6-bin) and also sun-java6-fonts. Hopefully you'll be good to go then.

---

### Post by parkerskouson on 2011-06-14
And how do i do that??

---

### Post by jim_deadlock on 2011-06-14
Do you have Ubuntu Software Center on your menu?

---

### Post by parkerskouson on 2011-06-14
> **jim_deadlock said:**
> Do you have Ubuntu Software Center on your menu?
yes

---

### Post by jim_deadlock on 2011-06-14
I don't really understand exactly what you're having trouble with then

---

