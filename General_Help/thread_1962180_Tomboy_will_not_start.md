---
title: "Tomboy will not start"
date: 2012-04-20
forum: General Help
---

### Post by SunShadow on 2012-04-20
Hi,
I have Ubuntu 11.10 (64 bit), and I have a problem with Tomboy. Basically, when I try to start it, the indicator icon appears but it just hangs there. If I click on the icon, it shows no notes (while I have them, and I can open them in GNote), and none of the various options work.

Following an advice on another thread, I tried to run "tomboy --debug" in a terminal. The output is:

```
** Running Mono with --debug    **
[DEBUG 19:23:30.922] NoteManager created with note path "/home/luigi/.local/share/tomboy".
[INFO 19:23:31.440] Initializing Mono.Addins

```

and nothing else appears. It seems like it can't complete the operation.

I've already tried reinstalling tomboy and varios Mono packages, including everything I had installed which started with "libmono" and the Mono runtime, but the problem persists.

Is there anything I can do?

Thanks in advance! :-)

---

### Post by directhex on 2012-04-20
Try rm -r ~/.tomboy/addin-db00*

---

### Post by SunShadow on 2012-04-21
> **directhex said:**
> Try rm -r ~/.tomboy/addin-db00*

It doesn't work because "file or directory doesn't exist" (I'm not posting the actual error since it's in italian).
I verified: there is no ".tomboy" directory in my home folder (of course I'm showing hidden files). Is this normal?

---

### Post by kazztan0325 on 2012-04-21
> **SunShadow said:**
> I verified: there is no ".tomboy" directory in my home folder (of course I'm showing hidden files). Is this normal?

Hi SunShadow,

I am using Tomboy too.

**'addin-db00*'** folder should be located at **/home/*username*/.config/tomboy/**.

Please confirm it, and try to remove 'addin-db00*' again.
However I myself don't know if it would work for your case...

By the way, have you already done Settings for Tomboy?

---

### Post by SunShadow on 2012-04-21
> **kazztan0325 said:**
> Hi SunShadow,

I am using Tomboy too.

**'addin-db00*'** folder should be located at **/home/*username*/.config/tomboy/**.

Please confirm it, and try to remove 'addin-db00*' again.
However I myself don't know if it would work for your case...

By the way, have you already done Settings for Tomboy?

I confirm that it works! Tomboy now starts normally and it works as it should!

Thanks to both you and directhex for the help! :-)

EDIT: thread marked as solved

---

### Post by kazztan0325 on 2012-04-21
You are welcome, SunShadow!

I'm happy to hear you have solved the problem.

See you again someday somewhere in Forums.

---

