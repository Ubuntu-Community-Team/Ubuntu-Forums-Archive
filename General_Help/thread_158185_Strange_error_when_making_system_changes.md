---
title: "Strange error when making system changes?"
date: 2006-04-10
forum: General Help
---

### Post by scratched on 2006-04-10
I tried installing lilypond the other day, and now whenever I get any updates or use the synaptic package manager (and a few other things, I think), I get this error:
```
E: lilypond-data: subprocess post-removal script returned error exit status 1

```

I've tried removing lilypond with the synaptic manager and it get the same error. Any ideas what I might have done to cause this error and how I might fix it?....

I tried removing lilypond, and I got this error:
```
E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: 
subprocess new post-removal script returned error exit status 1

```

---

### Post by dcstar on 2006-04-10
[QUOTE=scratched]I tried installing lilypond the other day, and now whenever I get any updates or use the synaptic package manager (and a few other things, I think), I get this error:
```
E: lilypond-data: subprocess post-removal script returned error exit status 1

```

I've tried removing lilypond with the synaptic manager and it get the same error. Any ideas what I might have done to cause this error and how I might fix it?....

I tried removing lilypond, and I got this error:
```
E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: 
subprocess new post-removal script returned error exit status 1

```[/QUOTE]
In Synaptic, try Edit-Fix Broken Packages.

---

### Post by scratched on 2006-04-10
[QUOTE=dcstar]In Synaptic, try Edit-Fix Broken Packages.[/QUOTE]
I tried that already, it didn't work.:(

---

### Post by scratched on 2006-04-10
I fixed my problem. For anyone who might happen to have the same problem and comes across this thread, all I did was type in this line in the terminal
```
aptitude install tetex-bin
```

It takes a while to finish, but it fixed my problem

---

