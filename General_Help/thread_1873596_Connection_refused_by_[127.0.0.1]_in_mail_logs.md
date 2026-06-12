---
title: "Connection refused by [127.0.0.1] in mail logs"
date: 2011-11-01
forum: General Help
---

### Post by terryit3 on 2011-11-01
Does anyone know why my mail logs are full of this entry?
I am using SendMail on Ubuntu 8.04 Hardy Heron.

I will provide as much information as I can in order to get some help.  Thanks!

Nov  1 15:13:52 mail sm-msp-queue[5455]: grew WorkList for /var/spool/mqueue-client to 52000
Nov  1 15:13:56 mail sm-msp-queue[5455]: grew WorkList for /var/spool/mqueue-client to 53000
Nov  1 15:14:00 mail sm-msp-queue[5455]: grew WorkList for /var/spool/mqueue-client to 54000
Nov  1 15:14:04 mail sm-msp-queue[5455]: grew WorkList for /var/spool/mqueue-client to 55000
Nov  1 15:14:08 mail sm-msp-queue[5455]: grew WorkList for /var/spool/mqueue-client to 56000
Nov  1 15:14:11 mail sm-msp-queue[5455]: grew WorkList for /var/spool/mqueue-client to 57000
 
[SIZE="4"]**===== AND ====**[/SIZE]

Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1c9013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5796647, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cA013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5796799, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cB013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5796955, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cC013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5797027, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cD013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5797044, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cE013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5797145, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cF013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5797154, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cG013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5797293, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cH013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5797310, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Nov  1 15:14:40 mail sm-msp-queue[5455]: p9VNK1cI013541: to=postmaster, delay=19:51:40, xdelay=00:00:00, mailer=relay, pri=5797783, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]

---

### Post by terryit3 on 2011-11-01
Also.. Sendmail is not slow and it sends mail just fine.
I'd just like to clear up my logs if possible.

Here is my Sendmail.mc file contents: 

#
define(`_USE_ETC_MAIL_')dnl
include(`/usr/share/sendmail/cf/m4/cf.m4')dnl
VERSIONID(`$Id: sendmail.mc, v 8.14.2-2build1 2008-01-24 14:29:57 cowboy Exp $')
OSTYPE(`debian')dnl
DOMAIN(`debian-mta')dnl
dnl # Items controlled by /etc/mail/sendmail.conf - DO NOT TOUCH HERE
undefine(`confHOST_STATUS_DIRECTORY')dnl        #DAEMON_HOSTSTATS=
dnl # Items controlled by /etc/mail/sendmail.conf - DO NOT TOUCH HERE
dnl #
dnl # General defines
dnl #
dnl # SAFE_FILE_ENV: [undefined] If set, sendmail will do a chroot()
dnl #	into this directory before writing files.
dnl #	If *all* your user accounts are under /home then use that
dnl #	instead - it will prevent any writes outside of /home !
dnl #   define(`confSAFE_FILE_ENV',             `')dnl
dnl #
dnl # Daemon options - restrict to servicing LOCALHOST ONLY !!!
dnl # Remove `, Addr=' clauses to receive from any interface
dnl # If you want to support IPv6, switch the commented/uncommentd lines
dnl #
FEATURE(`no_default_msa')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission, Addr=::1')dnl
dnl DAEMON_OPTIONS(`Port=smtp, Addr=127.0.0.1, Name=MTA`)dnl
dnl # Be somewhat anal in what we allow
define(`confPRIVACY_FLAGS',dnl
`needmailhelo,needexpnhelo,needvrfyhelo,restrictqrun,restrictexpand,nobodyreturn,authwarnings')dnl
dnl #
dnl # Define connection throttling and window length
define(`confCONNECTION_RATE_THROTTLE', `15')dnl
define(`confCONNECTION_RATE_WINDOW_SIZE',`10m')dnl
dnl #
dnl # Features
dnl #
dnl # use /etc/mail/local-host-names
FEATURE(`use_cw_file')dnl
dnl #
dnl # The access db is the basis for most of sendmail's checking
FEATURE(`access_db', , `skip')dnl
dnl #
dnl # The greet_pause feature stops some automail bots - but check the
dnl # provided access db for details on excluding localhosts...
FEATURE(`greet_pause', `1000')dnl 1 seconds
dnl #
dnl # Delay_checks allows sender<->recipient checking
FEATURE(`delay_checks', `friend', `n')dnl
dnl #
dnl # If we get too many bad recipients, slow things down...
define(`confBAD_RCPT_THROTTLE',`3')dnl
dnl #
dnl # Stop connections that overflow our concurrent and time connection rates
FEATURE(`conncontrol', `nodelay', `terminate')dnl
FEATURE(`ratecontrol', `nodelay', `terminate')dnl
dnl #
dnl # If you're on a dialup link, you should enable this - so sendmail
dnl # will not bring up the link (it will queue mail for later)
dnl define(`confCON_EXPENSIVE',`True')dnl
dnl #
dnl # Dialup/LAN connection overrides
dnl #
include(`/etc/mail/m4/dialup.m4')dnl
include(`/etc/mail/m4/provider.m4')dnl
dnl #
dnl # Default Mailer setup
MAILER_DEFINITIONS
MAILER(`local')dnl
MAILER(`smtp')dnl

---

