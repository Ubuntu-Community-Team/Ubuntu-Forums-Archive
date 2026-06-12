---
title: "XBMC lag"
date: 2012-09-29
forum: General Help
---

### Post by Ahmadii Sahrab on 2012-09-29
I downloaded XBMC and it worked fine with no lag but after a while it started to lag, I didnt have lag with the default skin but after a while it got very laggy even with lightweight skins like quartz, the pc is used as a media center connected to a hdtv.

---

### Post by josephmills on 2012-09-29
Could you please open your terminal (in the media box)
and enter in these commands, then paste the output here ? 
```
lsb_release -c
``` 
```
apt-cache policy xbmc 
``` 
```
cat /proc/cpuinfo
``` 
```
free -m 
```

Thanks 
also you are using xbmc as default DE or are you on Unity or something and launching it that way ?

---

### Post by Ahmadii Sahrab on 2012-09-29
I'm going to sleep now but I'll answer your question, I'm on lubuntu and I use XBMC by clicking on it in the menu and its not the default media player, my default media player it gnomeplayer or mplayer not sure of the name.

---

### Post by Ahmadii Sahrab on 2012-09-30
```
lsb_release -c
``` 
Codename:	precise

```
apt-cache policy xbmc 
``` 
xbmc:
  Installed: 2:11.0~git20120423.cd20772-1
  Candidate: 2:11.0~git20120423.cd20772-1
  Version table:
 *** 2:11.0~git20120423.cd20772-1 0
        500 [http://bh.archive.ubuntu.com/ubuntu/](http://bh.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status

```
cat /proc/cpuinfo
``` 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Pentium(R) D CPU 3.00GHz
stepping	: 5
cpu MHz		: 2400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
bogomips	: 5999.93
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Pentium(R) D CPU 3.00GHz
stepping	: 5
cpu MHz		: 2400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
bogomips	: 6000.10
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

```
free -m 
```
             total       used       free     shared    buffers     cached
Mem:           871        785         85          0         65        364
-/+ buffers/cache:        355        515

---

### Post by Ahmadii Sahrab on 2012-09-30
bump

---

### Post by Ahmadii Sahrab on 2012-10-01
bump

---

### Post by esc1 on 2012-10-01
I have the same speed dual core cpu and no dedicated gpu. If I leave a browser open that is using flash I will notice a decrease in speed. Maybe that's happening for you? Also, bear in mind higher quality videos will be harder to play especially with full hd.

---

### Post by Ahmadii Sahrab on 2012-10-02
I dont have anything open but xmbc and its not running movies lag its menu lag

---

### Post by esc1 on 2012-10-02
What about desktop effects and eye candy? Mine doesn't play nice when those are enabled..

---

### Post by Ahmadii Sahrab on 2012-10-03
nothing on and i have dirty regions on

---

### Post by josephmills on 2012-10-03
Have you thought of or tried myth tv ? Do you have capture card ?

---

### Post by scratman on 2012-10-13
Have you checked System Monitor to see whether anything is crashing/not responding/in an infinite loop?

I'm running XBMC on an Acer Aspire One which has dual core 1.6Ghz processor, 512 MB Ram and an 8Gb SSD, and experience no lag.  If hardware as limited as mine plays nicely, I don't see why yours wouldn't.

Other options would be to check for system updates.  I'll check which skin I use when I get home, perhaps a different skin will make the difference.

---

### Post by joe_newbie on 2012-10-23
I also have been having trouble with XBMC in 12.10. Just purchased a Quad core A8 5600K processor (running ay 4.3Ghz right now). 
XBMC has visible lag issues. Same video played in VLC is flawless. I love XBMC but for now it seems broken in Ubuntu. Add to that the fact that it cannot fullscreen correctly with multiple monitors (when VLC can), and I am thinking I may have to abandon XBMC until some of these problems are rectified.

Joe

---

### Post by scratman on 2012-10-28
Right, I'm using XBMC Eden on Lubuntu 12.10.  Laptop has Intel Atom 1.6Ghz processor with 512 Mb Ram and 8Gb SSD drive.  Works fine with Quartz skin.

---

### Post by UbuFunky on 2013-06-25
I'm having exactly the same situation and it's driving me nuts!!... Have you ever solved the problem?

---

