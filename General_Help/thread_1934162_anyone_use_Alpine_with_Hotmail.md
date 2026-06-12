---
title: "anyone use Alpine with Hotmail?"
date: 2012-03-01
forum: General Help
---

### Post by chickenPie4breakfast on 2012-03-01
I am trying to get it to check my hotmail acount with no luck so anyone managed?
if so what  are the pop3 settings?

---

### Post by NickoHall on 2012-03-01
Since MSN became Windows Live it dropped POP3 support. I know that you can't connect outlook on windows to a hotmail account unless you download a fix which allows outlook to connect through HTTP instead of POP3. Can you try and enter your email details as HTTP instead of POP3?

---

### Post by howefield on 2012-03-01
With @hotmail.co.uk address I am using pop3.live.com and smtp.live.com

---

### Post by chickenPie4breakfast on 2012-03-02
yes I know you can use pop3 as  another program I use has no problem getting mail from hotmail with pop3 but those same settings are not working with Alpine so I wondered if anyone has had success and what were the settings.

oh solved it - it was my Firewall that was blocking the incomming on port 995   I thought I had unblocked that port - note to me must learn more about firewalls!!
anyway for anyone else these settings work for me
inbox-path={pop3.live.com:995/novalidate-cert/user=misterx@hotmail.co.uk/pop3/ssl}inbox

---

