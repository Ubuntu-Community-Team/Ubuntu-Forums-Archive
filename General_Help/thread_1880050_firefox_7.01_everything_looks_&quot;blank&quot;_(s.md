---
title: "firefox 7.01 everything looks &quot;blank&quot; (see screenshot) in natty"
date: 2011-11-12
forum: General Help
---

### Post by malmsteen84 on 2011-11-12
Hi guys,
Recently I just realized that something is wrong with my firefox. Personally I use chromium most of the time. So here I uploaded 2 screenshots :

1. $ sudo firefox -a asdf
   everything looks just like what i think i should be seeing

2. $ firefox (this is the command in my firefox shortcuts in panel)
   everything becomes "clean", no text at all, GOOGLE logo still there  though (my assumption it's a picture).

Already remove, reinstall, erase the .mozilla folder, erase profiles, anything, but no result.

Any idea? I can just forget about this and go back to my chromium, but it's not a good way to live :)

---

### Post by lovinglinux on 2011-11-13
Never use sudo with Firefox. See the fifth item on [this list](http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions)

About the blank issue open “Edit >> Preferences >> Content” and click the “Advanced” button in the “Fonts & Colors” section, then edit the font size and color. Untick the option “Allow pages to use their own fonts, instead of my selections above”.

---

### Post by malmsteen84 on 2011-11-13
SOLVED!!

lovinglinux,
thanks for the suggestion. it worked! i knew somehow that this was about font, i did change the font to many different styles, but didn't "untick" that option. 

as i remember, i didn't set anything last time after my FF was still "okay" so strange thing happened.

about never use sudo, i read about this too. but if just "$ firefox -a asdf" it gave blank pages just like "$ firefox". i just wanted to give as many scenarios as possible for you guys to figure this problem out. many thanks!

ps)im in love with linux too :)

---

### Post by lovinglinux on 2011-11-13
> **malmsteen84 said:**
> SOLVED!!

lovinglinux,
thanks for the suggestion. it worked! i knew somehow that this was about font, i did change the font to many different styles, but didn't "untick" that option. 

as i remember, i didn't set anything last time after my FF was still "okay" so strange thing happened.

about never use sudo, i read about this too. but if just "$ firefox -a asdf" it gave blank pages just like "$ firefox". i just wanted to give as many scenarios as possible for you guys to figure this problem out. many thanks!

ps)im in love with linux too :)

You are welcome. Just keep in mind if you have executed Firefox with sudo recently, then you need to change the .mozilla folder ownership back to you, otherwise you will get problems.

---

