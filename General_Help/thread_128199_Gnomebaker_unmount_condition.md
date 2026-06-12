---
title: "Gnomebaker unmount condition"
date: 2006-02-10
forum: General Help
---

### Post by mjunior on 2006-02-10
Hello guys,

I have a new issue that need your help. I've tried to burn a audio cd by using the soundjuicer to copy the files from a previous music cd and then burn into a empty cd by using gnomebaker.

The process runs smoothly until about 60% while the gnomebaker signs me it's performing a file conversion...and then..when the burning process actually begins I receive the following error: umount: /media/cdrom0: não montado 
and the Gnomebaker stucks..only closing by forcing quit...

Any clue?

---

### Post by cdhotfire on 2006-02-10
When you put in the cd does it show in "Places -> Computer"?

---

### Post by mjunior on 2006-02-14
Yes, the cd appears on my computer for sure..I can also use the soundjuicer normally as I said.

---

### Post by cdhotfire on 2006-02-14
Im asking, when you insert your blank cd. Because the error is saying your cd is not mounted.  So you might want to do
```

$ sudo mount -a

```
Once you insert your blank cd, then try gnomebaker.

---

### Post by mjunior on 2006-02-16
Oh sorry, my misunderstood..
The cd is mounting normally..by the way when I insert a blank CD the Ubuntu prompt me an option tab asking for open, burn,...

---

