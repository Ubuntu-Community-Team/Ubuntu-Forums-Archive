---
title: "Missing Items - Upgarde to Linux 2.6.31-17"
date: 2010-01-31
forum: General Help
---

### Post by Mukoi on 2010-01-31
Hi,

I recently installed Ubuntu 9.10 and with a lot of help from the Forum I was able to access the internet via my dialup winmodem.

Update Manager recommended that I download a number of security updates, which I did.  There was 200+ downloads.  One of the downloads was Linux 2.6.31-17 which was installed.

Going into Linux 2.6.31-17 I notice that my wvdial to access the internet is not operational:

[I]--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Cannot open /dev/ttySHSF0: Input/output error
--> Cannot open /dev/ttySHSF0: Input/output error
--> Cannot open /dev/ttySHSF0: Input/output error   [/I]
  
I also notice that I don't hear the* drum* before my logon and no sound of the *drums* at startup.  So I guess that there is no sound.  Also there is no sound icon showing on the top right-hand bar.

Is there anything that I should have done to enable these to be updated in Linux 2.6.31-17?

---

### Post by Mukoi on 2010-02-02
All seems ok with Linux 2.6.31-14, so I'll boot with that until I can find a solution to my problem.

---

### Post by GeorgeVita on 2010-02-03
Hi **Mukoi**,
some 'dial up' drivers are kernel dependant (as your driver creating the **ttySHSF0**).

a. read/check info for the specific driver to find if it 'fits' to the newer kernel

b. use **sudo wvdial** to connect (and not sudo wvdial /etc/wvdial.conf) as the default configuration file **is** /etc/wvdial.conf and you have placed all parameters under the [Dialer Defaults] section.
Note: to use other parameters file (ex. **/etc/my.conf**) use: **sudo wvdial -C /etc/my.conf**

Regards,
George

---

### Post by Mukoi on 2010-02-04
Hi George,

Thanks for answering this thread.  I was really hoping that you would see it and offer some advice.

Please excuse my inexperience.  How do I read/check the info for the specific driver to find if it 'fits' to the newer kernel?  And what do you mean in your note about the other parameters file?

Would my sound problem be similar?

Thanks

---

### Post by GeorgeVita on 2010-02-04
Hi **Mukoi**, I do not have enough experience with internal modems but I think most of them need a new installation of the driver for the newer kernel. To determine possible changes review your previous [thread]("http://ubuntuforums.org/showthread.php?t=1383273") and documentation from the site you got the driver.

To connect run wvdial without '/etc/wvdial.conf'. This will remove the warning: > --> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.

Regards,
George

---

### Post by Mukoi on 2010-02-06
Thank you.

My winmodem driver was installed to the linux 2.6.31-14 kernel.

I notice that there has been a further upgrade to 2.6.31-19, so I will install this first and reinstall the driver for the modem to the new kernel.  Hopefully my sound problem will also be fixed when all this is done.

---

### Post by Mukoi on 2010-02-06
Something strange has happened.

My wvdial is not working in my older kernel (2.6.31-14).  I wonder if it is because of bad weather affecting the landlines.

[I]--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT1234567890
--> Waiting for carrier.
ATDT1234567890
CONNECT 460800 
User Access Verificationlogin:
--> Carrier detected.
  Starting PPP immediately.
--> Starting pppd at Mon Feb  8 00:39:34 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2708
--> Disconnecting at Mon Feb  8 00:39:35 2010
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)
[/I]

---

### Post by Mukoi on 2010-02-10
Ok,
Have downloaded to linux 2.6.31-19 kernel and reinstalled my winmodem following [http://ubuntuforums.org/showthread.php?t=1383273](http://ubuntuforums.org/showthread.php?t=1383273).  My modem is now being recognized in the latest kernel and I have sound.

Still getting the message mentioned in the above threat #7 when use wvdial.  I can hear the internet connection noise, but then it cuts off and the terminal shows the above message.  Seems to be a problem with my settings.  I'll redo the pppconfig and wvdialconfig again.

Any suggestions on why I get this response when I use wvdial to dialup?

---

### Post by alexfish on 2010-02-10
hi

You could have a look here . don't know if it will help but the site is worth a read

  	 	 	 	 	 	  
[LIST]
[*][[COLOR=#0000ff][SIZE=2]PPP 	Connection Utilities[/SIZE][/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")

[LIST]
[*][[COLOR=#0000ff][SIZE=2]The 		gnome-ppp dialer utility[/SIZE][/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")

[LIST]
[*][[COLOR=#0000ff][SIZE=2]User 			Priviledges- the dip and dialout groups [/SIZE][/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout") 			
[*][[COLOR=#0000ff][SIZE=2]Permissions 			for /etc/ppp/pap-secrets and etc/ppp/chap-secrets[/SIZE][/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets") 						
[/LIST]
 	
[/LIST]
 
[/LIST]
 Regards 

alexfish

---

### Post by Mukoi on 2010-02-10
Thank you alexfish.

The information from the site was very helpful.

Just had to change my user privileges to allow me to use the internet.

---

