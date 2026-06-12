---
title: "ekiga - registration failed"
date: 2006-03-15
forum: General Help
---

### Post by pchachte on 2006-03-15
I would like to try ekiga, but I can't get it off the ground.  I've been trying to connect with ekiga's free server, but I always get "registration failed".

I signed up for an account at ekiga.net and can login whenever I want.

Then I added an account to ekiga; called the account "ekiga"; typed in "ekiga.net" as my registrar; put my user-name (tried both chook and [email]chook@ekiga.net[/email]); and entered in my password.

When I click to activate the account, however, it thinks for a while and then informs me that the registration failed.  

I'm working under a shorewall firewall, but I also tried it after turning off the firewall for a second, but it still didn't work. 

Does anyone have any ideas?

---

### Post by kaamos on 2006-03-15
1) Make sure you are using stun

2) Run the wizard again (edit->guided blaa blaa) and choose "I don't want to register with ekiga.net". Then under edit->accounts add a new account with registar:ekiga.net and username:pchachte. Click ok and tick to box in the accounts window so that the account will try to connect.

3) If it still does not work, run ekiga in a terminal with "ekiga -d 4" and try to make some sense of the output. This is truly a last resort..

---

### Post by pchachte on 2006-03-16
Thanks for your advice, I tried it and below is the full log from a clean start:

Thanks in advance for any insight. 

charles
============================================

