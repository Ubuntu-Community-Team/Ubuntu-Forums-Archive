---
title: "AutoKey / Python - Switch Active Window"
date: 2012-03-22
forum: General Help
---

### Post by sbarrow on 2012-03-22
I've searched everywhere and can't seem to get what I'm looking for. I have AutoKey installed and a few scripts and phrases defined. What i would like to do is have a script only execute if the active window is firefox. eventually I would like one that will switch to firefox and then execute other commands. 

If anyone can point me in the right direction I would greatly appreciate it. 

thanks

---

### Post by stinkeye on 2012-03-22
Edit: ...

---

### Post by sbarrow on 2012-03-22
Thanks anyway, but that didn't work.

---

### Post by mobilediesel on 2012-03-22
> **sbarrow said:**
> I've searched everywhere and can't seem to get what I'm looking for. I have AutoKey installed and a few scripts and phrases defined. What i would like to do is have a script only execute if the active window is firefox. eventually I would like one that will switch to firefox and then execute other commands. 

If anyone can point me in the right direction I would greatly appreciate it. 

thanks

In the Autokey settings, on the right there's a setting for Window Filter. Click on your script first then on "Set" to the right of "Window Filter" and enter ".* - Mozilla Firefox" into the box that comes up. Then save and it will only run that script in Firefox.
You can go to [http://code.google.com/p/autokey/w/list](http://code.google.com/p/autokey/w/list) for more help with Autokey.

---

### Post by sbarrow on 2012-03-22
I can't believe it was that easy and I wasted so much time on it. 

thanks a bunch

---

### Post by mobilediesel on 2012-03-23
> **sbarrow said:**
> I can't believe it was that easy and I wasted so much time on it. 

thanks a bunch

With something that has the potential that autokey has, it's easy to overthink what you're trying to do. Same thing with Linux in general, too.

---

