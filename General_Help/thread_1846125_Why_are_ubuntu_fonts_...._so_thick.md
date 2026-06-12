---
title: "Why are ubuntu fonts .... so thick?"
date: 2011-09-18
forum: General Help
---

### Post by Zombithium on 2011-09-18
Hi ..!

I am back to using Ubuntu after about 4 years - mainly because my development environment has changed to Ubuntu (for good) ! However, just this one thing about the fonts keeps me nagging ...

I think every one would have noticed this, and would probably know the reason - as to why Ubuntu fonts are so 'thick' - if I may use that word to describe what i feel. This is in comparison to Windows fonts - I am absolutely newbie in font related terminology (like anti-aliasing etc).

I have a dual boot with Window7/Ubuntu 10.10 with the same resolution of 1366x768 in both - however, somehow there seems to be 'less space' to work with in Ubuntu. I believe this is something to do with the way fonts are rendered in Ubuntu Vs Windows ?

Can anyone please enlighten - why this major difference - and is it not a cause of concern among Ubuntu users? - because I have not seen many threads related to this issue. 

Also - is there a clean way of getting 'thin' fonts in Ubuntu - without many hacks and the complete Ubuntu environment looking seamless with these changes?

[P.S. this is posted from Windows after numerous failed attempts at posting from Ubuntu got stuck at Waiting from Ubuntuforums.org .... ]

---

### Post by Triblaze on 2011-09-18
Thick? Mine all seem fine, where do they seem thick? In a certain program? Everywhere?


Check your appearance settings, and go to the "fonts" tab. What are the settings there? Maybe they're set bigger than they should be.

---

### Post by NightwishFan on 2011-09-18
Why do people complain about fonts like it is the end of the world. You can try fixing settings with fontconfig, this works on Debian but I am not sure it works on ubuntu:
```
sudo dpkg-reconfigure fontconfig
```
then
```
sudo dpkg-reconfigure fontconfig-config
```

---

### Post by Zombithium on 2011-09-18
I think they are everywhere... all the applications, icon texts, menu items etc. This is just not with me but all the systems around me ..!

---

### Post by TeoBigusGeekus on 2011-09-18
Are your dpi settings correct?

---

### Post by Zombithium on 2011-09-18
Wow..! Thanks.. can't believe it was that simple - changing the DPI to a lower number did the trick..

---

### Post by pratikk on 2011-09-18
I'm not sure I understand what you mean by phat phonts, but I have noticed an irritating problem in word processing programs, most visible in Abiword: lag in writing/corrections which produces bent or pixellated characters and generally deformed text. When you write/edit a lot -- I do about 30,000 words a month, entirely under Ubuntu -- this becomes an issue. It's hard to explain, same as phat phonts, but the 'shape' of sentences and paragraphs becomes important. If you can see shapes clearly, you work faster and more surely. In Linux word processors, this is not always possible. Maybe screen refresh has something to do with it?

---

### Post by TeoBigusGeekus on 2011-09-18
Glad to hear it and don't forget to mark the thread as solved.

---

