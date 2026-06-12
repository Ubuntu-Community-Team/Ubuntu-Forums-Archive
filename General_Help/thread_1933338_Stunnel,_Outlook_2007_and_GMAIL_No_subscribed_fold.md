---
title: "Stunnel, Outlook 2007 and GMAIL: No subscribed folders or calendar"
date: 2012-02-29
forum: General Help
---

### Post by Jonners59 on 2012-02-29
I have managed to get my stunnel working with gMail for Outlook 2007.  I have now reached a next level of problem and need some help.

The accounts sync but it will not load the sub-folders, and when I try and set up the calendars I get error messages.

I have always wanted to migrate back to outlook from Evolution, but had trouble setting up stunnel.  Now Evolution is not working I need to speed up my Outlook project.

Any ideas please.

---

### Post by Jonners59 on 2012-03-10
Any help with this please?

Stunnel Conf enclosed (Converted to txt).
Each Google eMail account in Outlook is assigned a different port to access, matching the ports in the conf file.

---

### Post by Jonners59 on 2012-03-13
I made some changes to my stunnel config, and had one account working.  I added the remaining 3 and it seemed to start to work, but now it has stopped.  Outbound (send) seems to be fine.  Any ideas?????

Telnet and post listening test results:

```
$ netstat -an | grep -iw LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3000          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3001          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3002          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3003          0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN     
baronipc@baronipc:~$ telnet localhost 3000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
baronipc@baronipc:~$ telnet localhost 3001
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
baronipc@baronipc:~$ telnet localhost 3002
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
baronipc@baronipc:~$ telnet localhost 3003
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
baronipc@baronipc:~$ 

```

Copy of config file:
```
    ; Sample stunnel configuration file by Michal Trojnara 2002-2006
    ; Some options used here may not be adequate for your particular configuration
    ; Please make sure you understand them (especially the effect of chroot jail)

    ; Certificate/key is needed in server mode and optional in client mode
    cert = /etc/stunnel/mail.pem
    ;key = /etc/stunnel/mail.pem

    ; Protocol version (all, SSLv2, SSLv3, TLSv1)
    sslVersion = SSLv3

    ; Some security enhancements for UNIX systems - comment them out on Win32
    chroot = /var/lib/stunnel4/
    setuid = stunnel4
    setgid = stunnel4
    ; PID is created inside chroot jail
    pid = /stunnel4.pid

    ; Some performance tunings
    socket = l:TCP_NODELAY=1
    socket = r:TCP_NODELAY=1
    ;compression = rle

    ; Workaround for Eudora bug
    ;options = DONT_INSERT_EMPTY_FRAGMENTS

    ; Authentication stuff
    ;verify = 2
    ; Don't forget to c_rehash CApath
    ; CApath is located inside chroot jail
    ;CApath = /certs
    ; It's often easier to use CAfile
    ;CAfile = /etc/stunnel/certs.pem
    ; Don't forget to c_rehash CRLpath
    ; CRLpath is located inside chroot jail
    ;CRLpath = /crls
    ; Alternatively you can use CRLfile
    ;CRLfile = /etc/stunnel/crls.pem

    ; Some debugging stuff useful for troubleshooting
    debug = 7
    output = /var/log/stunnel4/stunnel.log

    ; Use it for client mode
    client = yes

    ; Service-level configuration

    ;[pop3s]
    ;accept = 995
    ;connect = 110

    [imaps Work]
    accept = 127.0.0.1:3000
    connect = imap.gmail.com:993
 [imaps Personal]
    accept = 127.0.0.1:3001
    connect = imap.gmail.com:993
 [imaps Admin]
    accept = 127.0.0.1:3002
    connect = imap.gmail.com:993
 [imaps Co]
    accept = 127.0.0.1:3003
    connect = imap.gmail.com:993

;[ssmtp Work]
    ;accept = 127.0.0.1:4000
    ;connect = smtp.gmail.com:465

;[ssmt Personal]
    ;accept = 127.0.0.1:4001
    ;connect = smtp.gmail.com:465

;[ssmtp Admin]
    ;accept = 127.0.0.1:4002
    ;connect = smtp.gmail.com:587

;[ssmtp Co]
    ;accept = 127.0.0.1:4003
    ;connect = smtp.gmail.com:587

;[ssmtp other]
    ;accept = 127.0.0.1:4004
    ;connect = 25

    ;[https]
    ;accept = 443
    ;connect = 80
    ;TIMEOUTclose = 0

    ; vim:ft=dosini
```

