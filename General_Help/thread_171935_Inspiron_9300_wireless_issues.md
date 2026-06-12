---
title: "Inspiron 9300 wireless issues"
date: 2006-05-07
forum: General Help
---

### Post by jtplaya182 on 2006-05-07
Im running Ubuntu 5.10 on my inspiron 9300, when I set up Ubuntu it found my wireless card (intel centrino technology). But when I get into the actual OS and go into the networking tab all i get is the prompt for my password. I put in my pass, and hit enter and nothing happens. It never brings up the next screen to let me config my wireless network. I have re-installed Ubuntu 4x trying to get this to work with no luck. If there is something i'm missing can someone please give me a hand here. Thanks. ;)

---

### Post by stinkypudding on 2006-05-07
Is your wireless card broadcom?   This is the site I used to get mine working:
[http://forums.us.dell.com/supportforums/board/print?board.id=sw_linux&message.id=7329&page=1&format=all](http://forums.us.dell.com/supportforums/board/print?board.id=sw_linux&message.id=7329&page=1&format=all)

---

### Post by jtplaya182 on 2006-05-07
I believe the onboard ethernet is the broadcom, from what i understand the wireless is a centrino, something or rather. Any other ideas?

---

### Post by stinkypudding on 2006-05-07
Check under System/Administration/Device Manager....that will show what your wireless card is in your system.   If it's a Dell, chances are it's a broadcom card, which is not supported in Linux.   You have to download the windows driver, the instructions I used were in the website above.   

Check your device manager and make sure it's a broadcom card.

---

