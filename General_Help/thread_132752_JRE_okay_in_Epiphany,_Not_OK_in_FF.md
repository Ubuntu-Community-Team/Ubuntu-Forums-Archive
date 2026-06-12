---
title: "JRE okay in Epiphany, Not OK in FF"
date: 2006-02-18
forum: General Help
---

### Post by fishmorg909 on 2006-02-18
When I go to a JRE-type chatroom at Yahoo, Firefox tells me I need the JRE extension, even though it's already there. But if I go to the same chatroom with Epiphany, the chatroom runs. Epiphany will also run other Java stuff where FF won't. Is there a thread on how to fix this FF glitch? I can't seem to locate what I'm looking for. Thanks. :confused:

---

### Post by dcstar on 2006-02-18
[QUOTE=fishmorg909]When I go to a JRE-type chatroom at Yahoo, Firefox tells me I need the JRE extension, even though it's already there. But if I go to the same chatroom with Epiphany, the chatroom runs. Epiphany will also run other Java stuff where FF won't. Is there a thread on how to fix this FF glitch? I can't seem to locate what I'm looking for. Thanks. :confused:[/QUOTE]
Is the "libjavaplugin.so" file (or link) in your Firefox plugins directory??

If not, do a file search for it on your system and copy (or link it) to that directory.

---

### Post by nanotube on 2006-02-19
simple way to check if your java plugin is there in firefox is to go to the "about:plugins" page in firefox - that will list all plugins, and whether they are enabled. see if java stuff is there.
if not, then follow dcstar's instructions.

---

### Post by fishmorg909 on 2006-02-19
Hmm, no -- putting libjavaplugin.so in there didn't do it... (and it was not in there before I put it in.)

---

### Post by kaamos on 2006-02-19
Are you using ff 1.5 ? Where did you install it to?

---

### Post by JimS on 2006-02-19
...

--Curious--
Since Epiphany works,
why not stick with it,
at least for this job,
and not worry about FF??

J[COLOR="Blue"]imS
Postate Cancer Aware
[/COLOR]
...

---

### Post by fishmorg909 on 2006-02-19
[QUOTE=JimS]...

--Curious--
Since Epiphany works,
why not stick with it,
at least for this job,
and not worry about FF??
...[/QUOTE]
 
Are you kidding, Sir? Firefox has its share of problems, but the SHEER JOY of sailing the web without pesty ads or VILE, FETID, EYE-TWITCH FLASH ADS is worth it. \\:D/ 

Anyway -- I solved it when I copied a link to libjavaplugin_oji.so in my FF 1.5 plugins folder. (The Mozilla/FF plugin page sez it's important to make a link, no use the plugin itself, to avoid crashes on startup.)

(Epiphany and Opera are great, but I sure do wish they had AdBlock and BlockFlash (with the clickable 'on' button).) :???:

---

### Post by fishmorg909 on 2006-02-19
[QUOTE=kaamos]Are you using ff 1.5 ? Where did you install it to?[/QUOTE]

I installed FF 1.5 in a seperate folder ("opt") in the Home folder... which is why I had to install the libjavaplugin_oji.so link.

---

### Post by Perfect Storm on 2006-02-19
> (Epiphany and Opera are great, but I sure do wish they had AdBlock and BlockFlash (with the clickable 'on' button).) 

I've heard that they are working on it and Epiphany gonna have it in the 2.14 release of Gnome.

---

### Post by JimS on 2006-02-19
...

I have had no problem with ads
using Epiphany than using FF (not 1.5).
My software is very up-to-date (except FF),
so that is probably why.

I have stopped using FF,
only because E is a bit lighter on its feet.
I still use TBird, but may experiment with
something lighter.

I may be an old man,
but "Sir" is not necessry.
I sit here in the afternoon in my PJs.
Retirement is nice, when there are so
many interesting things to do.

Wife is calling me to ...

MVH (Danish)

J[COLOR="Blue"]imS
Prostate Cancer Aware
[/COLOR]
...

---

### Post by Red Ghost on 2006-02-19
[QUOTE=fishmorg909]Are you kidding, Sir? Firefox has its share of problems, but the SHEER JOY of sailing the web without pesty ads or VILE, FETID, EYE-TWITCH FLASH ADS is worth it. \\:D/ 

Anyway -- I solved it when I copied a link to libjavaplugin_oji.so in my FF 1.5 plugins folder. (The Mozilla/FF plugin page sez it's important to make a link, no use the plugin itself, to avoid crashes on startup.)

(Epiphany and Opera are great, but I sure do wish they had AdBlock and BlockFlash (with the clickable 'on' button).) :???:[/QUOTE]
An extension that is exactly the same and blocks most ads by default is already in epiphany. sudo apt-get install epiphany-extensions. Then check it in the options.

---

### Post by dcstar on 2006-02-19
[QUOTE=fishmorg909]Hmm, no -- putting libjavaplugin.so in there didn't do it... (and it was not in there before I put it in.)[/QUOTE]
Have a read of this and see if it can help you:

[http://plugindoc.mozdev.org/faqs/java.html](http://plugindoc.mozdev.org/faqs/java.html)

Just out of interest, the /usr/local/firefox/plugins/libjavaplugin.so file in my system is linked to:

/usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

---

