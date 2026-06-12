---
title: "4GB phyical memory, but only display 3GB"
date: 2010-09-14
forum: General Help
---

### Post by benobiwan on 2010-09-14
When i run top. I saw the following output:
Mem:   3020652k total,   788048k used,  2232604k free,    69128k buffers
Swap:   975864k total,        0k used,   975864k free,   373288k cached

But my machine has 4 GB of physical memory, I am quite sure my video card is not taking up memory as it has 1 GB dedicated ram.

I googled, and got to understand that 32bit OS should be able to address up to 4GB of memory space.

Please help to unravel what is wrong.

---

### Post by asmoore82 on 2010-09-14
I think you need to install a "*-pae" kernel to go above 3GB of RAM on 32-bit.

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

---

### Post by benobiwan on 2010-09-15
thanks, it solve the issue.

---

