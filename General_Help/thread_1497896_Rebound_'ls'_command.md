---
title: "Rebound 'ls' command"
date: 2010-05-31
forum: General Help
---

### Post by MoshiMoshiMike on 2010-05-31
Hi, bit of a Linux n00b here, so please forgive me if this is fairly simple!

I (somewhat foolishly) lent someone my netbook the other night without supervision. He's rebound the 'ls' command, so that now when used it just returns the phrase "Aren't you glad I'm not evil?" XD

Whilst it is entertaining, I would rather like to fix this :P However, as mentioned, I am largely a n00b with Linux and most of the Google results have gone somewhat over my head. If anyone could point me in the right direction I'd be extremely grateful! Thanks!

---

### Post by sisco311 on 2010-05-31
Please post the output of:
```
alias ls
```
and
```
find / -name ls 2>/dev/null
```

---

### Post by MoshiMoshiMike on 2010-05-31
> **sisco311 said:**
> Please post the output of:
```
alias ls
```and
```
find / -name ls 2>/dev/null&
```

alias ls='echo aren'\''t you glad i'\''m not evil?'

and

```
mike@mike-eeePC:~$ find / -name ls 2>/dev/null&
[1] 1583
mike@mike-eeePC:~$ /bin/ls
/usr/share/locale/l10n/ls
/usr/lib/klibc/bin/ls


```

Thank you!

---

### Post by sisco311 on 2010-05-31
Run:
```
unalias ls
```

then edit the ~/.bashrc file and delete the "alias ls='echo aren'\''t you glad i'\''m not evil?'" line.

---

### Post by MoshiMoshiMike on 2010-05-31
Fantastic, thank you! :D

---

### Post by sisco311 on 2010-05-31
> **MoshiMoshiMike said:**
> Fantastic, thank you! :D

You're welcome! 

EDIT:
And welcome to the forums!

---

