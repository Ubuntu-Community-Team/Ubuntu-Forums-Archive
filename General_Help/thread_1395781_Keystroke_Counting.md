---
title: "Keystroke Counting"
date: 2010-02-01
forum: General Help
---

### Post by Yuki_Nagato on 2010-02-01
Are there any programs to count keystrokes (NOT keylog) for Linux?

If not, where could I start manually?

Poking around in /dev/input has turned up nothing usable.
xev only works if the window is selected.

I am trying to compile my usage data to prove to myself that the switch to Dvorak from QWERTY was meaningful.

---

### Post by t4thfavor on 2010-02-01
Found this 

> 
sudo cat /dev/input/event1 > ~/keyboard1.txt

look through ls -R /dev/input to see if keyboard is somewhere else, and make sure not to put the log in dev

part2 : getting keycount
Code:

echo $(( $(cat ~/keyboard1.txt | wc -c) / 96))


here:
[http://bbs.archlinux.org/viewtopic.php?id=62058](http://bbs.archlinux.org/viewtopic.php?id=62058)

Here in an OSS project, says it's for windows though, but it's in C++
[http://mgccl.com/2009/02/28/a-open-source-keystroke-counter-for-windows](http://mgccl.com/2009/02/28/a-open-source-keystroke-counter-for-windows)

also found this which looks really promising.
[http://www.ibm.com/developerworks/opensource/library/os-keystroke-perl-xev/index.html](http://www.ibm.com/developerworks/opensource/library/os-keystroke-perl-xev/index.html)

---

### Post by Yuki_Nagato on 2010-02-02
Thank you.  I will see if I can modify the IBM code for my purposes.

---

