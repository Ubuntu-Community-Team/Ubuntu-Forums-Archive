---
title: "Athlon II X4 630 Processor @ 2800.00MH"
date: 2010-04-23
forum: General Help
---

### Post by Zedman2k on 2010-04-23
I just jumped from a win xp box that had a rootkit(I tried to infect myself with the same virus my sister-in-law had to work it out but got a whole lot more)*

I'm still very green to linux and when searching the forums I think I'm not asking the right question.

I have an Athlon II X4 630 Processor @ 2800.00MHz but when I run a benchmark it only shows 1 core running @ 2.8. any help?

I'm running Ubuntu 9.1 with a 630 AMD an on a Gigabyte GA-MA785GT-UD3H:

Processors
AMD Athlon(tm) II X4 630 Processor    2800.00MHz
AMD Athlon(tm) II X4 630 Processor    800.00MHz
AMD Athlon(tm) II X4 630 Processor    800.00MHz
AMD Athlon(tm) II X4 630 Processor    800.00MHz

*Note to self- Don't download test viruses unless you 'KNOW' the person your getting it from!

---

### Post by cascade9 on 2010-04-23
What benchmark is showing 1 core?

---

### Post by dcstar on 2010-04-23
Got it wrong - sorry.

---

### Post by Zedman2k on 2010-04-23
Hi,
I'm using System profiler and benchmark - HardInfo "0.5c"

I found the problem, it was a setting in the bios. I guess this benchmark only stressed one core and the bios was set to save energy. 

Does anyone know a benchmark that will really test the system?

Thanks,
Zed

---

### Post by cascade9 on 2010-04-24
Hardinfo should NEVER have had 'and benchmark' in its name...its not a very good benchmark system. 

Try the phoronix test suite- 

[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