And /etc/default/stunnel4
```
# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel automatic startup
ENABLED=1
FILES="/etc/stunnel/*.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0
```

---

### Post by Jonners59 on 2012-11-19
Ubuntu 12:10 - 64-bitRAM 16.7GB
Processor: Intel® Core&#8482; i5-2500K CPU @ 3.30GHz × 4
Graphics: GeForce GT 430/PCIe/SSE2 

Still can not get Stunnel working...  driving me mad.  Here is everything I have installed on my machine and where configs refer to something what I have, or have not found.  At the foot are the outputs of commands......

I am getting no logs in the log file.  It is empty.

Nothing is in /var/run/stunnel4/ and nothing in /var/run/stunnel.pid, nor /stunnel.pid

/etc/default/Stunnel4

```
# /etc/default/stunnel
# Julien LEMOINE <speedblue@debian.org>
# September 2003

# Change to one to enable stunnel automatic startup
ENABLED=1
FILES="/etc/stunnel/*.conf"
OPTIONS=""

# Change to one to enable ppp restart scripts
PPP_RESTART=0
```/etc/stunnel/stunnel.conf

```
; Sample stunnel configuration file by Michal Trojnara 2002-2009
; Some options used here may not be adequate for your particular configuration
; Please make sure you understand them (especially the effect of the chroot jail)

; Certificate/key is needed in server mode and optional in client mode
cert = /etc/stunnel/mail.pem
;key = /etc/ssl/certs/stunnel.pem

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside the chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = zlib

; Workaround for Eudora bug
;options = DONT_INSERT_EMPTY_FRAGMENTS

; Authentication stuff
;verify = 2
; Don't forget to c_rehash CApath
; CApath is located inside chroot jail
;CApath = /certs
; It's often easier to use CAfile
;CAfile = /etc/stunnel/certs.pem
; Don't forget to c_rehash CRLpath
; CRLpath is located inside chroot jail
;CRLpath = /crls
; Alternatively you can use CRLfile
;CRLfile = /etc/stunnel/crls.pem

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

; [pop3s]
; accept  = 995
; connect = 110

[Gmail-IMAP Personal]
accept=127.0.0.1:3000
connect=imap.gmail.com:993
 [Gmail-SMTP]
accept=127.0.0.1:3001
connect=smtp.gmail.com:465

[Gmail-IMAP Work]
accept=127.0.0.1:3002
connect=imap.gmail.com:995
 [Gmail-SMTP]
accept=127.0.0.1:3003
connect=smtp.gmail.com:465

[Gmail-IMAP Baroni]
accept=127.0.0.1:3004
connect=imap.gmail.com:993
 [Gmail-SMTP]
accept=127.0.0.1:3005
connect=smtp.gmail.com:465

[Gmail-IMAP Adminsitration]
accept=127.0.0.1:3006
connect=imap.gmail.com:993
 [Gmail-SMTP]
accept=127.0.0.1:3007
connect=smtp.gmail.com:465

[Gmail-IMAP Information]
accept=127.0.0.1:3008
connect=imap.gmail.com:995
 [Gmail-SMTP]
accept=127.0.0.1:3009
connect=smtp.gmail.com:465

[ssmtp]
;accept  = 127.0.0.1:465
;connect = smtp.gmail.com:25

;[https]
;accept  = 443
;connect = 80
;TIMEOUTclose = 0

; vim:ft=dosini

[rdp]
accept = 1234
connect = 123.123.123.123:22
```Stunnel4 in/etc/init.d

