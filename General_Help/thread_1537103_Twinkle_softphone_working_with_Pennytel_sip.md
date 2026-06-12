---
title: "Twinkle softphone working with Pennytel sip"
date: 2010-07-23
forum: General Help
---

### Post by QBalls on 2010-07-23
I guess there are plenty of other nubes out there who might find this helpful.
I've been trying to get a softphone up n running using a 3fd party voip provider (pennytel) with little success, a mix of software/64bit incompatibilities until I installed Twinkle.
just had to forward a few ports on my modem. It's not perfect yet, as it gives an error when register request is made 
(fetching registrations failed: 400 Bad Request - 'Malformed/Missing Contact field')
BUT it is letting me make phone calls using my pennytel account.
So, below are the settings I've got working. Perhaps it'll help someone or perhaps someone might know why I get that error even though I am able to make calls

                                 **System Settings > Network tab**
 SIP port: = 5060
 RTP port: = 16384
 Max. SIP message size (UDP): = 65535
 Max. SIP message size (TCP): = 1000000
 

 **User Profile > User tab > SIP account**
 Your name: = me
 User name*: = your pennytel assigned user name (mine is all numeric)
 Domain*: = &#8220;sip.pennytel.com&#8221;
 Organisation: = blank
 

 

 **User Profile > User tab > SIP authentication**
 Realm: = sip.pennytel.com
 Authentication name: = same as user name above
 Password = private
 AKA OP: = 00000000000000000000000000000000
 AKA AMF: = 0000
 

 

 **User Profile > SIP server tab**
 Registrar: = pennytel.com




This is on Ubuntu10.04 Lucid running on a 64bit i7 with a gigabyte ex58-udp board

---

