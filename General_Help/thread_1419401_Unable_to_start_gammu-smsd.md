---
title: "Unable to start gammu-smsd"
date: 2010-03-01
forum: General Help
---

### Post by Jeboy on 2010-03-01
Hi,

Sorry, don't know exactly where to put this.

I'm having problem with gammu smsd, following error occurred when issuing command "gammu-smsd --config /etc/gammu-smsdrc":

"Error connecting to database: Access denied for user 'root'@'localhost' (using password: NO)"

but database login credential is correct.

Following are my gammu configs. located at /etc:

**gammu-smsdrc**
# Configuration file for Gammu SMS Daemon

# Gammu library configuration, see gammurc(5)
[gammu]
# Please configure this!
port = /dev/ttyUSB0
connection = at19200
# Debugging
#logformat = textall

# SMSD configuration, see gammu-smsdrc(5)
[smsd]
service = MYSQL
logfile = syslog
# Increase for debugging information
debuglevel = 0

# Paths where messages are stored
inboxpath = /var/spool/gammu/inbox/
outboxpath = /var/spool/gammu/outbox/
sentsmspath = /var/spool/gammu/sent/
errorsmspath = /var/spool/gammu/error/

**smsdrc**
# This is a sample Gammu SMSD configuration file. It's required for gammu-smsd,
# see gammu-smsdrc(5) for documentation.

# Gammu configuration, this section is like section "gammu" in "gammurc" file,
# see gammurc(5) for documentation.
[gammu]
port = /dev/ttyUSB0
#model = 6110
connection = at19200
#synchronizetime = yes
#logfile = gammulog # this is not used at all in SMSD mode
#logformat = textall
#use_locking = yes
#gammuloc = gammu.us
#startinfo = yes

# When uncomment this section and insert numbers here, smsd will process
# incoming sms only from numbers written here (incoming sms from all other
# numbers will be deleted)
#[include_numbers]
#number1 = 1234

# When uncomment this section and insert numbers here, smsd will process
# incoming sms from all numbers not written here (incoming sms from numbers
# written here will be deleted). This is "black" list.
# Note: after using "include_numbers" section this one will be ignored
#[exclude_numbers]
#number1 = 1234

# General SMSD settings, see gammu-smsdrc(5) for detailed description.
[smsd]
# SMSD service to use, one of FILES, MYSQL, PGSQL, DBI
service = MYSQL
# PIN for SIM card
PIN = 1234
# File (or stderr, syslog, eventlog) where information will be logged
logfile = smsdlog
# Amount of information being logged, each bit mean one level
debuglevel = 0
# Configuration for using more phones on same database
#phoneid = MyPhone1
# Script to be executed when new message has been received
#runonreceive = /some/script
# Commication frequency settings
commtimeout = 30
sendtimeout = 30
#receivefrequency = 0

# Phone communication settings
#checksecurity = 1
#resetfrequency = 0

# Delivery report configuration
#deliveryreport = no
#deliveryreportdelay = 10

# Ignoring broken SMSC
#skipsmscnumber = +48602123456

# Database backends congfiguration
user = root
password = pass
pc = localhost
# pc can also contain port or socket path after colon (eg. localhost:/path/to/socket)
database = sms

# DBI configuration
driver = sqlite
# driverspath = /usr/lib/dbd/
# Database directory for sqlite
# dbdir = /var/lib/smsd

# Files backend configuration
#inboxpath = /var/spool/sms/inbox/
#outboxpath = /var/spool/sms/outbox/
#sentsmspath = /var/spool/sms/sent/
#errorsmspath = /var/spool/sms/error/
#inboxformat = unicode
#transmitformat = auto

**gammurc**
; This is a sample ~/.gammurc file.
; In Unix/Linux  copy it into your home directory and name it .gammurc
;                or into /etc and name it gammurc
; In Win32       copy it into directory with Gammu.exe and name gammurc
; More about parameters later
; Anything behind ; or # is comment.
; -----------------------------------------------------------------------------

[gammu]

