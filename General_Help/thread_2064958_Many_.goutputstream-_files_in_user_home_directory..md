---
title: "Many .goutputstream-* files in user home directory."
date: 2012-09-30
forum: General Help
---

### Post by kleenex on 2012-09-30
Hello, today I noticed, that in user home directory there is many (about 100) hidden files e.g. **[COLOR=SeaGreen].goutputstream-TTPPJV[/COLOR]** etc. Each file have different names, I mean entries after [COLOR=SeaGreen]**.goutputstream-**[COLOR=Black]. Does somebody know for what they are and what for? Can I safely delete them?[/COLOR][/COLOR]

---

### Post by PaulW2U on 2012-09-30
> **kleenex said:**
> Hello, today I noticed, that in user home directory there is many (about 100) hidden files e.g. **[COLOR=SeaGreen].goutputstream-TTPPJV[/COLOR]** etc. Each file have different names, I mean entries after [COLOR=SeaGreen]**.goutputstream-**[COLOR=Black]. Does somebody know for what they are and what for? Can I safely delete them?[/COLOR][/COLOR]

According to the bug report at [https://bugs.launchpad.net/xorg-server/+bug/984785](https://bugs.launchpad.net/xorg-server/+bug/984785) the files are created at shutdown. Yes, they can be deleted.

---

### Post by Scott Goodgame on 2012-09-30
It is the result of a bug.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)

Just delete them. You don't by any chance use ubuntu one do you?

---

### Post by vasa1 on 2012-09-30
> **Scott Goodgame said:**
> It is the result of a bug.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)

Just delete them. You don't by any chance use ubuntu one do you?
AFAICT, it's not related to using Ubuntu One.

---

### Post by stinkeye on 2012-09-30
...and it seems there's no hurry to fix it.
Have a hunded odd of these in Quantal.

---

### Post by kleenex on 2012-10-01
Hello, I do not use Ubuntu One. System has started normally after removing these files. According to **stinkeye **opinion I will create a simple script to remove these files and put it for example in cron task/directory. Of course until official fix appears. Thanks, "problem" solved.

Oh, one more thing. I should first check launchpad page before starting this topic. Sorry!

---

### Post by lunalui on 2012-10-23
I've just noticed my home folder is invaded by these files, too. (I have ubuntu one installed)

---

