---
title: "upper and lower title bar became empty crash"
date: 2010-01-03
forum: General Help
---

### Post by hatewindows7 on 2010-01-03
Hi This is my first post in this community.....I am rebel of windows want to be with ubuntu
but first day it self I saw a crash in ubuntu 

I upgraded ubuntu to latest 9.10 version....after that the upper and bottom menu option are disppared and I am not able to right click to add panel...I serached so many post here but nothing worked for me it is really bad experience for me

I reinstalled gnome-panel but still the problem persists......I tried all options gnome-panel --help commands nothing works for me....I tried to boot in recovery mode also and terminal I am able to access execute commands.....but upper and lower panel are empty and I can not add any new stuff to them

Please help me in this regard

Long live linux windows sucks ha ha :P:P:P:P:P:P

---

### Post by hatewindows7 on 2010-01-03
can some body please post some solution my entire day is wasted on this issue

---

### Post by warfacegod on 2010-01-03
From a terminal try:
```

sudo apt-get remove gdm
```

Then:

```
sudo apt-get install gdm
```

---

### Post by hatewindows7 on 2010-01-03
thanks [warfacegod]("http://ubuntuforums.org/member.php?u=537200") it worked

Thanks alot

---

### Post by warfacegod on 2010-01-03
Glad to help. Don't get discouraged. Linux has problems just like Mac and Windows but in my experience allot less than Windows (I never used Mac).

Don't forget to mark this as solved in thread tools.

---

### Post by warfacegod on 2010-01-03
My apologies, I see you already did mark solved.

---

