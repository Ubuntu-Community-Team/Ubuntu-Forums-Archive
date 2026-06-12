---
title: "please help, cpu frequency is all messed up!"
date: 2012-02-25
forum: General Help
---

### Post by ohnonot on 2012-02-25
i would like my machine to run on its highest cpu frequency all of the time, except when i take it down manually.
to achieve this i did what is written here:
[http://ubuntuforums.org/showpost.php?p=8790599&postcount=11](http://ubuntuforums.org/showpost.php?p=8790599&postcount=11)

plus i added a line to  /etc/rc.local:```
cpufreq-set -c 0 -g performance -d 2GHz
```- but neither seems to have consistent effect.

on my laptop is a switch for the fan - it seems to reduce the frequency at the same time.
right now i can switch between 800MHz userspace and 2GHz userspace.
weird, i never specified "userspace" anywhere. also before i started messing with this it was always either "performance" or "ondemand".

after the last reboot it stayed for a long time on 800 MHz "performance" and i could not get it higher - playing a .flac audio through jack took 100% cpu and stuttering...

btw, i'm getting these readings  from a cpu frequency monitor plugin for xfce-panel. it says it uses the powernow-k8 scaling driver and offers 
available frequencies: 800MHz, 1.6GHz, 1.8GHz and 2GHz, 
available governors:   ondemand, userspace, performance, conservative, powersave.
changing those has no effect, i guess that only works with root privileges, but as a passive monitor it seems reliable.

i'm running xubuntu 11.10 on a fujitsu-siemens amilo laptop with 

-Processor-
Name        : Mobile AMD Sempron(tm) Processor 3300+
Family, model, stepping        : 15, 44, 2 (AMD Opteron/Athlon64/FX)
Vendor        : AuthenticAMD
-Configuration-
Cache Size        : 128kb
Frequency        : 2000.00MHz
BogoMIPS        : 3991.98
Byte Order        : Little Endian
-Features-
FDIV Bug        : no
HLT Bug        : no
F00F Bug        : no
Coma Bug        : no
Has FPU        : yes
-Cache-
Level 1 (Data)        : 2-way set-associative, 512 sets, 64KB size
Level 1 (Instruction)        : 2-way set-associative, 512 sets, 64KB size
Level 2 (Unified)        : 16-way set-associative, 128 sets, 128KB size
-Capabilities-
fpu        : Floating Point Unit
vme        : Virtual 86 Mode Extension
de        : Debug Extensions - I/O breakpoints
pse        : Page Size Extensions (4MB pages)
tsc        : Time Stamp Counter and RDTSC instruction
msr        : Model Specific Registers
pae        : Physical Address Extensions
mce        : Machine Check Architeture
cx8        : CMPXCHG8 instruction
apic        : Advanced Programmable Interrupt Controller
sep        : Fast System Call (SYSENTER/SYSEXIT)
mtrr        : Memory Type Range Registers
pge        : Page Global Enable
mca        : Machine Check Architecture
cmov        : Conditional Move instruction
pat        : Page Attribute Table
pse36        : 36bit Page Size Extensions
clflush        : Cache Line Flush instruction
mmx        : MMX technology
fxsr        : FXSAVE and FXRSTOR instructions
sse        : SSE instructions
sse2        : SSE2 (WNI) instructions
syscall        : SYSCALL and SYSEXIT instructions
nx        : No-execute Page Protection
mmxext        : Extended MMX Technology
fxsr_opt
3dnowext        : Extended 3DNow! Technology
3dnow        : 3DNow! Technology
up        : smp kernel running on up
pni        : Streaming SIMD Extension 3 (Prescott New Instruction)
lahf_lm        : LAHF/SAHF in long mode

all help appreciated! thanks!
:popcorn:

---

### Post by idonthaverabbies on 2012-02-25
why would you want to do that? i love that my cpu throttles down when its not needed under load my rig pulls like  270 watts but when im surfing the web in linux i only use 70 watts sure saves me in my electric bill and never slow me down soon as im doing  havey computing  pc ramps back up

---

### Post by 3rdalbum on 2012-02-25
Set your fan switch to the highest setting. This seems to manually set the speed to 2GHz (which automatically engages the Userspace governor to make it stay there).

Running your laptop at 2GHz with no fan is a recipe for disaster.

Alternatively, just engage the Ondemand governor and the CPU will throttle up to 2GHz whenever necessary. You probably won't see any degradation of performance, but you will probably see better battery life.

---

### Post by ohnonot on 2012-02-26
> **3rdalbum said:**
> Set your fan switch to the highest setting. This seems to manually set the speed to 2GHz (which automatically engages the Userspace governor to make it stay there).

Running your laptop at 2GHz with no fan is a recipe for disaster.

Alternatively, just engage the Ondemand governor and the CPU will throttle up to 2GHz whenever necessary. You probably won't see any degradation of performance, but you will probably see better battery life.
thanks!
i watched more closely now, after another reboot.
- the governor stays on performance no matter what
- it stays on 2GHz until i press the fan button - after that it stays on 800MHz performance :-( 
obviously i can put everything back as it was.
but here
[http://wiki.linuxmusicians.com/doku.php?id=system_configuration#how_do_i_build_a_realtime_audio_workstation_on_linux](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#how_do_i_build_a_realtime_audio_workstation_on_linux)
it says that it's important to use highest cpufreq.
makes sense to me, esp since my hardware is so old.
(no worries about the battery, that's drained anyway)

so again, i don't want to loose the ability to throttle my cpu but i'd like to be able to 
- either disable that manually (meaning running the full 2GHz)
- or switch to manual completely (switching between frequencies)

i understand that that is connected to fan activity.

more ideas?
more popcorn?

---

### Post by gordintoronto on 2012-02-26
> **ohnonot said:**
> i would like my machine to run on its highest cpu frequency all of the time, except when i take it down manually.

This is not required at all. As soon as your CPU gets busy, it will jump to its highest speed.

---

### Post by ohnonot on 2012-03-10
> **gordintoronto said:**
> This is not required at all. As soon as your CPU gets busy, it will jump to its highest speed.
the problem is, it doesn't jump to it's highest speed *as soon as* but with a delay and sometimes not at all (e.g. playing youtube videos).

but, i got a little wiser and now think the better solution is to keep the default governor (ondemand) with an option to override that.
right now i accomplish that with 3 commands:```
sudo cpufreq-set -c 0 -g userspace 
sudo cpufreq-set -c 0  -d 2GHz 
sudo cpufreq-set -c 0  -f 2GHz
```but any more elegant solution is welcome.

@ 3rdalbum: the fanswitch switches only the fan in ondemand mode, and in userspace mode it switches both the fan and the cpu freq.

---

### Post by ohnonot on 2012-03-27
coming back to this thread after 2 weeks...

i had changed all the bootup manipulations back to default (ondemand)
and made a littl button that makes the cpu go to 2Ghz userspace.
It's a workaround and has helped me, and i had some time watching the behaviour of my machine (again, always assuming that the xfce panel applet cpu freq monitor is telling the truth!).

+++++It seems that the ondemand governor does not *always *scale the cpu up when it should. meaning, some app (synaptic applying final changes after a new installation, or playing .flac audio through jack with high quality output) can run on 100% cpu forever and the ondemand governor does not scale up.

i don't know how this works (is ondemand just monitoring cpu load or is it actually waiting for 'demands' being made by applications or some other daemon) - so i don't know where to look for solutions
:confused:

---

### Post by Jouke74 on 2012-03-27
You could try to use a tool called Jupiter. There you can put de modes of the CPU in various states, e.g. powersaving full etc. I only don't know how well it is going to work with AMD. 

[http://www.fewt.com/2010/02/meet-jupiter.html](http://www.fewt.com/2010/02/meet-jupiter.html)

---

