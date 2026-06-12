---
title: "OpenWengo Version 2"
date: 2006-05-19
forum: General Help
---

### Post by rcmn on 2006-05-19
I was wondering if someone is trying to built a package for the new version of Openwengo ?
I'm just very impatient to use it.
it look nice 

[http://wiki.wengo.com/index.php/WengoPhone_NG_quick_user_guide](http://wiki.wengo.com/index.php/WengoPhone_NG_quick_user_guide)

---

### Post by bailout on 2006-05-19
Hadn't realised it was out. Also hope it is packaged soon. Nice to see that they seem to be developing and releasing linux versions in tandem with the windows version.

---

### Post by rcmn on 2006-05-19
Actually i became so impatient and curious that i tried on my laptop where i have Xface and gnome.So i followed this instructions :
[http://openwengo.com/index.php/mp_download_wp_lin](http://openwengo.com/index.php/mp_download_wp_lin) 

and it worked right away and very nicely.

I was so impressed and reassured on the install (all library are in the tar file, so the tar files doesn't explode on u're machine and overwrite files of your system).
There is no need for any knowledge but decompress file and run executable from command line)...
I run to my workstation and tried it !!! 5 min later i was calling france and chat with my friend on yahoo/gmail/msn/icq...

I would say no need for package ^^ .work great for me.Hope it will be the same for everybody else.
It's a great beta. Good job Wengo dev!!!

---

### Post by Asad2k5 on 2006-05-20
rcmn,
"I run to my workstation and tried it !!! 5 min later i was calling france and chat with my friend on yahoo/gmail/msn/icq..."

How did you add the gmail, msn buddies ?

---

### Post by rcmn on 2006-05-20
[QUOTE=Asad2k5]rcmn,
How did you add the gmail, msn buddies ?[/QUOTE]

u add your msn account then you add your yahoo acc...etc.
And if it works for you like it did for me all my contact/buddies show up (i suppose retrieve automatically from msn/yahoo/etc...)

you have to click on the contact tab.make sure u're connected .The smiles smile when the connection is successfull.
To see the list of off line user just click on "contacts"==>"show/hide contacts offline"

---

### Post by Asad2k5 on 2006-05-21
Thanks, I have added MSN and Yahoo ok but gtalk doesnot seem to be connecting even though the buddies show but non show as online. I know that some are online because if i log in to gmail web i see them online but why not in wengo.

Will there will be audio/vedio for MSN,Yahoo or gtalk using wengo ?

---

### Post by daahli on 2006-05-21
Wengo 2.0 looks amazing, but I keep on getting a sip error. Any ideas?

(debug) 11:37:38 boolNetworkDiscovery::testSIPHTTPTunnel(conststd::string&,unsignedint,bool,conststd::string&,unsignedint): cannot create a tunnel to 165.254.145.160:443 for SIP server 213.91.9.210:5060 without  ssl
(debug) 11:37:38 boolNetworkDiscovery::testSIPHTTPTunnel(conststd::string&,unsignedint,bool,conststd::string&,unsignedint): proxy detected. Testing SIP tunnel connection
(debug) 11:37:39 boolNetworkDiscovery::testSIPHTTPTunnel(conststd::string&,unsignedint,bool,conststd::string&,unsignedint): cannot create a tunnel to 165.254.145.160:443 for SIP server 213.91.9.210:5060 with  ssl
(debug) 11:37:39 boolWengoAccount::discoverForSIP(): SIP cannot connect
(debug) 11:37:39 virtualboolWengoAccount::init(): error while discovering network for SIP

---

### Post by rcmn on 2006-05-21
are u behind a restricted firewall or proxy ?

---

### Post by daahli on 2006-05-21
Well I'm behind a college firewall, but I've never had problems with Skype, Twinklephone, Kiax, etc.

---

### Post by rcmn on 2006-05-22
Starting today i'm having problem with wengophone2 for some reason i cannot callout too.But i have no problem with the regular Wengo.
Wengophone 2 is still in Beta so maybe we should try to install the latest.

---

### Post by rcmn on 2006-05-22
Strangely it's ok again.Without doing anything...

---

### Post by daahli on 2006-05-22
[QUOTE=rcmn]Strangely it's ok again.Without doing anything...[/QUOTE]

Yeah, it's working for me now too. The service must simply have been down yesterday.

This new version is truly amazing!

---

### Post by Johnsie on 2006-07-26
I like the new Wengo a lot.... I think it looks nice but the fact that they seem to know a lot about audio/video is what makes me think this might be worth watching. Gaim is ok but I can't really see gaim competing with the new multimedia messengers that msn, yahoo and aol are rolling out.... I don't want to get left behind so my money is on Wengophone.

---

### Post by andlinux21 on 2006-07-26
Wengo is pretty cool is there a way to make it alphabatize the lists?

---

### Post by Cuppa-Chino on 2006-08-12
Stupid question maybe but how do I make a launcher to start openwengo? 

Do I have to write a script that performs the two commands or is there a way to just a have simple launcher do it?

```
cd wengophone-ng-binary-latest
LD_LIBRARY_PATH=. ./qtwengophone
```

Also anyone got a nice icon for it? or is it possible to "import" the windows icon

---

### Post by otacan on 2006-08-15
I tried to use this version but I had this error:
> 
(debug) 19:33:30 bool NetworkDiscovery::testHTTP(const std::string&, bool): cannot connect to ws.wengo.fr:443/softphone-sso/sso2.php with SSL
* About to connect() to ws.wengo.fr port 80
* Connection time-out
* Closing connection #0
* a timeout was reached
(debug) 19:33:40 bool NetworkDiscovery::testHTTP(const std::string&, bool): cannot connect to ws.wengo.fr:80/softphone-sso/sso2.php without SSL
(debug) 19:33:40 bool WengoAccount::discoverForSSO(): SSO cannot connect
(debug) 19:33:40 EnumSipLoginState::SipLoginState WengoAccount::discoverNetwork(): error while discovering network for SSO


I have both lib **libssl0.9.7** and **libssl0.9.8**
and I dont have any firewall or proxy

thanks for Help

---

