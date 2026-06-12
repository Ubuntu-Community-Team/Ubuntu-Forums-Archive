---
title: "ncidd server wont start? part of a caller id server setup"
date: 2009-10-11
forum: General Help
---

### Post by sdowney717 on 2009-10-11
I just cant get ncidd going?

[http://ubuntuforums.org/showthread.php?t=124603&highlight=ncid](http://ubuntuforums.org/showthread.php?t=124603&highlight=ncid)

ubuntu instructions
[http://ncid.sourceforge.net/ncid/INSTALL-Ubuntu.txt](http://ncid.sourceforge.net/ncid/INSTALL-Ubuntu.txt)
> scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd start
scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd stop
scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd status
 * Network Caller ID Server ncidd is stopped        

scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd start
scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd status
 * Network Caller ID Server ncidd is stopped                                   

scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd start
scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd status
 * Network Caller ID Server ncidd is stopped 
                                    
scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd reload
 * Reloading Network Caller ID Server ncidd                              [ OK ] 
scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd status
 * Network Caller ID Server ncidd is stopped

scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd start
scott2@scott2-desktop:~/martian$ sudo invoke-rc.d ncidd status
 * Network Caller ID Server ncidd is stopped  





anyway my modem is working
> scott2@scott2-desktop:~/martian$ sudo wvdial ATE1V1Q0
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer ATE1V1Q0] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
scott2@scott2-desktop:~/martian$ 


here is my ncidd.conf file
it is located in /etc/ncidd

> # NCID - Network CallerID Server Config File

# File last changed: Thu Aug 30, 2007

################################
# Definitions and Line formats #
################################

# lines can be blank, or start with the words: send, set #
#
# A line is divided into words, separated by spaces
#
# A word is either a string of non-blank characters, everything
# between double quotes, or an equal sign.
#
# SEND LINE FORMAT:
#   send DATATYPE [DATATYPE] ...
#        where DATATYPE = cidlog, cidinfo
#
# SET LINE FORMAT:
#   set ITEM = VALUE [ITEM = VALUE] ...
#       where ITEM = cidalias, cidlog, cidlogmax, datalog, initcid,
#                    initstr, lineid, lockfile, nomodem, noserial,
#                    pidfile, port, ttyclocal, ttyport, ttyspeed,
#                    verbose

##########################
# Log file verbose level #
##########################

# Set the verbose level
# The default value is 1, the range is 1-9
# set verbose = 3

############################
# Log and Info for Clients #
############################

# Send the call log to a client when connected
# The default is not to send the call log file
send cidlog

# Send call info (LINE and RING) to a client at each ring
# The default is not to send the call info line
send cidinfo

############################
# NCID Communications Port #
############################

# The default TCP/IP port is 3333
# set port = 3334

############################
# PID, Alias and Log Files #
############################

# Set pidfile to /var/run/ncidd.pid in rc and init scripts
# The default is no PID file
# set pidfile = /var/log/ncidd.pid

# The default CID alias file: /etc/ncid/ncidd.alias
# set cidalias = /etc/ncid/ncidd.alias

# The default CID call log file: /var/log/cidcall.log
# the log file must exist, ncidd will not create it
# (also make the change in /etc/logrotate.d/ncidd
#  and also /etc/ncid/ncidrotate.conf)
# set cidlog = /var/log/cidcall.log

# Set the maximum size in bytes for the CID log file
# The default is 110,000 bytes and the maximum is 100,000,000
# Do not include commas when setting cidlogmax
# set cidlogmax = 500000

# The default tty data log file: /var/log/ciddata.log
# the log file must exist, ncidd will not create it
#  (also make the change in /etc/logrotate.d/ncidd
#   and also /etc/ncid/ncidrotate.conf)
# set datalog = /var/log/ciddata.log

#######################
# Serial or No Serial #
#######################

# Normally a seriel device is required to capture CID information.
# If you are using one or more network based clients and do not have
# a serial device, set noserial to 1.

# If noserial is set to 1, the TTY Configuration, Modem, and Modem
# Initialization set commands are not used.

#  NETWORK AND NO SERIAL: noserial = 1 (do not use a serial port)
#  SERIAL AND NETWORK:    noserial = 0 (default - use a serial port)
# set noserial = 1
# NOTE: if noserial is set to 1, nothing needs to be configured beyond
#       this point.

############################
# Telephone Line Indicator #
############################

# Set the line indicator if you have more than one telephone
# line sending information to ncidd and noserial is set to 0.
# normally you would set it to the last 4 digits of your number.
# lineid default: -
# set lineid = 7744

#####################
# TTY Configuration #
#####################

# The default tty port: /dev/modem
# set ttyport = /dev/cu.modem # Macintosh OS X
set ttyport = /dev/ttySM0

# The default tty port speed: 19200
# The tty speed can be one of: 38400, 19200, 9600, 4800
# set ttyspeed = 4800 # NetCallerID port speed

# Ignore tty control signals for internal modems and 3 wire serial cables
#   Disable tty control signals: ttyclocal = 1
#   Enable tty control signals: ttyclocal = 0 (default)
# set ttyclocal = 1

# The lockfile name is generated automatically
# If tty port is /dev/modem, lockfile is: /var/lock/LCK..modem
# set lockfile = /var/lock/LCK..ttyS0

#####################
# Modem or No Modem #
#####################

# Obtain CallerID from a CID device or a modem
# The NetCallerID device is not a modem
#  DEVICE: nomodem = 1 (do not send AT commands)
#  MODEM:  nomodem = 0 (default - send AT commands)
# set nomodem = 1
set nomodem = 0

########################
# Modem Initialization #
########################

# The default modem initialization is: "AT Z S0=0 E1 V1 Q0"
set initstr = "ATE1V1Q0"
#
# If minicom can talk to the modem but ncidd fails, use the Minicom init string
# Minicom initialization string is "AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0"
# set initstr = "ATS7=45S0=0L1V1X4&c1E1Q0"
#
# Alternate modem initialization string
# set initstr = "AT&FE1V1Q0+VIP"
#
# Alternate modem initialization string for the Mac Motorola UbiSoft modem
# set initstr = "AT+FCLASS=8;+VCID=1" # Macintosh OS X

# The U.S.Robotics USR5631 56K Faxmodem has a +GCI command to set the
# country code to adjust parameters for a particular telephone network
# (perhaps other modems do also).  See the following on how to set +GCI
#   [http://www.usr.com/support/5631/5631-ug/generic.htm](http://www.usr.com/support/5631/5631-ug/generic.htm)
#   doc/Modem-init (has a copy of the information needed to set +GCI)

# Addon strings to set modem for Distinctive Ring:
#   [http://www.modemsite.com/56k/dring.asp](http://www.modemsite.com/56k/dring.asp)
#
# 3Com/USR/TI chipset: ATS41=1
#   Reported Ring Codes: RING A, RING B, RING C
# Rockwell/Conexant chipset: AT-SDR=7
#   Reported Ring Codes: RING 1, RING 2, RING 3
# Lucent/Agere chipset: AT+VDR=1,0
#   Reported DROF/DRON messages: DRON=5 DROF=11, DRON=5 DROF=34
#
# Example adds 3Com DR to the default modem initialization
# set initstr = "ATE1V1Q0S41=1"

# The default for ncidd is to try two CID strings to setup
# CallerID: "AT+VCID=1" and if that fails: "AT#CID=1".
# set initcid = "AT#CID=1"
#
# Alternate CID strings to try if default does not work:
# set initcid = "AT+FCLASS=8;+VCID=1"
# set initcid = "AT-STE=1;+VCID=1"
# set initcid = "AT-STE=1;#CID=1"

#################
# TiVo Settings #
#################
# set ttyclocal = 1 # TiVo requires CLOCAL
# set ttyport = /dev/ttyS1 # TiVo Modem Port
# set lockfile = /var/tmp/modemlock # needed for TiVo Modem Port
#
# To use a modem on the TiVo serial port
#   Tivo (stereo mini jack) ->
#   -> (stereo mini plug) TiVo serial cable (9-pin male) ->
#   -> (9-pin Female) PC modem cable (25-pin Male ->
#   -> (25-pin Female) Modem
# if the modem has switches, disable DTR
# Use this string to set the modem before attaching it to the TiVo:
#   AT&F0&D0&B1&W
#
# set ttyport = /dev/ttyS3 # TiVo Serial Port
#
# End TiVo Settings


[http://ncid.sourceforge.net/ncid/INSTALL-FreeBSD.txt](http://ncid.sourceforge.net/ncid/INSTALL-FreeBSD.txt)

I can start it in debug mode

> scott2@scott2-desktop:~/martian$ sudo ncidd -D
Started: 10/16/2009 10:49
Server: ncidd 0.74
Verbose level: 1
ncidd logfile: /var/log/ncidd.log
Processed config file: /etc/ncid/ncidd.conf
Configured to send 'cidlog' to clients.
Configured to send 'cidinfo' to clients.
Processed alias file: /etc/ncid/ncidd.alias
CID logfile: /var/log/cidcall.log
CID logfile maximum size: 110000 bytes
Data logfile not present: /var/log/ciddata.log
Telephone Line Identifier: -
CallerID from AT Modem and maybe Gateway
Modem initialized.
Unable to set modem CallerID: /dev/ttySM0
Terminated:  10/16/2009 10:49
scott2@scott2-desktop:~/martian$ 

[http://74.125.95.132/search?q=cache:LatXi9NRkbkJ:www.mythtv.org/wiki/Network_Caller_ID_%28NCID%29+Unable+to+set+modem+CallerID&cd=6&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.95.132/search?q=cache:LatXi9NRkbkJ:www.mythtv.org/wiki/Network_Caller_ID_%28NCID%29+Unable+to+set+modem+CallerID&cd=6&hl=en&ct=clnk&gl=us&client=firefox-a)

---

### Post by sdowney717 on 2009-10-17
i changed to an hcf modem and got ncidd to run.
however, it wont pass any callerid info, just ring shows up
run ncidd from terminal in debug verbose mode to see this.
i also booted up XP, and tried several callerid programs and they also only passed ring. now maybe it is the driver. i just dont know since the modem responds to +VCID=1 with ok


> scott2@scott2-desktop:~/Download$ ncidd -Dv3
/var/log/ncidd.log: Permission denied
Started: 10/17/2009 07:46
Server: ncidd 0.74
Verbose level: 3
ncidd logfile: /var/log/ncidd.log
Processed config file: /etc/ncid/ncidd.conf
Configured to send 'cidlog' to clients.
Configured to send 'cidinfo' to clients.
Processed alias file: /etc/ncid/ncidd.alias
CID logfile: /var/log/cidcall.log
CID logfile maximum size: 110000 bytes
Data logfile not present: /var/log/ciddata.log
Telephone Line Identifier: -
TTY port opened: /dev/ttySHCF0
TTY port speed: 19200
TTY lock file: /var/lock/LCK..ttySHCF0
TTY port control signals enabled
CallerID from AT Modem and maybe Gateway
ATE1V1Q0
OK
Try 1 to init modem: return = 0.
Modem initialized.
AT+VCID=1
OK
Modem set for CallerID.
Network Port: 3333
Not using PID file, there was no '-P' option.
Client 5 connected, sent call log: /var/log/cidcall.log
CIDINFO: *LINE*-*RING*1*
CIDINFO: *LINE*-*RING*2*
CIDINFO: *LINE*-*RING*3*
CIDINFO: *LINE*-*RING*4*
CIDINFO: *LINE*-*RING*5*
CIDINFO: *LINE*-*RING*6*


---

### Post by cml37 on 2009-10-18
On several occasions, we have been seeing modems take the init string AT+VCID=1 yet not produce any CallerID data, one example I know of is the Rosewill RNX-56USB (folks have had varying degrees of success.. I know of at least three people who have had no success with it!) It's misleading, since you would expect it to return an error when it accepts the string!  

Have you tried any of the alternative init strings suggested in the config file?  Try uncommenting these lines, one at a time, starting ncidd, and see if your modem responds any differently.

# set initcid = "AT+FCLASS=8;+VCID=1"
# set initcid = "AT-STE=1;+VCID=1"

Barring that, you may want to have a look at  [http://sourceforge.net/projects/ncid/forums/forum/275237/topic/3276653](http://sourceforge.net/projects/ncid/forums/forum/275237/topic/3276653) on the NCID forums

---

### Post by sdowney717 on 2009-10-18
thanks for responding. i was thinking it could be the modem driver?
so i emailed linuxurant and asked if the driver supports caller id.
i suppose the xp driver could also be too old dated 2001. or the modems 
just dont work.

set initcid = "AT+VCID=1" is the only one that does not error, i tried all these. 

#set initcid = "AT#CID=1"
set initcid = "AT+VCID=1"

# Alternate CID strings to try if default does not work:
#set initcid = "AT+FCLASS=8;+VCID=1"
#set initcid = "AT-STE=1;+VCID=1"
#set initcid = "AT-STE=1;#CID=1"
#set initcid = "AT+FCLASS=8;+VCID=1"
#set initcid = "AT-STE=1;+VCID=1"

---

### Post by sdowney717 on 2009-10-18
ncidd.log is 2gb in size???
nciddata.log does not exist

i noticed i had lost a lot of free space. does this look rediculous? 
what can i do to view the info in there. for gedit it is too big

---

### Post by cml37 on 2009-10-18
> **sdowney717 said:**
> thanks for responding. i was thinking it could be the modem driver?

Probably not driver related.  When it comes to basic comm with the modem, it's just a function of a serial port connection or some sort of serial connection emulation (i.e. PCI, USB, etc.).  The Caller ID information will be provided in plain text when the modem detects it.  

If you wanted to test at a more fundamental level, you could start a terminal session (minicom is as good as any), connect to the modem, initiate the Caller ID init string (probably AT+VCID=1 in your case), place a call, and see if you get anything other than RING as a response.   If not, then your modem is not providing Caller ID info.


> **sdowney717 said:**
> ncidd.log is 2gb in size???
nciddata.log does not exist

i noticed i had lost a lot of free space. does this look rediculous? 
what can i do to view the info in there. for gedit it is too big


Did you launch ncidd in the background with the -D option?  This will cause your logfile to grow tremendously since, as I understand it, ncidd will connect to the terminal window if you use it.  Per the ncidd author, the same loginfo will be recorded to the logfile if you omit the -D option.  At this point, I'd probably just go ahead and delete it.

---

### Post by sdowney717 on 2009-10-18
thanks about minicom, anyway no data except ring
I also have an agere lucent pci modem i can make work with martian-modem, but never could get any callerid out of it. that modem also said ok to +VCID=1

> Welcome to minicom 2.3                                                         
                                                                               
OPTIONS: I18n                                                                  
Compiled on Sep 25 2009, 23:40:20.                                             
Port /dev/ttySHCF0                                                             
                                                                               
                  Press CTRL-A Z for help on special keys                      
at                                                                             
OK                                                                             
AT+VCID=1                                                                      
OK                                                                             
                                                                               
RING                                                                           
                                                                               
RING                                                                           
                                                                               
RING                                                                           
       

---

### Post by sdowney717 on 2009-10-18
[http://www.imptec.com/modems.htm](http://www.imptec.com/modems.htm)

article here says the agere modem has good caller id .
but it is a bad driver issue. 
SO, i wonder if the lucent martian_modem driver is not useful for caller id?

---

### Post by jlc46 on 2009-10-21
> **sdowney717 said:**
> ncidd.log is 2gb in size???
nciddata.log does not exist

i noticed i had lost a lot of free space. does this look rediculous? 
what can i do to view the info in there. for gedit it is too big

You have to be very careful when using ncidd in debug mode and when using a high verbose level.  The debug mode keeps ncidd attached to the terminal.  It does not provide debug information, verbose does.  Verbose information always goes into the ncidd.log file, even when displayed on screen in debug mode.  If you go above verbose level 3, you will get messages every time there is a poll event so never use a verbose level above 3 for any length of time and always delete it or remove it from ncidd.log.  This will prevent large log files.  Mostly with log files, you are concerned with the end rather the beginning so if you have a large log file you can use "tail" on it.  I would suggest you delete your 2gb log file.

The nciddata.log file is optional, you must create it for it to be used.  It shows all output from a modem or gateway.  if your modem does not send Caller ID information between ring 1 and ring 2, your modem is either not in Caller ID mode or it does not support Caller ID.  A lot of cheap modems will return OK when you try to initialize them to Caller ID, even if they do not support it.

---

