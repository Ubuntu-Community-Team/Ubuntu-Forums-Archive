---
title: "proftpd"
date: 2012-02-12
forum: General Help
---

### Post by ptmuldoon on 2012-02-12
I'm setting up proftpd, and had troubles the first time, thus I removed and re-installed the package.

However, I can not seem to connect to the server, and keep getting the following error when using Filezilla.  Unfortunately, the error message does seem to tell much as it connects but doesnt?

Any thoughts?

> 
Status:	Connecting to 192.168.11.45:21...
Status:	Connection established, waiting for welcome message...
Error:	Could not connect to server


---

### Post by josephmills on 2012-02-12
if you go to file-->sitemanager in filezilla 
then set up to be sftp and change port to 22 
change to normal log in ,change   username and password press connect . Can you connect?

---

### Post by ptmuldoon on 2012-02-12
I think I had a bad/corrupt config file.  After replace it with a default example, things starting working.   Just not sure what I did to mess up the config file.

---

