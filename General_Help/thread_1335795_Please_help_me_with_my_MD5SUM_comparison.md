---
title: "Please help me with my MD5SUM comparison"
date: 2009-11-23
forum: General Help
---

### Post by youbuntu on 2009-11-23
So I just downloaded the Karmic alternate CD, and MD5SUM checked the iso as:

3faa345d298deec3854e0e02410973dc

which is fine. I had an issue installing the software - the system just hangs, so I did this:

```

md5sum /dev/cdrom

```

and the MD5 is:

4efe95491193d465434f895c308bae5e


Have I got the command for MD5 checking the *burned CD* right?. If so, this is a failed burn, right?.

Thanks.

---

### Post by CharlesA on 2009-11-23
Looks right. Have you done an md5sum on the iso?

---

### Post by mikewhatever on 2009-11-23
Whoever said md5sum was for checking burnt cds?

---

### Post by CharlesA on 2009-11-23
> **mikewhatever said:**
> Whoever said md5sum was for checking burnt cds?

Says so right here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by bodhi.zazen on 2009-11-23
> **mikewhatever said:**
> Whoever said md5sum was for checking burnt cds?

It works, I do use this frequently to check the burn.

---

### Post by sldavid on 2009-11-23
glossywhite

Suggestion: Download another ISO image and see if you have trouble with that too. It could be your CD writer.

I had a similar problem except my CD would boot but fail in the middle of the installation. The MD5SUM passed and the "check CD option" from the main install menu passed as well. I went through about 10 CDs trying to fix the problem.

Long story short - I put a new (used) CD writer in my laptop and all problems went away.

---

### Post by mikewhatever on 2009-11-24
> **CharlesA said:**
> Says so right here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> **bodhi.zazen said:**
> It works, I do use this frequently to check the burn.

Indeed, thanks, didn't know that.

---

