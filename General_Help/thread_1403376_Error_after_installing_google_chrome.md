---
title: "Error after installing google chrome"
date: 2010-02-10
forum: General Help
---

### Post by colobix on 2010-02-10
Now when I try to install or manage a package or anything i get this error:
E:_Cache->open()..
and it tells me something about an archive log I have to go to to fix this thing. wtf is this?

---

### Post by 3rdalbum on 2010-02-10
> **colobix said:**
> Now when I try to install or manage a package or anything i get this error:
E:_Cache->open()..
and it tells me something about an archive log I have to go to to fix this thing. wtf is this?

I can't really tell by what you've posted - can you please copy and paste the exact error message into this thread?

---

### Post by colobix on 2010-02-10
I can't copy/paste from sypnatic for some reason, but it says something like
E:type<Chromium>unknown line 57 in source list etc/apt
sorry if that's not 100 procent right but that's all I can remember.

---

### Post by 3rdalbum on 2010-02-10
You've modified the /etc/apt/sources.list file, I imagine, to include an external repository. However, you've made a mistake and this is confusing the package manager.

Edit the file again:

```
gksudo gedit /etc/apt/sources.list
```

On line 57, where the mistake is, either correct your mistake or "comment-out"* the line by putting a # symbol at the beginning of the line.

Save your changes and close the text editor. You can now go to Synaptic and hit Reload and your package manager will work again.

In future, use the Software Sources program to add new repositories, as it prevents these sorts of mistakes from happening. Very common problem as you can tell by my signature!

*comment-out: When a line begins with a #, the computer will ignore it. We use this to put comments into computer-readable files, hence the term "commenting-out".

---

### Post by colobix on 2010-02-10
aha that's what it means. ohkay. thanks alot.
Btw, I found the mistake. I copied and pasted some extra text and stuff lol.
Good to get that out of the way, and thanks alot :)

---

