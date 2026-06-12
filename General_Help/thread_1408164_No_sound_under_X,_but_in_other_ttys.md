---
title: "No sound under X, but in other ttys"
date: 2010-02-16
forum: General Help
---

### Post by Serguei_89 on 2010-02-16
Hello,

I'm looking for any suggestions on fixing the following issue:

1. I start up my machine and am greeted at console login prompt (I don't have gdm)
2. I type 'startx'
3. Window manager (wmii) launches
4. I open terminal and type 'alsamixer' and get 
   " function snd_ctl_open failed for default: No such file or directory"
5. alsactl says:
   alsactl: init:1727: No soundcards found...
6. sudo alsactl says:
   Unknown hardware: "HDA-Intel" "Realtek ALC272" "HDA:10ec0272,1179ff6e,00100001" "0x1179" "0xff6e"
Hardware is initialized using a guess method

7. BUT! If i press CTRL-ALT-F3 and run alsamixer on console there, all problems dissapear!

Any suggestions or leads are appreciated. I'm really puzzled by this one

---

