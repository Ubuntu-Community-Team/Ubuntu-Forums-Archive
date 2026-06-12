---
title: "vgetty Refuses to answer?"
date: 2009-09-18
forum: General Help
---

### Post by cuddles71 on 2009-09-18
Well, since NOBODY even ATTEMPTED to help, it's back to Windows XP for me. 

And yet, Linux advocates wonder why nobody likes Linux.

----------------

Hi all.

I'm trying to set up VOCP, but for some reason vgetty isn't answering the phone!

I'm fairly certain it's something to do with the modem initialization string (the modem is a Diamond Express 56e Pro), but I just can't figure it out.

Here's the log:
```

09/18 13:45:52 yS0  vgetty: experimental test release 0.9.32 / with duplex patch
09/18 13:45:52 yS0  mgetty: interim release 1.1.36-Jun15
09/18 13:45:52 yS0  reading generic configuration from config file /etc/mgetty/voice.conf
09/18 13:45:52 yS0   reading /etc/mgetty/voice.conf...
09/18 13:45:52 yS0   conf lib: read: 'part generic'
09/18 13:45:52 yS0   section: part generic, **found**
09/18 13:45:52 yS0   conf lib: read: 'voice_log_level 4'
09/18 13:45:52 yS0   conf lib: read: 'voice_shell_log /var/log/vgetty_voice_shell.%s'
09/18 13:45:52 yS0   conf lib: read: 'voice_dir /var/spool/voice'
09/18 13:45:52 yS0   conf lib: read: 'phone_owner root'
09/18 13:45:52 yS0   conf lib: read: 'phone_group voice'
09/18 13:45:52 yS0   conf lib: read: 'phone_mode 0660'
09/18 13:45:52 yS0   conf lib: read: 'message_flag_file .flag'
09/18 13:45:52 yS0   conf lib: read: 'receive_dir incoming'
09/18 13:45:52 yS0   conf lib: read: 'message_dir messages'
09/18 13:45:52 yS0   conf lib: read: 'message_list Index'
09/18 13:45:52 yS0   conf lib: read: 'backup_message standard.rmd'
09/18 13:45:52 yS0   conf lib: read: 'port_speed 115200'
09/18 13:45:52 yS0   conf lib: read: 'voice_shell /usr/bin/perl'
09/18 13:45:52 yS0   conf lib: read: 'port_timeout 10'
09/18 13:45:52 yS0   conf lib: read: 'dial_timeout 90'
09/18 13:45:52 yS0   conf lib: read: 'command_delay 100'
09/18 13:45:52 yS0   conf lib: read: 'dtmf_len 30'
09/18 13:45:52 yS0   conf lib: read: 'dtmf_threshold 40'
09/18 13:45:52 yS0   conf lib: read: 'dtmf_wait 7'
09/18 13:45:52 yS0   conf lib: read: 'ignore_fax_dle false'
09/18 13:45:52 yS0   conf lib: read: 'raw_data false'
09/18 13:45:52 yS0   conf lib: read: 'rec_compression 0'
09/18 13:45:52 yS0   conf lib: read: 'rec_speed 0'
09/18 13:45:52 yS0   conf lib: read: 'rec_silence_len 70'
09/18 13:45:52 yS0   conf lib: read: 'rec_silence_threshold 40'
09/18 13:45:52 yS0   conf lib: read: 'rec_remove_silence false'
09/18 13:45:52 yS0   conf lib: read: 'rec_max_len 300'
09/18 13:45:52 yS0   conf lib: read: 'rec_min_len 0'
09/18 13:45:52 yS0   conf lib: read: 'do_hard_flow true'
09/18 13:45:52 yS0   conf lib: read: 'beep_frequency 933'
09/18 13:45:52 yS0   conf lib: read: 'beep_length 1500'
09/18 13:45:52 yS0   conf lib: read: 'max_tries 3'
09/18 13:45:52 yS0   conf lib: read: 'retry_delay 5'
09/18 13:45:52 yS0   conf lib: read: 'watchdog_timeout 60'
09/18 13:45:52 yS0   conf lib: read: 'receive_gain -1'
09/18 13:45:52 yS0   conf lib: read: 'transmit_gain -1'
09/18 13:45:52 yS0   conf lib: read: 'enable_command_echo false'
09/18 13:45:52 yS0   conf lib: read: 'poll_interval 10'
09/18 13:45:52 yS0   conf lib: read: 'enable_compression_mapping_querry TRUE'
09/18 13:45:52 yS0   conf lib: read: 'compression_8bit_linear_signed 0'
09/18 13:45:52 yS0   conf lib: read: 'compression_16bit_linear_signed 0'
09/18 13:45:52 yS0   conf lib: read: 'compression_8bit_linear_unsigned 1'
09/18 13:45:52 yS0   conf lib: read: 'compression_8bit_ulaw 4'
09/18 13:45:52 yS0   conf lib: read: 'compression_8bit_alaw 5'
09/18 13:45:52 yS0   conf lib: read: 'compression_2bit_adpcm 140'
09/18 13:45:52 yS0   conf lib: read: 'compression_4bit_adpcm 141'
09/18 13:45:52 yS0   conf lib: read: 'compression_4bit_ima_adpcm 129'
09/18 13:45:52 yS0   conf lib: read: 'program vgetty'
09/18 13:45:52 yS0   found CT_KEYWORD program vgetty
09/18 13:45:52 yS0   conf lib: read: 'port ttyS0'
09/18 13:45:52 yS0   conf lib: read: 'rings 2'
09/18 13:45:52 yS0   conf lib: read: 'answer_mode voice:fax:data'
09/18 13:45:52 yS0   conf lib: read: 'force_autodetect false'
09/18 13:45:52 yS0   conf lib: read: 'toll_saver_rings 0'
09/18 13:45:52 yS0   conf lib: read: 'rec_always_keep true'
09/18 13:45:52 yS0   conf lib: read: 'button_program '
09/18 13:45:52 yS0   conf lib: read: 'call_program /etc/vocp/vocp.pl'
09/18 13:45:52 yS0   conf lib: read: 'dtmf_program dtmf.sh'
09/18 13:45:52 yS0   conf lib: read: 'message_program '
09/18 13:45:52 yS0   conf lib: read: 'do_message_light false'
09/18 13:45:52 yS0   conf lib: read: 'ring_report_delay 15'
09/18 13:45:52 yS0   conf lib: read: 'program vm'
09/18 13:45:52 yS0   conf lib: read: 'voice_devices ttyS0'
09/18 13:45:52 yS0   conf lib: read: 'dialout_timeout 90'
09/18 13:45:52 yS0   conf lib: read: 'ringback_goes_away 70'
09/18 13:45:52 yS0   conf lib: read: 'ringback_never_came 100'
09/18 13:45:52 yS0   conf lib: read: 'program pvf'
09/18 13:45:52 yS0   conf lib: read: 'port ttyS0'
09/18 13:45:52 yS0   conf lib: read: 'ring_type virtual'
09/18 13:45:52 yS0   conf lib: read: 'answer_mode fax:data'
09/18 13:45:52 yS0   conf lib: read: 'ring_type ring'
09/18 13:45:52 yS0   conf lib: read: 'ring_type ring1'
09/18 13:45:52 yS0   key: 'part', type=6, flags=4, data=(ignored)
09/18 13:45:52 yS0   key: 'program', type=6, flags=4, data=(ignored)
09/18 13:45:52 yS0   key: 'port', type=6, flags=4, data=(ignored)
09/18 13:45:52 yS0   key: 'ring_type', type=6, flags=4, data=(ignored)
09/18 13:45:52 yS0   key: 'voice_log_level', type=0, flags=3, data=4
09/18 13:45:52 yS0   key: 'voice_shell_log', type=1, flags=3, data=/var/log/vgetty_voice_shell.%s
09/18 13:45:52 yS0   key: 'voice_shell', type=1, flags=3, data=/usr/bin/perl
09/18 13:45:52 yS0   key: 'port_speed', type=0, flags=3, data=115200
09/18 13:45:52 yS0   key: 'port_timeout', type=0, flags=3, data=10
09/18 13:45:52 yS0   key: 'dial_timeout', type=0, flags=3, data=90
09/18 13:45:52 yS0   key: 'command_delay', type=0, flags=3, data=100
09/18 13:45:52 yS0   key: 'dtmf_len', type=0, flags=3, data=30
09/18 13:45:52 yS0   key: 'dtmf_threshold', type=0, flags=3, data=40
09/18 13:45:52 yS0   key: 'dtmf_wait', type=0, flags=3, data=7
09/18 13:45:52 yS0   key: 'ignore_fax_dle', type=3, flags=3, data=FALSE
09/18 13:45:52 yS0   key: 'raw_data', type=3, flags=3, data=FALSE
09/18 13:45:52 yS0   key: 'rec_compression', type=0, flags=3, data=0
09/18 13:45:52 yS0   key: 'rec_speed', type=0, flags=3, data=0
09/18 13:45:52 yS0   key: 'rec_silence_len', type=0, flags=3, data=70
09/18 13:45:52 yS0   key: 'rec_silence_threshold', type=0, flags=3, data=40
09/18 13:45:52 yS0   key: 'rec_remove_silence', type=3, flags=3, data=FALSE
09/18 13:45:52 yS0   key: 'rec_max_len', type=0, flags=3, data=300
09/18 13:45:52 yS0   key: 'rec_min_len', type=0, flags=3, data=0
09/18 13:45:52 yS0   key: 'do_hard_flow', type=3, flags=3, data=TRUE
09/18 13:45:52 yS0   key: 'force_autodetect', type=3, flags=1, data=FALSE
09/18 13:45:52 yS0   key: 'watchdog_timeout', type=0, flags=3, data=60
09/18 13:45:52 yS0   key: 'receive_gain', type=0, flags=3, data=-1
09/18 13:45:52 yS0   key: 'transmit_gain', type=0, flags=3, data=-1
09/18 13:45:52 yS0   key: 'enable_command_echo', type=3, flags=3, data=FALSE
09/18 13:45:52 yS0   key: 'poll_interval', type=0, flags=3, data=10
09/18 13:45:52 yS0   key: 'forceV253', type=3, flags=1, data=FALSE
09/18 13:45:52 yS0   key: 'forceV253subset', type=3, flags=1, data=FALSE
09/18 13:45:52 yS0   key: 'enable_compression_mapping_querry', type=3, flags=3, data=TRUE
09/18 13:45:52 yS0   key: 'compression_8bit_linear_signed', type=0, flags=3, data=0
09/18 13:45:52 yS0   key: 'compression_16bit_linear_signed', type=0, flags=3, data=0
09/18 13:45:52 yS0   key: 'compression_8bit_linear_unsigned', type=0, flags=3, data=1
09/18 13:45:52 yS0   key: 'compression_8bit_ulaw', type=0, flags=3, data=4
09/18 13:45:52 yS0   key: 'compression_8bit_alaw', type=0, flags=3, data=5
09/18 13:45:52 yS0   key: 'compression_2bit_adpcm', type=0, flags=3, data=140
09/18 13:45:52 yS0   key: 'compression_4bit_adpcm', type=0, flags=3, data=141
09/18 13:45:52 yS0   key: 'compression_4bit_ima_adpcm', type=0, flags=3, data=129
09/18 13:45:52 yS0   key: 'rings', type=1, flags=1, data=3
09/18 13:45:52 yS0   key: 'answer_mode', type=1, flags=1, data=voice:fax:data
09/18 13:45:52 yS0   key: 'toll_saver_rings', type=0, flags=1, data=0
09/18 13:45:52 yS0   key: 'rec_always_keep', type=3, flags=1, data=TRUE
09/18 13:45:52 yS0   key: 'voice_dir', type=1, flags=3, data=/var/spool/voice
09/18 13:45:52 yS0   key: 'phone_owner', type=1, flags=3, data=root
09/18 13:45:52 yS0   key: 'phone_group', type=1, flags=3, data=voice
09/18 13:45:52 yS0   key: 'phone_mode', type=0, flags=3, data=432
09/18 13:45:52 yS0   key: 'message_flag_file', type=1, flags=3, data=.flag

09/18 13:45:52 yS0   key: 'receive_dir', type=1, flags=3, data=incoming
09/18 13:45:52 yS0   key: 'message_dir', type=1, flags=3, data=messages
09/18 13:45:52 yS0   key: 'message_list', type=1, flags=3, data=Index
09/18 13:45:52 yS0   key: 'backup_message', type=1, flags=3, data=standard.rmd
09/18 13:45:52 yS0   key: 'button_program', type=1, flags=1, data=
09/18 13:45:52 yS0   key: 'call_program', type=1, flags=1, data=
09/18 13:45:52 yS0   key: 'dtmf_program', type=1, flags=1, data=dtmf.sh
09/18 13:45:52 yS0   key: 'message_program', type=1, flags=1, data=
09/18 13:45:52 yS0   key: 'do_message_light', type=3, flags=1, data=FALSE
09/18 13:45:52 yS0   key: 'pre_message', type=1, flags=1, data=
09/18 13:45:52 yS0   key: 'beepsound', type=1, flags=1, data=
09/18 13:45:52 yS0   key: 'beep_frequency', type=0, flags=3, data=933
09/18 13:45:52 yS0   key: 'beep_length', type=0, flags=3, data=1500
09/18 13:45:52 yS0   key: 'max_tries', type=0, flags=3, data=3
09/18 13:45:52 yS0   key: 'retry_delay', type=0, flags=3, data=5
09/18 13:45:52 yS0   key: 'dialout_timeout', type=0, flags=1, data=90
09/18 13:45:52 yS0   key: 'ringback_goes_away', type=0, flags=1, data=70
09/18 13:45:52 yS0   key: 'ringback_never_came', type=0, flags=1, data=100
09/18 13:45:52 yS0   key: 'ring_report_delay', type=0, flags=1, data=15
09/18 13:45:52 yS0   key: 'voice_devices', type=1, flags=1, data=
09/18 13:45:52 yS0  reading program vgetty configuration from config file /etc/mgetty/voice.conf
09/18 13:45:52 yS0  reading port ttyS0 configuration from config file /etc/mgetty/voice.conf
09/18 13:45:52 yS0  check for lockfiles
09/18 13:45:52 yS0  locking the line
09/18 13:45:52 yS0  lowering DTR to reset Modem
09/18 13:45:53 yS0  send: \dATQ0V1H0[0d]
09/18 13:45:54 yS0  waiting for ``OK'' ** found **
09/18 13:45:54 yS0  send: AT[0d]
09/18 13:45:54 yS0  waiting for ``OK'' ** found **
09/18 13:45:54 yS0  mdm_send: 'ATI'
09/18 13:45:54 yS0  Generic Rockwell modem (56000)
09/18 13:45:54 yS0  mdm_send: 'ATI3'
09/18 13:45:54 yS0  mdm_send: 'ATI4'
09/18 13:45:54 yS0  additional info: 'a007040284C6002F'
09/18 13:45:54 yS0  modem quirks: 0004
09/18 13:45:54 yS0  mdm_send: 'AT+FCLASS=2' -> OK
09/18 13:45:54 yS0  mdm_send: 'AT+FCLASS=0' -> OK
09/18 13:45:54 yS0  mdm_send: 'AT+FAA=1;+FCR=1' -> OK
09/18 13:45:54 yS0  mdm_send: 'AT+FBOR=0' -> OK
09/18 13:45:54 yS0  mdm_send: 'AT+FLID=""' -> OK
09/18 13:45:54 yS0  mdm_send: 'AT+FDCC=1,5,0,2,0,0,0,0' -> OK
09/18 13:45:54 yS0  detecting voice modem type
09/18 13:45:56 yS0  Rockwell detected
09/18 13:46:07 yS0  vgetty: timeout while reading character from voice modem
09/18 13:46:07 yS0  initializing ROCKWELL voice modem
09/18 13:46:07 yS0  vgetty: Modem returned ERROR
09/18 13:46:07 yS0  can't set silence period
09/18 13:46:07 yS0  vgetty: Modem returned ERROR
09/18 13:46:07 yS0  can't set transmit gain
09/18 13:46:07 yS0  vgetty: Modem returned ERROR
09/18 13:46:07 yS0  can't set record gain
09/18 13:46:07 yS0  vgetty: Modem returned ERROR
09/18 13:46:07 yS0  can't disable silence deletion
09/18 13:46:08 yS0  vgetty: Modem returned ERROR
09/18 13:46:08 yS0  can't set DLE responses
09/18 13:46:08 yS0  vgetty: Modem returned ERROR
09/18 13:46:08 yS0  can't set silence threshold
09/18 13:46:08 yS0  vgetty: Modem returned ERROR
09/18 13:46:08 yS0  waiting...
09/18 13:54:37 yS0  wfr: waiting for ``RING''
09/18 13:54:37 yS0  wfr: waiting for ``RING''
09/18 13:54:47 yS0  mdm_read_byte: read returned -1: Interrupted system call
09/18 13:54:47 yS0  wfr: timeout waiting for RING
09/18 13:54:47 ##### phone stopped ringing (rings=1, dev=ttyS0, pid=10301, caller='none')

09/18 13:54:47 yS0  waiting...
09/18 13:54:49 yS0  wfr: waiting for ``RING''
09/18 13:54:49 yS0  wfr: waiting for ``RING''

```

