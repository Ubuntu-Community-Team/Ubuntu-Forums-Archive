---
title: "Help with conky calender"
date: 2010-08-20
forum: General Help
---

### Post by elliotn on 2010-08-20
Please help me align the calendar with the rest.

---

### Post by elliotn on 2010-08-20
And the script is here

---

### Post by elliotn on 2010-08-20
Anyone please help here

---

### Post by Quackers on 2010-08-20
I'm no expert but I would suggest one of the following.
Either put ${offset 240} at the beginning of the CALENDAR line
OR
Remove all the offsets from every other line.

The first one is the quickest way.
I would copy the conkyrc you currently use as a backup first!

---

### Post by elliotn on 2010-08-20
Well atlest i managed but had to do a simple one no curent day highlighted but it serves the purpose.

${offset 240}${exec cal} 

The above worked

---

### Post by mobilediesel on 2010-08-20
> **elliotn said:**
> Well atlest i managed but had to do a simple one no curent day highlighted but it serves the purpose.

${offset 240}${exec cal} 

The above worked

The line with the calendar can be changed to this:
```
${font monospace}${execpi 3600 cal | sed -e "s/\<$(date +%-d)\>/\${color orange}&\${color}/" -e '/^ *$/d'  -e 's/^/\${offset 240}/'}
```

The calendar wont line up properly without a monospaced font. Then the **sed** command will put the **${offset 240}** at the beginning of each line output by the calendar as well as coloring the current date.

---

