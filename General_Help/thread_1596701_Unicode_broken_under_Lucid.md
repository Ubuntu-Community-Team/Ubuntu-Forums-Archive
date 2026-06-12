---
title: "Unicode broken under Lucid"
date: 2010-10-14
forum: General Help
---

### Post by Darxus on 2010-10-14
On one of my two Lucid desktop machines, unicode stopped working.

If I type ctrl-shift-u2014 in gnome-terminal, it gives me two characters, "--", when it should give me a "—", m-dash (long dash).  Interestingly, ctrl-shift-ub0 correctly gives me a "°".  2639 gives me "?" (a question mark), when it should give me "&#9785;" (frown).  

If I cat a text file containing these characters, b0 gives me "Â°".  Same in rxvt-unicode.  

This all used to work on this machine.  

The "--" makes me think I'm somehow using the wrong character set, and something is aware of this and trying to compensate.

In gnome-terminal I have "Use the system fixed width font" selected.

In gnome-terminal, Terminal / Set Character Encoding says "Unicode (UTF-8)".

I am running 64-bit Ubuntu (also on the machine that works).

---

### Post by Darxus on 2010-10-14
Reboot didn't help.

---

### Post by Darxus on 2010-10-14
My locale was set to en_US.

I changed the contents of /etc/default/locale to 

LANG="en_US.UTF-8"

Rebooting.

Any idea how that could have changed?  The timestamp on /etc/default/locale was 2010-07-19.

---

### Post by Darxus on 2010-10-14
Worked.

And I realized that this problem might have started when I got a new machine with a new install of ubuntu, so unicode might never have worked on this computer.  (And it was actually installed by somebody else.)

---

### Post by The Cog on 2010-10-14
Chuckle. Now, that's what I **call** a monologue. 

But other people are reading and learning even if they aren't able to help, so thanks for posting the solution.

---

