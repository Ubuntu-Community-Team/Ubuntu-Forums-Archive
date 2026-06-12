---
title: "CPU Overclocking?"
date: 2010-02-11
forum: General Help
---

### Post by Hman242 on 2010-02-11
Can anyone tell me why my CPU overclocks itself after being on so long, and give me a solution to fixing it? I don't like my CPU to overheat, which happens when it overclocks.

---

### Post by undecim on 2010-02-11
What kind of CPU? Go to a terminal and type 'grep "model name" /proc/cpuinfo' to tell.

---

### Post by Hman242 on 2010-02-11
Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz

---

### Post by BrandonBan6 on 2010-02-11
Have you checked your BIOS settings for anything funky? 

Also, can you paste the output of these commands:

```
 ps -eo pcpu,pid,user,args | sort -k 1 -r | head -10
```

and

```
iostat
```

---

### Post by Hman242 on 2010-02-11
The first one brought up 

```
%CPU   PID USER     COMMAND
 8.3  4641 hunter   gnome-terminal
 7.7  4554 hunter   /usr/lib/firefox-3.5.7/firefox
 7.5  2011 root     /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-0U8uXr/database -nolisten tcp vt7
 6.0  4645 hunter   bash
 1.9     5 root     [sirq-timer/0]
 1.8    19 root     [sirq-timer/1]
 0.5  2754 hunter   /usr/bin/pulseaudio --start
 0.3    23 root     [sirq-tasklet/1]
 0.3  1518 root     [irq/18-eth%d]
```

I had to install sysstat to get the second one, but it brought up

```
Linux 2.6.31-9-rt (ubuntu)     02/11/2010     _x86_64_    (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          11.80    0.54    6.55    3.29    0.00   77.82

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              11.07       295.89       358.71    1256873    1523680
```

---

### Post by BrandonBan6 on 2010-02-11
Thanks for that; It doesn't look like anything crazy is running. Can you make it 'overclock'? Or does it just happen after a certain time, regardless of what you are running? 



> **Hman242 said:**
> The first one brought up 

%CPU   PID USER     COMMAND
 8.3  4641 hunter   gnome-terminal
 7.7  4554 hunter   /usr/lib/firefox-3.5.7/firefox
 7.5  2011 root     /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-0U8uXr/database -nolisten tcp vt7
 6.0  4645 hunter   bash
 1.9     5 root     [sirq-timer/0]
 1.8    19 root     [sirq-timer/1]
 0.5  2754 hunter   /usr/bin/pulseaudio --start
 0.3    23 root     [sirq-tasklet/1]
 0.3  1518 root     [irq/18-eth%d]

I had to install sysstat to get the second one, but it brought up

Linux 2.6.31-9-rt (ubuntu)     02/11/2010     _x86_64_    (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          11.80    0.54    6.55    3.29    0.00   77.82

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              11.07       295.89       358.71    1256873    1523680

---

### Post by Hman242 on 2010-02-11
It seems to just happen by itself regardless of what I'm doing. It usually happens after the computer has been running for 6 hours or longer.

---

### Post by Hman242 on 2010-02-13
Bump?

---

### Post by Jive Turkey on 2010-02-13
the application cpufreq might offer you some control.  It is intended for downclocking your cpu when idle to help save power.  You might be having a hardware problem if your frequency is randomly changing.  How are you monitoring the frequency?

---

### Post by Hman242 on 2010-02-13
If it happens, I can usually tell. I don't use anything to monitor it. My computer becomes slow, and I will shut it down. When I do, scrolling text goes down my screen saying something about my CPU temperature, and that it has overclocked. I'm not sure how long it has been overclocked before it overheats, but I would like to stop it all together.

---

### Post by Linuxforall on 2010-02-13
My guess is that some program is consuming full CPU resources at 100% and therefore that pushes the CPU to run at full speed which is the feature of Intel's Speed Step and AMD's Power On.

---

### Post by Hman242 on 2010-02-13
I would say that would be the case, but it's not. When I had Windows(before Jan 11) my CPU would be running at 60% usage without me doing anything and would easily top out at 100% if I did so much as to watch a video on Youtube. However, since switching to Ubuntu, my CPU no longer says it's being used up like it was. It stays around 30% when I'm doing multiple things. It's not being overloaded by anything as far as I know, but it still overclocks, which causes it to overheat.

---

### Post by undecim on 2010-02-18
> **Hman242 said:**
> I would say that would be the case, but it's not. When I had Windows(before Jan 11) my CPU would be running at 60% usage without me doing anything and would easily top out at 100% if I did so much as to watch a video on Youtube. However, since switching to Ubuntu, my CPU no longer says it's being used up like it was. It stays around 30% when I'm doing multiple things. It's not being overloaded by anything as far as I know, but it still overclocks, which causes it to overheat.

So when your CPU begins to overheat, you are still at 30% usage?

---

### Post by Jackzor on 2010-02-18
Sounds to me like you may need a new processor.

I have seen this before.

You could also just try re-seating the processor.

---

### Post by sandy8925 on 2010-03-06
You sure the processor is actually overclocking ? i.e is it going beyond the default 2 Ghz ? If it's just going upto 2 Ghz (which I assusm it is). In that case it's NOT overclocking. The newer CPU's (including some single core CPU's) have this feature where they run in a low frequency mode for ordinary usage in order to save power. If CPU usage rises then the CPU's frequency is increased to cope with the demand. So it's not overclocking.

You said 6 hours which is a pretty long time. The CPU is bound to heat up when kept on for long periods of time (especially multi-core CPU's) not to mention we're moving towards summer.

---

