---
title: "Compiz ; Installed (local or obsolete) - something is wrong"
date: 2010-08-03
forum: General Help
---

### Post by winchendonsprings on 2010-08-03
As of about a week ago I noticed Compiz and its counterparts are in the Installed (local or obsolete) section of synaptic. I can't find any package I removed or altered that could have caused this.

Has this happened to anyone else? 

I also noticed, and I'm sure they are related, that when running Virtualbox I can no longer resize the window and have the VM fit the new window size. Also anything that needs composting inside the VM is having problems.

Any ideas?

---

### Post by kerry_s on 2010-08-03
you try clicking reload?

---

### Post by winchendonsprings on 2010-08-03
yes, for the most part I do all my updates from within synaptic.

---

### Post by stinkeye on 2010-08-04
Have you enabled the compiz ppa?
or another ppa that contains compiz packages?

If you look at my screenie for compiz installed version I have
```
1:0.8.4-0ubuntu15
```

Although It's hard to see your version looks like it has
something else after the 1:0.8.4-0ubuntu15

Try  checking it's origin.

---

### Post by winchendonsprings on 2010-08-05
I did not have the compiz ppa enabled. I only had compiz from the main repository I guess. So, I enabled the compiz ppa and that seemed to fix the problem for that. Previously at the same time that compiz jumped to the Installed (local or obsolete) section so did indicator-application. 

Any idea how I can fix that? It appears I have them installed from the main repository so I'm not exactly sure why they are there.

---

