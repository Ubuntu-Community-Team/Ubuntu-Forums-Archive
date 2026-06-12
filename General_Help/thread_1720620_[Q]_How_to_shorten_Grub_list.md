---
title: "[Q] How to shorten Grub list"
date: 2011-04-03
forum: General Help
---

### Post by psyionx on 2011-04-03
my computer have windows 7  and also a ubuntu in it (i started with version 10.04). i've just updated my ubuntu and i found that the list in the grub menu got longer by 2.and i feel its a long list....

so how do i shorten the list... i'll be ok if i just have the latest Linux and its recovery mode. than memtest86 and the other and last Windows 7...
i dont need the old ubuntu in the list.... its redundant....
i have startup-manager installed but does not do what i wanted....


any help or guide please....

---

### Post by muteXe on 2011-04-03
Hiya,
This is a great guide in my opinion:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Rubi1200 on 2011-04-03
You might be interested in a new GUI application called Grub Customizer:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by drs305 on 2011-04-03
There is also this guide, which recommends Ubuntu Tweak if you are trying to remove older kernels. (It's recommended to keep at least one older working kernel but that's up to you).

[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by psyionx on 2011-04-03
Thanks man.... i got it done with Grub Customizer... just what i need.

---

### Post by Rubi1200 on 2011-04-03
> **psyionx said:**
> Thanks man.... i got it done with Grub Customizer... just what i need.
Excellent! You are more than welcome :)

---

### Post by psyionx on 2011-04-03
> **drs305 said:**
> There is also this guide, which recommends Ubuntu Tweak if you are trying to remove older kernels. (It's recommended to keep at least one older working kernel but that's up to you).

[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

ok... thats a backup plan.... i'll add another 2 on the list... 
erm.... i'll just leave the old kernel as they are, its not that they are taking up a lot of space or something.... its just the grub list that grew that bothers me... ^^ 

thanks..

---

### Post by drs305 on 2011-04-03
> **psyionx said:**
> ok... thats a backup plan.... i'll add another 2 on the list... 
erm.... i'll just leave the old kernel as they are, its not that they are taking up a lot of space or something.... its just the grub list that grew that bothers me... ^^ 

thanks..

If you keep them on the machine but use Grub Customizer to hide them, they would still be available to you but you wouldn't see them on the menu. 

If you had problems with the one on the menu, all you would have to do at the Grub menu would be to press "e" to edit the first entry, then use the cursor to change the kernel number down one (or to your backup kernel number, e.g. 2.6.35-14 to 2.6.35-13) in two lines. Then CTRL-x to boot.

You can to the same with the recovery mode - hide it from view but alter the first entry if you need to. You would change the end of the linux line  by removing 'quiet splash' and adding 'single', then CTRL-x to boot.

But we are getting into the weeds now, so I'll stop.

I'll respond to any questions you have on this but when you are ready you can mark the thread solved via the 'Thread Tools' link at the top right of the first post.

---

