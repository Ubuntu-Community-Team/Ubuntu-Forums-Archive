---
title: "Conky moving!"
date: 2010-06-20
forum: General Help
---

### Post by UT8F on 2010-06-20
Hello, I have a problem, 
When CPU usage is about 9%, conky window is smaller, when it's more than 10%, it's become bigger, I mean moving.
How to make it's fixed? (Only on CPU line)

---

### Post by Groodles on 2010-06-20
If you want to maintain fixed spacing between items use the $goto variable.

It allows you to force conky to print the next item as a certain X value from where the last item was printed.

---

### Post by Joeb454 on 2010-06-20
Thread Moved to General Help.

As for your request - I haven't used conky for a long time, but I imagine it's because 10% has an extra character than 9%, so will move everything else along slightly to make room

---

### Post by UT8F on 2010-06-20
> **Groodles said:**
> If you want to maintain fixed spacing between items use the $goto variable.

It allows you to force conky to print the next item as a certain X value from where the last item was printed.

Thank you!

---

