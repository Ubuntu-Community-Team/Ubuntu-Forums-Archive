---
title: "problem with desktop effects"
date: 2009-08-08
forum: General Help
---

### Post by tkblackbelt on 2009-08-08
How come randomly when im useing ubuntu the desktop effects will turn off and cant be enabled again unless i reinstall the os.

---

### Post by SoftwareExplorer on 2009-08-08
Do they ever turn on again after not working, even if it is random? Do you have any idea what brand your graphics card is?

---

### Post by CatKiller on 2009-08-08
> **chuckbenger said:**
> How come randomly when im useing ubuntu the desktop effects will turn off and cant be enabled again unless i reinstall the os.

That probably isn't true, you know.

---

### Post by DeMus on 2009-08-08
> **CatKiller said:**
> That probably isn't true, you know.

Just writing that doesn't help much. Explain why you wrote that so the OP can benefit from it.

---

### Post by CatKiller on 2009-08-08
> **DeMus said:**
> Just writing that doesn't help much. Explain why you wrote that so the OP can benefit from it.

Well, the OP hasn't said what the actual problem is, so no one can provide a fix. But the number of problems that **require** a re-install are vanishingly small. And this certainly isn't one of them. You've been here a while, you already know that.

My suspicion is that the OP has /apps/metacity/general/compositing_manager set, but without further details there's no way to be sure.

---

### Post by abhilashm86 on 2009-08-08
what actually happens?? compiz fails or you wont get a X server Graphics screen?? please explain in detail.......

---

### Post by starcannon on 2009-08-08
Lets have a look at a few things, I don't know if I can help, but we can at least get information collection going to aid in trouble shooting:

Please post the output of the following in a code box, its a lot of output, so please code box. You can insert code box tags by clicking the # upper right corner of your message editor window.
Find out your exact video card.
```

sudo lshw -C video

```Look at modules/drivers that are loaded
```

lsmod

```Is direct rendering working?
```

glxinfo

```
```

pstree | grep compiz

```
GL

---

