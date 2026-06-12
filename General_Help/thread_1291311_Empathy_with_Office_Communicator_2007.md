---
title: "Empathy with Office Communicator 2007"
date: 2009-10-14
forum: General Help
---

### Post by snaga on 2009-10-14
I have recently been able to get Pidgin to use my MS Office Communicator 2007 account. It seems to do IM well enough, but no audio/video. No huge loss for me.

I would like to get Empathy to work instead, but it doesn't at this point. The SIP protocol it uses doesn't support TLS, which is why I am assuming it doesn't work with OCS 2007.

Is anyone using Empathy with OCS 2007? If so, I would appreciate a howto.

---

### Post by markhirota on 2009-10-19
I also an very interested in getting Empathy to work with Communicator 2007 -- but I'm also interested in how to get Pidgin working if Empathy solution doesn't yet exist...

---

### Post by snaga on 2009-10-19
If you install the pidgin-sipe package, you should be able to connect to Comm 2007.

---

### Post by Payteer on 2010-03-09
You can do the pidgin Sipe plugin, but this is just for IM, no A/V or for conference documents working etc.  Can anyone help on this.  Also the current Office Communicator 2007 is in port 443.
Any joy on this, someone must have an answer?

---

### Post by Another Monkey on 2010-03-31
I have been trying to find an answer as well.  I am forced to use Office Communicator and it does not work very well under virtualisation.

---

### Post by Payteer on 2010-04-13
Please, someone out there must be able to help on this.

---

### Post by rossouwap on 2010-04-14
Hi - I too am in a situation where the office uses OCS and I don't run a Windows laptop.

According to the SIPE project site: 
"The SIP/SIMPLE is an open protocol with a documented specification. The  Microsoft Live Communication Server (LCS)[]("http://www.microsoft.com/office/livecomm/prodinfo/default.mspx") has support very similar the  Sip/Simple protocol (indeed is based 100% on it), but  it has non  standard especifications classical for a MSN product, is an extend  version SIP." You can read more at [http://sipe.sourceforge.net/]("http://sipe.sourceforge.net/history/")

If anybody has any information on whether either Pidgin or Empathy will start supporting voice/video, please share :) .

Andre

---

### Post by huygens on 2010-04-16
We use Office Communicator 2007 here at work. And I manage to use it with both Pidgin and Empathy (though I'm using Ubuntu 10.4 Lucid Beta 2)

Here is how to configure the SIPE account in Empathy:
[LIST]
[*]Account: the username for communicator (at my company it is my e-mail)
[*]Password: obvious ;-)
[*]Server: it seems required to give the server with Empathy (whereas Pidgin Sipe since 1.7 autodetects it). Ask your administrator, or use Communicator and check the network (using Wireshark for instance) to see which server it connects to.
[*]Transport: auto works for me
[*]SSO: I had to check this one
[*]Email: as this is the same as my username, I left it blank
[*]Email login: here I had to put my SSO login (in the form of domain\domainlogin)
[*]Email password: as it is the same for the domain and Communicator, I left it blank
[/LIST]

The other fields, I left them blank or unchecked.

---

### Post by huygens on 2010-04-26
Actually, I have found a problem with a vanilla install of Ubuntu Lucid.  There is sporadic deconnection every minute of the SIPE client using  Empathy.
Ubuntu Lucid comes with pidgin-sipe plug-in in release 1.8 which does  not seem to please much Empathy (though it works fine with Pidgin). Side  note: it is not necessary to install pidgin; you can simply and only  install pidgin-sipe. Empathy can use some of Pidgin's libpurple  compatible plug-ins.

So, I have updated my pidgin-sipe to 1.10 and it is working perfectly  with Empathy.

