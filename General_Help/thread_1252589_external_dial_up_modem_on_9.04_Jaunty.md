---
title: "external dial up modem on 9.04 Jaunty"
date: 2009-08-29
forum: General Help
---

### Post by Gyrotwister on 2009-08-29
Hi, I'm in the process of hopefully migrating from Hardy to Jaunty.  At the moment I have both 8.04 and 9.04 on my Desktop pc and can boot to either.   So far I've been unable to get Jaunty connected to the internet.  

I've managed to install wvdial and gnome-ppp the same as my 8.04 but gnome-ppp seems to hang towards the end when authenticating.  Username, password, phone number etc settings are all correct.  

I know this is not a hardware issue because Win xp and Hardy both connect without any problems.  This is a Jaunty issue.  

Can anyone advise how to get this OS to connect to my isp?

---

### Post by baskar007 on 2009-08-29
friend i am using an wireless data modem in ubuntu 9.04 ja... without any problem.
Did you configured your modem for os in wvdial.conf file?
check it for rite setting. modem commandes ect.

<><><Newbie to ubuntu<><<> just 3 days exp:)

---

### Post by Gyrotwister on 2009-08-29
My wvdial.conf file resides at /etc/wvdial.conf.  It looks like this...

[Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Modem Type = Analog Modem 
; Phone = 0198666743 
ISDN = 0 
; Password = password123 
New PPPD = yes 
; Username = [email]correct@blank.com.au[/email] 
Modem = /dev/ttyS0 
Baud = 115200

Password, username and phonenumber are phoney for the purposes of this discussion but I assure you they are correct in the real file.  
Is there anything I need to fix?  

When I try to connect I get the following...

r@r-desktop:~$ wvdial 
--> WvDial: Internet dialer version 1.60 
--> Cannot set information for serial port. 
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


And yes, my user name is “r”.  Lazy, I know.

---

### Post by GeorgeVita on 2009-08-29
Hi **Gyrotwister**,
first remove semicolons from phone, user, password and add a line into your configuration file:```
gksudo /etc/wvdial.conf
``` edit your file to become: ```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = 0198666743
Password = password123
New PPPD = yes
Username = correct@blank.com.au
Modem = /dev/ttyS0
Baud = 115200
Stupid Mode = yes

```
Be sure that you are using correct phone/user/pass and post here any terminal output if not connected.

>>> **connect using: sudo wvdial**

Regards,
George

---

### Post by TopEnder on 2009-08-29
G'Day I connect to my dialup service using the file [COLOR="Blue"]pppconfig[/COLOR] and [COLOR="Blue"]sudo nano /etc/chatscripts/provider[/COLOR] to silent the modem speaker and wvdial mainly for GNOME PPP. My wvdial.conf file very basic but it works for GNOME PPP (GNOME Dialup Tool): 
[COLOR="Blue"][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <*44 0198308888>
ISDN = 0
; Password = <Abc1234Cba>
New PPPD = yes
; Username = <User_Name>
Modem = /dev/ttyS0
Baud = 115200[/COLOR]
Very basic but works well for me, hope this will help until you get your connection sorted out using wvdial.conf.  TopEnder

---

### Post by Gyrotwister on 2009-08-29
Mr GeorgeVita.  

Removing the semicolons did the trick.  
I'm not a programmer but I vaguely remember that certain ascii characters such as “#” and “;” can be used to define a comment as distinct from a line of code depending on the language being used.  It makes sense to remove them, I should have thought of that.  

Thankyou.

---

### Post by Gyrotwister on 2009-08-29
Topender, 

I'm not familiar with pppconfig.  
Can you point me towards a good howto for this utility?  
I may need it someday.  

Thanks.

---

### Post by TopEnder on 2009-08-29
> **Gyrotwister said:**
> Topender, 

I'm not familiar with pppconfig.  
Can you point me towards a good howto for this utility?  
I may need it someday.  

Thanks.
Gyrotwister,  pppconfig is straight forward to use, it must be or I would not be able to use it (keep for getting things), just type in pppconfig (I don't think I used sudo) the package is pretty straight forward given info on each of the screens, currently cleaning up WinXP, will be back using 9.04 later today, will be looking to see if you had any luck.  TopEnder

---

### Post by Gyrotwister on 2009-08-30
So I've managed to connect with wvdial and have been checking that my favourite apps run in 9.04.  So far gnome-ppp still hangs when authenticating which seems weird since it's supposed to only be a front end for gnome-ppp.  

Does gnome-ppp work in 9.04?  
Is anybody using it?  

I've also been looking at pppconfig.  
After entering all my details into the editor I tried the pon command without success.  

r@r-desktop:~$ pon

Error: only members of the 'dip' group can use this command.

r@r-desktop:~$ 


What's “dip”.

---

### Post by _duncan_ on 2009-08-30
> **Gyrotwister said:**
> Topender, 

I'm not familiar with pppconfig.  
Can you point me towards a good howto for this utility?  
I may need it someday.  

Thanks.

Try [[COLOR="Blue"]**this**[/COLOR]]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html") link. The page takes a while to load on dial-up coz it has a lot of screenshots. Scroll down to the section pppconfig with pon/poff when it's done loading.

----------------------

> Error: only members of the 'dip' group can use this command.

Enter the following command in a terminal:

```
sudo adduser [COLOR="Blue"]**yourUserID**[/COLOR] dip
```

replace [COLOR="Blue"]**yourUserID**[/COLOR] with your actual user ID.

assuming your user id is 'r' (???) the command should look like this:

```
sudo adduser r dip
```

---

### Post by Gyrotwister on 2009-08-31
OK, I'm now officially a member of the dip club but it's still not connecting.  After it dials I get the recorded message that the number is incorrect "please check the number and dial again".  

The number is correct so I'm guessing the tones are getting fired off before a dial tone is heard.  Is there a "wait for dial tone" option in pppconfig somewhere?

---

### Post by GeorgeVita on 2009-08-31
Hi **Gyrotwister**,
if you need just a delay, you can use comma (**,**) within phone number.
ATDT123 dials directly 123
ATDT,123 dials 123 after a short delay
ATDT,123,,,4 dials 123 after a short delay, then waits and finally dials 4

If you need 'wait for dial tone' you can place **W** at phone number (I have not checked this). Try **ATDTW123**

Note: as the system sets ATDT (selecting tone dialling) you have only to change the Phone# to: ,,123 or W123

Regards,
George

---

### Post by Gyrotwister on 2009-08-31
I've been experimented with the commas and I can hear the difference they make but it just isn't working.  It seems my telephone providers equipment can't make sense of the DTMF signals when the modem is being controlled by pppconfig.  I get the "please check the number and try again" message as soon as it starts dialing regardless of where I insert pauses.  To my ear it sounds the same as when wvdial is in control.  I don't understand.  

I thought it would be nice to have pppconfig as an option in case wvdial & gnome-ppp ever developed a problem.  Never mind.  

On the upside gnome-ppp started working OK after I reinstalled it via synaptic.  

Thankyou George, 
Thankyou Duncan.

---

