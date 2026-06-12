---
title: "Need help with Control Characters For Point Of Sale System Ubuntu"
date: 2011-10-27
forum: General Help
---

### Post by cipher_neo on 2011-10-27
Hi guys,

I am trying to open a cash drawer by sending some control characters to the attatched printer. 

I got this working in windows by running the following:

echo <esc>p0>COM1

where <esc> is the actual escape control character.

I do NOT know how to do the same in ubuntu. 

I have tried variations of all types of command using the lp command. 

Can anyone help?

thanks,

Lee

---

### Post by dcstar on 2011-10-29
> **cipher_neo said:**
> Hi guys,

I am trying to open a cash drawer by sending some control characters to the attatched printer. 

I got this working in windows by running the following:

echo <esc>p0>COM1

where <esc> is the actual escape control character.

I do NOT know how to do the same in ubuntu. 

I have tried variations of all types of command using the lp command. 

Can anyone help?

thanks,

Lee

Linux serial ports are /dev/tty* etc.:

[http://tldp.org/HOWTO/Serial-HOWTO.html](http://tldp.org/HOWTO/Serial-HOWTO.html)

Escape codes can be sent in various ways:

[http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/escapingsection.html](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/escapingsection.html)

---

### Post by cipher_neo on 2011-10-29
exactly what I needed, thanks!

---

### Post by dcstar on 2011-10-30
> **cipher_neo said:**
> exactly what I needed, thanks!

Please read my Sig.

---

