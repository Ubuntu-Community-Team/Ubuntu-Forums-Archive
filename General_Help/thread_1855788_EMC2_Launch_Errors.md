---
title: "EMC2 Launch Errors"
date: 2011-10-06
forum: General Help
---

### Post by slayer04 on 2011-10-06
When I run the setup utility, everything is great, I can even test the machine and everything function according to plan but when I go to launch the actual program I get an error and a printout which reads:

Print file information:
RUN_IN_PLACE=no
EMC2_DIR=
EMC2_BIN_DIR=/usr/bin
EMC2_TCL_DIR=/usr/share/emc/tcl
EMC2_SCRIPT_DIR=
EMC2_RTLIB_DIR=/usr/realtime-2.6.32-122-rtai/modules/emc2
EMC2_CONFIG_DIR=
EMC2_LANG_DIR=/usr/share/emc/tcl/msgs
INIVAR=inivar
HALCMD=halcmd
EMC2_EMCSH=/usr/bin/wish8.5
EMC2 - 2.4.6
Machine configuration directory is '/home/sean/emc2/configs/my-mill'
Machine configuration file is 'my-mill.ini'
INIFILE=/home/sean/emc2/configs/my-mill/my-mill.ini
PARAMETER_FILE=emc.var
EMCMOT=motmod
EMCIO=io
TASK=milltask
HALUI=
DISPLAY=axis
NML_FILE=
Starting EMC2...
Starting EMC2 server program: emcsvr
Loading Real Time OS, RTAPI, and HAL_LIB modules
Starting EMC2 IO program: io
Starting EMC2 TASK program: milltask
Starting EMC2 DISPLAY program: axis
Shutting down and cleaning up EMC2...
Killing task emcsvr, PID=2925
Killing task milltask, PID=2969
Removing HAL_LIB, RTAPI, and Real Time OS modules
Removing NML shared memory segments
Cleanup done

Debug file information:
/usr/bin/emc: line 654:  2970 Segmentation fault      $EMCDISPLAY -ini "$INIFILE" $EMCDISPLAYARGS $EXTRA_ARGS
2925
  PID TTY      STAT   TIME COMMAND
2969
  PID TTY      STAT   TIME COMMAND
Stopping realtime threads
Unloading hal components

Kernel message information:
[ 1950.966620] I-pipe: Domain RTAI registered.
[ 1950.966629] RTAI[hal]: <3.8.1> mounted over IPIPE-NOTHREADS 2.6-03.
[ 1950.966632] RTAI[hal]: compiled with gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) .
[ 1950.966640] RTAI[hal]: mounted (IPIPE-NOTHREADS, IMMEDIATE (INTERNAL IRQs DISPATCHED), ISOL_CPUS_MASK: 0).
[ 1950.966644] PIPELINE layers:
[ 1950.966647] f85a1e20 9ac15d93 RTAI 200
[ 1950.966650] c085cb20 0 Linux 100
[ 1950.995197] RTAI[malloc]: global heap size = 2097152 bytes, <BSD>.
[ 1950.995346] RTAI[sched]: IMMEDIATE, MP, USER/KERNEL SPACE: <with RTAI OWN KTASKs>, kstacks pool size = 524288 bytes.
[ 1950.995353] RTAI[sched]: hard timer type/freq = APIC/8312480(Hz); default timing: periodic; linear timed lists.
[ 1950.995358] RTAI[sched]: Linux timer freq = 250 (Hz), TimeBase freq = 2793120000 hz.
[ 1950.995361] RTAI[sched]: timer setup = 999 ns, resched latency = 2944 ns.
[ 1950.995475] RTAI[usi]: enabled.
[ 1951.101854] RTAI[math]: loaded.
[ 1951.188647] config string '0x378 out  '
[ 1952.530016] axis[2970]: segfault at 4 ip 00230ef6 sp bff20c60 error 4 in libGL.so.1.2[1cb000+a7000]
[ 1953.278675] RTAI[math]: unloaded.
[ 1953.357739] SCHED releases registered named ALIEN RTGLBH
[ 1953.373580] RTAI[malloc]: unloaded.
[ 1953.472024] RTAI[sched]: unloaded (forced hard/soft/hard transitions: traps 0, syscalls 0).
[ 1953.477364] I-pipe: Domain RTAI unregistered.
[ 1953.477376] RTAI[hal]: unmounted.


Any suggestions?

---

