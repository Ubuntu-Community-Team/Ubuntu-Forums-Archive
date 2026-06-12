---
title: "Evolution"
date: 2010-08-19
forum: General Help
---

### Post by TNT1 on 2010-08-19
So suddenly, I can't send meeting requests from evolution... Connected  to a hosted exchange 2007 platform, I can send and receive mails just  fine, I send a new meeting, and I get this:
Delivery has failed to these recipients or distribution lists:

------------------
Your message wasn't delivered because of security policies. Microsoft  Exchange will not try to redeliver this message for you. Please provide  the following diagnostic text to your system administrator.


Sent by Microsoft Exchange Server 2007 







Diagnostic information for administrators:

Generating server: vbexhub01.VBHMC.local

xxxxxx.xxxxxx@xxxxxx
#550 5.7.1 Delivery not authorized, message refused ##

Original message headers:

Received: from [192.168.101.xxx] (66.8.102.xxx) by vbexhub01.vbhmc.local
 (172.20.2.76) with Microsoft SMTP Server id 8.2.x.x; Thu, 19 Aug 2010
 10:02:02 +0200
Subject: Cape Town Installation
From: xxxxx xxxxx<xxxxxx.xxxxxx@xxxxxx>
Reply-To: xxxxxx.xxxxxx@xxxxxx
To: xxxxx xxxxx<xxxxxx.xxxxxx@xxxxxx>
Content-Type: text/calendar; name="calendar.ics"; charset="utf-8";
    method=REQUEST
Organization: Xxxxxx
Date: Thu, 19 Aug 2010 10:01:57 +0200
Message-ID: <1282204917.x.5.camel@Asterix>
MIME-Version: 1.0
X-Mailer: Evolution 2.28.3 
Content-Transfer-Encoding: 7bit
Return-Path: xxxxxx.xxxxxx@xxxxxx


Any ideas?

I got this a few times from people I have sent meetings to in the past...

(I did post this elsewhere, but no response, and i desperate...)

---

### Post by TNT1 on 2010-08-20
Please, somebody must have a vague suggestion...

---

### Post by dcstar on 2010-08-20
> **TNT1 said:**
> So suddenly, I can't send meeting requests from evolution... Connected  to a hosted exchange 2007 platform, I can send and receive mails just  fine, I send a new meeting, and I get this:
Delivery has failed to these recipients or distribution lists:

------------------
Your message wasn't delivered because of security policies. Microsoft  Exchange will not try to redeliver this message for you. Please provide  the following diagnostic text to your system administrator.


Sent by Microsoft Exchange Server 2007 


Diagnostic information for** administrators**:

Generating server: vbexhub01.VBHMC.local

xxxxxx.xxxxxx@xxxxxx
**#550 5.7.1 Delivery not authorized, message refused ##**

............
Any ideas?

I got this a few times from people I have sent meetings to in the past...

(I did post this elsewhere, but no response, and i desperate...)

Ask your Exchange administrator.

---

### Post by TNT1 on 2010-08-21
Right, so after a day of testing, I am no closer. I did discover that from a windows machine I can setup my account in evolution for windows, and send meeting invites no problem.

---

### Post by borobudur on 2010-08-24
Calender doesn't work for me neither. I'm connected with MS exchange 2007 via MAPI and I just can check my mail :-(

Please tell us if you found out more..

---

### Post by TNT1 on 2010-08-25
I tried creating my account on several different machines running 10.04.1 and no luck... I can send and recieve mail, and calendar.ics messages, I can send a calendar.ics as an attachment in a regular mail, but creating a new meeting results in the rejection as per original post.

I did install 10.04.1 Kubuntu netbook release on a VM, create my account in Kontact, and then I can send meetings to external domains. Does Kontact use a format different to calendar.ics?

Using kontact.Tbird/whatever is not an option, for corporate reasons, I need to present inline pictures in my e-mail signature, only evolution does this satisfactorily enough in the Linux world as far as I can tell.

If anyone has any ideas, I'm open...

The admins of the Hosted Exchange platform have assisted, but are also out of ideas. I keep thinking it is a mail transport or mail flow rule on the HMC platform, but I need to prove what so I can ask them to test whatever change I propose.

---

### Post by TNT1 on 2010-09-11
Anyone?

---

