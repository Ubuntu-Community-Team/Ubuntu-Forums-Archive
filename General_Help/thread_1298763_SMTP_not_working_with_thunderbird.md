---
title: "SMTP not working with thunderbird"
date: 2009-10-23
forum: General Help
---

### Post by JulesBl on 2009-10-23
Hi

Suddenly today Thunderbird has stopped sending email over smtp, I just, eventually get an error:

Sending of message failed.
Message could not be sent because connecting to SMPT server smtp.w34u.com failed. The server may be unavailable or is refusing SMTP connections etc. etc.

I can send using evolution.

I have removed and re-installed Thunderbird, no change.

This error has just started happeing today with no change to my system.

Getting the following with nc

nc -z -v smtp.w34u.com 25
DNS fwd/rev mismatch: [www.w34u.com](www.w34u.com) != jbweb-44245-001.dsvr.co.uk
[www.w34u.com](www.w34u.com) [212.69.197.118] 25 (smtp) open

so it does not look like a firewall problem.

Running 9.10 Jaunty

Jules

---

### Post by mike555 on 2009-10-23
you could try a different port .... although if another program is sending ok and is set to the same port I guess your isp isn't blocking port 25 ...

---

### Post by JulesBl on 2009-10-23
It is beginning to look like a dns problem, if Thunderbird checked less it would just send the thing and work.

---