Any ideas where I'm going wrong?

---

### Post by cuddles71 on 2009-09-18
Update:

I now know that it IS the initialization strings being sent to the modem.

BUT, even though I've set the init-chat string in /etc/mgetty/mgetty.config, something is sending OTHER init strings that are overriding my choices:
```

09/18 20:44:11 yS0  check for lockfiles
09/18 20:44:11 yS0  locking the line
09/18 20:44:11 yS0  lowering DTR to reset Modem
09/18 20:44:12 yS0  send: ATZ[0d]
09/18 20:44:12 yS0  waiting for ``OK'' ** found **
09/18 20:44:12 yS0  send: AT+FCLASS=8[0d]
09/18 20:44:12 yS0  waiting for ``OK'' ** found **
09/18 20:44:12 yS0  mdm_send: 'ATI'
09/18 20:44:12 yS0  Generic Rockwell modem (56000)
09/18 20:44:12 yS0  mdm_send: 'ATI3'
09/18 20:44:12 yS0  mdm_send: 'ATI4'
09/18 20:44:12 yS0  additional info: 'a007040284C6002F'
09/18 20:44:12 yS0  modem quirks: 0004
09/18 20:44:12 yS0  mdm_send: 'AT+FCLASS=2' -> OK
09/18 20:44:13 yS0  mdm_send: 'AT+FCLASS=0' -> OK
09/18 20:44:13 yS0  mdm_send: 'AT+FAA=1;+FCR=1' -> OK
09/18 20:44:13 yS0  mdm_send: 'AT+FBOR=0' -> OK
09/18 20:44:13 yS0  mdm_send: 'AT+FLID=""' -> OK
09/18 20:44:13 yS0  mdm_send: 'AT+FDCC=1,5,0,2,0,0,0,0' -> OK
09/18 20:44:13 yS0  detecting voice modem type
09/18 20:44:15 yS0  Rockwell detected

```