charles@chook:~$ ekiga-snapshot -d 4
2006/03/16 10:42:05.456   0:01.346               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:05.477   0:01.350               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:05.477   0:01.350               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:05.477   0:01.350               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:05.640   0:01.513               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:05.641   0:01.514               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:05.641   0:01.514               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:42:05.641   0:01.514               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:05.641   0:01.514               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:05.641   0:01.514               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:42:17.780   0:13.653               ekiga-snapshot GnomeMeeting version 2.0.1
2006/03/16 10:42:17.781   0:13.654               ekiga-snapshot OPAL version unknown
2006/03/16 10:42:17.781   0:13.654               ekiga-snapshot PWLIB version 1.11.0
2006/03/16 10:42:17.781   0:13.654               ekiga-snapshot GNOME support enabled
2006/03/16 10:42:17.781   0:13.654               ekiga-snapshot Fullscreen support enabled
2006/03/16 10:42:17.781   0:13.654               ekiga-snapshot DBUS support disabled
2006/03/16 10:42:17.892   0:13.765               ekiga-snapshot Set TCP port range to 3000030010
2006/03/16 10:42:17.892   0:13.766               ekiga-snapshot Set RTP port range to 50005059
2006/03/16 10:42:17.893   0:13.766               ekiga-snapshot Set UDP port range to 50605100
2006/03/16 10:42:17.948   0:13.821               ekiga-snapshot OpalEP  Created endpoint: h323
2006/03/16 10:42:18.004   0:13.877               ekiga-snapshot H323    Created endpoint.
2006/03/16 10:42:18.047   0:13.921               ekiga-snapshot OpalMan Added route "pc:.*=h323:<da>"
2006/03/16 10:42:18.090   0:13.963               ekiga-snapshot OpalEP  Created endpoint: sip
2006/03/16 10:42:18.102   0:13.975               ekiga-snapshot SIP     Created endpoint.
2006/03/16 10:42:18.123   0:13.996               ekiga-snapshot OpalMan Added route "pc:.*=sip:<da>"
2006/03/16 10:42:18.123   0:13.996               ekiga-snapshot OpalEP  Created endpoint: pc
2006/03/16 10:42:18.126   0:13.999               ekiga-snapshot PCSS    Created PC sound system endpoint.
2006/03/16 10:42:18.126   0:13.999               ekiga-snapshot OpalMan Added route "h323:.*=pc:<da>"
2006/03/16 10:42:18.126   0:13.999               ekiga-snapshot OpalMan Added route "sip:.*=pc:<da>"
2006/03/16 10:42:18.385   0:14.258        Opal Listener:8446620 Listen  Started listening thread on tcp$10.10.10.1:1720
2006/03/16 10:42:18.429   0:14.303        Opal Listener:8446620 Listen  Waiting on socket accept on tcp$10.10.10.1:1720
2006/03/16 10:42:18.482   0:14.410        Opal Listener:8425568 Listen  Started listening thread on udp$10.10.10.1:5060
2006/03/16 10:42:18.539   0:14.464        Opal Listener:8425568 Listen  Waiting on UDP packet on udp$10.10.10.1:5060
2006/03/16 10:42:19.523   0:15.397               ekiga-snapshot Listen  Stopping listening thread on tcp$10.10.10.1:1720
2006/03/16 10:42:19.581   0:15.454               ekiga-snapshot Listen  Stopping listening thread on udp$10.10.10.1:5060
2006/03/16 10:42:19.582   0:15.456        Opal Listener:8425568 Listen  UDP select error: Interrupted system call
2006/03/16 10:42:19.633   0:15.507        Opal Listener:85451c0 Listen  Started listening thread on tcp$10.10.10.1:1720
2006/03/16 10:42:19.635   0:15.559        Opal Listener:85451c0 Listen  Waiting on socket accept on tcp$10.10.10.1:1720
2006/03/16 10:42:19.833   0:15.707        Opal Listener:852c1c0 Listen  Started listening thread on udp$10.10.10.1:5060
2006/03/16 10:42:19.835   0:15.760        Opal Listener:852c1c0 Listen  Waiting on UDP packet on udp$10.10.10.1:5060
2006/03/16 10:42:40.636   0:36.509        GMStunClient:08565de0 OPAL    STUN server "stun.ekiga.net" replies Symmetric Firewall, external IP 68.72.168.244
2006/03/16 10:42:50.345   0:46.218               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:50.345   0:46.218               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:50.345   0:46.218               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:50.346   0:46.219               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:50.423   0:46.296               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:50.423   0:46.297               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:50.424   0:46.297               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:42:50.424   0:46.297               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:50.424   0:46.297               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:50.424   0:46.297               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:42:50.824   0:46.698               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:50.825   0:46.698               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:50.825   0:46.698               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:50.825   0:46.698               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:50.902   0:46.775               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:50.903   0:46.776               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:50.903   0:46.776               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:42:50.903   0:46.776               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:50.903   0:46.776               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:50.903   0:46.776               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:42:51.306   0:47.179               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:51.306   0:47.179               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:51.306   0:47.179               ekiga-snapshot Detected audio plugins: ALSA
2006/03/16 10:42:51.306   0:47.179               ekiga-snapshot Detected video plugins: YUVFile,Picture,V4L
2006/03/16 10:42:51.467   0:47.341               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:51.468   0:47.341               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:51.468   0:47.341               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:42:51.468   0:47.341               ekiga-snapshot Detected the following audio input devices: Audigy 2 Value [SB0400],Default with plugin ALSA
2006/03/16 10:42:51.468   0:47.341               ekiga-snapshot Detected the following audio output devices: Audigy 2 Value [SB0400],Default with plugin ALSA2006/03/16 10:42:51.468   0:47.341               ekiga-snapshot Detected the following video input devices: No device found with plugin V4L
2006/03/16 10:43:33.666   1:29.540      GMAccounts...t:085a6640 OpalUDP Binding to interface: 10.10.10.1:35084
2006/03/16 10:43:33.667   1:29.540      GMAccounts...t:085a6640 SIP     Created transport udp$0.0.0.0<if=udp$10.10.10.1:35084>
2006/03/16 10:43:33.690   1:29.563      GMAccounts...t:085a6640 OpalUDP Started connect to 213.186.62.145:5060
2006/03/16 10:43:33.692   1:29.565      GMAccounts...t:085a6640 OpalUDP STUN could not create socket!
2006/03/16 10:43:33.693   1:29.566      GMAccounts...t:085a6640 OpalUDP Connect on pre-bound interface: 10.10.10.1
2006/03/16 10:43:33.694   1:29.567      GMAccounts...t:085a6640 SIP     Created Transport for Registrar udp$213.186.62.145:5060<if=udp$10.10.10.1:5061>
2006/03/16 10:43:33.700   1:29.573        SIP Transport:85a63f8 SIP     Read thread started.
2006/03/16 10:43:33.703   1:29.577        SIP Transport:85a63f8 SIP     Waiting for PDU on udp$213.186.62.145:5060<if=udp$10.10.10.1:5061>
2006/03/16 10:43:33.714   1:29.587      GMAccounts...t:085a6640 SIP     Sending PDU on udp$213.186.62.145:5060<if=udp$10.10.10.1:5061>
REGISTER sip:ekiga.net SIP/2.0
CSeq: 1 REGISTER
Via: SIP/2.0/UDP 68.72.168.244:5061;branch=z9hG4bK46e914ad-79b3-da11-9504-0090278a100e;rport
User-Agent: Ekiga/2.0.1-20060316-01
From: <sip:chook@ekiga.net>;tag=ac9214ad-79b3-da11-9504-0090278a100e
Call-ID: 581f0ead-79b3-da11-9504-0090278a100e@chook
To: <sip:chook@ekiga.net>
Contact: <sip:chook@68.72.168.244:5061;transport=udp>
Allow: INVITE, ACK, OPTIONS, BYE, CANCEL, REGISTER, SUBSCRIBE, NOTIFY, REFER, MESSAGE
Expires: 3600
Content-Length: 0
Max-Forwards: 70


