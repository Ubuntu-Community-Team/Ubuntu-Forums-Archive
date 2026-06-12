---
title: "Where can I find flash game saves?"
date: 2011-07-19
forum: General Help
---

### Post by chabos9 on 2011-07-19
So I've been playing a very long flash game called anti idle lately.  I have a bunch of hours of time playing it, and I want to back up my save.  But I can't find where it is.  The FAQ for the game says it should be under ~/.macromedia/Flash_Player/#SharedObjects/(random letters/numbers)/chat.kongregate.com/antiIdle_file0.sol 
Bash apparently recognizes the file path, at least up to #SharedObjects, I was able to CD to it without problem.  But because the next part is random, I can't go further.  I tried looking with Nautilus, but the macromedia folder isn't coming up, even with view hidden files enabled.  So, does any one have a way to get to the file?  It seems like typing the file path into Nautilus would work, if I could get it to display file paths instead of just the stupid icon things on the top bar.  Any help will be greatly appreciated.
Thanks,
Chabos.

---

### Post by lovinglinux on 2011-07-20
Try this:

```
cp ~/.macromedia/Flash_Player/#SharedObjects/**/chat.kongregate.com/antiIdle_file0.sol ~/Desktop/antiIdle_file0.sol
```

---

### Post by chabos9 on 2011-07-20
That worked.  Thank you.

---

### Post by lovinglinux on 2011-07-20
> **chabos9 said:**
> That worked.  Thank you.

You are welcome.

---

