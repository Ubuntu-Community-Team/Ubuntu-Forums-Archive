---
title: "How can i run (.exe) portable apps"
date: 2009-10-22
forum: General Help
---

### Post by emigrant on 2009-10-22
hi,
im wondering whether there is a way that i can run .exe portable applications.

thank you very much.

---

### Post by ColdFFF on 2009-10-22
You could try wine.

Check the [wine AppDB]("http://appdb.winehq.org/") to check how well each app works

---

### Post by WolfRage on 2009-10-22
```
 
sudo apt-get install wine

```
Then you should be able to double click the .exe and it will open and install in WINE. But as noted above make sure the app is supported. Even if it is not WINE is constantly changing so it is worth a try anyways.

---

### Post by emigrant on 2009-10-22
thanks for the replies.
i know .exe files (most of them) run on wine. but im speaking here about *portable applications* (no installaion)
:)

---

### Post by gillmt on 2009-10-22
If you have a look at the PA site, I think wou will see a post involving John Haller (?) about being able run PA on Linux if you have Wine installed.

---

### Post by 3rdalbum on 2009-10-22
> **emigrant said:**
> thanks for the replies.
i know .exe files (most of them) run on wine. but im speaking here about *portable applications* (no installaion)
:)

Yes. They're still Microsoft Windows executables, regardless of whether they need to be installed or not.

---

### Post by LoloftheRings on 2009-10-22
Why don't you just try? :)

In my experience, only very complicated applications have trouble on wine, such as games (not for warcraft 3 though!) and apps with an own toolkit such as live messenger (.NET)

---

### Post by Aero-Z on 2009-10-22
Just right click the .exe file and choose Properties. Then navigate to Open With tab and choose Wine Windows Program Loader.

---

