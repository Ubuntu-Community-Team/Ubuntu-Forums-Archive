---
title: "How can i get internet explorer on my laptop?"
date: 2009-09-26
forum: General Help
---

### Post by BabiiNiya on 2009-09-26
how can i get internet explorer on my laptop...

---

### Post by sports fan Matt on 2009-09-26
I think IE4LINUX would work..is there a particular reason why you need it?

---

### Post by wakojakop on 2009-09-26
> **sox fan Matt said:**
> I think IE4LINUX would work

Wine is a good option too

---

### Post by BabiiNiya on 2009-09-26
> **sox fan Matt said:**
> I think IE4LINUX would work..is there a particular reason why you need it?


well yes there is....most of the website i go on in firefox doesnt really show as much as IE

---

### Post by wakojakop on 2009-09-26
but some websites are made for firefox, like scripting and stuff

---

### Post by MelDJ on 2009-09-26
do you mean you cant see sites that use silverlight?

---

### Post by BabiiNiya on 2009-09-26
> **wakojakop said:**
> but some websites are made for firefox, like scripting and stuff

well also i dont really like firefox

---

### Post by BabiiNiya on 2009-09-26
> **MelDJ said:**
> do you mean you cant see sites that use silverlight?


you can say so

---

### Post by MelDJ on 2009-09-26
try moonlight then: [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

---

### Post by river226 on 2009-09-26
> **MelDJ said:**
> do you mean you cant see sites that use silverlight?

if that is the problem just download moonlight:
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by wakojakop on 2009-09-26
but have you seen the new personas addon for firefox

---

### Post by BabiiNiya on 2009-09-26
> **river226 said:**
> if that is the problem just download moonlight:
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

what do i do after that i download it

but sorry for changing the subject but i really need help on this too...
do anyone know how to fix the update manager...
it keep saying that there is an error: something 57 source or something like that...
any suggestion how i fix this

---

### Post by BabiiNiya on 2009-09-26
> **wakojakop said:**
> but have you seen the new personas addon for firefox

what is that

---

### Post by MelDJ on 2009-09-26
> **BabiiNiya said:**
> what do i do after that i download it

but sorry for changing the subject but i really need help on this too...
do anyone know how to fix the update manager...
it keep saying that there is an error: something 57 source or something like that...
any suggestion how i fix this

it will be like a plugin like firefox. you just have to install it thats all. personas is an add-on for firefox which lets you change the theme of the browser. you just have to click the theme you want and it will change to it automatically. could you post the update error here or give us a screenshot?

---

### Post by BabiiNiya on 2009-09-26
> **MelDJ said:**
> it will be like a plugin like firefox. you just have to install it thats all. personas is an add-on for firefox which lets you change the theme of the browser. you just have to click the theme you want and it will change to it automatically. could you post the update error here or give us a screenshot?

this is the error: E: Type 'wget' is not known on line 57 in source list /etc/apt/sources.list

---

### Post by MelDJ on 2009-09-26
screenshot please:KS

---

### Post by BabiiNiya on 2009-09-26
> **MelDJ said:**
> screenshot please:KS

how do i do that

---

### Post by MelDJ on 2009-09-26
press print screen on your keyboard or go to applications-accesories-take screenshot.
the screenshot will be on your desktop.
come back here and press manage attachments and upload the screenshot

---

### Post by CatKiller on 2009-09-27
> **BabiiNiya said:**
> this is the error: E: Type 'wget' is not known on line 57 in source list /etc/apt/sources.list

Why have you been sticking stuff in sources.list?

You've put the wrong line in there.

For some reason, on line 57 of that file, you've put a wget line in there. Take it out the same way you put it in there and it will magically work again.

---

### Post by BabiiNiya on 2009-10-18
> **CatKiller said:**
> Why have you been sticking stuff in sources.list?

You've put the wrong line in there.

For some reason, on line 57 of that file, you've put a wget line in there. Take it out the same way you put it in there and it will magically work again.



i dont know what and how it's in there...can someone help me with it...

---

### Post by jward3010 on 2009-10-18
> **BabiiNiya said:**
> how can i get internet explorer on my laptop...

I crapped myself laughing at this, I'm sorry dude, but thats funny!!!

I mean [SIZE="5"]WHY!![/SIZE]

---

### Post by sync on 2009-10-18
If you just straight up don't like Firefox, there's other options out there for browsing.  Opera, Google's Chrome, etc.  I personally wouldn't recommend running IE, but if you need to, then yeah, just run it in Wine.

---

### Post by jward3010 on 2009-10-18
Out of interest what Silverlight stuff is out there that might be worth looking at?

---

### Post by CatKiller on 2009-10-18
> **BabiiNiya said:**
> i dont know what and how it's in there...can someone help me with it...

Whatever that line is, you put it there. It didn't do it by itself. ```
gksudo gedit /etc/apt/sources.list
```will open that file for editing. Find line 57. It's the one that starts with *wget*. Delete that line. Save the file.

---

### Post by wilee-nilee on 2009-10-18
> **MelDJ said:**
> it will be like a plugin like firefox. you just have to install it thats all. personas is an add-on for firefox which lets you change the theme of the browser. you just have to click the theme you want and it will change to it automatically. could you post the update error here or give us a screenshot?

 Are you referring to User Agent Switcher.

---

### Post by HomoGleek on 2009-10-19
Personas is something very different from UAS, its basically a skinning add-on for firefox.

---

### Post by wilee-nilee on 2009-10-19
> **DarrenTod said:**
> Personas is something very different from UAS, its basically a skinning add-on for firefox.

 Thanks I used to install something like personas, maybe it was it actually but it wasn't stable, like the set up of personas though.

---

