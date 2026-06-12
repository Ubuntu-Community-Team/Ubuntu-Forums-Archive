---
title: "Nautilus with root access..."
date: 2009-10-18
forum: General Help
---

### Post by artheus on 2009-10-18
Hey!

I've got a little annoying problem using Nautilus.. Every time I want to open files as root through a Nautilus window I'll have to do

```
sudo nautilus
```

And I personally think that is annoying, as no-one else is going to use my computer, I'd like to open Nautilus with root access every time I open it.
As there is no valuable stuff in my computer, and I'm just playing around with Ubuntu to get to learn more about it, I don't feel that the security-breach in this is threatening at all..

So how could I make this happen, the easiest way? 

Cheers,
Artheus

---

### Post by zzzBrett on 2009-10-18
> **artheus said:**
> Hey!

I've got a little annoying problem using Nautilus.. Every time I want to open files as root through a Nautilus window I'll have to do

```
sudo nautilus
```

And I personally think that is annoying, as no-one else is going to use my computer, I'd like to open Nautilus with root access every time I open it.
As there is no valuable stuff in my computer, and I'm just playing around with Ubuntu to get to learn more about it, I don't feel that the security-breach in this is threatening at all..

So how could I make this happen, the easiest way? 

Cheers,
Artheus


One way would be to enable and log in as root (of course not recommended).

---

### Post by KlinerDraken on 2009-10-18
Add a "Custom Application Launcher" to one of you panels.

```
Name: what ever you want
Command: gksu nautilus
comment: again what ever you want
```

If you want to change the Icon just click on the pic of the icon on the left in that window.

you will have to enter your password when you launch it but thats better then running the command every time.

---

### Post by jward3010 on 2009-10-18
I found that annoying to begin with as I was used to root access based distros like Slax etc. but thats because of my dependence on the desktop was so high. I'm married to the terminal most of the time now (the best invention ever) and throwing sudo in front of commands is handy as hell. You'll gradually learn to love it. It's a brilliant security feature.

---

### Post by mike555 on 2009-10-18
You might want to get " nautilus-gksu " from package manager .......... then you can just rt. click on a file and open as admin .......

---

