---
title: "Terminal output from apt-get is stuck in Japanese."
date: 2011-04-21
forum: General Help
---

### Post by FoobyZeeky on 2011-04-21
Hi,

I recently installed Ubuntu 10.10 x64 alongside my Windows 7 installation. I'd used Ubuntu a bit before so I knew the basics. I started messing around with language packs a bit, because I wanted to get a Japanese input method working. However, this didn't go as expected, and the entire OS changed its main language to Japanese (I hadn't wanted this, Japanese wasn't anywhere near the top of the list in Language Support). I corrected this by uninstalling the language pack for Japanese. However, it still seems to be there...

The OS is in English, except for a couple of things. For starters, all output from the apt-get command in the terminal is shown in Japanese, seemingly inexplicably. Secondly, hovering over the ATI Catalyst Control Center menu entry shows a tooltip in Japanese. Finally (there may be others but I haven't seen them), the list of language packs in Install/Remove Languages is shown in Japanese.

This is a bit of a pain. It's not too much of a problem, but I'd like it resolved. I'm not that new to Ubuntu, but if I need to input a long list of commands into the terminal, then give me the exact commands please :)

By the way, the output from the 'env' command says my LANGUAGE variable is set to "en_GB:ja:en". This may have something to do with it, but when I tried nullifying the variable, the changes didn't stay.

Any help is appreciated to solve this! Thanks in advance.

---

### Post by user1397 on 2011-04-21
try the localepurge program ```
sudo apt-get install localepurge
```it'll ask you which language you want on your system, and will delete all other language files for all programs on your computer

---

### Post by FoobyZeeky on 2011-04-21
Thanks a lot! :D

This fixed the problem with the list of languages and with apt-get output. However, ATI Catalyst Control Center's menu entry is still in Japanese. The program itself isn't in Japanese, but I'd like to get it back to the way it was. If reinstalling the ATI graphics drivers (along with CCC) is the only way to solve this then I'll do that. Thanks again!

---

### Post by user1397 on 2011-04-21
> **FoobyZeeky said:**
> Thanks a lot! :D

This fixed the problem with the list of languages and with apt-get output. However, ATI Catalyst Control Center's menu entry is still in Japanese. The program itself isn't in Japanese, but I'd like to get it back to the way it was. If reinstalling the ATI graphics drivers (along with CCC) is the only way to solve this then I'll do that. Thanks again!hmm well I don't know why localepurge didn't work for that, maybe because it's the non-free driver but I don't really know.  yea reinstalling would probably fix that, if it's not too much of a headache.

oh and no problem :)

---

