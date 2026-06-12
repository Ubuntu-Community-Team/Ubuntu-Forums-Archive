---
title: "Problem caused by hibernate/suspend"
date: 2011-10-22
forum: General Help
---

### Post by vaskark on 2011-10-22
I'm using Natty since Oneiric didn't install for me. I tried to use the hibernate menu option but all that did was turn the screensaver on. I rebooted and now whenever I choose to boot into ubuntu my monitor turns off and no amount of moving the mouse or pressing keyboard keys will get it to wake up again.

 Please help. I've reinstalled Ubuntu so many times this week due to problems that I'm at my wits end.

Thanks.

---

### Post by crazy bird on 2011-10-22
You're not the only one with this problem, see this forum for more threads with this issue: [http://ubuntuforums.org/showthread.php?t=1849598](http://ubuntuforums.org/showthread.php?t=1849598) (as example).

Best is to avoid hibernate/suspend mode since this was always an issue with Ubuntu. As long as i'm using Ubuntu (since 7.04) there was always problems with it.

---

### Post by utnubuuser on 2011-10-22
Is this fixable by adding the "nomodeset" parameter to the kernel?

---

### Post by vaskark on 2011-10-22
So there isn't a solution right now?

---

### Post by crazy bird on 2011-10-22
You can disable these 2 functions by doing this:

- open a terminal
- type in[COLOR=Black][B]: sudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy
[/B]
- Find  a line called:**<action id="org.freedesktop.upower.suspend">**
- Change *<allow_active>yes</allow_active>* into **<allow_active>no</allow_active>**

- find a line called: [B]<action id="org.freedesktop.upower.hibernate">
[/B][/COLOR][COLOR=Black]- Change *<allow_active>yes</allow_active>* into **<allow_active>no</allow_active>**[/COLOR]

This will disable suspend and hybernate and will be shown any longer in the shutdown button.

I'm not sure if you have to logout/logon or restart, but you can try 1 of these 2 options ;-)

---

### Post by vaskark on 2011-10-22
Thanks for your reply. But I can't login without my monitor powering down. Is there anything I can do from the recovery console?

Update: I was able to get into my system. Not sure why it worked this time. I followed your suggestions and removed those 2 options from my shutdown menu. All should be well now. Thanks so much for your help and patience :)

---

