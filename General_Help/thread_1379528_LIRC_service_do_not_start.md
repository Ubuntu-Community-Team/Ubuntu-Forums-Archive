---
title: "LIRC service do not start"
date: 2010-01-12
forum: General Help
---

### Post by mmarre on 2010-01-12
Hi all,

I am really driving crazy. I am trying to start LIRC (service lirc start) and got the response that the modules loading fine but the remote control daemon fail:

```

 * Loading LIRC modules                                                                                          [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                      [fail]

```hardware.conf is proper configured as well as lircd.conf.

When I start 

/usr/sbin/lircd -H dev/input -d /dev/input/event5 -n

and in another shell irw I can see the key presses of the remote well returned.

I have no further idea why the service fail to start.

If I put 'set -x' in /etc/init.d/lirc I get following output:

```

+ . /lib/lsb/init-functions
+ FANCYTTY=
+ [ -e /etc/lsb-base-logging.sh ]
+ . /etc/lsb-base-logging.sh
+ test -f /usr/sbin/lircd
+ test -f /usr/sbin/lircmd
+ START_LIRCMD=true
+ START_LIRCD=true
+ START_IREXEC=true
+ [ -f /etc/lirc/hardware.conf ]
+ . /etc/lirc/hardware.conf
+ LIRCD_ARGS=
+ START_LIRCMD=false
+ LOAD_MODULES=true
+ DRIVER=dev/input
+ DEVICE=/dev/lirc
+ MODULES=
+ LIRCD_CONF=
+ LIRCMD_CONF=
+ [ ! -f /etc/lirc/lircd.conf ]
+ grep -q ^#UNCONFIGURED /etc/lirc/lircd.conf
+ [ ! -f /etc/lirc/lircmd.conf ]
+ grep -q ^#UNCONFIGURED /etc/lirc/lircmd.conf
+ START_LIRCMD=false
+ [ ! -f /etc/lirc/lircrc ]
+ START_IREXEC=false
+ OLD_SOCKET=/dev/lircd
+ [ -z  ]
+ REMOTE_SOCKET=/var/run/lirc/lircd
+ [ -z  ]
+ TRANSMITTER_SOCKET=/var/run/lirc/lircd
+ [ true = true ]
+ [ true = true ]
+ load_modules
+ MODULES_MISSING=false
+ log_daemon_msg Loading LIRC modules
+ [ -z Loading LIRC modules ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ usplash_write TEXT Loading LIRC modules
+ log_to_console log_daemon_msg Loading LIRC modules
+ [ n != y ]
+ [ no != yes ]
+ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ [ /dev/pts/0 != /dev/pts/0 ]
+ return 0
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ [ -t 1 ]
+ [ xxterm != x ]
+ [ xxterm != xdumb ]
+ [ -x /usr/bin/tput ]
+ [ -x /usr/bin/expr ]
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ [ -z ]
+ FANCYTTY=1
+ true
+ /usr/bin/tput xenl
+ /usr/bin/tput cols
+ COLS=120
+ [ 120 ]
+ [ 120 -gt 6 ]
+ /usr/bin/expr 120 - 7
+ COL=113
+ printf  * Loading LIRC modules
 * Loading LIRC modules       + /usr/bin/expr 120 - 1
+ /usr/bin/tput hpa 119
                                                                                                                       + printf
 + log_end_msg 0
+ [ -z 0 ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ [ 0 -eq 0 ]
+ usplash_write SUCCESS OK
+ log_to_console log_end_msg 0
+ [ n != y ]
+ [ no != yes ]
+ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ [ /dev/pts/0 != /dev/pts/0 ]
+ return 0
+ [ 113 ]
+ [ -x /usr/bin/tput ]
+ printf \r
+ /usr/bin/tput hpa 113
                                                                                                                 + [ 0 -eq 0 ]
+ echo [ OK ]
[ OK ]
+ return 0
+ false
+ [ true = true ]
+ [ -d /var/run/lirc ]
+ log_daemon_msg Starting remote control daemon(s) : LIRC
+ [ -z Starting remote control daemon(s) : LIRC  ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ usplash_write TEXT Starting remote control daemon(s) : LIRC
+ log_to_console log_daemon_msg Starting remote control daemon(s) : LIRC
+ [ n != y ]
+ [ no != yes ]
+ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ [ /dev/pts/0 != /dev/pts/0 ]
+ return 0
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ [ -t 1 ]
+ [ xxterm != x ]
+ [ xxterm != xdumb ]
+ [ -x /usr/bin/tput ]
+ [ -x /usr/bin/expr ]
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ [ -z 1 ]
+ true
+ true
+ /usr/bin/tput xenl
+ /usr/bin/tput cols
+ COLS=120
+ [ 120 ]
+ [ 120 -gt 6 ]
+ /usr/bin/expr 120 - 7
+ COL=113
+ printf  * Starting remote control daemon(s) : LIRC
 * Starting remote control daemon(s) : LIRC        + /usr/bin/expr 120 - 1
+ /usr/bin/tput hpa 119
                                                                                                                       + printf
 + build_remote_args
+ REMOTE_ARGS=
+ [ -z  ]
+ [ -z  ]
+ [ -c ]
+ REMOTE_DEVICE=
+ [ ! -z  ]
+ [ ! -z  ]
+ echo
+ REMOTE_LIRCD_ARGS=
+ build_transmitter_args
+ TRANSMITTER_ARGS=
+ [ ! -z  ]
+ [ ! -z  ]
+ echo
+ TRANSMITTER_LIRCD_ARGS=
+ [ ! -z  ]
+ [ ! -z  ]
+ log_end_msg 1
+ [ -z 1 ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ [ 1 -eq 0 ]
+ usplash_write FAILURE failed
+ log_to_console log_end_msg 1
+ [ n != y ]
+ [ no != yes ]
+ readlink /proc/self/fd/0
+ stdin=/dev/pts/0
+ [ /dev/pts/0 != /dev/pts/0 ]
+ return 0
+ [ 113 ]
+ [ -x /usr/bin/tput ]
+ printf \r
+ /usr/bin/tput hpa 113
                                                                                                                 + [ 1 -eq 0 ]
+ printf [
[+ /usr/bin/tput setaf 1
+ printf fail
fail+ /usr/bin/tput op
+ echo ]
]
+ return 1
+ [ false = true ]
+ [ false = true ]
+ exit 0

```

