---
title: "CD Burning error"
date: 2009-07-30
forum: General Help
---

### Post by sigurnjak on 2009-07-30
Does anyone have any idea how to fixthis error or is this hardware problem with my DVD burner :
Failure: SCSI error on write(16,16): key=5 asc=21h ascq=02h

I have tried  nautilus burn  , braser and xfburn and still same error .

---

### Post by alphacrucis2 on 2009-07-30
> **sigurnjak said:**
> Does anyone have any idea how to fixthis error or is this hardware problem with my DVD burner :
Failure: SCSI error on write(16,16): key=5 asc=21h ascq=02h

I have tried  nautilus burn  , braser and xfburn and still same error .

I have a lot more luck with K3B with my burner. The only downside is that if you don't use any other KDE apps then installing it will pull in quite a lot of KDE libs that it depends on.

---

### Post by nikhilk on 2009-07-30
> **sigurnjak said:**
> Does anyone have any idea how to fixthis error or is this hardware problem with my DVD burner :
Failure: SCSI error on write(16,16): key=5 asc=21h ascq=02h

I have tried  nautilus burn  , braser and xfburn and still same error .

What is it that you are trying to burn? If you are trying to burn an iso image, the simplest way is
```
cdrecord -v dev=/dev/sr0 /path/to/iso
```

---

### Post by ajgreeny on 2009-07-30
> **alphacrucis2 said:**
> I have a lot more luck with K3B with my burner. The only downside is that if you don't use any other KDE apps then installing it will pull in quite a lot of KDE libs that it depends on.
+1
I have always used k3b in spite of having gnome as my DE.  I find brasero, and in the past gnomebaker, give me far too many errors and leave me with the coasters that are no use for anything except coffee mugs.

Give it a try.  Even with all the kde libraries etc it will bring in with it, it is worth it.  It's the best CD/DVD burner software on any platform, including windows, I think, and I couldn't manage without it.

---

### Post by sigurnjak on 2009-07-30
I did have K3B  , and still no luck . I did not go to xp yet , but i am wondering if it is problem with my dvd burner . 
Also , what the heck is meaning of that error ?

---

