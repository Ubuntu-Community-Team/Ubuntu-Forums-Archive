---
title: "apt-get mozilla, gimp???"
date: 2006-06-25
forum: General Help
---

### Post by charles.g.moore on 2006-06-25
I'm trying to get firefox and GIMP, should i use apt-get or some other means.  

I would like to try doing it with a command line, I figured the more I use it the better i'll get at it...

Can someone tell me the best way to go about it?

If I were to download firefox onto the HDD can I just double click the file and have it load automatically? (Like Windows)  I don't want to necessarily do it that way but it's good to know as many ways to skin the cat as possible.

---

### Post by hippy4life on 2006-06-25
If I were to download firefox onto the HDD can I just double click the file and have it load automatically? yes this is possible, so long as you download a .deb file.

from a command line try this

sudo apt-get update

sudo apt-cache search gimp

then find the file exact file you want

sudo apt-get install <insert name of file here>

and your done!

of course if this is all too much hassle use the synaptic package manager, which is a graphical frontend to apt that will perform the same function

---

### Post by 23meg on 2006-06-25
[QUOTE=charles.g.moore]I'm trying to get firefox and GIMP,[/QUOTE]
May I ask why and how exactly, since both come preinstalled?

---

### Post by hippy4life on 2006-06-25
duh, thats a bloody good point actually!

lol

---

### Post by aysiu on 2006-06-25
[QUOTE=23meg]May I ask why and how exactly, since both come preinstalled?[/QUOTE]
They don't come preinstalled in Kubuntu.

---

### Post by hippy4life on 2006-06-25
[QUOTE=aysiu]They don't come preinstalled in Kubuntu.[/QUOTE]

well you learn something new every day, dont you? :-D

---

### Post by FredB on 2006-06-25
Erh, you could have find the answer by yourself ;)

This is why I dislike a little Kubuntu.

---

### Post by aysiu on 2006-06-25
[QUOTE=FredB]Erh, you could have find the answer by yourself ;)

This is why I dislike a little Kubuntu.[/QUOTE]
What?

---

### Post by 3rdalbum on 2006-06-25
You should definately install Firefox and The Gimp from the repositories, unless you need the absolute latest version (most people don't). You can do it with the command line if you like:

```

sudo apt-get update
sudo apt-get install firefox gimp

```

If you are asked if you want to install all the packages, type *y* and hit Enter.

(definately do the update step - the Firefox package has changed since Dapper's release)

---

### Post by FredB on 2006-06-25
[QUOTE=aysiu]What?[/QUOTE]

I appreciate ubuntu based distro, like Kubuntu, but not having firefox on your hard-drive if you install it, it is annoying.

Also, I was joking in my last sentence.

---

### Post by FredB on 2006-06-25
[QUOTE=3rdalbum]You should definately install Firefox and The Gimp from the repositories, unless you need the absolute latest version (most people don't). You can do it with the command line if you like:

```

sudo apt-get update
sudo apt-get install firefox gimp

```

If you are asked if you want to install all the packages, type *y* and hit Enter.

(definately do the update step - the Firefox package has changed since Dapper's release)[/QUOTE]

Firefox update is a security one. So if you use Firefox, it is better to have it up-to-date.

I disagree with "absolute latest version (most people don't)" because of security updates.

---

