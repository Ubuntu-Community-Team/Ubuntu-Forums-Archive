---
title: "Intrepid unexpected shutdowns"
date: 2009-08-04
forum: General Help
---

### Post by kpatz on 2009-08-04
I have a machine I built back in February running Intrepid Server (to which I've installed Gnome, compiz, and a few other things).

Every once in a while it will shut down unexpectedly.  It's never done it when I was sitting at the machine, but it appears to be a clean shutdown, not an abrupt power cut or kernel panic.

It happened again this morning and here's my syslog file from the time it appeared to do it:

```
Aug  4 07:09:46 quattro sensord: Sensor alarm: Chip w83627ehf-isa-0290: Sys Temp: 34.0 C (limit = -3.0 C, hysteresis = -123.0 C) [ALARM]
Aug  4 07:10:01 quattro /USR/SBIN/CRON[19569]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug  4 07:10:46 quattro sensord: Sensor alarm: Chip w83627ehf-isa-0290: Sys Temp: 34.0 C (limit = -3.0 C, hysteresis = -123.0 C) [ALARM]
Aug  4 07:11:46 quattro sensord: Sensor alarm: Chip w83627ehf-isa-0290: Sys Temp: 34.0 C (limit = -3.0 C, hysteresis = -123.0 C) [ALARM]
Aug  4 07:12:46 quattro sensord: Sensor alarm: Chip w83627ehf-isa-0290: Sys Temp: 34.0 C (limit = -3.0 C, hysteresis = -123.0 C) [ALARM]
Aug  4 07:12:51 quattro kernel: [40115.902569] compiz.real[6838] trap stack segment ip:41024e sp:7fff6e5bbce0 error:0
Aug  4 07:12:54 quattro kernel: [40119.448815] [fglrx] Firegl kernel thread PID: 19738
Aug  4 07:12:54 quattro kernel: [40119.452628] APIC error on CPU2: 08(08)
Aug  4 07:12:54 quattro kernel: [40119.452629] APIC error on CPU0: 08(08)
Aug  4 07:12:54 quattro kernel: [40119.452639] APIC error on CPU1: 08(08)
Aug  4 07:12:54 quattro kernel: [40119.452649] APIC error on CPU3: 08(08)
Aug  4 07:12:54 quattro kernel: [40119.469856] [fglrx] Gart USWC size:1967 M.
Aug  4 07:12:54 quattro kernel: [40119.469876] [fglrx] Gart cacheable size:60 M.
Aug  4 07:12:54 quattro kernel: [40119.469888] [fglrx] Reserved FB block: Shared offset:0, size:1000000
Aug  4 07:12:54 quattro kernel: [40119.469894] [fglrx] Reserved FB block: Unshared offset:fbff000, size:401000
Aug  4 07:12:54 quattro kernel: [40119.469900] [fglrx] Reserved FB block: Unshared offset:17ffc000, size:4000
Aug  4 07:12:57 quattro gdmgreeter[19748]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks",
Aug  4 07:13:46 quattro sensord: Sensor alarm: Chip w83627ehf-isa-0290: Sys Temp: 34.0 C (limit = -3.0 C, hysteresis = -123.0 C) [ALARM]
Aug  4 07:14:05 quattro init: tty4 main process (5235) killed by TERM signal
Aug  4 07:14:05 quattro init: tty5 main process (5236) killed by TERM signal
Aug  4 07:14:05 quattro init: tty2 main process (5239) killed by TERM signal
Aug  4 07:14:05 quattro init: tty3 main process (5241) killed by TERM signal
Aug  4 07:14:05 quattro init: tty6 main process (5243) killed by TERM signal
Aug  4 07:14:05 quattro init: tty1 main process (6621) killed by TERM signal
Aug  4 07:14:09 quattro rpc.statd[4981]: Caught signal 15, un-registering and exiting.
Aug  4 07:14:09 quattro postfix/master[6183]: terminating on signal 15
Aug  4 07:14:09 quattro xinetd[6328]: Exiting...
Aug  4 07:14:09 quattro mysqld[5587]: 090804  7:14:09 [Note] /usr/sbin/mysqld: Normal shutdown
Aug  4 07:14:09 quattro mysqld[5587]:
Aug  4 07:14:09 quattro mysqld[5587]: 090804  7:14:09 [Note] /usr/sbin/mysqld: Shutdown complete
Aug  4 07:14:09 quattro mysqld[5587]:
Aug  4 07:14:09 quattro mysqld_safe[19996]: ended
Aug  4 07:14:13 quattro kernel: [40198.400746] nfsd: last server has exited, flushing export cache
Aug  4 07:14:13 quattro mountd[6109]: Caught signal 15, un-registering and exiting.
Aug  4 07:14:13 quattro avahi-daemon[5477]: Got SIGTERM, quitting.
Aug  4 07:14:13 quattro avahi-daemon[5477]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.12.
Aug  4 07:14:14 quattro exiting on signal 15

Aug  4 08:59:03 quattro syslogd 1.5.0#2ubuntu6: restart.

```
Don't mind the sensord alarms, I need to tweak the config file.  The machine isn't overheating or anything, and I don't see anything in any of the other logs that indicate a problem.

I think it has something to do with these 2 lines:

```
Aug  4 07:12:51 quattro kernel: [40115.902569] compiz.real[6838] trap stack segment ip:41024e sp:7fff6e5bbce0 error:0
Aug  4 07:12:54 quattro kernel: [40119.448815] [fglrx] Firegl kernel thread PID: 19738
```

This is the 3rd or 4th time this has happened since I built the machine last winter.  It shuts down, as if I did a normal "sudo shutdown -h now" or shut down from the GUI, and powers down.  

Thoughts?  Ideas?  Fix?

Vital stats:

ASRock A780GXE/128M AM2+/AM2 AMD 780G ATX AMD Motherboard w/integrated Radeon HD3200
AMD Phenom II X4 920 quad core CPU
8 GB RAM
80 GB Seagate SATA boot drive
4 1TB WD Green drives in a mdadm RAID5 array
Running Ubuntu Intrepid Server 64-bit w/Gnome and Compiz installed

---

### Post by wojox on 2009-08-04
The ubuntu server and desktop use different kernels. It looks like you would be better installing the desktop version and adding LAMP instead off the server version and installing GNOME and Compwiz.

---

### Post by kpatz on 2009-08-05
Actually, it turns out that my wife shut the server down. :o  I forgot to switch the KVM back to the Windows machine and she couldn't figure out how to get out of the "Linux" desktop so she hit the shutdown button.  Time to lock that out me thinks. ;)

But, if the machine powers down unexpectedly again, I'll be back with new logs...

---

