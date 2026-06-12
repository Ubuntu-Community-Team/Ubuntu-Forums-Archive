---
title: "Flash version change"
date: 2010-10-02
forum: General Help
---

### Post by jodlajodla on 2010-10-02
Hi!
I get this link ( [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) ) for change my version of flash, because I can't playing flash when I have turned on effects. So I downloaded file for my Ubuntu 10.04 64-bit and I extracted it. But there is problem, because I don't know on which location I need to copy .so file?

Thanks! :)

---

### Post by howefield on 2010-10-02
For Firefox (and Chrome) 

```
/usr/lib/mozilla/plugins
```

For Opera

```
/usr/lib/opera/plugins
```

---

### Post by drs305 on 2010-10-02
The extracted file should be *libflashplayer.so*

You can place it the proper location with the following command if you currently have it on your Desktop and use Firefox:

```
sudo cp ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/
```

---

