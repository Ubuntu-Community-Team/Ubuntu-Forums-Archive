---
title: "Trying to install drivers for my ATI 9800"
date: 2006-04-29
forum: General Help
---

### Post by pkulak on 2006-04-29
Okay, so I got most of the way down this tutorial (method 2):

[http://ubuntuforums.org/newthread.php?do=newthread&f=99](http://ubuntuforums.org/newthread.php?do=newthread&f=99)

except when I try to do:

```

sudo module-assistant prepare,update

```

I get:

```

sudo module-assistant prepare,update

```

I googled all over for that package, but I can't find it. Am I missing something? Thanks!

---

### Post by pkulak on 2006-05-02
Crap, I'm sorry about that. I didn't look at what was in my clipboard before I pasted. This is the guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Alright, well, I think this is a bit more relevent. When I install the first option (from the repos) and I type fglrxinfo I get:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I was under the impression the vendor string should say something about my 9800. Anyway, any help is much apreciated.

---

### Post by jecos on 2006-05-02
[QUOTE=pkulak]Crap, I'm sorry about that. I didn't look at what was in my clipboard before I pasted. This is the guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Alright, well, I think this is a bit more relevent. When I install the first option (from the repos) and I type fglrxinfo I get:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I was under the impression the vendor string should say something about my 9800. Anyway, any help is much apreciated.[/QUOTE]


You posted the dapper guide??  you need to use the Breezy guide.
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

---

### Post by pkulak on 2006-05-02
Actually, I posted this in the wrong forum... this thread probably just needs to be deleted. I think it was about 2 in the morning when I posted it, and there are no redeming qualities at all. :D

---

