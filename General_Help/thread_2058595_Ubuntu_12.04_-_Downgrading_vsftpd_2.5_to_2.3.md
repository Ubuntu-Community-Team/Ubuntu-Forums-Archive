---
title: "Ubuntu 12.04 - Downgrading vsftpd 2.5 to 2.3"
date: 2012-09-16
forum: General Help
---

### Post by Mad Professor on 2012-09-16
Good day all.

I am looking for help and advice with regards to downgrading vsftpd 2.5 to 2.3 within Ubuntu 12.04.

I am trying to run Easy Hosting Control Panel (EHCP), but vsftpd 2.5 fails to work with Ubuntu 12.04 and EHCP 0.30.9.

On the EHCP site it says that you can downgrading vsftpd 2.5 to 2.3, and it will all work fine again.

Being a newbe to linux I am unsure of how to downgrading vsftpd 2.5 to 2.3

Can you please advice this newbe?

Thanks for your time. 
 
Best Regards.

---

### Post by jerrrys on 2012-09-16
12o4 has 2.3 installed by default.

[http://packages.ubuntu.com/precise/vsftpd](http://packages.ubuntu.com/precise/vsftpd)

---

### Post by Mad Professor on 2012-09-16
Thank you for your reply. 
 
I have been messing around with vsftpd, so I can't be 100% sure what version I started with, i.e if EHCP installs another version. 
 
But I have just run "vsftpd -v" and it does report back that I am now running version 2.3.5

Here is a link to the info on the ehcp site: [http://ehcp.net/?q=node/1257]("http://ehcp.net/?q=node/1257")

But I am still having grate problems getting FTP working.

Each time I try and connected to the server via an FTP client in my case FlashFXP, I get the following:

> 
FlashFXP 4.2.5 (build 1813)
Support Forums [http://forum.flashfxp.com](http://forum.flashfxp.com)
Winsock 2.2 -- OpenSSL 1.0.1c 10 May 2012
[R] Connecting to [www.xxxxxxxxxxxx.co.uk](www.xxxxxxxxxxxx.co.uk) -> DNS=www.xxxxxxxxxxxx.co.uk IP=xxx.xxx.xxx.xxx PORT=21
[R] Connected to [www.xxxxxxxxxxxx.co.uk](www.xxxxxxxxxxxx.co.uk)
[R] 220 Welcome to vsFTPd Server, managed by EHCP (Easy Hosting Control Panel, [www.ehcp.net](www.ehcp.net) )
[R] USER xxxxxxxxxxxx
[R] 331 Please specify the password.
[R] PASS (hidden)
[R] **libgcc_s.so.1 must be installed for pthread_cancel to work**
[R] Connection failed (Connection closed by server)
[R] Delaying for 120 seconds before reconnect attempt #1
[R] Retry attempt Aborted


Can you please advice.

Best Regards.

---

### Post by Mad Professor on 2012-09-23
I need to remove vsftpd v2.3.5 and install vsftpd v2.3.2

Can someone please advice me on how to install vsftpd v2.3.2?

Thanks for your time. 
 
Best Regards.

---

### Post by claracc on 2012-09-23
In my system, 12.04.01 the vsftpd available is 2.3.5-1

I don't think it would be a good idea to downgrade the package to a before release, I think you can find dependencies problems.

Any case, you can explore the possibility of using other version of the package through synaptic manager, you look for the package, select it and click on force version to see if you have other available version to install.

---