Any ideas? Google and forumsearch wasn't helpful.

Regards
Michael

---

### Post by mmarre on 2010-01-12
Additional my config files:

hardware.conf:

```

# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

lircd.conf:

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(devinput) on Mon Oct 19 19:38:48 2009
#
# contributed by
#
# brand:                       lircd.conf
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  lircd.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          199989
  toggle_bit_mask 0x80010074

      begin codes
          1                        0x0074
          2                        0x0002
          3                        0x0003
          4                        0x0004
          5                        0x0005
          6                        0x0006
          7                        0x0007
          8                        0x0008
          9                        0x0009
          MENU                     0x0160
          INFO                     0x0193
          TV/RADIO                 0x006A
          POWER                    0x000B
          MUTE                     0x00AD
          EXT                      0x00A7
          A/B                      0x0172
          EPG                      0x00D0
          BACK                     0x008B
          OK                       0x018E
          UP                       0x0077
          DOWN                     0x0066
          LEFT                     0x0069
          RIGHT                    0x0067
          RED                      0x0177
          GREEN                    0x00CF
          YELLOW                   0x009E
          BLUE                     0x00A8
          TXT                      0x0197
          STOP                     0x0189
          HELP                     0x016D
      end codes

end remote

```

No entrys seen in the syslog.

Regards

Michael

---

### Post by mmarre on 2010-01-12
BTW: /dev/input/event5 also don't work in hardware.conf

regards
Michael

---

### Post by mmarre on 2010-01-13
-Push-

No one has an idea?

Regards,
Michael

---

