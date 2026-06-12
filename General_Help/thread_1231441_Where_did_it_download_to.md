---
title: "Where did it download to?"
date: 2009-08-04
forum: General Help
---

### Post by cquigley on 2009-08-04
HI everyone-

 I d/l  a large file from a website, and it downloaded in the firefox's d/l manager. However when its done it doesn't show up in the designated folder I specfied.

I go into the d/l manager in firefox and click on it open it, but it will not open it. 

Does anyone know what is happening? Do I need to d/l again, if so how do d/l it and be able to open it?

Anyone help would be greatly appreciated,

thx
 cquigley

---

### Post by jocampo on 2009-08-04
> **cquigley said:**
> HI everyone-

 I d/l  a large file from a website, and it downloaded in the firefox's d/l manager. However when its done it doesn't show up in the designated folder I specfied.

I go into the d/l manager in firefox and click on it open it, but it will not open it. 

Does anyone know what is happening? Do I need to d/l again, if so how do d/l it and be able to open it?

Anyone help would be greatly appreciated,

thx
 cquigley

What did you download: ISO, Linux program, TAR, can you be more specific? You can browse to that directory and run the following command in order to find out what kind of file is that


```
file /home/cquigley/thefileidownladed.abc
```

Once executed, you'll get a better idea (in case you don't recognize the extension) of what did you download to your machine

---

### Post by BslBryan on 2009-08-04
Also you might try to right-click the file in the Download Manager and select "Open Containing Folder."

---

### Post by credobyte on 2009-08-04
Open terminal, replace filename with what you [COLOR=DimGray]have[/COLOR] downloaded & execute this command:
```
find $HOME -name "filename"

```

If it returns nothing, you haven't downloaded it ..

---

### Post by cquigley on 2009-08-04
thx everyone-

looks like it didn't actually d/l. It was a .iso of back-track from their website. I tried all your suggestions and still nothing.

I'll just d/l again and see what happens.

thanks,
 cquigley

---

