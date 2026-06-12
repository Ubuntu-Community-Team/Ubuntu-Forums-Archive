---
title: "want to use bash &quot;diff&quot; command with CDROM"
date: 2010-04-30
forum: General Help
---

### Post by cloud3737 on 2010-04-30
Hi,

Just got Lucid installed, and can't seem to use the standard diff command to compare files on hard drive with those on CDROM. 

When I go into "media" directory I see the CD as "Data disc (30 Apr 10)". But a diff command of the form

diff -q -r /media/Data disc (30 Apr 10) ~/Documents

chokes with

bash: syntax error near unexpected token `('

There is no "cdrom0" anymore. 

What am I supposed to do?

---

### Post by StuartN on 2010-04-30
> **cloud3737 said:**
> I see the CD as "Data disc (30 Apr 10)"

You need to esacpe the spaces, e.g. **Data\ disc\ (30\ Apr\ 10)**, but the easiest way is to use Bash completion by typing /media/Data and then pressing Tab.

---

### Post by jobix on 2010-04-30
Try putting in the "\" character just before the "(" and the ")" in order to prevent the system from interpreting them as something else. A simple way to see this in action is to execute these commands from the command line:

> echo (
echo \(

See what happens. That should tell you something.

---

### Post by cloud3737 on 2010-04-30
The bash completion idea works like a charm -- thanks!

---

