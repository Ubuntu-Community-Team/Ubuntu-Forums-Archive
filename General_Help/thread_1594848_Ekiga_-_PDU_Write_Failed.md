---
title: "Ekiga - PDU Write Failed"
date: 2010-10-12
forum: General Help
---

### Post by purecharger on 2010-10-12
I am attempting to use Ekiga for some VoIP work and am unable to do so. Ekiga cannot register my account nor can it connect to ekiga.net for a test call or my own local Asterisk server. Enabling debug gives me the following output, where the clear error message is "SIP PDU Write Failed". I have tried running Ekiga as root with the same results.

```

2010/10/12 14:31:33.828	  0:00.039	                       		Version 3.2.6 by  on Unix Linux (2.6.32-25-generic-x86_64) with PTLib (v2.6.5) at 2010/10/12 14:31:33.828
2010/10/12 14:31:33.828	  0:00.039	                       	Ekiga git revision: unknown
2010/10/12 14:31:33.829	  0:00.039	                       	Ekiga registered on D-Bus: org.ekiga.Ekiga
2010/10/12 14:31:33.829	  0:00.040	                       	PWLib	File handle high water mark set: 17 Thread unblock pipe
2010/10/12 14:31:33.829	  0:00.040	                       	PTLib	Thread high water mark set: 2
2010/10/12 14:31:33.829	  0:00.040	                       	PWLib	File handle high water mark set: 19 Thread unblock pipe
2010/10/12 14:31:33.829	  0:00.040	                       	PTLib	Thread high water mark set: 3
2010/10/12 14:31:33.830	  0:00.040	                       	PWLib	File handle high water mark set: 21 Thread unblock pipe
2010/10/12 14:31:33.830	  0:00.041	                       	PWLib	File handle high water mark set: 23 Thread unblock pipe
2010/10/12 14:31:33.831	  0:00.041	                       	PTLib	Thread high water mark set: 4
2010/10/12 14:31:33.831	  0:00.042	                       	HalManager_dbus	Initialising HAL Manager
2010/10/12 14:31:33.832	  0:00.042	                       	HalManager_dbus	Populating device list
2010/10/12 14:31:33.969	  0:00.180	                       	HalManager_dbus	Populated device list with 21 devices
2010/10/12 14:31:33.970	  0:00.181	                       	HalManager_dbus	Populating interface list
2010/10/12 14:31:33.971	  0:00.181	                       	HalManager_dbus	Populating full interface list failed - Method "getDevices" with signature "" on interface "org.freedesktop.NetworkManager" doesn't exist

2010/10/12 14:31:33.971	  0:00.182	                       	Detecting V4L2 devices
2010/10/12 14:31:33.971	  0:00.182	                       	Unable to detect v4l2 directory
2010/10/12 14:31:33.986	  0:00.197	                       	PWLib	File handle high water mark set: 28 Thread unblock pipe
2010/10/12 14:31:33.987	  0:00.197	                       	PTLib	Thread high water mark set: 5
2010/10/12 14:31:33.987	  0:00.197	                       	OpalMan	Created manager.
2010/10/12 14:31:33.987	  0:00.197	                       	OpalMan	Attached endpoint with prefix pc
2010/10/12 14:31:33.987	  0:00.197	                       	OpalEP	Created endpoint: pc
2010/10/12 14:31:34.013	  0:00.224	                       	PCSS	Created PC sound system endpoint.
Players:
Default
Logitech USB Headset
HDA Intel
HDA Intel (1)
EKIGA
*.wav
/dev/dsp
/dev/dsp1
Recorders:
Default
Logitech USB Headset
HDA Intel
EKIGA
*.wav
/dev/dsp
/dev/dsp1

2010/10/12 14:31:34.013	  0:00.224	                       	OPAL	SetMediaFormatOrder()
2010/10/12 14:31:34.013	  0:00.224	                       	OPAL	SetMediaFormatMask()
2010/10/12 14:31:34.014	  0:00.224	                       	OpalMan	Attached endpoint with prefix sip
2010/10/12 14:31:34.014	  0:00.224	                       	OpalEP	Created endpoint: sip
2010/10/12 14:31:34.014	  0:00.225	                       	PWLib	File handle high water mark set: 29 PUDPSocket
2010/10/12 14:31:34.014	  0:00.225	                       	IfaceMon	Initial interface list:
127.0.0.1 [00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:01] <00-00-00-00-00-00> (lo)
10.10.20.12 [fe:80:00:00:00:00:00:00:02:25:64:ff:fe:8c:05:4d] <00-25-64-8C-05-4D> (eth0)
172.16.104.1 [fe:80:00:00:00:00:00:00:02:50:56:ff:fe:c0:00:01] <00-50-56-C0-00-01> (vmnet1)
172.16.45.1 [fe:80:00:00:00:00:00:00:02:50:56:ff:fe:c0:00:08] <00-50-56-C0-00-08> (vmnet8)

2010/10/12 14:31:34.014	  0:00.225	                       	PWLib	File handle high water mark set: 30 Thread unblock pipe
2010/10/12 14:31:34.014	  0:00.225	                       	PTLib	Thread high water mark set: 6
2010/10/12 14:31:34.014	  0:00.225	                       	PWLib	File handle high water mark set: 32 Thread unblock pipe
2010/10/12 14:31:34.014	  0:00.225	Network In...0x34910710	IfaceMon	Started interface monitor thread.
2010/10/12 14:31:34.014	  0:00.225	                       	PTLib	Thread high water mark set: 7
2010/10/12 14:31:34.014	  0:00.225	Network In...0x34910710	PWLib	File handle high water mark set: 33 PUDPSocket
2010/10/12 14:31:34.014	  0:00.225	                       	OpalMan	Attached endpoint with prefix sips
2010/10/12 14:31:34.015	  0:00.225	                       	SIP	Created endpoint.
2010/10/12 14:31:34.015	  0:00.225	                       	MonSock	Created socket bundle for all interfaces.
2010/10/12 14:31:34.015	  0:00.225	                       	PWLib	File handle high water mark set: 34 PUDPSocket
2010/10/12 14:31:34.015	  0:00.226	                       	PWLib	File handle high water mark set: 35 Thread unblock pipe
2010/10/12 14:31:34.015	  0:00.226	                       	PTLib	Thread high water mark set: 8
2010/10/12 14:31:34.015	  0:00.226	Opal Liste...0x3488e710	Listen	Started listening thread on udp$*:5060
2010/10/12 14:31:34.015	  0:00.226	                       	OpalMan	Added route "sip:.*=pc:*"
2010/10/12 14:31:34.015	  0:00.226	                       	OpalMan	Added route "pc:.*=sip:<da>"
2010/10/12 14:31:34.015	  0:00.226	                       	OpalMan	Attached endpoint with prefix h323
2010/10/12 14:31:34.015	  0:00.226	                       	OpalEP	Created endpoint: h323
2010/10/12 14:31:34.015	  0:00.226	                       	OpalMan	Attached endpoint with prefix h323s
2010/10/12 14:31:34.016	  0:00.226	                       	H323	Created endpoint.
2010/10/12 14:31:34.016	  0:00.226	                       	PWLib	File handle high water mark set: 36 PTCPSocket
2010/10/12 14:31:34.016	  0:00.226	                       	PWLib	File handle high water mark set: 38 Thread unblock pipe
2010/10/12 14:31:34.016	  0:00.226	                       	PTLib	Thread high water mark set: 9
2010/10/12 14:31:34.016	  0:00.227	                       	OpalMan	Added route "h323:.*=pc:<db>"
2010/10/12 14:31:34.016	  0:00.227	Opal Liste...0x3484d710	Listen	Started listening thread on tcp$*:1720
2010/10/12 14:31:34.016	  0:00.227	Opal Liste...0x3484d710	Listen	Waiting on socket accept on tcp$*:1720
2010/10/12 14:31:34.016	  0:00.227	                       	OpalMan	Added route "pc:.*=h323:<da>"
2010/10/12 14:31:34.025	  0:00.235	                       	MediaFormat	Removing codecs SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF
2010/10/12 14:31:34.025	  0:00.236	                       	OPAL	SetMediaFormatMask(PCM-16-48kHz,PCM-16-32kHz,PCM-16-16kHz,PCM-16,G.726-16k,G.726-24k,G.726-32k,G.726-40k,GSM-06.10,GSM-AMR,LPC-10,MS-GSM,MS-IMA-ADPCM,SpeexIETFNarrow-11k,SpeexIETFNarrow-15k,SpeexIETFNarrow-18.2k,SpeexIETFNarrow-24.6k,SpeexIETFNarrow-5.95k,SpeexIETFNarrow-8k,SpeexNB,SpeexWNarrow-8k,YUV420P,RFC4175_YCbCr-4:2:0,RGB32,RGB24,RFC4175_RGB,SIP-IM,T.140,H.224/H323AnnexQ,H.224/HDLCTunneling,Linear-16-Stereo-48kHz)
2010/10/12 14:31:34.025	  0:00.236	                       	OPAL	SetMediaFormatOrder(SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF)
2010/10/12 14:31:34.031	  0:00.242	                       	MediaFormat	Removing codecs SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF
2010/10/12 14:31:34.031	  0:00.242	                       	OPAL	SetMediaFormatMask(PCM-16-48kHz,PCM-16-32kHz,PCM-16-16kHz,PCM-16,G.726-16k,G.726-24k,G.726-32k,G.726-40k,GSM-06.10,GSM-AMR,LPC-10,MS-GSM,MS-IMA-ADPCM,SpeexIETFNarrow-11k,SpeexIETFNarrow-15k,SpeexIETFNarrow-18.2k,SpeexIETFNarrow-24.6k,SpeexIETFNarrow-5.95k,SpeexIETFNarrow-8k,SpeexNB,SpeexWNarrow-8k,YUV420P,RFC4175_YCbCr-4:2:0,RGB32,RGB24,RFC4175_RGB,SIP-IM,T.140,H.224/H323AnnexQ,H.224/HDLCTunneling,Linear-16-Stereo-48kHz)
2010/10/12 14:31:34.031	  0:00.242	                       	OPAL	SetMediaFormatOrder(SpeexIETFWide-20.6k,SpeexWB,SpeexWide-20.6k,G.711-uLaw-64k,G.711-ALaw-64k,G.722-64k,theora,H.261,H.261-CIF,H.261-QCIF)
2010/10/12 14:31:34.037	  0:00.247	                       	PWLib	File handle high water mark set: 40 Thread unblock pipe
2010/10/12 14:31:34.037	  0:00.247	                       	PTLib	Thread high water mark set: 10
2010/10/12 14:31:34.037	  0:00.247	StunDetector:0x3480c710	PWLib	File handle high water mark set: 41 PUDPSocket
2010/10/12 14:31:34.067	  0:00.278	                       	PWLib	File handle high water mark set: 55 PUDPSocket
2010/10/12 14:31:34.067	  0:00.278	                       	SIP	Changing SUBSCRIBE handler from Unavailable to Subscribing, target=sip:500@ekiga.net, id=48923ec1-b5d4-df11-9ee1-0025648c054d@ryan-lin
2010/10/12 14:31:34.067	  0:00.278	                       	DNS	SRV Lookup ekiga.net service _sip._udp
2010/10/12 14:31:34.106	  0:00.316	                       	SIP	No SRV record found.
2010/10/12 14:31:34.146	  0:00.356	                       	OpalUDP	Binding to interface: 0.0.0.0:5060
2010/10/12 14:31:34.146	  0:00.357	                       	PWLib	File handle low water mark set: 53 PUDPSocket
2010/10/12 14:31:34.146	  0:00.356	                       	SIP	Created transport udp$86.64.162.35:5060<if=udp$*:5060>
2010/10/12 14:31:34.146	  0:00.357	                       	OpalUDP	Started connect to 86.64.162.35:5060
2010/10/12 14:31:34.147	  0:00.357	                       	OpalUDP	Writing to interface 0 - "10.10.20.12%eth0"
2010/10/12 14:31:34.147	  0:00.358	                       	OpalMan	Listener interfaces: associated transport=None
    udp$10.10.20.12:5060,udp$172.16.104.1:5060,udp$172.16.45.1:5060
2010/10/12 14:31:34.316	  0:00.527	StunDetector:0x3480c710	PWLib	File handle low water mark set: 43 PUDPSocket
2010/10/12 14:31:34.318	  0:00.529	                       	PWLib	File handle high water mark set: 56 PUDPSocket
2010/10/12 14:31:37.773	  0:03.983	                       	PWLib	File handle low water mark set: 53 PUDPSocket
2010/10/12 14:31:37.773	  0:03.984	StunDetector:0x3480c710	PWLib	File handle low water mark set: 41 PUDPSocket
2010/10/12 14:31:37.855	  0:04.065	StunDetector:0x3480c710	OPAL	STUN server "stun.ekiga.net" replies Restricted NAT, external IP 173.198.4.114
2010/10/12 14:31:37.855	  0:04.066	                       	PWLib	File handle low water mark set: 39 PUDPSocket
2010/10/12 14:31:37.856	  0:04.066	                       	SIP	Transaction created.
2010/10/12 14:31:37.858	  0:04.069	                       	DNS	SRV Lookup ekiga.net service _sip._udp
2010/10/12 14:31:37.892	  0:04.102	                       	SIP	No SRV record found.
2010/10/12 14:31:37.892	  0:04.103	                       	SIP	Transaction remote address is udp$ekiga.net:5060
2010/10/12 14:31:37.892	  0:04.103	                       	SIP	Sending PDU (550 bytes) to: rem=udp$86.64.162.35:5060,local=udp$*:5060,if=10.10.20.12%eth0
SUBSCRIBE sip:500@ekiga.net SIP/2.0

CSeq: 2 SUBSCRIBE

Via: SIP/2.0/UDP 173.198.4.114:5060;branch=z9hG4bKd8db80c3-b5d4-df11-9ee1-0025648c054d;rport

User-Agent: Ekiga/3.2.6

From: "ryan" <sip:ryan@173.198.4.114>;tag=0aa080c3-b5d4-df11-9ee1-0025648c054d

Call-ID: 48923ec1-b5d4-df11-9ee1-0025648c054d@ryan-lin

To: <sip:500@ekiga.net>

Contact: <sip:ryan@173.198.4.114>

Accept: application/pidf+xml

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,SUBSCRIBE,NOTIFY,REFER,MESSAGE,INFO,PING

Expires: 300

Event: presence

Content-Length: 0

Max-Forwards: 70




2010/10/12 14:31:37.893	  0:04.103	                       	SIP	PDU Write failed: No such file or directory
2010/10/12 14:31:37.893	  0:04.103	                       	OpalUDP	Setting interface to 10.10.20.12%eth0
2010/10/12 14:31:37.893	  0:04.104	                       	SIP	Set state Terminated_TransportError for SUBSCRIBE transaction id=z9hG4bKd8db80c3-b5d4-df11-9ee1-0025648c054d
2010/10/12 14:31:37.893	  0:04.104	                       	SIP	Did not start transaction on udp$86.64.162.35:5060<if=udp$*:5060>
2010/10/12 14:31:37.893	  0:04.104	                       	OpalUDP	Writing to interface 1 - "172.16.104.1%vmnet1"
2010/10/12 14:31:37.894	  0:04.104	                       	OpalMan	Listener interfaces: associated transport=None
    udp$10.10.20.12:5060,udp$172.16.104.1:5060,udp$172.16.45.1:5060

```

EDIT:
I am running Ubuntu 10.04 and have the same results from both the Ubuntu Ekiga package and the Ekiga + LibOpal+NAT patch obtained from Yannek's PPA at [http://ppa.launchpad.net/sevmek/ppa/ubuntu](http://ppa.launchpad.net/sevmek/ppa/ubuntu)

---

### Post by whittylp on 2010-12-26
Yep, same problem here - running 10.04 also.  Get that error and fail to register for ekiga.net and a local VOIP provider.  I don't have anything to add other than "you're not the only one".

I'm updating to 10.10 in a mo, so I'll let you know if anything improves with that.

---

### Post by purecharger on 2010-12-26
FWIW, I gave up on Ekiga and have been using Blink with great results.

---

