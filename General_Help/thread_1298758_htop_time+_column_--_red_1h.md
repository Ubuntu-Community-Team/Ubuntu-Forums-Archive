---
title: "htop time+ column -- red 1h??"
date: 2009-10-23
forum: General Help
---

### Post by jfbilodeau on 2009-10-23
Good day,

In htop, I'm wondering if anyone know what the red '1h' in the TIME+ column means. I've attached a screenshot for reference.

I did a bit of googling, but failed to find an answer.

Thanks in advance,

J-F

---

### Post by baytuni on 2009-11-20
bump

---

### Post by MianoSM on 2010-03-15
Column descriptions:

**PID**: A process&#8217;s process ID number.

**USER**: The process&#8217;s owner.

**PR**: The process&#8217;s priority. The lower the number, the higher the priority.

**NI**: The nice value of the process, which affects its priority.

**VIRT**: How much virtual memory the process is using.

**RES**: How much physical RAM the process is using, measured in kilobytes.

**SHR**: How much shared memory the process is using.

**S**: The current status of the process (zombied, sleeping, running, uninterruptedly sleeping, or traced).

%**CPU**: The percentage of the processor time used by the process.

%**MEM**: The percentage of physical RAM used by the process.

**TIME**+: How much processor time the process has used.

**COMMAND**: The name of the command that started the process.

I realize that this is a couple month old thread, but it does hit Google as one of the first links. Hopefully it will make someone else's day easier.

Just because you have a [COLOR="Red"]1h[/COLOR] for a PID/Process, it isn't a terrible thing, if the CPU% is steadily high, that may be more of an issue.

---

### Post by gmargo on 2010-03-15
It took only a few minutes with the **htop** source to figure out that **htop** highlights any time figures that are over 1 hour.  Sadly it is undocumented.  For me, right now, both X and firefox show up this way.  Compare to manual ps: "ps -efw | grep -v " 00:" - the same processes show up.

---

### Post by pbrane on 2010-03-15
Actually I have several time values over one hour that are not highlighted. But I have many nice values that are -5 that are highlighted red.

---

### Post by Vacri on 2010-09-28
The times that are not highlighted are actually in MM:SS.xx format. The ones that are highlighted are in HhMM:SS - and the highlight shows the ones that are in hours

Have a look at the unhighlighted times, there aren't two colons separating three values, there's one colon separating two values, the second being a decimal.

---

