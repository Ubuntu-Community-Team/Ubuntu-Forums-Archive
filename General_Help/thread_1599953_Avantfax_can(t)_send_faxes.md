---
title: "Avantfax can(t) send faxes"
date: 2010-10-18
forum: General Help
---

### Post by mac-duff on 2010-10-18
Hello,

I setup succesfully Avantfax on a ubuntu server machine and it works quite well, but the problem is sending faxes. At first I got every time the error "no local dialtone" which I could solve by changing the config file to: 
```

ModemResultCodesCmd:    ATQ0X3          # enable result codes

```
but when I now send a faxes the pages is almost totally blank.

Here is my config
```

CountryCode:            34
AreaCode:               96
FAXNumber:              +34.962.907.665
LongDistancePrefix:     34
InternationalPrefix:    34
DialStringRules:        etc/dialrules
ServerTracing:          1
SessionTracing:         11
RecvFileMode:           0600
LogFileMode:            0600
DeviceMode:             0600
RingsBeforeAnswer:      1
SpeakerVolume:          off
GettyArgs:              "-h %l dx_%s"
LocalIdentifier:        "NothingSetup"
TagLineFont:            etc/lutRS18.pcf
TagLineFormat:          "From %%l|%c|Page %%P of %%T"
MaxRecvPages:           25
#
#
# Modem-related stuff: should reflect modem command interface
# and hardware connection/cabling (e.g. flow control).
#
ModemType:              Class1          # use class 1 interface
ModemRate:              19200           # rate for DCE-DTE communication
ModemFlowControl:       xonxoff         # software flow control
#
ModemSetupDTRCmd:       ATS13=1&D2      # setup so DTR drop resets modem
ModemSetupDCDCmd:       AT&C1           # setup so DCD reflects carrier (or not)
ModemNoFlowCmd:         AT&H0&I0&R1     # setup modem for no flow control
ModemHardFlowCmd:       AT&H1&I0&R2     # setup modem for hardware flow control
ModemSoftFlowCmd:       AT&H2&I2&R1     # setup modem for software flow control

ModemResultCodesCmd:    ATQ0X3          # enable result codes
#ModemATCmdDelay:       100
#
ModemMfrQueryCmd:       !USR
ModemModelQueryCmd:     ATI3
ModemRevQueryCmd:       ATI7            # XXX returns a multi-line result
#
# When AT+FCLASS=1 is issued the modem automatically switches
# to software flow control; these parameters let the fax software
# reset flow control as needed after entering Class 1.
#
Class1NFLOCmd:          AT&H0&I0&R1     # setup modem for no flow control
Class1HFLOCmd:          AT&H1&I0&R2     # setup modem for hardware flow control
Class1SFLOCmd:          ""              # modem does this automatically
#
# This should resolve "DIS/DTC received 3 times" errors:
#
Class1ResponseWaitCmd:  AT+FRS=1        # wait after sending TCF for response
#
# The remainder of this configuration is included so that the
# modem "idles" in Class 0 while not sending or receiving facsimile.
#
ModemSetupAACmd:        AT+FCLASS=0     # leave modem idling in class 0
ModemAnswerCmd:         AT+FCLASS=1A    # answer in Class 1
#
# When using AT+FRS=n we see USR modems reset themselves in the middle of sessions
# this is not good.  So, we seem to work-around that problem by not using the
# command.  Unfortunately, this isn't an ideal thing.
#
Class1SwitchingCmd:     "<delay\0727>"

#
## AvantFAX
#
FaxRcvdCmd:     bin/faxrcvd.php
DynamicConfig:  bin/dynconf.php
UseJobTSI:      true
#
## AvantFAX
#
FaxRcvdCmd: bin/faxrcvd.php
DynamicConfig: bin/dynconf.php
UseJobTSI: true
#
## AvantFAX
#
FaxRcvdCmd: bin/faxrcvd.php
DynamicConfig: bin/dynconf.php
UseJobTSI: true

```

Attached a pdf file how our printer/fax machine receives this fax. Its also doesnt matter if I send pdf o text file, everytime blank :/

I hope someone can give me a hint

---

### Post by mac-duff on 2010-10-19
ok, I found the solution here:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2332312.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2332312.html)

and here

[http://launchpadlibrarian.net/49954331/hylafax.patch](http://launchpadlibrarian.net/49954331/hylafax.patch)

---

