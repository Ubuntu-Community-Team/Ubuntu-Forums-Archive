---
title: "I can't open IMDB web page"
date: 2010-08-20
forum: General Help
---

### Post by carpediem_dt on 2010-08-20
Greetings.

Well, that's pretty much about it. I just can't open the IMDB web page.  It never loads and the page is just blank. The firefox tab says:  "loading" and later says "the connection was reset" blablabla. It is the  only web page that I can't view so far.

What is going on? Help please.

Thank you in advance!

---

### Post by lovinglinux on 2010-08-21
See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by carpediem_dt on 2010-08-24
I did the first method, nothing happened. I tried the second method, and when I try to update grub on the terminal it says "/etc/default/grub: 9: quiet: not found"

so... help? =(

---

### Post by lovinglinux on 2010-08-24
```
gksudo gedit  /etc/default/grub
```

---

### Post by carpediem_dt on 2010-08-24
[SIZE=4]Yes. I did that and I changed "GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”. But in the last step, updating the grub, "[/SIZE]*[SIZE=4]sudo update-grub" it says "[/SIZE]*/etc/default/grub: 9: quiet: not found"

---

### Post by lovinglinux on 2010-08-24
> **carpediem_dt said:**
> [SIZE=4]Yes. I did that and I changed "GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”. But in the last step, updating the grub, "[/SIZE]*[SIZE=4]sudo update-grub" it says "[/SIZE]*/etc/default/grub: 9: quiet: not found"

Don't need to use capital letters. 

I'm sorry I didn't understand your last post correctly. I'm very busy these days withe some heavy coding and I guess my brain freezes sometimes.

Have you installed Ubuntu from Windows or are you using dual-boot?

I don't know why are unable to update grub. You will have to search some thread with the same issue. I don't know how to solve this problem.

---

### Post by carpediem_dt on 2010-08-25
About the capital letters... I didn't mean it, haha. Sorry. It's just the way I pasted it.

I don't have Windows at all. I have a complete Ubuntu installation.

I read about grub, but I only found how to upgrade it or installing it.

 It's very strange because I can open any web page I normally visit but imdb won't open. Another suggestion? 

Thank you very much.

---

### Post by carpediem_dt on 2010-08-25
Actually, I have kind of another issue... haha. This page, the ubuntu forums, I just realized that it loads very slow. It takes a while considering how my browser loads other pages. Any idea why?

---

### Post by Ralph L on 2010-08-25
[http://www.imdb.com/](http://www.imdb.com/) comes up fine on my lucid system using firefox.  The only change that I did that I can think of was to install flashplugin-installer with Synaptic.  I didn't even remove gnash.  I did this so I could play youtube videos, which wouldn't play with gnash.

Maybe this could help.

Ralph

---

