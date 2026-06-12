---
title: "Ekiga configuration"
date: 2009-07-15
forum: General Help
---

### Post by mohxinn on 2009-07-15
I want to configure Ekiga for a connect2pk.com account. The settings are given on the page:

[http://www.connect2pk.com/settings.html](http://www.connect2pk.com/settings.html)

How can I configure these settings on Ekiga?

The screenshots shown the settings I have configured in Ekiga.

I get error "Could not register(Timeout)"

Ekgia version: 3.2
Linux distro: Ubuntu 9.04

Thanks in advance!

---

### Post by wojox on 2009-07-15
When did you register?

Have a look here:

[http://www.connect2pk.com/blog/2009/07/01/important-notice-for-all-connect2pk-users/](http://www.connect2pk.com/blog/2009/07/01/important-notice-for-all-connect2pk-users/)

---

### Post by mohxinn on 2009-07-15
I registered it quite a while ago. I want to use Ekiga as it is the default softphone for ubuntu. I just tried zoiper and it works. The only problem is that when zoiper is running, all other sounds are blocked. It seems to get a lock on the sound card.

I can't find any option to set domain in Ekgia :(

---

### Post by mohxinn on 2009-07-15
Anyone?

---

### Post by pooja on 2009-07-29
I want to configure Ekiga to work with FreeCall.com [ list of providers]("http://wiki.ekiga.org/index.php/List_of_PC_to_phone_providers")

In particular, I don't know how to fill in the "Create SIP Account" form, from [FONT="Courier New"]Edit-->Accounts[/FONT].

I'm attaching a couple of pictures so that you can understand my problem.

---

### Post by pooja on 2009-07-29
By the way what should I write to call another country?

sip:003902345689@sip.freecall.com ?

That is, do I have to write "00" before the country code?

---

### Post by pooja on 2009-08-07
Can anybody help me, please?

These are the setting for FreeCall.com, as published in their site:

 	SIP port : 5060
	Registrar : sip.voiparound.com
	Proxy server : sip.voiparound.com
	Outbound proxy server : leave empty
	Account name : your FreeCall username
	Password : your FreeCall password
	Display name/number : your FreeCall username or voipnumber
	Stunserver (option) : stun.voiparound.com

I have an account with FreeCall that works well under Windows XP and Vista, but just can't figure out how to make it work in Ubuntu 9.04.

Can anyone suggest any other VoIP softphone under Ubuntu?
Thank you.

---

### Post by pooja on 2009-08-09
I managed to solve the problem! Hurray!!

I downloaded and installed Linphone ([FONT="Courier New"]Applications > Add/Remove > Linphone[/FONT]) and set it to work with FreeCall.com.
Here's how I did it.

By the way these are the settings published by FreeCall.com on their website:

   SIP port : 5060
   Registrar : sip.voiparound.com
   Proxy server : sip.voiparound.com
   Outbound proxy server : leave empty
   Account name : your FreeCall username
   Password : your FreeCall password
   Display name/number : your FreeCall username or 

Open Linphone. Click on "Preferences" under the menu "GO".

_In the "Network" tab_ don't check the "Use IPv6 network if available" box; select the radio button of "Stun server" and write "stun.voiparound.com" in the blank space; leave the "RTP properties" section unchanged; check the "Use SIP INFO instead of RTP" (perhaps, you could just leave it as it is).

_In the Sound Device tab_ check the "Enable eco-canceler" box. The rest is all "ALSA" and microphone.

_In the SIP tab_ port 5060 is already written as default listening port. Under "Identity" section, un-check the "Automatically guess a valid hostname" so that you can write your sip domain in the box. Write like this: **username** @ **sip.voiparound.com**. The username is that of your FreeCall.com account.

_In the Codec tab_ don't change anything.

Press [FONT="Courier New"]Apply[/FONT] and then [FONT="Courier New"]OK[/FONT].

Now try calling your land phone number and see if it works. For example, in the "SIP Address" square box I wrote "sip:+390612345678@sip.voiparound.com" where "+39" is the country code, "06" is the city/area/province telephone code and "12345678" is the number you're trying to reach. Press "Call" button. A window pops open asking you for the password and userID of the sip.voiparound.com domain. Type in your FreeCall login details. Press OK. In a few minutes you should hear your phone ringing.

I've noticed Linphone is a little slow in receiving the "Hangup" command and the video can be improved but still, it's better than Ekiga. I think I'll save space by uninstalling Ekiga. Now I'll transfer all the contacts into Linphone's address book. 

Hope this helps others too.
Bye!

---

### Post by trungd_t on 2009-08-10
> **mohxinn said:**
> Anyone?

I noticed you only entered connect2pk.com in the registar. Try adding connect2pk.com:5065 in the registar box. All the rest should be the same. You may also want to add the user into the authentication user box.

Good luck.

---

