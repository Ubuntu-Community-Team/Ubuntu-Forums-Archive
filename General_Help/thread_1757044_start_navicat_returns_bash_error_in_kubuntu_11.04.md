---
title: "start_navicat returns bash error in kubuntu 11.04"
date: 2011-05-13
forum: General Help
---

### Post by walter_j on 2011-05-13
Running start_navicat script in kubuntu 11.04 returns bash error ./start_navicat: 10: arithmetic expression: expecting EOF: "2*100+13 2". The same navicat version runs fine in ubuntu 10.10 and 10.04. I tried deleting navicat folders - including hidden folders and reinstalling, but get the same error.

Can't test ubuntu 11.04 because i can't get it running (black screen - even grub). xubuntu 11.04 is very unstable too. kubuntu 11.04 is very stable otherwise.

no idea what to do, other than continue using ubuntu 10.10 (which is the best ubuntu version to date imho)

---

### Post by bsulzen on 2011-05-15
Same issue here, but in Ubuntu 11.04. Never had problems in previous releases of Ubuntu

---

### Post by elbunuelo on 2011-05-15
Greetings from Colombia.
I had the same error and I have just solved it, it's pretty simple, actually

Just replace the tenth line of the start_navicat script with this 

```
MINOR=`echo $VERSION_STR | cut -d. -f2 | cut -d" "  -f1`
```

What happens is that when the script gets the glibc version it is returned twice for some reason. So, instead of being 2.13 it gets 2.13 2.13, and when it parses the minor version of the string what it gets is 13 2 instead of just 13 and that is what causes the script to crash.
What I did to fix it was to add an extra operation to get the portion of the version before the whitespace using ```
cut -d" "  -f1
```

I hope that I made myself clear and that my solution is useful to you

---

### Post by walter_j on 2011-05-15
I tried this fix, but now the script completes w/o doing anything. No error either.

I saw that it was returning the major version twice, but I don't know my way around bash scripts to correct the error.

Can you recheck your modification?

OK. Reinstalled, and it's working. Seems like there might be a grep error in a previous line?

---

### Post by hayvanAdam on 2011-05-16
thanks elbunuelo, It's fixed me.

---

### Post by bsulzen on 2011-05-16
Brilliant! Worked for me as well. Thanks.

---

### Post by teo69 on 2012-09-21
thanks elbunuelo, It's fixed me too.

---