To upgrade it to 1.10, you can use the following PPA:  [https://launchpad.net/~aavelar/+archive/ppa]("https://launchpad.net/%7Eaavelar/+archive/ppa")
Though, it is only for Jaunty and Karmic, you can use the Karmic release  on Lucid. After you have install the PPA in Lucid, just change "lucid"  to "karmic" for this PPA.

Then you can follow my previous post recommendations.

---

### Post by jimmij01 on 2010-04-27
Can someone tell me what I might be doing wrong? pidgin-sipe works perfectly in pidgin. However, I cannot get empathy to succesfully log in to an OCS server. It just spins "Connecting..." Packet trace says TLS/SSL has completed, but after that nothing. I've tried multiple combinations of SSO, Kerberos, SSL, auto, etc. without any luck. I've tried to login with [email]username@domain.tld[/email], domain\username, [email]username@domain.tld[/email],username, etc. Nothing seems to work.

I upgraded to the 1.10 package from the PPA, but that hasn't helped.

---

### Post by huygens on 2010-04-28
Hi jimmij01

have you tried to put the server hostname in the settings? If yes, have you tried to remove it (leave the field blank)?
Also, have you try to put something different for the transport setting? You should maybe try TCP instead of auto.

Here is what I use

[LIST]
[*]Account: [email]email_username@company.tld[/email]
[*]Password: mypasswd
[*]Server: it seems required to give the server with Empathy (whereas  Pidgin Sipe since 1.7 autodetects it). Ask your administrator, or use  Communicator and check the network (using Wireshark for instance) to see  which server it connects to.
[*]Transport: auto works for me, but you could try TCP
[*]KRB: unchecked
[*]SSO: I had to check this one
[*]Email: as this is the same as my username, I left it blank but you could repeat it
[*]Email login: here I had to put my SSO login (in the form of  domain\domainlogin) but you could use email_username or your Email login
[*]Email password: as it is the same for the domain and Communicator, I  left it blank but you could repeat it
[/LIST]
I hope this help.

---

### Post by jimmij01 on 2010-04-28
I believe my issue may be with SSL. OCS here is only using SSL(no TCP, UDP). Wireshark shows the SSL negotiation and then the communications just stop.

Anyone know if there should be issues with SSL and pidgin-sipe, telepathy?

---

### Post by huygens on 2010-04-30
We are using the TLS transport here, and there is no issue as far as I'm concern about it using telepathy, pidgin-sipe and OCS 2007.
To force TLS, you just put tls as the transport mean.
I'm not sure exactly how TLS and SSL are related...

---

### Post by bbrand on 2010-05-03
I could not get SIPE to work in Empathy. I installed Pidgin and it worked like a charm. 

Next step: remove Empathy, obviously a bad choice to include this as the default. Just looking at the number of cool plugins for Pidgin makes me wonder why Empathy was chosen in the first place:

My take: If you need Office Communicator: Install Pidgin, get the latest version of that plugin for sipe (see previous posts on how to, thanks for that!!)

---

### Post by spintel on 2010-05-06
> **huygens said:**
> We use Office Communicator 2007 here at work. And I manage to use it with both Pidgin and Empathy (though I'm using Ubuntu 10.4 Lucid Beta 2)

Here is how to configure the SIPE account in Empathy:
[LIST]
[*]Account: the username for communicator (at my company it is my e-mail)
[*]Password: obvious ;-)
[*]Server: it seems required to give the server with Empathy (whereas Pidgin Sipe since 1.7 autodetects it). Ask your administrator, or use Communicator and check the network (using Wireshark for instance) to see which server it connects to.
[*]Transport: auto works for me
[*]SSO: I had to check this one
[*]Email: as this is the same as my username, I left it blank
[*]Email login: here I had to put my SSO login (in the form of domain\domainlogin)
[*]Email password: as it is the same for the domain and Communicator, I left it blank
[/LIST]

The other fields, I left them blank or unchecked.

You have been able to get pidgin to work with audio/video?  I was able to get into my Office Communicator but all I can do is IM, no audio/video

---

### Post by huygens on 2010-05-08
I haven't tried using this feature (audio/video). I have no clue if it is working.

---

### Post by Kango_V on 2010-05-27
Has anyone got this working yet?

---

### Post by rossouwap on 2010-06-10
I've checked with the admins at our company - they are using a SSL certificate from the local Active Directory CA. Empathy doesn't let me (as far as I know) import the certificate.
Pidgin does work for me here - and I can see the certificate if I go to Tools -> Certificates.

If anybody knows how to import certificates so that Empathy can use them... that would be great.

---

### Post by rossouwap on 2010-06-10
Ok - I got empathy to work with the Office Communicator Server at our office. I had to get the root certificate for our organisation from a Windows machine, convert it to .pem and copy it to /etc/ssl/certs

Empathy is configured so: 
Account: emailaddress,domain\username
Password: password
Advanced - 
Server: nothing
Transport: auto
Useragent: nothing
Krb5: unchecked
Sso: checked
Calendar: EXCH
Email Url: nothing
Email: nothing
Email Login: nothing
Email Password: nothing

I don't see any advantage to using Empathy over Pidgin for OCS yet - no voice and no free/busy information. Granted there is no voice using Pidgin, but there is free/busy information from the IM client, which I've gotten used to. 
On the whole, it is easier for me to continue using Pidgin for OCS and Empathy for my other IM services. Pidgin seems to handle the comms from OCS a little more gracefully.

Now that I know how to get Empathy to talk to OCS, I'll park it and wait for voice...

---

### Post by cefn on 2010-07-05
> **huygens said:**
>  

it is not necessary to install pidgin; you can simply and only  install pidgin-sipe. Empathy can use some of Pidgin's libpurple  compatible plug-ins.

So, I have updated my pidgin-sipe to 1.10 and it is working perfectly  with Empathy.



I'd like to follow your recommendation, but there's no information on how to begin configuring a SIPE account in Empathy.

In my version of Empathy (2.28.1.1 on Karmic) there is no SIPE or Office Communicator, or Microsoft LCS protocol available in the new accounts list even with pidgin-sipe 1.10.0.1-ubuntu1 installed from the aavelar repo.

Once the account config screen is up for a SIPE account, I can try to follow your instructions. Any idea how I can get there if SIPE is not listed.

---

### Post by huygens on 2010-07-12
Hi Cefn,

Sorry for the late reply.
The package pidgin-sipe install the protocol for Pidgin. This protocol uses a special "purple" interface which is an underlying layer of Pidgin (technically speaking).
Empathy can be made compatible with this purple interface and can then use pidgin protocols. You need to install this package (it was install on my system, I thought it was default): telepathy-haze

Cheers,

---

### Post by MBybee on 2010-07-13
> **rossouwap said:**
> Ok - I got empathy to work with the Office Communicator Server at our office. I had to get the root certificate for our organisation from a Windows machine, convert it to .pem and copy it to /etc/ssl/certs

Empathy is configured so: 
Account: emailaddress,domain\username
Password: password
Advanced - 
Server: nothing
Transport: auto
Useragent: nothing
Krb5: unchecked
Sso: checked
Calendar: EXCH
Email Url: nothing
Email: nothing
Email Login: nothing
Email Password: nothing

I don't see any advantage to using Empathy over Pidgin for OCS yet - no voice and no free/busy information. Granted there is no voice using Pidgin, but there is free/busy information from the IM client, which I've gotten used to. 
On the whole, it is easier for me to continue using Pidgin for OCS and Empathy for my other IM services. Pidgin seems to handle the comms from OCS a little more gracefully.

Now that I know how to get Empathy to talk to OCS, I'll park it and wait for voice...


This worked perfectly for me, with Empathy on 10.04
Thanks! I was going nuts on this.

---

### Post by mangloid on 2010-10-13
bump to mention that this post got me up and running with OCS with 10.10 and sipe plugin with empathy.

---

### Post by Another Monkey on 2010-10-19
> **mangloid said:**
> bump to mention that this post got me up and running with OCS with 10.10 and sipe plugin with empathy.

What do you mean by "running"?  Did voice and video work?  Without audio and video (desktop sharing etc), there is no alternative to OCS.  :(

Forgot one: telephony.  I think I'm going to be stuck having to run Windows ](*,)

---

### Post by Another Monkey on 2010-10-20
Well, I've been trying to get Empathy working for about 24 hours now and failing miserably.
1) It won't connect to MSN (but Pidgin can)
2a) On 10.10 Empathy will allow me to start an Audio or Video Call over Sipe, but "telepathy-haze" seems to suffer a segfault and then reconnects
2b) On 10.04 it does not permit Audio or Video Calls
3) On 10.10, "Share My Desktop" is not enabled.

