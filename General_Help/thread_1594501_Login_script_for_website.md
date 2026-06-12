---
title: "Login script for website"
date: 2010-10-12
forum: General Help
---

### Post by cramie10 on 2010-10-12
Hi, I've not-so-recently got Linux, and have familiarized myself with how it works, and adapted it to work a little more easily, with help from you guys in getting my wireless working. Many thanks for that.
 Anyway I've been curious about writing a few basic scripts, and while I know bits and bobs of programming language, I don't know much 'Linux Language'. I don't even know what language the terminal uses, I think it's bash but I'd be thankful if someone might tell me, it seems to have bits and pieces from all other languages which I know.
 So what I was wondering, is it possible to write a log on script for a website. I've googled it and what comes up is how to write a log on script for your own website for people to log into. That's not what I mean, what I want is a script that I can run in the terminal which will physically log onto a website for me, like open up the web page and log on. I don't know if it's possible, is it? I know this is a big step for a beginner but I'd be really interested if its possible and if someone could show me.
 Also in your answer, please appreciate I know very little scripting and you'll have to take it slow with me, for even the things you guys are easily capable of I struggle with.
Many thanks! 
Matt

---

### Post by Chesamo on 2010-10-12
You mean entering authentication information? I've never heard of such a thing...

BASH is just Linux commands with some additional data structures, so unless the browser in question supports argument-based authentication, then you're SOL. The only browser I know of that supports it is lynx (and probably elinks), but it only works on basic authentication, not form-based authentication. Something you might want to look into is a password manager (most browsers ship with one; I know FF, Chromium, Opera and Epiphany do).

---

