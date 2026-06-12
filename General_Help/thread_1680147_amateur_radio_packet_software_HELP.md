---
title: "amateur radio packet software HELP"
date: 2011-02-02
forum: General Help
---

### Post by ~dr,j on 2011-02-02
hey all~
so i'm an amateur radio [ham radio] operator. i prefer to do everything in ubuntu and hate having to boot in to windows for anything. sadly, there is but one thing radio related i can't do in ubuntu: packet/pactor radio.

i have installed fbb BUT don't know exactly how to configure it ... if i give it my best guess, i inevitably screw it up [as evident in it won't launch and gives errors relating to the config file]

so i truned to trying linAMC ... i can't launch the message processor options NOR can i initiate a call [start forward session]

can anyone help? for either program or both? i've looked on line but most of what i find is greek to me. i mean i'm okay with the command line but i'm no programmer ... an what they talk about makes no sense to me :s

thanks in advance for any help! :P
73 [in ham radio that means 'best wishes']
~j

---

### Post by [Snc] on 2011-02-02
Hello there!

Could you post the error messages, that are given to you?

In my experience, the messages tell a whole bunch of useful things and almost always point to a "how to fix" section.

---

### Post by ~dr,j on 2011-02-03
snc~
okay so i did a reinstall ... redid the config file an this is what error i get [actually it's the entire terminal readout from the command to launch fbb thru to the error]

jason@jason-monkey-laptop:~$ fbb

Configuration files does not exist. Create them (Y/N) ?Y

Callsign of the BBS without ssid   (Ex: F6FBB)        : n7yrt
SSID of the BBS                    (Ex : 1)           : 10
Hierarchical address               (Ex : FMLR.FRA.EU) : nw.usa.na 
QRA-Locator of the BBS             (Ex : JN03QL)      : dn18dd
City of the BBS                    (Ex : Toulouse)    : valley
Name of the SysOp                  (Ex : Jean-Paul)   : guy
Callsign of the SysOp without SSID (Ex : F6FBB)       : n7yrt
Difference with GMT time           (Ex : +1)          : -8

BBS     : n7yrt.nw.usa.na
SSID    : 10
LOCATOR : dn18dd (valley)
SYSOP   : n7yrt (guy)
TIME    : GMT -8

Correct (Y/N) ? Y
/usr/sbin/fbb: 515: cannot create /etc/ax25/fbb.conf: Permission denied
file epurmess.ini already exists. Replace (Y/N) ? Y
/usr/sbin/fbb: 515: cannot create /etc/ax25/fbb/epurmess.ini: Permission denied

Name of the port #1 as named in axport (<CR> to end) : 


Correct (Y/N) ? Y
Creating port.sys ... Ok
/usr/sbin/fbb: 515: cannot create /etc/ax25/fbb/port.sys: Permission denied
Checking fbb tree.... Ok
Checking fbb configuration :
*********************************************************
* XFBB Linux daemon version 7.04j (Feb  4 2010) PID=29967
* Copyright F6FBB 1986-1999. All rights reserved.
*
* This software is in the public domain. It can be copied
* or installed for any use abiding by the laws.
*
* F6FBB (Jean-Paul ROUBELAT) declines any responsibilty
* in the use of XFBB software.
*
* This software is free of charge, but a 100 FF or 20 US$
* (or more) contribution will be appreciated.
*********************************************************
fbb.conf : Cannot open file 0
End PG ***
Configuration error ! Giving up.
jason@jason-monkey-laptop:~$ 


A few things to point out ... as i said, i am not 100% sure on what info to give where [like the sysOp [is that the bbs owner or me] etc. AND the axport's, according to other programs, are not named ... they just exsists as axport 1 or whatever ... so this is one error ... i'll try to get it to spit out the other errors as well.

thanks for at least trying to see if you can help :)
~j

---

### Post by ~dr,j on 2011-02-04
hey~
I'm still hoping to get help here to get either fbb or linAmc working BUT and FYI [or in ham lingo a QST] regarding using windows made ham software [in my case airmail] under wine in ubuntu [and in theory any linux].

i looked at a thread about wine not recognizing com ports [of course windows calls them com ... linux they are tty <or is its a usb to serial adapter ttyUSB>] 

you can get the programs your running under wine to recognize them if you add a symbolic [or maybe its a hard ... don't really know the differenece] link from /dev/tty [after tty add the number of the prot, i.e. 0 or 1 or 2 ...] to the dosdevices folder in the .wine directory!

i been using airmail all day! works like a charm ... now to get the linux made software working!
~j

---

### Post by [Snc] on 2011-02-04
> **~dr,j said:**
> 
...
/usr/sbin/fbb: 515: cannot create /etc/ax25/fbb.conf: Permission denied
file epurmess.ini already exists. Replace (Y/N) ? Y
/usr/sbin/fbb: 515: cannot create /etc/ax25/fbb/epurmess.ini: Permission denied
...
/usr/sbin/fbb: 515: cannot create /etc/ax25/fbb/port.sys: Permission denied
...
fbb.conf : Cannot open file 0
...
Configuration error ! Giving up.

Well, from the extract above, I assume, that most of the problem persists, because you don't have the permission to write to those folders or files.

There are two possible ways to resolve this:
1- run as administrator 
```
sudo "program_name"
```

2- run nautilus as administrator
```
sudo nautilus
```
browse to '/etc/ax25/', select the folder 'fbb', right click it and set the permissions so, that you will be the owner and will have permission to 'create and delete files' also hit the 'apply permissions to Enclosed files' button.

I recommend the second solution, that should get you a running application.

If you are still gonna have problems, tell us.

---

### Post by ~dr,j on 2011-02-18
hey there~
i'll try to do your suggestions sometime in the next few days :) thank you for your help with this ... and sry its taken me so long to reply. (been busy here)

~j

---

### Post by akbrider on 2011-10-02
Can someone recommend a simple sofware for packet on VHF ham radio? I plan to use a Kenwood (TM 241a) radio on VHF FM. I am using a RIGblaster but I need a simple sofware program to use with it. Thanks. [EMAIL="akbrider@aol.com"]akbrider@aol.com[/EMAIL]

---

### Post by kd5mkv on 2011-10-22
here is a solutions to open com ports on Ubuntu using wine!

I used the cd (change directory) to .wine( $ cd .wine ) then 
( cd dosdevices ) 
that puts you into the directory /.wine/dosdevices/  then:
ln -s /dev/ttyUSB0 com1
ln -s /dev/ttyUSB1 com2
ln -s /dev/ttyUSB2 com3
ln -s /dev/ttyUSB3 com4


I also suggest Xastir aprs program, is the best developed (linux) program around! The repository version is very old, a debian file of xastir-1.9.9 or 2.0.0 will have all the new maps!
 steve kd5mkv

---

### Post by FlaHAM on 2012-03-14
I Just got logged on again and have been browzing the HEP ME stuff.
I have been running Linux FBB, FPAC and Linux RMS for a million years.
How can I hep U?

73
<<Charley>>
   k4gbb

---

### Post by ~dr,j on 2012-03-26
k4gbb~
i got airmail working via wine ... so for normal packet that's what i use now [when I remember to check my airmail lol]

for other digital stuff, i got flDigi working so i gave up on fbb etc
thanks though :]
73
~j

---

### Post by kd5mkv on 2012-04-02
You could try keyboard to keyboard mode to connect to bbs, for example
c kd5mkv  Connected**  sp kd5mkv
connect to         send personal message. I sent messages to other airmail
mailboxs while they  were sending messages out.I still haven't made time for
LinAmc, looks like need to give it root permission, run kiss mode tnc, and edit out all the authors callsign to your own.
Steve kd5mkv

---

