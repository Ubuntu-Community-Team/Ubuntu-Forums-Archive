---
title: "no 3d acceleration, but can see nvidia logo at startup ??"
date: 2006-06-12
forum: General Help
---

### Post by c-m on 2006-06-12
As per title, I have nvidia-glx installed and when X boots I get the nvidia splash screen, but when i test in cedega or wheni run glxgears manually, I do not have 3d acceleration at all?

Can anyone help with this at all please?

---

### Post by bluevoodoo1 on 2006-06-12
What does...

```
glxinfo | grep rendering
```

tell you?

---

### Post by c-m on 2006-06-12
carl@carl:/media/windows$ glxinfo | grep rendering
direct rendering: Yes
carl@carl:/media/windows$

---

### Post by bluevoodoo1 on 2006-06-12
Then it *should* be on. 

glxgears isn't a "benchmark" tool (see 2nd command) but if you like, you can see your FPS with...

```
glxgears -printfps
```
or 
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

If 3d acc. isn't working in cedega, then it's beyond me (I have no experience with cedega)

---

### Post by c-m on 2006-06-12
its not that its not working in cedega its not working fullstop. cedega does a test using glxgears. 

Glxgears is incredibly slow.

could it be that a second screen (tv out) is enabled in the xorg.conf, but i don't have anything else attached apart from my single display

---

### Post by bluevoodoo1 on 2006-06-12
[QUOTE=c-m]its not that its not working in cedega its not working fullstop. cedega does a test using glxgears. [/quote]

Ok

[QUOTE=c-m]Glxgears is incredibly slow.[/quote]
Do you have other apps open?

[QUOTE=c-m]could it be that a second screen (tv out) is enabled in the xorg.conf, but i don't have anything else attached apart from my single display[/QUOTE]

Hmm, I don't know, you could try turning it off, and see if there's a difference.

What video card do you have?

---

### Post by c-m on 2006-06-12
deleted the tvout options in xorg.conf but still i have no 3d aceleration.

I have an nvidia 5600.

---

### Post by grte on 2006-06-12
[QUOTE=bluevoodoo1]What does...

```
glxinfo | grep rendering
```

tell you?[/QUOTE]

Sorry for the hijack, but I noticed something here, and I hope it'll be a quick resolution.  I also have nvidia-glx installed, the nvidia driver is selected in xorg.conf, and I get the splash screen at start.  I'm using a Geforce 6800XT.  However, when I do the specified command, I get this:

```
direct rendering: No
```

How can I fix that?

---

### Post by NESFreak on 2006-06-12
does it says that it doesn't work or doesn't it work. cause cedega also says that there is something wrong with my 3d setup, but i just ignored it because i can play 3d games (in cedega) so this means that the damn testing tool is screwed. LOL

---

### Post by bluevoodoo1 on 2006-06-12
Perhaps something from this link might help...
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

The author, tseliot is very good with nvidia issues.

---

