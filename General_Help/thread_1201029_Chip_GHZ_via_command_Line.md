---
title: "Chip GHZ via command Line?"
date: 2009-06-30
forum: General Help
---

### Post by jsmidt on 2009-06-30
I am using a machine with only a terminal.  How can I tell how fast the processor is using a terminal command?  How many GHZ?  Thanks.

---

### Post by lykwydchykyn on 2009-06-30
```

cat /proc/cpuinfo |grep MHz

```

Gives it in MHz, of course, but you have the speed nonetheless.

---

### Post by bodhi.zazen on 2009-06-30
> **lykwydchykyn said:**
> ```

cat /proc/cpuinfo |grep MHz

```Gives it in MHz, of course, but you have the speed nonetheless.

cat | grep , tisk, tisk [-X

```
grep MHz /proc/cpuinfo
```

:-\"

---

### Post by Yashiro on 2009-06-30
This will tell you the processors max rated speed. 

edit: It works fine. Displays the CPUs *current* speed in Mhz.

---

### Post by m_duck on 2009-06-30
> **Yashiro said:**
> This will tell you the processors max rated speed. Not the speed it might actually be running at.
That isn't the case for me. My 1.6 GHz cpu is currently displaying its scaled down 800 MHz in /proc/cpuinfo.

---

### Post by jerome1232 on 2009-06-30
> **m_duck said:**
> That isn't the case for me. My 1.6 GHz cpu is currently displaying its scaled down 800 MHz in /proc/cpuinfo.

Ditto, on both my machines.

---

### Post by Yashiro on 2009-06-30
Yeah you are correct. My CPU usage must have spiked when I opened the terminal and tested it earlier today.

---

### Post by lykwydchykyn on 2009-07-01
> **bodhi.zazen said:**
> cat | grep , tisk, tisk [-X

```
grep MHz /proc/cpuinfo
```

:-\"

I can't do nuthin right.  Dang.

---

