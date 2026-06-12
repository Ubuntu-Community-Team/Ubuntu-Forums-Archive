---
title: "need help..  sound doesnt work, after fresh install"
date: 2009-09-30
forum: General Help
---

### Post by Adrenochrom3 on 2009-09-30
ok i installed ubuntu on my new dell, and my sound does not work... how would i go about fixing this?

---

### Post by Littleweseth on 2009-09-30
You need to provide more information before you can be helped.

- What model of Dell?
- What have you tried/what doesn't work?

Self-serve help : have you read this? : [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
and this? : [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Adrenochrom3 on 2009-09-30
i have a studio 1555  and my sound card isssss:

"Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)"

---

### Post by Adrenochrom3 on 2009-09-30
I got it working! thank you for that second link, it got my sound card configured! sweetness! :)

---

### Post by mb007 on 2009-09-30
I have installed Ubuntu for the first time (after beeing fed up with Vista) and have the same problem (no sound). As I am new to Ubuntu can some help me to find details of my installed soundcard, please?

---

### Post by nothingspecial on 2009-09-30
```
lspci -v
```

```
aplay -l
```

Post which card you have after running either/both of thos commands.

---

### Post by Adrenochrom3 on 2009-09-30
what i did was i went to the second link Littleweseth posted, and on that page i found a link.

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

and followed the directions and it configured my sound card. it takes like 10 mins, but it works!
just copy and paste in terminal. :)

---

### Post by mb007 on 2009-09-30
Thanks for all those fast answers.
I used the procedure through the link and after two days of searching it solved the problem

---

### Post by Adrenochrom3 on 2009-10-23
ok i messed up big time... i installed something via package manager, and it did something to my sound and i fail to get my sound to work. its stressing me out and i have no idea what happened. please help

---

### Post by Adrenochrom3 on 2009-10-24
Please help me!!

---

