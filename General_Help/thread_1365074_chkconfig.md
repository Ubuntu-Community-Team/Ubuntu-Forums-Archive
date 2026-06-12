---
title: "chkconfig"
date: 2009-12-26
forum: General Help
---

### Post by chuina on 2009-12-26
Hi,all,

I install chkconfig.
chkconfig can the daemons list well. but it can not turn off.
like:

```
chkconfig  cups off
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'sreadahead' missing LSB tags and overrides
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: script 'usplash' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv:  loop involving service pulseaudio at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv:  loop involving service bluetooth at depth 2
insserv: exiting without changing boot order!
/sbin/insserv failed, exit code 1
```

what is wrong with chkconfig ?

Thnx.

---

### Post by jonest1 on 2009-12-26
There is quite a good thread at [http://swiss.ubuntuforums.org/showthread.php?t=1016694](http://swiss.ubuntuforums.org/showthread.php?t=1016694)

This caught me a bit by surprise as I'm an on RH admin and had the exact same results as you with chkconfig.  The thread in the link I gave mentions the preferred tool which is update-rc.d

---

### Post by chuina on 2009-12-27
Thanks jonest1.

```
 sudo apt-get install sysv-rc-conf
```

Alternately , it solves the problem.
But , "chkconfig" developers should take a look about this.

Anyway, i'm marking this thread solved.

thanks.

---

### Post by dcstar on 2009-12-27
> **chuina said:**
> 
.........
But , "chkconfig" developers should take a look about this.


And they probably will if a bug is reported, has it been reported?

---

### Post by chuina on 2009-12-29
sorry,

never report bug before, didn't found any clue 
for reporting a bug in this forum.
until now,i'm not smart enough to report a bug. 
need help reporting bug.

(perhaps u didn't saw my signature)

---

### Post by afrodocter on 2010-08-13
i thought this command was semi-clever way to find which executables link to the libGL, and determine if its missing, so i posted it. they all seem fine. 

could this be a 64/32 bit issue?


[code]            
/opt/ansoft/hfss11# for i in *; do if [ -f $i ]; then ldd $i | grep libGL && echo $i ;fi;done
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7195000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf6cf3000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf56c5000)
libem_moduledll.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7375000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf6ed3000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf58a5000)
libempostdll.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7222000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf6d80000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5752000)
libfieldspostprocessor.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf6176000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf60b1000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf46c4000)
libgeometry3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf6cc9000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf6827000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf51f9000)
liblayouttranslator.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf76cc000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf722b000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5bfc000)
libmodulebase.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7621000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf717f000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b51000)
libplot3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7691000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf71f0000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5bc1000)
libreport3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7581000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf74bc000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5ad0000)
libview3d.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7370000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf717d000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf58a0000)
libvkitools_ported_optimized.so
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf767a000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf75b5000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b4e000)
mesh3d_ng
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7718000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf7653000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5bec000)
modeler3
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf768f000)
        libGL.so.1 => /usr/lib32/nvidia-current/libGL.so.1 (0xf75ca000)
        libGLcore.so.1 => /usr/lib32/nvidia-current/libGLcore.so.1 (0xf5b63000)
stepiges2sm3
[\code]

---

