---
title: "Assistance with Citrix ICA Client"
date: 2012-02-11
forum: General Help
---

### Post by latinlightning on 2012-02-11
Hello,

I am using Citrix to access some of my school folders. I can successfully log into Citrix and I see the Windows Explorer folder to connect to my folders but when I click on it I immediately receive an error message from the Citrix Receiver: 

"SSL Error. Contact your help desk with the following information: You have not chosen to trust the "AddTrust External CA Root" the issuer of the server's security certificate (SSL error 61).

Upon doing some lurking on the web, I found people having similar issues with that "SSL error 61." This link [http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex) has a pretty easy way to fix that problem but I don't see the ICAClient under the /usr/lib directory.

I installed the ICA Client from here [http://www.citrix.com/site/SS/downloads/details.asp?downloadId=2316611&productId=1689163#top](http://www.citrix.com/site/SS/downloads/details.asp?downloadId=2316611&productId=1689163#top) which is the latest one.

I'm on Ubuntu 11.04 and running Firefox 10.0. After checking the certificates in FF that particular CA (AddTrust) IS in there so I'm out of ideas here . . . .

Any help is appreciated.

---

### Post by latinlightning on 2012-02-12
Anyone, please? 

I don't live too far from campus but it would be nice to be able to do my work from home and not have to boot into my Windows machine.

---

### Post by Toz on 2012-02-12
> **latinlightning said:**
> has a pretty easy way to fix that problem but I don't see the ICAClient under the /usr/lib directory.

I installed the ICA Client from here [http://www.citrix.com/site/SS/downloads/details.asp?downloadId=2316611&productId=1689163#top](http://www.citrix.com/site/SS/downloads/details.asp?downloadId=2316611&productId=1689163#top) which is the latest one.

Which file did you install?
If you installed the .deb file as root, it installs the receiver to /opt/Citrix.

If you ran the install file from the .tar.gz as a regular user (like me), it installs into your home directory to ICAClient.

EDIT: Here is another link that might help. See post #4. [https://answers.launchpad.net/ubuntu/+question/124616]("https://answers.launchpad.net/ubuntu/+question/124616")

---

### Post by latinlightning on 2012-02-12
YES!!! Toz, thank you very much!

As a note, I did install the .deb as root and yes it is located under /opt/Citrix. I followed post #4 (to download the .crt) and post #6 to mv that certificate in the proper directory (in my case /opt/Citrix/ICAClient/keystore/cacerts) from that link you pointed me to.

Hope this helps someone since it seemed like most other threads concerning this were from some time ago :D

---