port = /dev/ttyUSB0
connection = at19200
; Do not use model configuration unless you really need it
;model = 6110
;synchronizetime = yes
;logfile = gammulog
;logformat = textall
;use_locking = yes
;gammuloc = locfile
;startinfo = yes
;gammucoding = utf8
;usephonedb = yes

[gammu1]

port = com8:
;model = 6110
connection = fbusblue
;synchronizetime = yes
;logfile = gammulog
;logformat = textall
;use_locking = yes
;gammuloc = locfile
;startinfo = yes
;gammucoding = utf8

; Step 1. Please find required Connection parameter and look into assigned 
; with it port type. With some Connection you must set concrete model

; ================================================================ cables =====
; New Nokia protocol for FBUS/DAU9P
;    Connection "fbus", port type serial
; New Nokia protocol for DLR3/DLR3P
;    Connection "fbusdlr3"/"dlr3", port type serial 
; New Nokia protocol for DKU2 (and phone with USB converter on phone mainboard
;                              like 6230)
;    Connection "dku2phonet"/"dku2", port type dku2 on Windows
;    Connection "fbususb" on Linux
; New Nokia protocol for DKU5 (and phone without USB converter on phone
;                              mainboard like 5100)
;    Connection "dku5fbus"/"dku5", port type dku5
; New Nokia protocol for PL2303 USB cable (and phone without USB converter
;                                          on phone mainboard like 5100)
;    Connection "fbuspl2303", port type usb
; Old Nokia protocol for MBUS/DAU9P
;    Connection "mbus", port type serial
; Variants: 
; You can modify a bit behaviour of connection using additional flags
; specified just after connection name like connection-variant.
; If you're using ARK3116 cable (or any other which does not like dtr 
; handling), you might need -nodtr variant of connection, eg. dlr3-nodtr.
; If cable you use is not powered over DTR/RTS, try using -nopower variant of 
; connection, eg. fbus-nopower.
; -----------------------------------------------------------------------------
; AT commands for DLR3, DKU5 or other AT compatible cable (8 bits, None
; parity, no flow control, 1 stop bit). Used with Nokia, Alcatel, Siemens, etc.
;    Connection "at19200"/"at115200"/.., port type serial
; AT commands for DKU2 cable
;    Connection "dku2at", port type dku2
; ============================================================== infrared =====
; Nokia protocol for infrared with Nokia 6110/6130/6150
;    Connection "fbusirda"/"infrared", port type serial
; Nokia protocol for infrared with other Nokia models
;    Connection "irdaphonet"/"irda", port type irda
; -----------------------------------------------------------------------------
; AT commands for infrared. Used with Nokia, Alcatel, Siemens, etc.
;    Connection "irdaat", port type irda
; -----------------------------------------------------------------------------
; OBEX for infrared
;    Connection "irdaobex", port type irda.
; ============================================================= Bluetooth =====
; Nokia protocol with serial port set in BT stack (WidComm, other) from
; adequate service and Nokia 6210
;    Connection "fbusblue", port type serial
; Nokia protocol with serial port set in BT stack (WidComm, other) from
; adequate service and other Nokia models
;    Connection "phonetblue", port type serial
; -----------------------------------------------------------------------------
; Nokia protocol for Bluetooth stack with Nokia 6210
;    Connection "bluerffbus", port type BT
; Nokia protocol for Bluetooth stack with DCT4 Nokia models, which don't inform
; about services correctly (6310, 6310i with firmware lower than 5.50, 8910,..)
;    Connection "bluerfphonet", port type BT
; Nokia protocol for Bluetooth stack with other DCT4 Nokia models
;    Connection "bluephonet", port type BT
; -----------------------------------------------------------------------------
; AT commands for Bluetooth stack and 6210 / DCT4 Nokia models, which don't
; inform about BT services correctly (6310, 6310i with firmware lower 
; than 5.50, 8910,..)
;    Connection "bluerfat", port type BT
; AT commands for Bluetooth stack with other phones (Siemens, other Nokia,etc.)
;    Connection "blueat", port type BT
; -----------------------------------------------------------------------------
; OBEX for Bluetooth stack with DCT4 Nokia models, which don't inform about
; BT services correctly (6310, 6310i with firmware lower than 5.50, 8910,...)
;    Connection "bluerfobex", port type BT
; OBEX for Bluetooth stack with other phones (Siemens, other Nokia, etc.)
;    Connection "blueobex", port type BT.
; -----------------------------------------------------------------------------
;    Connection "bluerfgnapbus", port type BT, model "gnap"
;    Connection "irdagnapbus", port type irda, model "gnap"

