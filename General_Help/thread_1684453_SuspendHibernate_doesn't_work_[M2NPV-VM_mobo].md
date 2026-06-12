---
title: "Suspend/Hibernate doesn't work [M2NPV-VM mobo]"
date: 2011-02-09
forum: General Help
---

### Post by P1C0 on 2011-02-09
The OS is Lucid 64-bit . Before I begin I must say suspend/hibernate works fine with 3 other machines, so I'm trying to find out what's wrong with this one.
I tried [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) and also I tried changing acpi-support. It currently is as this:
```
#
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 

```
_**Suspend**_
Suspend seems to work judging by the pm-suspend.log, BUT I can't get my pc to wake up:

```
Initial commandline parameters: 
Tue Feb  8 23:24:47 EET 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux oblivion 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7960  1 
ipt_ULOG                8199  1 
snd_hda_codec_analog    78702  1 
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mpu401              6875  0 
snd_mpu401_uart         6857  1 snd_mpu401
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hwmon_vid               3130  0 
ppdev                   6375  0 
ns558                   3704  0 
gameport               10966  2 ns558
ipt_REJECT              2384  1 
xt_recent               8218  2 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  12 
ipt_addrtype            2151  4 
xt_state                1490  9 
ip6table_filter         2887  1 
ip6_tables             19618  1 ip6table_filter
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
nf_nat_ftp              2513  0 
nf_nat                 19501  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      12980  11 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
nf_conntrack           73966  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2791  1 
ip_tables              18390  1 iptable_filter
x_tables               22461  10 ipt_ULOG,ipt_REJECT,xt_recent,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
psmouse                64576  0 
serio_raw               4918  0 
snd                    71251  18 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sbp2                   22819  0 
parport_pc             29958  1 
asus_atk0110           10033  0 
nvidia              10832442  38 
vga16fb                12757  0 
vgastate                9857  1 vga16fb
edac_core              45423  0 
edac_mce_amd            9278  0 
k8temp                  4040  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvesafb                24962  1 
usbhid                 41116  3 
hid                    83536  1 usbhid
usb_storage            49961  1 
ohci1394               30260  0 
floppy                 63156  0 
ieee1394               94771  2 sbp2,ohci1394
sata_nv                23714  4 
pata_amd               11962  2 
forcedeth              55624  0 
             total       used       free     shared    buffers     cached
Mem:       4057760     989264    3068496          0      33384     373892
-/+ buffers/cache:     581988    3475772
Swap:      3229024          0    3229024
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Feb  8 23:24:50 EET 2011: performing suspend

```[U][B]Hibernate
[/B][/U]On the other hand hibernate works, BUT I have to manually force the pc to shut down by pressing the power button for some secs. When I start the pc again it resumes to its previous state.

I'd appreciate a guidance to what I should look for, cause I don't know what else to try.

Thank you!
Mike

---

### Post by P4man on 2011-02-09
Check out the link in my signature for some possible solutions.

---

### Post by P1C0 on 2011-02-09
> **P4man said:**
> Check out the link in my signature for some possible solutions.Thank you for your answer!

