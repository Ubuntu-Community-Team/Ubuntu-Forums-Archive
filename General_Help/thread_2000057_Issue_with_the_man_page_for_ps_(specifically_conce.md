---
title: "Issue with the man page for ps (specifically concerning vsz)"
date: 2012-06-09
forum: General Help
---

### Post by Keiran230 on 2012-06-09
Directly from the man page of ps:
*vsz VSZ virtual memory size of the process in KiB (1024-byte units). Device mappings are currently excluded; this is subject to change. (alias vsize)*

ps -eo vsz,comm reports that nautilus is using a whopping 645.22 MB of memory, which is absolutely not true

System Monitor reports nautilus is using 37.8MB of memory (a reasonable number, so I'm assuming this is accurate)

Either vsz has been documented wrong in the man page of ps, or I'm confused. What units are vsz actually using? If I wanted to see memory usage in bytes or kilobytes, what would be a better option to send to ps -eo ? If it's a simple math conversion, I can deal with it, but I need to know what the conversion is.

Here's a short script to demonstrate:
```
ps -eo vsz,comm | awk '/nautilus/ {print $1}' | awk '{ sum=$1 ;
            hum[1024^2]="GB"; hum[1024]="MB"; hum[1]="KB";
            for (x=1024^2; x>=1; x/=1024){
                if (sum>=x) {
                    printf "%.2f %s\n",sum/x,hum[x];break
                }
            }
        }'
```

If you're curious, this is what I'm up to: [http://keiran.us/stuff/check_mem](http://keiran.us/stuff/check_mem)

---

### Post by hansdown on 2012-06-09
Hi Keiran230.

How does

```
ps -e -o pid,vsz,comm= | sort -n -k 2
```

work?

---

### Post by Keiran230 on 2012-06-09
@hansdown

come to think of it, vsz seems to have no correlation to a program's size:
```
$ ps -e -o pid,vsz,comm= | sort -n -k 2 | egrep 'nautilus|compiz|thunderbird'
 1936 318476 compiz
 1951 569812 nautilus
 2142 887472 thunderbird-bin
```

Actual sizes, according to system monitor:
compiz: 12.0M
nautilus: 9.3M
thunderbird-bin: 71.5M

What makes this even more interesting is that it seems to have no rhyme or reason of where ps is getting these numbers from. It's not even directly correlated with its actual size. If it was, each of these divisions should come out to around the same number:
887472 / 71.5 = 12412
569812 / 8.3 = 61270
318476 / 12.0 = 26539

**EDIT**:
This isn't limited to Ubuntu derivatives either. I just tried this on Fedora and CentOS with the same result. Interesting.

---

### Post by Keiran230 on 2012-06-10
I figured it out; the issue was me just not understanding how the kernel segregates memory.

There are different ways to measure the amount of memory a process is consuming. If you turn on all columns in gnome-system-monitor, you'll see it.

If I understand each right:
**virtual memory**: this is the output of *ps -eo vsz* OR *pmap -d `pidof $PROGRAM` | awk '/^mapped/ {print $2}'*. It's the sum of shared memory, resident memory, and a couple other things
**resident memory**: this is the output of *pmap -d `pidof $PROGRAM` | awk '/^mapped/ {print $4}'* . This is the best measurement of how much memory an app is consuming in my opinion, so this one right here resolves my issue
**writable memory**: the default memory size displayed by gnome-system-monitor. Not directly accessible with ps or pmap. It is typically only a few KB or a few MB smaller than resident memory and can sometimes be identical
**shared memory**: this is the output of *pmap -d `pidof $PROGRAM` | awk '/^mapped/ {print $6}'*. I think it has to do with the memory space of the shared libraries of an application
**X server memory**: how much graphical memory a process is taking to render in X server. Not directly accessible with ps or pmap

pmap's output is good enough for my script, so marking this as resolved.

---

