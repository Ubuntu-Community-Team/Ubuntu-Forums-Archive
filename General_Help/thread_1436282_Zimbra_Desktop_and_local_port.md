---
title: "Zimbra Desktop and local port"
date: 2010-03-22
forum: General Help
---

### Post by e24ohm on 2010-03-22
Folks:
I am playing around with Zimbra, and I had a few questions for those individuals who have played with Zimbra.

Why does Zimbra Desktop listen to local port? I have install the application on Fedora and Windows, and a confirmation screens says the application will listen on local port xx33 something.

Thank you,
J

---

### Post by e24ohm on 2010-03-23
Folks:
Wanted to share what I have found out with Zimbra Desktop and Google Apps.

After working with Zimbra desktop and Google Apps, I discovered the follwoing ports need to be open: 1187, 1206, 1210, 1218, 1259.

I was not able to connect to Google Apps until I used Wireshark to see what ports were being hit - then I opened the ports on my firewall.

Just wanted to share.

Thanks,
J

---

