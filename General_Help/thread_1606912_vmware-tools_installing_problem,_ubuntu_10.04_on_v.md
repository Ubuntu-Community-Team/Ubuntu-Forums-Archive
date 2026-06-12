---
title: "vmware-tools installing problem, ubuntu 10.04 on vmware6.0.2"
date: 2010-10-27
forum: General Help
---

### Post by xxgeneral on 2010-10-27
I have installed ubuntu 10.04 on vmware6.0.2, then I try to get vmware-tools installed. And come up with some problems.
Can anybody help me?
Thanks a lot!
 
-->install VMware tools...
-->cp VMwareTools-6.0.2-59824.tar.gz /tmp
-->tar zxvf VMwareTools-6.0.2-59824.tar.gz
-->cd vmware-tools-distrib
-->sudo ./vmware-install.pl
 
/*******************************/
            Warnings & Errors
/*******************************/
Stopping VMware Tools services in the virtual machine:
Guest operating system daemon: done
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umounts' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `umountnfs.sh' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and cups if stopped
insserv: loop involving service cups at depth 3
insserv: loop involving service rsyslog at depth 2
insserv: loop involving service udev at depth 1
insserv: There is a loop between service cups and rsyslog if stopped
insserv: exiting now without changing boot order!
Trying to find a suitable vememctl module for your running kernel.
 
None of the pre-built vmmemctl modules for VMware Tools is suitable for your running kernel. Do you want this program to try to build the vmmemctl module for 
your system (you need to have a C compiler installed on your system)? [yes]
 
Using compiler "usr/bin/gcc". Use environment variable CC to override.
What is the location of the directory of C header files that match your running kernel? [/lib/modules/2.6.32-21-generic/build/include]
 
Extracting the vmmemctl module.
 
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config12/vmmemctl-only'
make: -C /lib/modules/2.6.32-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-header-2.6.32-21-generic'
CC [M] /tmp/vmware-config12/vmmemctl-only/os.o
In file included from /tmp/vmware-config12/vmmemctl-only/os.c:40:
/tmp/vmware-config12/vmmemctl-only/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config12/vmmemctl-only/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config12/vmmemctl-only/os.c:40:
/tmp/vmware-config12/vmmemctl-only/compat_wait.h:60: error: conflicting types for 'poll_initwait'
include/linux/poll.h:70: note: previous declaration of 'poll_initwait' was here
/tmp/vmware-config12/vmmemctl-only/os.c: In fuction 'os_init':
/tmp/vmware-config12/vmmemctl-only/os.c:567: error: 'struct proc_dir_entry' has no member named 'get_info'
make[2]: *** [/tmp/vmware-config12/vmmemctl-only/os.o] Error 1
make[1]: *** [_module_/tmp/vmware-config12/vmmemctl-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [vmmemctl.ko] Error 2
make: Leaving directory `/tmp/vmware-config12/vmmemctl-only'
Unable to build the vmmemctl module.

---

### Post by dcstar on 2010-10-27
> **xxgeneral said:**
> I have installed ubuntu 10.04 on vmware6.0.2, then I try to get vmware-tools installed. And come up with some problems.
Can anybody help me?
...........

What does it say about issues like this in the Virtualization forum?

---

