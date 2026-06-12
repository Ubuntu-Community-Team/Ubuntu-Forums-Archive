---
title: "how do i start a program as minimized"
date: 2009-11-03
forum: General Help
---

### Post by colobix on 2009-11-03
HEy.
whats the command I need to use to start emesene minimized when ubuntu starts?
I meanm when I add emesene to sessions it will start with the emesene window opened.

---

### Post by HarmCla on 2010-03-06
Hi,

I'm looking for this command too.
Have you found any solution already?

I'm just gonna use "emesene" for now, it opens the contactscreen.

---

### Post by HarmCla on 2010-03-06
Hmm, this might be a solution. :)

[http://linuxinside.blogspot.com/2007/05/alltray.html](http://linuxinside.blogspot.com/2007/05/alltray.html)

---

### Post by wojox on 2010-03-06
Don't know about it being minimized. You could start it in the background using:

```
emesene &
```

Then when you want to access it open a terminal and:

```
jobs
```

```
fg <job_number>
```

---

### Post by wojox on 2010-03-06
> **HarmCla said:**
> Hmm, this might be a solution. :)

[http://linuxinside.blogspot.com/2007/05/alltray.html](http://linuxinside.blogspot.com/2007/05/alltray.html)

That will probably work better and easier.

---

