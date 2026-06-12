---
title: "keyboard: map commands to keys in ttys"
date: 2012-05-13
forum: General Help
---

### Post by smeagol271006 on 2012-05-13
Hi folks,

What I'm trying to do is to map commands to keystrokes in BASH or another shell.

NOT in X. Just sticking to the TTYS !

So far I have worked the following table.

```

### keycodes

## play/pause

#quick
0x00 0x81 0xa4 0x80 0x81 0xa4

#slow
0x00 0x81 0xa4
0x80 0x81 0xa4

## stop

#quick 
0x00 0x81 0xa6 0x80 0x81 0xa6

#slow
0x00 0x81 0xa6 
0x80 0x81 0xa6



### Scancodes

## play/pause

#quick
0xe0 0x22 0xe0 0xa2

#slow
0xe0 0x22 
0xe0 0xa2


## stop

#quick
0xe0 0x24 0xe0 0xa4

#slow
0xe0 0x24
0xe0 0xa4


```

These were made with showkey.

Now I would like to map them in this fashion
[https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys_in_Console](https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys_in_Console)

Another alternative I have tried is 
[http://www.linuxhowtos.org/System/assign_commands_to_keys.htm](http://www.linuxhowtos.org/System/assign_commands_to_keys.htm)
But some of the keys do not output anything.

Thanks in advance

---

### Post by smeagol271006 on 2012-05-23
bumping

---