Currenty my grub configuration has this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"
```

I'll try combining acpi_osi, noapic, nolapic to see whether it helps. I also tend to believe that it is a BIOS issue, so I'll first boot into BIOS to see if there are some settings I can play with.

Mike

---

### Post by ranbo on 2011-02-09
I'm having a similar problem.  (Lenovo ThinkPad T500; 64-bit Ubuntu 10.10; "2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux")

Whether I close my laptop lid (set to do "suspend"), or select "suspend" or "hibernate" from the power menu, none of these work any longer.  The screen goes black, occasionally I get an error message, and then I'm back at the "screen lock" username and password prompt.  The machine won't suspend or hibernate.  This only started happening since the last time I updated (probably January 21).  Before that suspend & hibernate worked fine.

What broke? How can I diagnose this?

---

### Post by garyjmellor on 2011-02-09
@ranbo: have you installed anything like VirtualBox before noticing the issue? Suspend does not work with some VirtualBox settings (suspending the host I mean) but hibernate should still work. If you think this may be your issue, let me know and I'll try and figure out which setting it is that stops suspend. My other suggestion would still be to try and hunt down what you have installed before noticing the issue.
 
[EDIT] I think I got that the wrong way around. Anyway, if this is your problem, check dcstar's first posting here: [http://ubuntuforums.org/showthread.php?t=1673771](http://ubuntuforums.org/showthread.php?t=1673771)

---

### Post by P1C0 on 2011-02-09
acpi_osi= doesn't work.

It's so strange, all logs show that the pc suspends and hibernates fine, it's right after it suspends or hibernates that the problems occur.
Suspend -> can't wake up the pc after succesfully suspending it 
Hibernate -> can't completely shut down the pc after hibernation is complete, just stays with fans on.

---

### Post by P4man on 2011-02-09
Try some of the other options, like acpi_osi=Linux
Also make double sure the kernel is loaded with those parameters set. You can do that from a terminal with

cat /proc/cmdline

---

### Post by P1C0 on 2011-02-09
I tried it too, doesn't do anything. I even installed **uswsusp** package and still same effect: system suspends/hibernates ok, untill the next crucial step.

I booted into Windows 7 and it sleeps fine from there, monitor goes off and after that the whole pc. I press the power button and I'm back on track.

In ubuntu not even my monitor goes off, it just stays black.

I'll try and troubleshoot it some more :)

Mike

---

### Post by P1C0 on 2011-02-10
In a clean install (on a separate disk) of 10.10 64bit with binary nvidia drivers on and without interfering with any other settings, same problems occurs only that this time the monitor actually goes off.

---

### Post by P4man on 2011-02-10
Have you tried before installing the proprietary drivers? Not that I think nvidia drivers are to blame here actually (works fine here anyway). Have you checked for a BIOS update for your motherboard?

---

### Post by P1C0 on 2011-02-10
> **P4man said:**
> Have you tried before installing the proprietary drivers? Not that I think nvidia drivers are to blame here actually (works fine here anyway). Have you checked for a BIOS update for your motherboard?I don't think I have checked, but I could do that. Currently my BIOS is:
ASUS M2NPV-VM ACPI BIOS Revision 0603

There are many newer revisions provided by ASUS, but only for supporting new CPUs, except from a "Patch DMI rebuilding issue" revision.

My mobo has also HPET (High Presision Event Timer) enabled. I don't know if that has sth to do with anything. I'll try disabling it.

---

### Post by Huss on 2011-02-12
It seems like a common issue. On hibernate I have to pull the battery out to get it to shut down and then I had great difficulty in booting up after that. 

Advice would be appreciated.

Specs:
10.10
HP Tx2, Radeon graphics card, 64 bit.

---

### Post by Huss on 2011-02-12
Adding 'acpi_sleep s3_bios' to grub seemed to fix it fore me. Hibernate takes a while to come back to life, but at least it works

---

### Post by fresta on 2011-07-26
With S3 suspend you can try adding a quirk to pm-suspend.

I'm running Maverick 64-bit with an ASUS M2NPV-VM board and an Nvidia GeForce 6150. Resuming from suspend did not work. Running

sudo pm-suspend --quirk-s3-bios

did it for me. It even responds nicely to wakeonlan.

There are various settings in /usr/lib/pm-utils/video-quirks/20-video-quirk-pm-asus.quirkdb to automate this but none of it matches M2NPV-VM. Note that the system.hardware.* keys are not set by my board (a bug?) so I had to use system.board.* instead when modifying the file.

---

### Post by fresta on 2011-07-26
Sorry, that was a bit of a red herring. It turned out that the computer still froze after suspending sometimes, but never the first time! Looking at /var/log/pm-suspend gave no clues, it seems to happen after that.

However, after upgrading the Bios from version 0901 to 1401, S3 suspend and resume has been working (without any "quirks"). At least so far... There was a small glitch with the new bios; I had to disable legacy usb support to reenable keyboard and mouse.

---

