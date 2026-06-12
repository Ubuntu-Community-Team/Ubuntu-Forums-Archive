---
title: "VSFTPD and ports"
date: 2010-10-29
forum: General Help
---

### Post by malcmail on 2010-10-29
A fairly simple one I hope. Got VSFTPD up and running on my server. Purely there as my parents PC gave up and I've recovered the drive and stuck the info on my server for the moment. The idea being they can FTP in and grab the files they need. Who knows if they buy a new PC I've a new drive :).

Anyway I can get it to work fine on port 21 but clearly the world and his wife keep trying to hit it when I forward that port on my router to my server. I've tried forwarding another port, lets call it 11000, to port 21 via the router but when I log in the ftp client tells me it is running in passive mode, says getting directory contents then the connection closes.  It doesnt seem to matter what port I use other than 21. I've also tried forwardnig 11000 to 11000 and changing the port the server listens to. Same problem.

Any ideas gratefully received.

And no it isnt using TLS/SSL - mainly as I suspect my parents will use a web browser to grab the info (even worse on PC than me, if you can believe that!)

---

