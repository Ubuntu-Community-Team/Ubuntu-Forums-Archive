---
title: "GRUB Automatic Boot After Crash"
date: 2011-03-28
forum: General Help
---

### Post by Karmic Kiwi on 2011-03-28
I'm running Ubuntu 10.10 Server, and anytime my system crashes and starts back up, GRUB prompts for an OS to run. Since I'm usually not at my server to press enter, how do I get it to boot automatically?

---

### Post by mathgeek2000 on 2011-03-28
In /etc/default/grub:
the line
> 
GRUB_TIMEOUT=600

Time in seconds.

---

### Post by Karmic Kiwi on 2011-03-29
> **mathgeek2000 said:**
> In /etc/default/grub:
the line

Time in seconds.

Thanks, but that seems to be the timeout for a normal boot, but that seems to be overrridden in case of a system crash.

I know I can edit my /etc/boot/grub/grub.cfg:
```
if [ "$recordfail}" = 1 ]; then
[INDENT]set timeout=-1[/INDENT]
```
And set the timeout to something other than -1. But if I do that, would my changes be overwritten every time I update GRUB?

---

### Post by Krytarik on 2011-03-29
It seems like modifying those part of "/etc/grub.d/00_header" would be the trick then:
```
cat << EOF
if [ \${recordfail} = 1 ]; then
[B][COLOR=Blue]  set timeout=-1[/COLOR]
[/B]else
  set timeout=${GRUB_TIMEOUT}
fi
EOF
```But I guess those modification gets reverted when the package "grub-common" gets upgraded, however that seems not to happen too often.

Greetings.

---

### Post by Karmic Kiwi on 2011-03-29
> **Krytarik said:**
> It seems like modifying those part of "/etc/grub.d/00_header" would be the trick then:
```
cat << EOF
if [ \${recordfail} = 1 ]; then
[B][COLOR=Blue]  set timeout=-1[/COLOR]
[/B]else
  set timeout=${GRUB_TIMEOUT}
fi
EOF
```But I guess those modifications get reverted when the package "grub-common" gets upgraded, however that seems not to happen too often.

Greetings.

Awesome, that seems to do the trick. I'll just have to mess around with it. Thanks!

---