2006/03/16 10:43:33.963   1:29.836                  Housekeeper SIP     Transaction 1 REGISTER timeout, making retry 1
2006/03/16 10:43:33.964   1:29.837                  Housekeeper SIP     Sending PDU on udp$213.186.62.145:5060<if=udp$10.10.10.1:5061>
REGISTER sip:ekiga.net SIP/2.0
CSeq: 1 REGISTER
Via: SIP/2.0/UDP 68.72.168.244:5061;branch=z9hG4bK46e914ad-79b3-da11-9504-0090278a100e;rport
User-Agent: Ekiga/2.0.1-20060316-01
From: <sip:chook@ekiga.net>;tag=ac9214ad-79b3-da11-9504-0090278a100e
Call-ID: 581f0ead-79b3-da11-9504-0090278a100e@chook
To: <sip:chook@ekiga.net>
Contact: <sip:chook@68.72.168.244:5061;transport=udp>
Allow: INVITE, ACK, OPTIONS, BYE, CANCEL, REGISTER, SUBSCRIBE, NOTIFY, REFER, MESSAGE
Expires: 3600
Content-Length: 0
Max-Forwards: 70


2006/03/16 10:43:34.465   1:30.338                  Housekeeper SIP     Transaction 1 REGISTER timeout, making retry 2
2006/03/16 10:43:34.466   1:30.339                  Housekeeper SIP     Sending PDU on udp$213.186.62.145:5060<if=udp$10.10.10.1:5061>
REGISTER sip:ekiga.net SIP/2.0
CSeq: 1 REGISTER
Via: SIP/2.0/UDP 68.72.168.244:5061;branch=z9hG4bK46e914ad-79b3-da11-9504-0090278a100e;rport
User-Agent: Ekiga/2.0.1-20060316-01
From: <sip:chook@ekiga.net>;tag=ac9214ad-79b3-da11-9504-0090278a100e
Call-ID: 581f0ead-79b3-da11-9504-0090278a100e@chook
To: <sip:chook@ekiga.net>
Contact: <sip:chook@68.72.168.244:5061;transport=udp>
Allow: INVITE, ACK, OPTIONS, BYE, CANCEL, REGISTER, SUBSCRIBE, NOTIFY, REFER, MESSAGE
Expires: 3600
Content-Length: 0
Max-Forwards: 70


2006/03/16 10:43:35.466   1:31.339                  Housekeeper SIP     Transaction 1 REGISTER timeout, making retry 3
2006/03/16 10:43:35.466   1:31.340                  Housekeeper SIP     Sending PDU on udp$213.186.62.145:5060<if=udp$10.10.10.1:5061>
REGISTER sip:ekiga.net SIP/2.0
CSeq: 1 REGISTER
Via: SIP/2.0/UDP 68.72.168.244:5061;branch=z9hG4bK46e914ad-79b3-da11-9504-0090278a100e;rport
User-Agent: Ekiga/2.0.1-20060316-01
From: <sip:chook@ekiga.net>;tag=ac9214ad-79b3-da11-9504-0090278a100e
Call-ID: 581f0ead-79b3-da11-9504-0090278a100e@chook
To: <sip:chook@ekiga.net>
Contact: <sip:chook@68.72.168.244:5061;transport=udp>
Allow: INVITE, ACK, OPTIONS, BYE, CANCEL, REGISTER, SUBSCRIBE, NOTIFY, REFER, MESSAGE
Expires: 3600
Content-Length: 0
Max-Forwards: 70


