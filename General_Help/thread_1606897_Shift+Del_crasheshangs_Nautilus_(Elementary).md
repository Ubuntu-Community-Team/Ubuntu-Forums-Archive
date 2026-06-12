---
title: "Shift+Del crashes/hangs Nautilus (Elementary)"
date: 2010-10-27
forum: General Help
---

### Post by forteller on 2010-10-27
NB:
I've tried searching the forums with no luck, please direct me to the correct thread if I've missed it. Or maybe you know of a bug I can vote on?

System:
Nautilus Elementary, Elementary Theme, Ubuntu 10.10, x64, updated from a clean installed 10.04.

Issue:
Every time I try to delete a file with Shift+Del Nautilus crashes. First it shows me the normal "are you sure?" alert, but no matter which button I click it always crashes. The Nautilus window and the "are you sure" alert does not go away, they just become unresponsive forever (at least as long as I've had the patience to wait). The only way to fix it is to open system monitor and kill Nautilus. Normal delete works fine.

There's no output in the terminal when crashing Nautilus like this after opening it trough the terminal.

---

### Post by ammonkey on 2010-10-27
thx to report the bug here: [https://bugs.launchpad.net/nautilus-elementary](https://bugs.launchpad.net/nautilus-elementary)

I'll take a look at it.

---

### Post by juergi on 2010-11-02
I can confirm this problem.

---

### Post by Protocol84 on 2010-11-12
I can confirm this as well, I tried to do a backtrace as per: **[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)** but usin the instruction under "already running programs" I get to step 5, nautilus hangs and I press ctrl+c to get to the (gdb) but ctrl+c does nothing it just sits there saying "continuing"

---

### Post by forteller on 2010-11-14
juergi, Protocol84: Thanks for confirming!

Please click "this bug also affects me" in this bug report: [https://bugs.launchpad.net/nautilus-elementary/+bug/667508]("https://bugs.launchpad.net/nautilus-elementary/+bug/667508")

---

