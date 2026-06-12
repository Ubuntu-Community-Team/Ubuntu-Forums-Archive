---
title: "Two or more proccess of Skype."
date: 2011-05-22
forum: General Help
---

### Post by kirill578 on 2011-05-22
I don't know if you have noticed but when you click the (X) on Skype window closes, but you can reopen it from the notification area, however if try to reopen it via shortcut on the desktop it will open a new process of skype. 

Is there a solution for this problem?

---

### Post by kd7swh on 2011-05-22
Hmm...

You could kill all skype processes from a terminal:

```
 sudo killall skype
```

Or list the running skype processes and kill just one of them:

```
 pgrep -l skype

222 skype
223 skype

 sudo kill 222
```

---

### Post by kirill578 on 2011-05-22
> **kd7swh said:**
> Hmm...

You could kill all skype processes from a terminal:

```
 sudo killall skype
```Or list the running skype processes and kill just one of them:

```
 pgrep -l skype

222 skype
223 skype

 sudo kill 222
```

That is not a problem to close the new skype window, it is just annoying.

I think that plugin like "minimize on start and close" (Thunderbird) would solve this. I have been looking for something like this but with no success

---

### Post by kirill578 on 2011-05-25
bump

---