; Step2. According to port type from Step1 and used OS set Port parameter

; -----------------------------------------------------------------------------
; Port type | "Port" parameter in Windows/DOS | "Port" parameter in Linux/Unix
; ----------|---------------------------------|--------------------------------
; serial    | "com*:"                         | "/dev/ttyS*"
;           | (example "com1:")               | (example "/dev/ttyS1")
;           |                                 | or "/dev/tts/**" (with DevFS)
;           |                                 | virtual serial ports like
;           |                                 | "/dev/ircomm*" or "/dev/rfcomm*"
; ----------|---------------------------------|--------------------------------
; irda      | ignored (can be empty)          | ignored (can be empty)
; ----------|---------------------------------|--------------------------------
; BT        | Bluetooth device address (example "00:11:22:33:44:55").
;           | Optionally you can also include channel after slash
;           | (example "00:11:22:33:44:55/12"). Can be also empty.
; ----------|---------------------------------|--------------------------------
; dku2      | ignored (can be empty)          | /dev/ttyUSB* or /dev/ttyACM*
; ----------|---------------------------------|--------------------------------
; dku5      | ignored (can be empty)          | connection with it not possible
; ----------|---------------------------------|--------------------------------
; usb       | connection with it not possible | "/dev/ttyUSB*"

; Step3. Set other config parameters

; -----------------------------------------------------------------------------
; Parameter name  | Description
; ----------------|------------------------------------------------------------
; Model           | Should not be used unless you have a good reason to do so.
;                 | If Gammu doesn't recognize your phone model, put it here. 
;                 | Example values: "6110", "6150", "6210", "8210"
; SynchronizeTime | if you want to set time from computer to phone during
;                 | starting connection. Do not rather use this option when
;                 | when to reset phone during connection (in some phones need
;                 | to set time again after restart)
; GammuLoc        | name of localisation file
; StartInfo       | this option allow to set, that you want (setting "yes")
;                 | to see message on the phone screen or phone should enable
;                 | light for a moment during starting connection. Phone
;                 | WON'T beep during starting connection with this option.
; GammuCoding     | forces using specified codepage (in win32 - for example
;                 | "1250" will force CP1250) or UTF8 (in Linux - "utf8")
; ----------------|------------------------------------------------------------
; Logfile         | Use, when want to have logfile from communication.
; Logformat       | What debug info and format should be used:
;                 |   "nothing" - no debug level (default)
;                 |   "text"    - transmission dump in text format
;                 |   "textall" - all possible info in text format
;                 |   "errors"  - errors in text format
;                 |   "binary"  - transmission dump in binary format
; ----------------|------------------------------------------------------------
; Features        | Custom features for phone. This can be used as override
;                 | when values coded in common/gsmphones.c are bad or
;                 | missing. Consult include/gammu-info.h for possible values
;                 | (all Feature values without leading F_ prefix).
;                 | Please report correct values to Gammu authors.
; ----------------|------------------------------------------------------------
; Use_Locking     | under Unix/Linux use "yes", if want to lock used device
;                 | to prevent using it by other applications. In win32 ignored

; vim: et ts=4 sw=4 sts=4 tw=78 spell spelllang=en_us

---

### Post by thom_ on 2010-05-10
> **Jeboy said:**
> 
"Error connecting to database: Access denied for user 'root'@'localhost' (using password: NO)"

but database login credential is correct.

Error with that warning is just because your configuration -mysql pasword- isn't correct. Look at your configuration quoted below :
> **Jeboy said:**
> 
# Database backends congfiguration
user = root
**password = pass**
pc = localhost
# pc can also contain port or socket path after colon (eg. localhost:/path/to/socket)
database = sms

IMHO, replace password the blocked line with the correct password will solve the problem

---

