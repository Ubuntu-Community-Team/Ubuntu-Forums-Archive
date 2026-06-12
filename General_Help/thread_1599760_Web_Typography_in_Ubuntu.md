---
title: "Web Typography in Ubuntu"
date: 2010-10-18
forum: General Help
---

### Post by arturoherrero on 2010-10-18
Typography in web pages has never looked good in Linux. Why?

[COLOR=Blue][Web Typography in Ubuntu: Part 1]("http://www.kilobitspersecond.com/2010/05/03/web-typography-in-ubuntu-part-1/")[/COLOR] describes the problem

Could I install a package to be displayed correctly as in Windows or OSx.[COLOR=#000000] Some time ago I tried to install msttcorefonts, but I think everything was the same[/COLOR].

Any solution?

---

### Post by arturoherrero on 2010-10-19
Please!!!! I need help!!!!!

This problem is for all

---

### Post by Gibbs on 2010-10-19
> Typography in web pages has never looked good in Linux. Why?

Well that's your opinion, I beg to differ. 

However.. Web designers generally use "web safe" fonts which, as you've experienced, aren't web safe at all. Websites are "meant" to specify a font family so that should "Times" not be found then the systems default sans is used. That's either the problem or you don't like the system defaults.

Anyway what you're looking for is to probably to install the Microsoft "core" fonts? If so use this command in the terminal:
```
sudo apt-get install msttcorefonts && sudo fc-cache -fv
```

If that isn't the case then it might be down to your browser. For example in Firefox (Edit > Preferences > Content > Advanced) you can specify what font to fall back on.

---

### Post by qamelian on 2010-10-19
> **arturoherrero said:**
> Please!!!! I need help!!!!!

This problem is for all
It isn't a problem "for all". I don't have this problem at all. In fact, I prefer the way web typography looks in my browser in Linux compared to the same browser in Windows. I find the font rendering in Ubuntu to be much easier on my eyes.

---

### Post by Grenage on 2010-10-19
Indeed, I also refer Ubuntu rendering.

You said you tried with core fonts, did they install?  Do they exist?  Do they have the right names?

---

