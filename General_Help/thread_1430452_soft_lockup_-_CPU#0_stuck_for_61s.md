---
title: "soft lockup - CPU#0 stuck for 61s"
date: 2010-03-15
forum: General Help
---

### Post by goslings on 2010-03-15
Have the following message from the console window
298.503995 BUG; soft lockup - CPU#0 stuck for 61s [fsck.839]

system will boot into windows ok - dual boot setup
nvidia drivers ?

---

### Post by goslings on 2010-03-15
tried another reboot
console reports the following and just hangs

fsck from util-linux 2.16
/dev/sda3 clean 
fsck from util-linux 2.16
init: unreadahead-other main process terminated with status 4
/dev/sda3 recover journal
/dev/sda3 clean
fsck from util-linux 2.16
* setting preliminary keymap
*setting AppArmor profiles
* eettinh up console font and keymap
dosfsck 3.0.3 18 may, FAT32, LFN
* nvidia (173.14.20) ...
.... done
PulseAudio configured for per-user sessions
*enabling additional executable binary formats-support
checking battery status .. done 

Ubuntu 9.10 goslinux tty1 
goslinux login: /dev/sda7: 314 files anumber/anumber clusters 

anyone another clever thoughts on how to get my ststem back
reboot into win xp is ok 

many thanks

---

### Post by goslings on 2010-03-15
came across this
[http://ubuntuforums.org/showthread.php?t=1331500](http://ubuntuforums.org/showthread.php?t=1331500)
have already tried the manual fsch on the last  /dev/sda# in the list

it used dosfsch and was ok

---