Any idea on where these could be coming from, and how to stop them?

Thanks!

---

### Post by cuddles71 on 2009-09-19
Does nobody have an answer?

---

### Post by cuddles71 on 2009-09-19
Well, I've made SOME progress (thanks to nobody here, btw)...

```

09/19 16:08:44 yS0  send: AT+FCLASS=8[0d]
09/19 16:08:44 yS0  waiting for ``OK'' ** found **
09/19 16:08:45 yS0  waiting...
09/19 16:09:02 yS0  wfr: waiting for ``RING''
09/19 16:09:02 yS0  wfr: waiting for ``RING''
09/19 16:09:12 yS0  mdm_read_byte: read returned -1: Interrupted system call
09/19 16:09:12 yS0  wfr: timeout waiting for RING
09/19 16:09:12 ##### phone stopped ringing (rings=1, dev=ttyS0, pid=23350, caller='none')

09/19 16:09:13 yS0  waiting...
09/19 16:09:14 yS0  wfr: waiting for ``RING''
09/19 16:09:14 yS0  wfr: waiting for ``RING''
09/19 16:09:24 yS0  mdm_read_byte: read returned -1: Interrupted system call
09/19 16:09:24 yS0  wfr: timeout waiting for RING
09/19 16:09:24 ##### phone stopped ringing (rings=1, dev=ttyS0, pid=23350, caller='none')

```

