---
title: "Burning dvdr.img file"
date: 2006-02-20
forum: General Help
---

### Post by Saxphile on 2006-02-20
Hi,

I have a few dvdr.img files that I got from... sources... I tried both Nero linux and GnomeBaker and neither of them recognized it. I googled a bit, but all the information I could find were for Windows. Could someone tell me how you burn those files in Ubuntu?

Thanks.

---

### Post by Saxphile on 2006-02-21
Nevermind.. Just change the file extension to iso and it worked..

---

### Post by akiro.yamamoto on 2006-02-21
Changing the file extension may not work. As far as I know you have to use UltraIso 
( Use WINE) to CONVERT the .img file to a .iso file.

---

### Post by akiro.yamamoto on 2006-02-21
I suspect that your using the ahhh x86 image file?
If so use the UltraISO demo that you can download from their web-site to convert the file. Good Luck ;)

---

### Post by slazh on 2006-02-21
Or you could just burn it right away, without converting it :)

```
$ growisofs -dvd-compat -Z /dev/dvdrw=dvd.img
```

Where ```
/dev/dvdrw
``` is your dvd/cd burner.
Mine for example is /dev/hdb.

---

### Post by taurus on 2006-02-21
k3b can burn .img with no problem at all!!!

---

### Post by Saxphile on 2006-02-23
Thanks you guys for all the help, but for the one file I tried I really just renamed it and it worked. I'll check the other files and try your suggestions if needed.

---

### Post by SysFail on 2007-08-23
This guy is right...I just re-named one and it burned perfectly too

---

### Post by shields on 2007-08-24
> **taurus said:**
> k3b can burn .img with no problem at all!!!

Thanks - k3b worked great.

---

### Post by unbeleve on 2008-03-22
> **taurus said:**
> k3b can burn .img with no problem at all!!!

thanks

---

