---
title: "Scrolling in Terminal?"
date: 2009-06-29
forum: General Help
---

### Post by Blackdragon1400 on 2009-06-29
I googled and couldn't find a very reliable way to scroll in an active terminal "program" when the programs output is more than one page, and is constantly being edited.... and suggestions? 

I've tried "shift"+ pg down
"shift"+ down arrow
"Ctrl"+ pg down
"Ctrl"+ down arrow

Running 9.04 if that helps

Thanks!

---

### Post by t4thfavor on 2009-06-29
If you have gui, there is a scroll bar on the right side of the terminal, if you dont, the only way I have ever seen it is to pipe output through more.

you could also try screen, as I believe it has scrolling abilities.

---

### Post by viljun on 2009-06-29
1. Mouse wheel
2. shift + page up (page down doesn't work always)

---

### Post by t4thfavor on 2009-06-29
The above only works if you are running a gui, if you are pure terminal you will have to try something else.

pipe your program into more, and press h to see the commands, there is also a program called less that can do pretty much the same thing.

it goes like this.

./program |more

then press h to see.
Most commands optionally preceded by integer argument k.  Defaults in brackets.
Star (*) indicates argument becomes new default.
-------------------------------------------------------------------------------
<space>                 Display next k lines of text [current screen size]
z                       Display next k lines of text [current screen size]*
<return>                Display next k lines of text [1]*
d or ctrl-D             Scroll k lines [current scroll size, initially 11]*
q or Q or <interrupt>   Exit from more
s                       Skip forward k lines of text [1]
f                       Skip forward k screenfuls of text [1]
b or ctrl-B             Skip backwards k screenfuls of text [1]
'                       Go to place where previous search started
=                       Display current line number
/<regular expression>   Search for kth occurrence of regular expression [1]
n                       Search for kth occurrence of last r.e [1]
!<cmd> or :!<cmd>       Execute <cmd> in a subshell
v                       Start up /usr/bin/vi at current line
ctrl-L                  Redraw screen
:n                      Go to kth next file [1]
:p                      Go to kth previous file [1]
:f                      Display current file name and line number
.                       Repeat previous command
-------------------------------------------------------------------------------

---

### Post by Blackdragon1400 on 2009-06-29
well im currently running airodump which is giving me a real time updated  network list.

---

### Post by t4thfavor on 2009-06-29
airodump has a bunch of keys defined for sorting stuff. You can also make your terminal longer than the screen, and just move it around. I haven't used it since WEP went out of style, but I am fairly certain you can get it to work with any screen syie/type.

---

### Post by Blackdragon1400 on 2009-06-29
yeah i knew you can do it with the screen size im just too lazy.... and just because WEP is out of style, doesn't mean that more than 80% of all the networks i have ever found are still using it\\:D/

---

### Post by t4thfavor on 2009-06-29
Look into packet injection, it makes your time much more "free" to do other things. I was evaluating some security in my younger days where you could break a 104bit wep key in around 10 seconds with the right setup.  Glad I use WPA now (oh wait thats been broken too?) Guess I will stick to wires.

---

### Post by Blackdragon1400 on 2009-06-29
i thought WPA was only crackable with a 100% word/list match....?

---

