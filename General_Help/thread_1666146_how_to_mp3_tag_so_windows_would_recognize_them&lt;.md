---
title: "how to mp3 tag so windows would recognize them&lt;"
date: 2011-01-13
forum: General Help
---

### Post by strnad on 2011-01-13
Hello guys,

I have tagged my mp3 collection using Rhytmbox.

The problem is that my mp3 player is a Windows bastard and does not recogniye these ID tags. Also, when I examine files in Windows, I see only empty spaces.

When I did taging in Windows, mp3 player recognized them without any problems.

Can you guys recomend me some SW to ID tag my mp3s that would also be recognized by Windows/my mp3 player?

Thanks a lot.

Sincerely

Peter

---

### Post by karthick87 on 2011-01-13
```
sudo apt-get install easytag
```

---

### Post by cmoraes on 2011-01-13
[PuddleTag]("http://puddletag.sourceforge.net/") is another good MP3 tag editor in linux.  

BTW, check which version of ID3 tags your Windows mp3 player supports.  For e.g. Windows media player v11 reads ID3v2.3 tags.  If Rhytmbox box is writing ID3v2.4 tags they may be incompatible for some tag info.

---

### Post by strnad on 2011-01-14
Hello guys.

Thank you for your help.

I have installed EasyTag and it works perfectly.

Peter

---