```
#! /bin/sh -e
### BEGIN INIT INFO
# Provides:          stunnel4
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      $syslog
# Should-Stop:       $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start or stop stunnel 4.x (SSL tunnel for network daemons)
# Description:       Starts or stops all configured SSL network tunnels. Each *.conf file in
#                    /etc/stunnel/ will spawn a separate stunnel process. The list of files
#                    can be overriden in /etc/default/stunnel, and that same file can be used
#                    to completely disable *all* tunnels.
### END INIT INFO

DEFAULTPIDFILE="/var/run/stunnel4.pid"
DAEMON=/usr/bin/stunnel4
NAME=stunnel
DESC="SSL tunnels"
OPTIONS=""
ENABLED=0

get_pids() {
   local file=$1
   if test -f $file; then
     CHROOT=`grep "^chroot" $file|sed "s;.*= *;;"`
     PIDFILE=`grep "^pid" $file|sed "s;.*= *;;"`
     if [ "$PIDFILE" = "" ]; then
       PIDFILE=$DEFAULTPIDFILE
     fi
     if test -f $CHROOT/$PIDFILE; then
       cat $CHROOT/$PIDFILE
     fi
   fi
}

startdaemons() {
  if ! [ -d /var/run/stunnel4 ]; then
    rm -rf /var/run/stunnel4
    install -d -o stunnel4 -g stunnel4 /var/run/stunnel4
  fi
  for file in $FILES; do 
    if test -f $file; then
      ARGS="$file $OPTIONS"
      PROCLIST=`get_pids $file`
      if [ "$PROCLIST" ] && kill -s 0 $PROCLIST 2>/dev/null; then
        echo -n "[Already running: $file] "
      elif $DAEMON $ARGS; then
    echo -n "[Started: $file] "
      else
    echo "[Failed: $file]"
    echo "You should check that you have specified the pid= in you configuration file"
    exit 1
      fi
    fi
  done;
}

killdaemons()
{
  SIGNAL=${1:-TERM}
  for file in $FILES; do
    PROCLIST=`get_pids $file`
    if [ "$PROCLIST" ] && kill -s 0 $PROCLIST 2>/dev/null; then
       kill -s $SIGNAL $PROCLIST
       echo -n "[stopped: $file] "
    fi
  done
}

if [ "x$OPTIONS" != "x" ]; then
  OPTIONS="-- $OPTIONS"
fi

test -f /etc/default/stunnel4 && . /etc/default/stunnel4
if [ "$ENABLED" = "0" ] ; then
  echo "$DESC disabled, see /etc/default/stunnel4"
  exit 0
fi

# If the user want to manage a single tunnel, the conf file's name
# is in $2. Otherwise, respect /etc/default/stunnel4 setting. If no
# setting there, use /etc/stunnel/*.conf
if [ -n "${2:-}" ]; then
  if [ -e "/etc/stunnel/$2.conf" ]; then
    FILES="/etc/stunnel/$2.conf"
  else
    echo >&2 "/etc/stunnel/$2.conf does not exist."
    exit 1
  fi
else
  if [ -z "$FILES" ]; then
    FILES="/etc/stunnel/*.conf"
  fi
fi

test -x $DAEMON || exit 0

set -e

case "$1" in
  start)
        echo -n "Starting $DESC: "
        startdaemons
        echo "$NAME."
        ;;
  stop)
        echo -n "Stopping $DESC: "
        killdaemons
        echo "$NAME."
        ;;
  reopen-logs)
        echo -n "Reopening log files $DESC: "
        killdaemons USR1
        echo "$NAME."
        ;;
  force-reload|reload)
        echo -n "Reloading configuration $DESC: "
        killdaemons HUP
        echo "$NAME."
        ;;  
  restart)
        echo -n "Restarting $DESC: "
        killdaemons
        sleep 5
        startdaemons
        echo "$NAME."
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|reload|reopen-logs|restart} [<stunnel instance>]" >&2
        exit 1
        ;;
esac

exit 0
```/usr/bin/stunnel4 - an executable application not openable, plus
/usr/bin/stunnel3

