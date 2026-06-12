---
title: "vsftpd v2.3.5 &amp; Ubuntu 12.04 problems"
date: 2012-09-21
forum: General Help
---

### Post by Mad Professor on 2012-09-21
Good Day All.
 
I am a linux newbe and I am looking for help and advice with regards to getting vsftpd v2.3.5 & Ubuntu 12.04 server x64 working.
 
I have my own home server, that I use for CCTV Recording, Web site hosting, and media streaming.
 
I have just upgraded the server and done a clean install of, Ubuntu 12.04 Server x64, EHCP v0.30.9, ZoneMinder v1.25.0, and MediaTomb.
 
But I am now having grate problems getting FTP working on my server.
 
On my windows PC I am using FlashFXP as the FTP client, but each time I try and connect to my server I get the following.

> FlashFXP 4.2.5 (build 1813)
 Support Forums [http://forum.flashfxp.com](http://forum.flashfxp.com)
 Winsock 2.2 -- OpenSSL 1.0.1c 10 May 2012
 [R] Connecting to xxx.xxx.xxx.xxx -> IP=xxx.xxx.xxx.xxx PORT=21
 [R] Connected to xxx.xxx.xxx.xxx
 [R] 220 Welcome to vsFTPd Server, managed by EHCP (Easy Hosting Control Panel, [www.ehcp.net](www.ehcp.net) )
 [R] USER TestUser1
 [R] 331 Please specify the password.
 [R] PASS (hidden)
 [R] libgcc_s.so.1 must be installed for pthread_cancel to work
 [R] Connection failed (Connection closed by server)
 [R] Delaying for 120 seconds before reconnect attempt #1
 [R] Retry attempt Aborted

So as I am having problems I downloaded and installed VirtualBox on my windows PC.
 
I then installed Ubuntu 12.04 Server x64, vsftpd was not installed within the install, so I then installed EHCP v0.30.9, now I have vsftpd v2.3.5 installed, but once again get the same error as above.
 
I then installed Ubuntu 11.10 Server x64, once again vsftpd was not installed within the install, so I then installed EHCP v0.30.9, this now installs vsftpd v2.3.2, and FTP works fine.
 
So can someone please advice this linux newbe on how to get vsftpd v2.3.5 working on Ubuntu 12.04 Server x64.
 
Thanks for your time. 
 
 Best Regards.

---

### Post by Wim Sturkenboom on 2012-09-21
I guess there is a vsftp server in the repositories; to prevent dependency issues (like you seem to have), that would be my choice.

I'm not on a 12.04 system at the moment.

---

### Post by Wim Sturkenboom on 2012-09-21
Just checked; vsftpd 2.3.5 is in the repositories.

---

