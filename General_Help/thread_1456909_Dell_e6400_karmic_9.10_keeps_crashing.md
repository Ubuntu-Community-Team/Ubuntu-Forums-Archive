---
title: "Dell e6400 karmic 9.10 keeps crashing  ?"
date: 2010-04-17
forum: General Help
---

### Post by ullastharakan on 2010-04-17
HI,
I recently installed KArmic Kola on my DELL E6400 - 9600 INTEL PROCESSOR, 4GB RAM, NVIDIA GRAPHIC QUADRO 160. I have the following issues which is making me nervous to work on the system

- System keeps crashing - all of sudden the Caps button LED, NUM LOCK LED keeps blinking and system freezes for a while and restarts

Just before crashing it logged the following messages, ANY HELP is greatly appreciated -

Apr 17 10:50:38 ullas-laptop kernel: [ 2535.806128] generic-usb 0003:045E:0745.0004: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft® 2.4GHz Transceiver v4.0] on usb-0000:00:1d.1-1/input1
Apr 17 10:50:38 Sulla-laptop kernel: [ 2535.833302] input: Microsoft Microsoft® 2.4GHz Transceiver v4.0 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.2/input/input18
Apr 17 10:50:38 ullas-laptop kernel: [ 2535.833419] generic-usb 0003:045E:0745.0005: input,hiddev96,hidraw3: USB HID v1.11 Device [Microsoft Microsoft® 2.4GHz Transceiver v4.0] on usb-0000:00:1d.1-1/input2
Apr 17 11:17:39 ullas-laptop kernel: [ 4156.848681] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = 00:1f:33:f3:92:9a tid = 6
Apr 17 11:43:50 ullas-laptop kernel: [ 5727.558160] iwlagn 0000:0c:00.0: iwl_tx_agg_start on ra = 00:1f:33:f3:92:9a tid = 1
Apr 17 12:07:09 ullas-laptop kernel: [ 7126.231468] dell-wmi: Unknown key fff0 pressed
Apr 17 12:09:33 ullas-laptop kernel: [ 7270.627503] dell-wmi: Unknown key fff1 pressed
Apr 17 13:47:56 ullas-laptop kernel: [13173.231230] dell-wmi: Unknown key ffd0 pressed
Apr 17 13:48:13 ullas-laptop kernel: [13189.912833] dell-wmi: Unknown key ffd1 pressed
Apr 17 14:36:45 ullas-laptop kernel: [16102.189765] dell-wmi: Unknown key ffd0 pressed
Apr 17 14:38:52 ullas-laptop kernel: [16229.728397] dell-wmi: Unknown key ffd1 pressed
Apr 17 15:09:11 ullas-laptop kernel: [18048.222745] dell-wmi: Unknown key ffd0 pressed
Apr 17 15:17:07 ullas-laptop kernel: [18524.161373] dell-wmi: Unknown key ffd1 pressed
Apr 17 15:47:44 ullas-laptop kernel: [20361.192555] dell-wmi: Unknown key ffd0 pressed
Apr 17 17:53:47 ullas-laptop kernel: [27924.489799] dell-wmi: Unknown key ffd1 pressed
Apr 17 19:42:57 ullas-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr 17 19:42:57 ullas-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="939" x-info="http://www.rsyslog.com"] (re)start
Apr 17 19:42:57 ullas-laptop rsyslogd: rsyslogd's groupid changed to 102
Apr 17 19:42:57 ullas-laptop rsyslogd: rsyslogd's userid changed to 101
Apr 17 19:42:57 ullas-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 17 19:42:57 ullas-laptop kernel: [    0.000000] Initializing cgroup subsys cpu

---

### Post by retropdarb on 2010-12-31
Any update on this?
I am getting a similar crash with a Dell XPS Studio 16.
Running Ubuntu 10.10
I get "dell-wmi: Unknown key 3a pressed"

It happens at a time when no one is obviously around to press a key of any kind...

---

