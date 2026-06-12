---
title: "Trying to find a pacakge to fix."
date: 2006-06-16
forum: General Help
---

### Post by Compucore on 2006-06-16
I wanted to do an update on my Dapper drake  on my old Aptiva 2185-281 computer. There was a update for gnome and some others a total of 56 of them. When I said okay to update. It mentioned that it couldn't download the updates until I fixs some pakcages. I went under Synaptic packages and manually ran Edit > fix packages to see where it could be. It came back with nothing that needed to be fixed. Is there a way to do a sudo command under the terminal to do the same and then manually fix it that way? Since Synaptic cannot find it and click on apply to let it do it by itself?

COmpucore

---

### Post by mlind on 2006-06-16
[QUOTE=Compucore]I wanted to do an update on my Dapper drake  on my old Aptiva 2185-281 computer. There was a update for gnome and some others a total of 56 of them. When I said okay to update. It mentioned that it couldn't download the updates until I fixs some pakcages. I went under Synaptic packages and manually ran Edit > fix packages to see where it could be. It came back with nothing that needed to be fixed. Is there a way to do a sudo command under the terminal to do the same and then manually fix it that way? Since Synaptic cannot find it and click on apply to let it do it by itself?

COmpucore[/QUOTE]

There was some sort of dependecy error when installing 'pcmcia-cs' package
You can see it by doing

```

sudo aptitude reinstall pcmcia-cs

```

---

### Post by Compucore on 2006-06-17
Yeah I had just tried that before w. ANd still nothing. Still can't do anything with Synaptic manager in trying to fix the suppose broken package. I am at a loss on that there.

Compucore


[QUOTE=mlind]There was some sort of dependecy error when installing 'pcmcia-cs' package
You can see it by doing

```

sudo aptitude reinstall pcmcia-cs

```[/QUOTE]

---

### Post by mlind on 2006-06-17
[QUOTE=Compucore]Yeah I had just tried that before w. ANd still nothing. Still can't do anything with Synaptic manager in trying to fix the suppose broken package. I am at a loss on that there.

Compucore[/QUOTE]

I guess it's a known bug for i686 and k7 kernels. You'll just have wait for a fix.

---

### Post by Compucore on 2006-06-17
Might be. But this is using the 386 kernel for the aptiva the is giving this specific  problem. My Dell computers never had this and it is running the 686 kernel on those. I am in the midst of actually trying the 686 kernel on the aptiva since teh AMD K6-2 400 to it since it is the equivilant to the PII class processor. 

Compucore

[QUOTE=mlind]I guess it's a known bug for i686 and k7 kernels. You'll just have wait for a fix.[/QUOTE]

---

