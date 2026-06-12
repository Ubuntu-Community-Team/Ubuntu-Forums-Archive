---
title: "Software center on strike? O.o"
date: 2011-11-09
forum: General Help
---

### Post by xic816 on 2011-11-09
Just installed ubuntu 10.10 on my laptop. 
When I search for different applications in software center I cant find anything of what I used to
be able to find before!

Examples;
- Flash
- SKype
etc...

Why cant I find the stuff I used to? Have they made any modifications
that I don't know about? 

and I can find things that that I havn't seen before, like ubuntu user issue 7 etc...

Please advise

:confused:

---

### Post by Rubykuby on 2011-11-09
Have you enabled the Canonical partner repository?

I don't know how to do this in Gnome 2 shell, but I guess you'll find something that says "Software Sources". Enable the Canonical partner repository and you should be able to find it.

---

### Post by oldos2er on 2011-11-09
Run ```
sudo apt-get update
``` then retry your Software Center searches. The correct package name for flash is "flashplugin-installer".

---

### Post by xic816 on 2011-11-09
> **oldos2er said:**
> Run ```
sudo apt-get update
``` then retry your Software Center searches. The correct package name for flash is "flashplugin-installer".

Yeah I have managed to install both flash and skype but not with the help of S-C
I just updated -> no change

---

### Post by xic816 on 2011-11-09
> **Rubykuby said:**
> Have you enabled the Canonical partner repository?

I don't know how to do this in Gnome 2 shell, but I guess you'll find something that says "Software Sources". Enable the Canonical partner repository and you should be able to find it.

Yes, both the main and universe even tried to change the server to others -> best server

---

### Post by madjr on 2011-11-09
> **xic816 said:**
> Just installed ubuntu 10.10 on my laptop. 
When I search for different applications in software center I cant find anything of what I used to
be able to find before!

Examples;
- Flash
- SKype
etc...

Why cant I find the stuff I used to? Have they made any modifications
that I don't know about? 

and I can find things that that I havn't seen before, like ubuntu user issue 7 etc...

Please advise

:confused:

i think you are confusing 10.10 with 11.10

did you upgrade or fresh install?

---

### Post by sikander3786 on 2011-11-09
> **madjr said:**
> i think you are confusing 10.10 with 11.10

did you upgrade or fresh install?
And probably having a look at the OPs sources.list file and apt-get update outputs would help.

So, please get to a Terminal and post the outputs of these commands:

```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by xic816 on 2011-11-09
> **madjr said:**
> i think you are confusing 10.10 with 11.10

did you upgrade or fresh install?

hehe nop, I just went back to 10.10. 11.04 and 11.10 was 
to demanding for my computer

Fresh install

---