2006/03/16 10:43:37.467   1:33.340                  Housekeeper SIP     Transaction 1 REGISTER timeout, making retry 4
2006/03/16 10:43:37.468   1:33.341                  Housekeeper SIP     Sending PDU on udp$213.186.62.145:5060<if=udp$10.10.10.1:5061>
REGISTER sip:ekiga.net SIP/2.0
CSeq: 1 REGISTER
Via: SIP/2.0/UDP 68.72.168.244:5061;branch=z9hG4bK46e914ad-79b3-da11-9504-0090278a100e;rport
User-Agent: Ekiga/2.0.1-20060316-01
From: <sip:chook@ekiga.net>;tag=ac9214ad-79b3-da11-9504-0090278a100e
Call-ID: 581f0ead-79b3-da11-9504-0090278a100e@chook
To: <sip:chook@ekiga.net>
Contact: <sip:chook@68.72.168.244:5061;transport=udp>
Allow: INVITE, ACK, OPTIONS, BYE, CANCEL, REGISTER, SUBSCRIBE, NOTIFY, REFER, MESSAGE
Expires: 3600
Content-Length: 0
Max-Forwards: 70


2006/03/16 10:43:39.713   1:35.587                  Housekeeper SIP     Set state Terminated_Timeout for transaction 1 REGISTER

---

### Post by it.henrik on 2006-03-16
Have you opened port 5060 for UDP in your firewall (maybe you are behind a net too)?
Did the NAT test report that you were behind a port restricted firewall (or something similar)?

If you havnt already tried it .. open 5060 in your firewall(s) and enable STUN.

---

### Post by pchachte on 2006-03-16
I've tried turning off my firewall entirely, but that doesn't help. The nat test reports that I have a symetrical firewall (when the firewall is on) and an open nat when the firewall is off, but the registration fails in both cases.  Ekiga gives me no complaints or errors (other than the registration failing).

not sure what a net is, so I can't comment on that.

thanks again
charles.

---

### Post by Buffalo Soldier on 2006-03-19
I know this is going to sound silly... but have you confirm/validate your email address that you use for registration? It's something like this:
> 
To finalize your registration please check the following URL within 24 hours:
[http://www.ekiga.net/example-example.example](http://www.ekiga.net/example-example.example) 
(If you confirm later you will have to re-register.) 


---

### Post by pchachte on 2006-03-20
yea, I'm fully registered and I can login in to the system at ekiga.net.  So it's plugged in, now I just need to turn it on. 

thanks,

charles

---

### Post by SlugO on 2006-03-20
I haven't been able to connect with my Ekiga.net account today either.
Wonder what's wrong... Usually it works every time.

Ekiga says: Registration failed: Not acceptable

---

### Post by SlugO on 2006-03-20
Hmm.. strange, seems there's something wrong with STUN at the moment.
Ekiga works perfectly now with IP translation after just switching to it :)

---

### Post by pchachte on 2006-03-21
I tried connecting with linphone and it works perfectly without changing anything in my firewall (using my ekiga.net account).

It would be nice to get ekiga working, because it has a nice interface, but I guess I'll stick with linphone now.

now I just need to figure out which company to use.

Thanks for your help.

---

### Post by damu on 2006-03-21
I use Ekiga, and finally managed to get through.

Don't use stun.ekiga.net ...it is down.

I use stun.voxgratia.org . It saved my day really...

Don't use the stun of sipdiscount if you think of choosing them...it didn't work for me. But sipdiscount works fine, if you use "stun.voxgratia.org" ...don't ask me why   :) 

As far as providers is concerned, I use [sipdiscount]("http://www.sipdiscount.com/en/freetrial.html")

**pros** : - phone calls to landlines are free as beer for 40 destinations, including UK, France, Italy, Spain, USA, China, Australia, Japan, Canada ...!
         - reliable: never had any problem with them  when using their Win softphone (Voipbuster). Seems to work great with Ekiga too!!

**cons** : - u need to install a windows applet to buy some credits!!!...duh! That's not a big deal for me as I still have to dual boot from time to time, and as I only pay communications to mobile phones, I don't buy credits very often... :) 
         - u need a minimum of credit of 10 euros to be allowed to give phone calls of more than a minute (free trial) towards free destinations. This credit has to be used within the next 3 months...shouldn't be a problem if you phone mobile phones too.

---

### Post by CFBauer on 2007-09-05
I'm bumping this thread because I used it to solve my issue.  I got the same registration failed error as before, so I enabled stun and it's fixed.  Thanks everyone!

---

### Post by sKAApGIF on 2008-05-01
For anyone who have open nat and no firewall and still can't register.  Make sure that the interface ekiga should listen on is selected.

Edit -> Network settings -> Listen on: ......  <- Make sure to select your internet connection here!

---

### Post by no_martini_no on 2008-06-30
and be sure about the outbound proxy ip in the "SIP settings" tag.
I had trouble because the autoconfiguration wizard gave me an outbound proxy ip, but I didn't need it...

---