My conclusion at the moment is is
1) Empathy does not work over SIPE; or
2) I am too stupid to use Linux and should got back to Windows.
:(

---

### Post by huygens on 2010-10-21
> **Another Monkey said:**
> My conclusion at the moment is is
1) Empathy does not work over SIPE; or
2) I am too stupid to use Linux and should got back to Windows.

I disagree with you on point 2. You probably not stupid at all ;-)
I don't use the audio/video functionality of Communicator at my work, therefore I was considering that it was working for me: I can chat.
But you're right Empathy lack proper audio/video support in general. On my experience it often crash (e.g. jabber) or does not work at all (e.g. sipe) when it comes to audio.

Have you try installing Office Communicator in Wine?

Anyway, I do use video sometimes with friends. But then, I either use Skype or Gmail (the web interface). Those are working alternatives to do a video-call.

---

### Post by Another Monkey on 2010-10-21
OCS does not work under WINE.

I would rather use Skype, Ekiga, Mumble or something; but OCS is mandated by my employer and I have to use it (for messaging, audio and video).  As I don't plan to have Windows at home any more (I want to get into Myth etc and don't want to pay for Windows7), I need to find a solution.

Using OCS in virtualised Windows is one answer, but it seems to kill the CPU for some reason.

---

### Post by Another Monkey on 2010-10-22
I am still fighting with this.

