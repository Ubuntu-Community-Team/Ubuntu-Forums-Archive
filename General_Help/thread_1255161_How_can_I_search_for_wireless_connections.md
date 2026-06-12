---
title: "How can I search for wireless connections?"
date: 2009-09-01
forum: General Help
---

### Post by fbjoey on 2009-09-01
How can I search for wireless connections?

Cheers
Fbjoey

---

### Post by nothingspecial on 2009-09-01
Click on your network icon. It looks like " tv`s usually. Might have an x infront of it.

---

### Post by fbjoey on 2009-09-01
I have done. I deleted a connection I needed. Can i make ubuntu search again manualy?

---

### Post by nothingspecial on 2009-09-01
```
sudo ifconfig wlan0 up
``` 

```
 iwlist wlan0 scan
```

---

### Post by AndyCee on 2009-09-01
There currently is no "refresh" button, like in Windows or OSX. I think there's an idea in brainstorm.ubuntu.com for it.

Typing in the code shown by nothingspecial should do the same thing, I believe.

---

### Post by 3rdalbum on 2009-09-01
If you go to "Connect to hidden wireless network" you can connect to any network, even when it's not on the scanned list. As long as you know the SSID and password.

---

