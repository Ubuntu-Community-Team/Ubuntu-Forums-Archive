---
title: "NX Server Web Player"
date: 2011-11-23
forum: General Help
---

### Post by inhumangeek on 2011-11-23
Not sure if this is the best place for this enquiry.

I've got NX server up and running on my Ubuntu box. I can connect to the server from a client installed on my Windows XP laptop.

According to the nomachine documentation [here]("http://www.nomachine.com/web-player.php") and [here]("http://www.nomachine.com/documents-preview/server/install-linux.pdf") the built-in "Web Player" should allow me connect to my server using any browser by pointing it to [http://ipaddress:4080](http://ipaddress:4080). I would therefore not have to use the client software and it might work on my smartphone/tablet, which would be really handy.

The docs say a pre-requisite is Apache, which I have installed and is working. On my laptop I can see the welcome pageserver from Ubuntu just fine. 

However, when trying to access the Web Player I get (in Chrome) "This web page is not available". 

Has anyone got NX Web Player to work successfully and can help me get it up and running please? It's on the same network, I have no software firewall on my server.

Thanks.

---

### Post by inhumangeek on 2012-01-07
I found the answer in the end - the version with web player integrated hasn't actually been released fully yet.

---

### Post by Loan_Refi on 2012-12-13
Hi, so are you connecting via browser now such as [http://ipaddress:4080?](http://ipaddress:4080?) If you can you let me know how you got it working?

Thanks,

---

### Post by Ladderal on 2013-01-17
Depending which version of NX you are running, you may need to download, install and configure NX Web Player separately.

[http://www.nomachine.com/configuration.php]("http://www.nomachine.com/configuration.php")

---

### Post by Loan_Refi on 2013-01-17
Thanks for responding. I'm still working on getting this work. I'm now trying to set up the NX Web Companion instead. I'm getting this error once I navigate to my servers web address; 

[http://mywebserverIP.com/plugin/nxapplet.html](http://mywebserverIP.com/plugin/nxapplet.html)

I have the NX Server, Client & node installed and I followed these instructions to set up the "NX Web Companion";

[https://help.ubuntu.com/community/NX_Web_Companion](https://help.ubuntu.com/community/NX_Web_Companion)

The error I get using Google Chrome is this: 
The option to support Java applets may be disabled in your browser
or you haven't a suitable Java Plugin installed.

Click on button below to download 
the Java Plugin.

Or if I use Internet Explorer: "An add on for this website fail to run.

**About my server:**
My Ubuntu server version is: Ubuntu 12.04.1 LTS Percise i686

My Java version: 
java version "1.6.0_24"
OpenJDK Runtime Environment (IceTea6 1.11.5) (6b24-1.11.5-0ubuntu1~12.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

Any ideas on how to troubleshoot this issue are greatly appreciated. 

Thanks,

---

### Post by Loan_Refi on 2013-01-17
I would suspect this error has something to do with the Java version I have installed on the server. Don't you think?

---

