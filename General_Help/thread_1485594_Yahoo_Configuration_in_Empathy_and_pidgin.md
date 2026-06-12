---
title: "Yahoo Configuration in Empathy and pidgin"
date: 2010-05-17
forum: General Help
---

### Post by sowjendra on 2010-05-17
Hi All,

I am not able to connect to yahoo server from empathy and pidgin. I am using Ubuntu 10.04. I tried all the available options which are available in the net. So please help me.

Regards
Surendra M

---

### Post by nischalinn on 2010-05-17
I have the same problem with Ubuntu 9.04 and Ubuntu 9.10. But after installing Ubuntu 10.04, I've no problem with pidgin but have logging in problem with **empathy**.

try the command [B]sudo apt-get purge pidgin
[/B]and reinstall it. I think it may help you.

---

### Post by oaksterdam on 2010-05-17
nischalinn: i've already tried this (karmic 64 bit, pidgin 2.6.6) to no success.  pidgin is working fine with AIM & Jabber accounts, but not yahoo.  Also the problem is not yahoo, as I'm able to login to the browser-based IM page (webmessenger.yahoo.com).

periodically, yahoo changes some login config and access is lost.  eventually someone figures out how to modify their account so it works; i'm waiting on that post.

also, pidgin 2.7.0 claims to resolve this, but a.) there is no deb package yet for ubuntu and b.) i couldn't install from source due to unresolvable dependency issues so i have no way to confirm or deny that 2.7 works.

---

### Post by oaksterdam on 2010-05-17
it is possible that the problem occurs when you have contacts who you have blocked or have set so that you always appear offline to them.  i read something brief (lost the link) on a blog that stated something along these lines.

using the browser interface, i removed an "always offline" contact and restarted pidgin, then re-enabled the Yahoo account.  it seems to work now.

---

### Post by cryptotheslow on 2010-05-17
Using Pidgin 2.6.2 on Karmic 32-bit from the usual repos here and all is well.

---

### Post by sowjendra on 2010-05-18
Hi all,

I am able to login to yahoo messenger through Kopete. Server settings are set to default, so i tried to find out to which server i have been connected  using netstat command. from there I came to know that the system is connected to following servers

First time when i have logged.
cs113.msg.ac4.yahoo.com:mmcc and cs111.msg.ac4.yahoo.com:daytime

Second time when i have logged
yts1.ab.vip.re3.yahoo.com:www , cs114.msg.sp1.yahoo.com:mmcc and rdis.msg.vip.ac4.yahoo.com:www

I have checked the ports in /etc/services, from there i came to know

mmcc - 5050
daytime - 13
www - 80

same settings when i try to configure through pidgin and empathy i am not able to connect. when i use 80 port with the above servers it says like it is connecting in empathy.. but no luck.

still in trace of connecting yahoo in pidgin and empathy.

Regards
Surendra M

---

### Post by yerong on 2010-06-26
I have the same problem, cannot connect to yahoo after upgrade my pidgin to 2.7.1. Now i cant even connect to yahoo with empathy...

---

### Post by Harpoon on 2010-06-29
> **yerong said:**
> I have the same problem, cannot connect to yahoo after upgrade my pidgin to 2.7.1. Now i cant even connect to yahoo with empathy...

Ditto, here.  Empathy did work after the initial install, but adding Pidgin 2.7 caused everything to break (except for the messenger app in yahoo mail).
Purged Pidgin; purged Empathy; reinstalled empathy from scratch, but no luck.  Seems I need to reinstall the OS (Lucid)?

---