One problem I am having is that Empathy behaves differently on different boxes.
On this one it will not allow audio or video calls at all.  This box is 10.04 and Skype runs fine.
One another box (and a virtual image) that are both 10.10, it will allow audio and video calls but "telepathy-haze" immediately segfaults.  As Empathy does not generate any logs that I can find, I only discovered this segault by digging through kern.log.

I guess Empathy just doesn't work over SIPE yet.  Time to go and raise some bugs.

If anyone has got this working (I don't care what the client is, so long as it runs on Linux) then please let me know.  And by "working" I mean full audio, video, desktop sharing.

---

### Post by snaga on 2010-11-08
> **rossouwap said:**
> Ok - I got empathy to work with the Office Communicator Server at our office. I had to get the root certificate for our organisation from a Windows machine, convert it to .pem and copy it to /etc/ssl/certs



Could I get some pointers on where to find the root cert on a windows 7 machine?

---

### Post by Batmensch on 2011-06-14
I got it Empathy working with Office Communicator (v 2010, I believe, certainly we are using Exchange 2010).  I had to specify both an IP address for the server and that the Transport is tcp.

I haven't been able to try audio or video; I don't see anyone on my contact list yet who seem to have either capability.  I do have a webcam hooked up and it works with Skype.

---

### Post by ingramproductions on 2011-08-25
Here is a good step by step tutorial with pictures on how to install and configure Pidgin with an Office Communicator or Lync account:

**[http://itswapshop.com/content/add-lyncoffice-communicator-account-pidginubuntu]("http://itswapshop.com/content/add-lyncoffice-communicator-account-pidginubuntu")**

---

### Post by topet2k12001 on 2011-11-26
> **rossouwap said:**
> Ok - I got empathy to work with the Office Communicator Server at our office. I had to get the root certificate for our organisation from a Windows machine, convert it to .pem and copy it to /etc/ssl/certs

Empathy is configured so: 
Account: emailaddress,domain\username
Password: password
Advanced - 
Server: nothing
Transport: auto
Useragent: nothing
Krb5: unchecked
Sso: checked
Calendar: EXCH
Email Url: nothing
Email: nothing
Email Login: nothing
Email Password: nothing

I don't see any advantage to using Empathy over Pidgin for OCS yet - no voice and no free/busy information. Granted there is no voice using Pidgin, but there is free/busy information from the IM client, which I've gotten used to. 
On the whole, it is easier for me to continue using Pidgin for OCS and Empathy for my other IM services. Pidgin seems to handle the comms from OCS a little more gracefully.

Now that I know how to get Empathy to talk to OCS, I'll park it and wait for voice...

Just wanted to share:

Configuration in the quoted message worked for me in Ubuntu 10.04 though I didn't need to extract/acquire certificates from our organization.

In Ubuntu 11.10 the configuration above didn't work. What worked for me is:

[B]Account: (your email address)
Login: domain\username[/B]

etc. etc. (same settings for the rest)

In Ubuntu 10.04, my settings were as follows:

[B]Account: (your email address),domain\username
[/B]etc. etc. (same settings for the rest)

I think our organization uses Exchange Server 2003.

I didn't check for voice calling features since I don't use it in our organization. Anyway, hope this helps. :)

---

### Post by cosmoKenney on 2011-12-02
> **topet2k12001 said:**
> Just wanted to share:

Configuration in the quoted message worked for me in Ubuntu 10.04 though I didn't need to extract/acquire certificates from our organization.

In Ubuntu 11.10 the configuration above didn't work. What worked for me is:

[B]Account: (your email address)
Login: domain\username[/B]

etc. etc. (same settings for the rest)

In Ubuntu 10.04, my settings were as follows:

[B]Account: (your email address),domain\username
[/B]etc. etc. (same settings for the rest)

I think our organization uses Exchange Server 2003.

I didn't check for voice calling features since I don't use it in our organization. Anyway, hope this helps. :)
Post #32 FTW!

---