The question is, what is causing that interrupted system call?

---

### Post by cuddles71 on 2009-09-20
Bump. Doesn't ANYONE know how to solve this?

---

### Post by cuddles71 on 2009-09-21
Okay, I've bumped the log level up to 9 to try and get more details about where vgetty is failing. 

```

09/21 12:27:23 yS0  waiting...
09/21 12:27:25 yS0    select returned 1
09/21 12:27:25 yS0   checking lockfiles, locking the line
09/21 12:27:25 yS0   makelock(ttyS0) called
09/21 12:27:25 yS0   do_makelock: lock='/var/lock/LCK..ttyS0'
09/21 12:27:25 yS0   lock made
09/21 12:27:25 yS0    vgetty: number of rings (2) was set directly
09/21 12:27:25 yS0  wfr: waiting for ``RING''
09/21 12:27:25 yS0   got: [10]R
09/21 12:27:25 yS0   wfr: rc=0, drn=0
09/21 12:27:25 yS0  wfr: waiting for ``RING''
09/21 12:27:25 yS0   got: [0d][0a]
09/21 12:27:35 yS0  mdm_read_byte: read returned -1: Interrupted system call
09/21 12:27:35 yS0  wfr: timeout waiting for RING
09/21 12:27:35 yS0   wfr: rc=-1, drn=0
09/21 12:27:35 ##### phone stopped ringing (rings=1, dev=ttyS0, pid=2826, caller='none')

09/21 12:27:35 yS0   waiting for line to clear (VTIME=3), read:
09/21 12:27:35 yS0   removing lock file
09/21 12:27:35 yS0  waiting...

```

