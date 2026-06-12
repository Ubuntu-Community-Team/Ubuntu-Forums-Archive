---
title: "brasero/dvd creator burning corrupted dvds"
date: 2010-12-22
forum: General Help
---

### Post by burningfail on 2010-12-22
i had used cd/dvd creator (that i think use brasero) for burning data dvds for years.
dont remember having any problem until 10.10
since installed the new version, only corrupted dvds are created, same laptop with 10.04 worked fine

---

### Post by TeoBigusGeekus on 2010-12-22
Try with growisofs from command line:
```
growisofs -Z /dev/dvd -R -J -speed=whateveryouwant /path/to/files/and/folders/
```
If that gives you corrupted dvds as well, I think it's time for a new cdr.

---

### Post by owiknowi on 2010-12-22
> **burningfail said:**
> i had used cd/dvd creator (that i think use brasero) for burning data dvds for years.
dont remember having any problem until 10.10
since installed the new version, only corrupted dvds are created, same laptop with 10.04 worked fine

have my fair share of problems with brassero too:
corrupted/unreadable cd/dvd's, not being able to use the appropriate extension to burn dvd's (have to use "burn data cd or dvd" where "burn movie" is applicable, can't burn 800MB cd's, etc.).

and of course tested on 6 pc's and 1 externeal cd/dvd recorder.

never had those problems in the past with k3b.

but since i'm not a programmer, who am i to complain? ;)

btw. TeoBigusGeekus: also make GIS app's like arcgis available to linux...

---

### Post by TeoBigusGeekus on 2010-12-22
> **owiknowi said:**
> ...btw. TeoBigusGeekus: also make GIS app's like arcgis available to linux...
Amen.

---

### Post by amjjawad on 2010-12-22
Not a direct answer/fix to your problem but I use K3b and I don't have any problem with it at all.

---

### Post by owiknowi on 2010-12-22
> **amjjawad said:**
> Not a direct answer/fix to your problem but I use K3b and I don't have any problem with it at all.

k3b is by far my favorite burning app.
adding it to ubuntu (10.04.1) though, it adds a 350MB of extra data.

i wouldn't mind using kubuntu but since v.4.x, it's to "ms titanic like" for my taste.

do you, or anyone else, perhaps know a way of installing k3b in ubuntu using less MB's?

---

### Post by amjjawad on 2010-12-22
> **owiknowi said:**
> k3b is by far my favorite burning app.
adding it to ubuntu (10.04.1) though, it adds a 350MB of extra data.

i wouldn't mind using kubuntu but since v.4.x, it's to "ms titanic like" for my taste.

do you, or anyone else, perhaps know a way of installing k3b in ubuntu using less MB's?

What do you mean by adding 350MB of extra data? could you please explain that?

I have 9 OS's, Kubuntu one of them but my main OS is Ubuntu. You can install K3b on Ubuntu. Just go to Synaptic and install it from there. NO need to install Kubuntu.

---

### Post by TeoBigusGeekus on 2010-12-22
> **amjjawad said:**
> What do you mean by adding 350MB of extra data? could you please explain that?

I have 9 OS's, Kubuntu one of them but my main OS is Ubuntu. You can install K3b on Ubuntu. Just go to Synaptic and install it from there. NO need to install Kubuntu.
I think he means the huge kde dependencies.

---

### Post by amjjawad on 2010-12-22
> **TeoBigusGeekus said:**
> I think he means the huge kde dependencies.

Oh ok, that makes sense :)

---

### Post by owiknowi on 2010-12-22
> **amjjawad said:**
> Oh ok, that makes sense :)

to be exact it's 313MB that has to be installed on top of my ubuntu installation to be able to use k3b.
all addictions, eh, dependencies i mean. ;)

and i have 10 os on my notebook, unless windos is not really a os...

---

### Post by amjjawad on 2010-12-22
> **owiknowi said:**
> to be exact it's 313MB that has to be installed on top of my ubuntu installation to be able to use k3b.


Quite honestly, I don't remember how much it required. I installed it long time ago, perhaps 3 months or something.
Nero requires more space if I'm not mistaken. Not to mention that Windows, by time, it gets slower, slower and slower.

I should stop saying the "W" word :D

---

### Post by owiknowi on 2010-12-23
> **amjjawad said:**
> Quite honestly, I don't remember how much it required. I installed it long time ago, perhaps 3 months or something.
Nero requires more space if I'm not mistaken. Not to mention that Windows, by time, it gets slower, slower and slower.

I should stop saying the "W" word :D

you brought it up yourself... ;)
and since ms vs. lindows i would be careful to use that word at all.
even when you have a broken w....., eh what should i call it: see through viewing device, ventana, raam, fenêtre...

so, having your best interest in mind, yes really, avoid it all to getter.
you can even ask a refund when it's sold with a pc and you don't want to use it (depending on where you live, alas).

back to the topic at hand:
i did a fake installation of k3b on ubuntu 10.04.1 and 313MB was needed for installation.
lot's of kde stuff will be installed like icons and sum such.

for now still recommend k3b instead of brasero though.
however i must admit that brasero is getting better with every release!

---

### Post by amjjawad on 2010-12-23
> **owiknowi said:**
> i did a fake installation of k3b on ubuntu 10.04.1 and 313MB was needed for installation.
lot's of kde stuff will be installed like icons and sum such.

for now still recommend k3b instead of brasero though.
however i must admit that brasero is getting better with every release!

I'll install it on my other PC and see how much it requires.
I have lots of stuff to do now but sooner or later, I'll install it on my other PC.
K3b is great indeed.

---

### Post by owiknowi on 2010-12-23
> **burningfail said:**
> i had used cd/dvd creator (that i think use brasero) for burning data dvds for years.
dont remember having any problem until 10.10
since installed the new version, only corrupted dvds are created, same laptop with 10.04 worked fine

hi burningfail,

been sliding off topic a bit, sorry for that.
is your problem solved or can you nevertheless do something with the answers (for example install k3b)?

if not go back to the first answer from TeoBigusGeekus or just let us know!
;)

---

### Post by Habitual on 2010-12-23
> **owiknowi said:**
> ... what should i call it: see through viewing device, ventana, raam, fenêtre...

a Pane in the glass!

---

