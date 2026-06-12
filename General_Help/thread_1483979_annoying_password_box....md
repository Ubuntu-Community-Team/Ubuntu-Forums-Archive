---
title: "annoying password box..."
date: 2010-05-15
forum: General Help
---

### Post by Stancel on 2010-05-15
It seems like for so much I do, I have to type in my password. Is it really that necessary? I don't have a shared computer, it's just mine. I really don't think I need to type it every time I install something. Is there any way to change this? I tried going to System -> Administration -> Authorizations but I didn't see anything relating to installation of programs....

---

### Post by mcduck on 2010-05-15
> **Stancel said:**
> It seems like for so much I do, I have to type in my password. Is it really that necessary? I don't have a shared computer, it's just mine. I really don't think I need to type it every time I install something. Is there any way to change this? I tried going to System -> Administration -> Authorizations but I didn't see anything relating to installation of programs....

Is your computer connected to Internet? If yes, then you should consider the computer as a shared system, and handle the security like in any multiuser environment (as you are effectively trying to stay as the only user of the system...)

So yes, password confirmation for administration tasks is a really, *really* important part of the security in Linux. Actually pretty much the *most* important part. Restricted access to admin tasks and tight separation of user accounts is what makes it so hard to create viruses for Linux. Remove that and you end in the same situation where older Windows version were, anybody and anything being able to replace system files and install things without you even knowing about it...

But you shouldn't have to type it over and over again, you are probably doing things in some harder way than you should be...

---

### Post by K.Mandla on 2010-05-15
> **mcduck said:**
> Is your computer connected to Internet? If yes, then you should consider the computer as a shared system, and handle the security like in any multiuser environment (as you are effectively trying to stay as the only user of the system...)

So yes, password confirmation for administration tasks is a really, *really* important part of the security in Linux. Actually pretty much the *most* important part.

But you shouldn't have to type it over and over again, you are probably doing things in some harder way than you should be...
All of this is true, and is probably the best advice. 

On the other hand, if you like, you could assign a password to the root account, and use your computer as the superuser. Some distros do that by default, but the potential for mistakes or damage or security problems is magnified.

---

### Post by piedro on 2010-05-15
Hi! 

I don't know if you can switch it off ... (well I#m sure you can somehow!) but I think you shouldn't. 
Yes I know: That's none of my business ... 

The password you type in qualifies your commands as superuser or administrative commands. You have to type it manually and it's hopefully somehow individual. 

Any program running has the same or less user rights (by most parts) than you have. This way your subprocess of your webbrowser e.g. cannot install a virus or change a firewall setting or do something eslse you obviously wouldn't want (because in order to do that your webbrowser would have to type in your superuser password!) 

So it's not about your system doesn't trust you - it's about your system is avoiding any process or program to use administrative rights. That's why you never should use a browser as Superuser ... 

This whole concept is very simple (in theory) and very effective. 
Even the mighty Microsoft startet to copy it, because it seems to be without any good alternative. 

But I'm sure you can switch it off - I just wouldn't. 

thx for reading, 
piedro

---

### Post by Stancel on 2010-05-15
> **mcduck said:**
> Is your computer connected to Internet? If yes, then you should consider the computer as a shared system, and handle the security like in any multiuser environment (as you are effectively trying to stay as the only user of the system...)

So yes, password confirmation for administration tasks is a really, *really* important part of the security in Linux. Actually pretty much the *most* important part. Restricted access to admin tasks and tight separation of user accounts is what makes it so hard to create viruses for Linux. Remove that and you end in the same situation where older Windows version were, anybody and anything being able to replace system files and install things without you even knowing about it...

But you shouldn't have to type it over and over again, you are probably doing things in some harder way than you should be...

Interesting. I knew about Ubuntu being virus-proof and secure. But I didn't know it was because of this. An acceptable sacrifice, I guess.

---