At this point it's probably useless for me to even ask, but can SOMEBODY PLEASE take a look and tell me what's going wrong and how to fix it?

Thanks.

---

### Post by rthomas67 on 2010-01-15
For the benefit of others who haven't given up and run back to Windoze, here is some info that might help sort it out if you've found this thread by a search on some of the same symptoms.

One of the likely reasons for voice modem functions not working under Linux is that vgetty sometimes erroneously detects a Rockwell modem, and attempts to use the Rockwell AT[COLOR=Red]_**#**_[/COLOR] command-set (e.g. AT#VLS=?) instead of the AT[COLOR=Red]_**+**_[/COLOR] command-set that might actually work with the modem (e.g. AT+VLS=?).

To address this flaw in vgetty's modem detection, the VOCP project actually provides a patch for the vgetty (mgetty+sendfax) source that allows overriding vgetty's modem detection. 
See: [http://vocpsystem.com/vgetty_install.php?mode=function](http://vocpsystem.com/vgetty_install.php?mode=function)

But, before patching mgetty / vgetty, you can verify that this might be the issue you have by starting a serial console on the modem device and trying a few AT commands.  (Install uucp with "**sudo apt-get install uucp**" if the cu command isn't found on your system).

[INDENT][me@mybox ~]# cu -l ttyS0
AT
OK
AT+FCLASS=?
0,1,1.0,2,2.0,**8**
AT+FCLASS=8
OK
AT[COLOR=Red]**#**[/COLOR]VLS=?[B]
ERROR[/B]
AT[COLOR=Red]**+**[/COLOR]VLS=?
0," ",0000000000,0000000000,B084008000
1,"T",0B8418E000,0FE418E000,0B8419E000
[COLOR=Gray]*...snip...*[/COLOR]
~.
Disconnected.
[me@mybox ~]# 
[/INDENT]More info on the differences in modem types and AT command sets at: [http://en.wikipedia.org/wiki/Voice_modem_command_set](http://en.wikipedia.org/wiki/Voice_modem_command_set)

BTW, Is anyone at all puzzled by the lack of responses to the OP's?  I wonder if that "you stupid people must help me now or else I'm gonna leave" approach has ever worked for him/her.

---

### Post by jward3010 on 2010-01-15
I'll be straight with you dude, the reason there's no one around to help is because almost NO-ONE uses modems anymore hence NO-ONE has experience with them. Another kick in the teeth was the invention of the Winmodem which meant that the vast majority of modems would never work with Linux (not just Ubuntu, I mean the entirety of Linux) unless you paid a some arseholes that charged for a driver. 

So when it comes to modems it's not going to be easy.

---

### Post by rthomas67 on 2010-01-15
Yup.  The only reason I'm messing with a modem is to set up a little glue trap for telemarketers who, in spite of my number being on the national do-not-call list, just refuse to stop calling and trying to sell me stuff I don't want.  

If I can make it work (in spite of vgetty, modem drivers, etc.), I hope to configure vgetty to have the modem will pick up calls when the caller-id is "unknown" and then...

[LIST=1]
[*]play a message like "Hello... hold on a second..."
[*]wait 30 seconds or so
[*]play another message like "Ok, I'm back... who's calling? {loud background noise} Hold on again... let me move to where I can hear you..."
[*]wait another 20 seconds or so
[*]play another message like "Can you hear me now?" (with garbled audio) No? Ok... hold on again... let me switch phones.  This one must have a battery about to go dead."
[*]wait another 30 or 40 seconds...
[*]play another message like "Is thi_ an_ b__ter?  Ca_ y__ h_re me?  So_ry. I'm swit_h_ng t_ a ha_ds_t.  J_st a s_c__nd."
[*]wait another 10 or 15 seconds...
[*]etc.
[*]etc.
[/LIST]

If I can keep this going for several minutes, maybe I can save one or two other people the trouble of having to listen to a sales pitch from a company that doesn't respect someone's request not to be called.  I'm sure there are still two or three people in the world who still depend on a modem for voice features under Linux, but it isn't anything critical for me, more of a hobby interest.  Like most reasonable people, I realize the support for modems on Linux or any other OS is waning, and that doesn't bother me too much.  I guess I am bothered by people who think the Linux "community" is responsible for supporting and fixing any and every hardware/software combination that doesn't work just right and gets snippy and derogatory when they don't get an answer from the "community" right away.

---

### Post by HectorG on 2010-12-19
Did you ever get this to work? I am looking for something similar only I just want it to match a list of phone numbers I have in a DB and if it matches I want it to play the message and hang up.  I had mgetty echoing out the name and phone of caller through festival and that works great. I want to take it to the next level

---

