---
title: "Linux versions of DVD Decrypter &amp; DVDSrink??"
date: 2006-03-02
forum: General Help
---

### Post by MJSOnline on 2006-03-02
Hi all.  I am after a program or programs that work like dvd decrypter and dvdsrink did on WIn XP.  I want to decrypt a DVD to VOB files... Pref GUI interface but dont mind comand line as long it makes sense.  Anyone got any ideas? Thanks. M

---

### Post by Ramses de Norre on 2006-03-02
```
sudo apt-get install dvdshrink dvdrip
```
And see which you like the most.

---

### Post by knalle on 2006-03-02
I have tried to get **dvdshrink** to work in **wine**, anybody?

---

### Post by Ramses de Norre on 2006-03-02
It's in the repo's, don't know which though.

---

### Post by MJSOnline on 2006-03-02
Thanks guys for your quick response.  I wil try them bioth out this weekend.  Do any of them decrypt a css dvd?  Are they GUI? M

---

### Post by akiro.yamamoto on 2006-03-02
DVD Shrink will work with wine. I used the version from WineHQ .deb 0.93 package.
With default settings.

---

### Post by akiro.yamamoto on 2006-03-02
knalle what problems were you getting with DVD Shrink and wine?

For all you out there who want to use the M$ version try this:
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
It's a little out dated but it will get you there.
YOU DO NOT NEED winesetuptk
Use the .deb packages from WineHq.com for best results ;) .
Ensure when you use "winecfg" you set your cd-rom drive properly.
The default is Local Hard Drive under the auto setting, change that to
CD_ROM (Click "Show Advanced" when you get to the "Drives" Tab)
The only extra setting I used is NT 4 for DVD Decrypter to work.

---

### Post by MJSOnline on 2006-03-02
Hi akiro.yamamoto.  I would rather not use wine as I would not like to run a windows app on linux as I worry about it being stable and the virus issue.  Any ideas? Anything in SPM? Thanks. M

---

### Post by akiro.yamamoto on 2006-03-02
Well without wine your options are Acidrip , dvd::rip. They are both available in the
repos. I don't use them because they do not give me the type of backup options I
need. I've heard great things about k9Copy but I have yet to try it. ;)

---

### Post by akiro.yamamoto on 2006-03-02
k9copy is available for dapper. but not for breezy, neither is it in the backports.

---

### Post by MJSOnline on 2006-03-02
Ok.  So if I install wine via S Package Manager I should be able to run dvd dcrypter and dvdsrink?  How do I do that? k9 does look good. but it is in french.  Would that change when its installed? M

---

### Post by knalle on 2006-03-02
[QUOTE=akiro.yamamoto]knalle what problems were you getting with DVD Shrink and wine?

For all you out there who want to use the M$ version try this:
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
It's a little out dated but it will get you there.
[/QUOTE]

didn't get this to work the dvdshring version i have (3.17) doesn't have the i/o tab that way and i can't recognice my dvdrom from dvdshring under wine.

---

### Post by MJSOnline on 2006-03-02
Anyone?

---

### Post by knalle on 2006-03-02
yes, i got dvdshrink to work. the first howto fixes the missing dvdrom, whats more was that i hadn't installed "libdecss2", after installing that dvdshrink seems to work, i'm half way trough a dvd now.

---

### Post by delsdog on 2006-03-30
I was using DVDShrink in Breezy, along with DVD Decrypter, both of which I set up using Mr.Bass guide mentioned earlier.

I've just installed K9copy in Dapper, and yes it comes up in English and not French, it looks pretty good as well, just putting it through its paces now. If it works well then I will have no need of the other two programs running in Wine.

---

### Post by John.Michael.Kane on 2006-03-30
[http://www.bunkus.org/dvdripping4linux/](http://www.bunkus.org/dvdripping4linux/)

---

