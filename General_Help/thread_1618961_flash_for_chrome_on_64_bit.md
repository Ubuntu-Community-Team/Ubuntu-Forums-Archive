---
title: "flash for chrome on 64 bit??"
date: 2010-11-11
forum: General Help
---

### Post by Mashvv on 2010-11-11
hey guys i installed ubuntu 10.10 64 by mistake  and i dont know how to install adobe flas player for google chrome!???
plzzz and another Q 
why are softwares for ubuntu 64 bit limited and hidden ???

---

### Post by I'mGeorge on 2010-11-11
method 1 install adobe flash player with synaptic from your repos
method 2 download it from here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) , extract the libflashplayer.so and copy it to /usr/lib64/mozilla/plugins

---

### Post by Mashvv on 2010-11-11
Hey , if u can explain how to do that exactlly cuz im a totall n00b to ubuntu :)

---

### Post by Mashvv on 2010-11-11
OK wait i think i got it , u mean i can install it from the synaptic package manager ?

---

### Post by pqwoerituytrueiwoq on 2010-11-11
extract the [libflashplayer.so]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz") file to /opt/google/chrome/plugins/
i assume you are using the google branded chromium

assumingyou want to do this via the GUI this will help
press alt+F2
gksu nautilus

@question 2 
You just have to look harder most apps are available in 64bit for ubuntu flash is about the only annoying one to deal with
if 64 bit is not specified it is usually 32bit

---

### Post by oldos2er on 2010-11-11
I recommend you use 64-bit flash, which is not in the repositories. Download it here: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)

After you extract it, copy libflashplayer.so to ~/.mozilla/plugins

---

