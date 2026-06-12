---
title: "Read not allowing operators in shell scripts"
date: 2010-12-26
forum: General Help
---

### Post by Mastermoose on 2010-12-26
Hello!
I'm trying to write a small application controlling spotify, running under wine, that I can run from my desktop computer and use via SSH on my mobile phone, and so far I've been quite successful.  At least until just recently, when I tried to use the read command to read a single key-press on my phone, and use that input instead of having to type the number for item in the menu I've created.
I tried to simply use the read command to silently listen to one key-press and output it to the variable opt. To do this I tried:

[COLOR=Sienna]**read -s -n1 opt**[/COLOR]

When I ran this in a shell-script this I got:
[B]
[COLOR=Red]*read: 1: Illegal option -s*[/COLOR]
[/B]
Seeing this, I tried to remove the[COLOR=Sienna] **-s**[/COLOR] operator, which left me with:
[B]
[COLOR=Red]*read: 1: Illegal option -n*[/COLOR][/B]

I decided to remove all operators and echo the variable opt, leaving me with:

[COLOR=Sienna][B]read opt
echo "$opt"[/B][/COLOR]

Which worked as expected. It echoed the key that I had pressed. I moved over to my terminal window and tried the read command from there, and it did exactly what it should. It silently recorded one key-press to the variable opt.

So, now for the question; why isn't read working with operators in shell scripts? Am I missing something obvious here?

---

### Post by gmargo on 2010-12-26
> **Mastermoose said:**
> Am I missing something obvious here?

Yes.  It's a **dash** vs. **bash** issue.  (Don't fret about; everyone makes this mistake. Once.)

The standard shell, **/bin/sh**, points to the **dash** shell.  The "read" syntax is different.

See the **dash(1)** man page, and the **bash(1)** man page.

Usage for dash:  read [-p prompt] [-r] variable [...]
Usage for bash:  read [-ers] [-a aname] [-d delim] [-i text] [-n nchars] [-N nchars] [-p prompt] [-t timeout] [-u fd] [name ...]

---

### Post by Mastermoose on 2010-12-28
Oh, thanks a lot. I ended up running the script with bash instead of sh, which did the trick.
I'm not surprised it was as simple as that, although I can't say I don't feel quite stupid.

---

### Post by octius4u on 2012-11-13
:PThis answer has been very help full for me as well (being as beginner) not knowing why the syntax is wrong on multiple occasions. Thanks for the question as well as the answer (even after 2 years).

 :cool: :P

---

### Post by wildmanne39 on 2012-11-13
Old thread closed.

---

