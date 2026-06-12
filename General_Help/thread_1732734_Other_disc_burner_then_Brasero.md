---
title: "Other disc burner then Brasero"
date: 2011-04-18
forum: General Help
---

### Post by PCaddicted on 2011-04-18
I have tried to make a video DVD with Brasero,but it just hung...is there any other disc burner available for Ubuntu?

---

### Post by CoolJohnB on 2011-04-18
If you look in software center you will see quite a number of disk burners

---

### Post by dniMretsaM on 2011-04-18
Look around in the Software Center for a different burner. Google is also a very good friend who may come in handy. And make sure it's not hanging because of something like a file being too large.

---

### Post by Miljet on 2011-04-18
You do have libdvdcss2 installed, don't you?

---

### Post by JRV on 2011-04-18
> **Miljet said:**
> You do have libdvdcss2 installed, don't you?

If not install it.

I use DVDstyler to create the DVD and save it as an .ISO then use brasero to burn it.

---

### Post by nitstorm on 2011-04-18
k3b - it never fails :D its a KDE app though, so be warned...

---

### Post by lhb1142 on 2011-04-18
> **PCaddicted said:**
> I have tried to make a video DVD with Brasero,but it just hung...is there any other disc burner available for Ubuntu?

I like K3b more than any other burner I have ever used. You will find it in the Synaptic Package Manager (assuming you have the Medibuntu repository installed). It is also present in the Ubuntu Software Center.

There is somewhat of a learning curve - K3b offers many setup options - but the program works very well indeed even at its default settings. Once you know it well, you'll wonder why other such programs aren't as good (at least in my opinion).

---

### Post by TeoBigusGeekus on 2011-04-18
```
growisofs -Z /dev/dvd -dvd-video /path/videofile
```

---