```
#!/usr/bin/perl
#
# stunnel3      Perl wrapper to use stunnel 3.x syntax in stunnel >=4.05
# Copyright (C) 2004-2012 Michal Trojnara <Michal.Trojnara@mirt.net>
# Version:      2.03
# Date:         2011.10.22
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the
# Free Software Foundation; either version 2 of the License, or (at your
# option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
# See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, see <http://www.gnu.org/licenses>.

use POSIX;
use Getopt::Std;

# Configuration - path to stunnel (version >=4.05)
$stunnel_bin='/usr/bin/stunnel4';

# stunnel3 script body begins here
($read_fd, $write_fd)=POSIX::pipe();
$pid=fork;
die "Can't fork" unless defined $pid;
if($pid) { # parent
    POSIX::close($write_fd);
    exec "$stunnel_bin -fd $read_fd";
    die "$stunnel_bin exec failed";
}
# child
POSIX::close($read_fd);
open(STUNNEL, ">&$write_fd");
# comment out the next line to see the config file
select(STUNNEL);

getopts('cTWfD:O:o:C:p:v:a:A:t:N:u:n:E:R:B:I:d:s:g:P:r:L:l:');

print("client = yes\n") if defined $opt_c;
print("transparent = yes\n") if defined $opt_T;
print("RNDoverwrite = yes\n") if defined $opt_W;
print("foreground = yes\n") if defined $opt_f;
print("debug = $opt_D\n") if defined $opt_D;
print("socket = $opt_O\n") if defined $opt_O;
print("output = $opt_o\n") if defined $opt_o;
print("ciphers = $opt_C\n") if defined $opt_C;
print("cert = $opt_p\n") if defined $opt_p;
print("verify = $opt_v\n") if defined $opt_v;
print("CApath = $opt_a\n") if defined $opt_a;
print("CAfile = $opt_A\n") if defined $opt_A;
print("session = $opt_t\n") if defined $opt_t;
print("service = $opt_N\n") if defined $opt_N;
print("ident = $opt_u\n") if defined $opt_u;
print("protocol = $opt_n\n") if defined $opt_n;
print("EGD = $opt_E\n") if defined $opt_E;
print("RNDfile = $opt_R\n") if defined $opt_R;
print("RNDbytes = $opt_B\n") if defined $opt_B;
print("local = $opt_I\n") if defined $opt_I;
print("accept = $opt_d\n") if defined $opt_d;
print("setuid = $opt_s\n") if defined $opt_s;
print("setgid = $opt_g\n") if defined $opt_g;
print("pid = $opt_P\n") if defined $opt_P;
print("connect = $opt_r\n") if defined $opt_r;
print("pty = yes\n"), $opt_l=$opt_L if defined $opt_L;
print("exec = $opt_l\nexecargs = " . join(' ', $opt_l, @ARGV) . "\n") if defined $opt_l;
print("[stunnel3]\n") if defined $opt_d;

close(STUNNEL);

# stunnel3 script body ends here
```Error messages:

When I start stunnel with ```
sudo stunnel4
``````
$ sudo stunnel4
[sudo] password for baronipc: 
Clients allowed=500
stunnel 4.53 on x86_64-pc-linux-gnu platform
Compiled with OpenSSL 1.0.1 14 Mar 2012
Running  with OpenSSL 1.0.1c 10 May 2012
Update OpenSSL shared libraries or rebuild stunnel
Threading:PTHREAD SSL:+ENGINE+OCSP Auth:LIBWRAP Sockets:POLL+IPv6
Reading configuration from file /etc/stunnel/stunnel.conf
Compression not enabled
Snagged 64 random bytes from /home/baronipc/.rnd
Wrote 1024 new random bytes to /home/baronipc/.rnd
PRNG seeded successfully
Initializing service section [Gmail-IMAP Personal]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Work]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Baroni]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Adminsitration]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Information]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [ssmtp]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Section ssmtp: Each service must define two endpoints
str_stats: 65 block(s), 13408 data byte(s), 3770 control byte(s)

```When I telnet

```

baronipc@baronipc:~$ telnet 127.0.0.1 993
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
baronipc@baronipc:~$ telnet 127.0.0.1 995
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
baronipc@baronipc:~$ telnet 127.0.0.1 465
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
baronipc@baronipc:~$ telnet 127.0.0.1 3000
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```When I start Stunnel using ```
sudo /etc/init.d/stunnel4 start
``````
$ sudo /etc/init.d/stunnel4 start
Starting SSL tunnels: Clients allowed=500
stunnel 4.53 on x86_64-pc-linux-gnu platform
Compiled with OpenSSL 1.0.1 14 Mar 2012
Running  with OpenSSL 1.0.1c 10 May 2012
Update OpenSSL shared libraries or rebuild stunnel
Threading:PTHREAD SSL:+ENGINE+OCSP Auth:LIBWRAP Sockets:POLL+IPv6
Reading configuration from file /etc/stunnel/stunnel.conf
Compression not enabled
Snagged 64 random bytes from /home/baronipc/.rnd
Wrote 1024 new random bytes to /home/baronipc/.rnd
PRNG seeded successfully
Initializing service section [Gmail-IMAP Personal]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Work]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Baroni]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Adminsitration]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-IMAP Information]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [Gmail-SMTP]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Initializing service section [ssmtp]
Insecure file permissions on /etc/stunnel/mail.pem
Certificate: /etc/stunnel/mail.pem
Certificate loaded
Key file: /etc/stunnel/mail.pem
Private key loaded
SSL options set: 0x00000004
Section ssmtp: Each service must define two endpoints
str_stats: 65 block(s), 13408 data byte(s), 3770 control byte(s)
[Failed: /etc/stunnel/stunnel.conf]
You should check that you have specified the pid= in you configuration file
```This line maybe the clue:
[HTML]You should check that you have specified the pid= in you configuration file[/HTML]the config file says that[HTML] pid = /stunnel4.pid[/HTML], but there is no such file in /

---

