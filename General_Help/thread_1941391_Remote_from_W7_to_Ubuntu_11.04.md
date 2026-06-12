---
title: "Remote from W7 to Ubuntu 11.04"
date: 2012-03-15
forum: General Help
---

### Post by latinlightning on 2012-03-15
Hello,

I used to be able to remote into my computer which runs Ubuntu 11.04 from a Windows 7 machine using mstsc and I used the following article to do this [http://www.liberiangeek.net/2011/06/connect-to-ubuntu-11-04-from-windows-via-remote-desktop/](http://www.liberiangeek.net/2011/06/connect-to-ubuntu-11-04-from-windows-via-remote-desktop/)

Xrdp worked fine the first couple of days and then it just completely stopped working. I like the fact that I didn't have to install any type of client software on the W7 machine and only the server side on my Ubuntu install. I've googled up and down to find a solution as to why xrdp doesn't respond anymore but have found no successive resolution.

Is there a similar program that doesn't require me to download the client onto the W7 machine and ONLY run the server side on my Ubuntu machine?

---

### Post by BertN45 on 2012-03-15
Did you install samba on the Ubuntu machine to share the Ubuntu files with Win 7? if yes, that caused that problem in 11.04.

---

### Post by latinlightning on 2012-03-15
> **BertN45 said:**
> Did you install samba on the Ubuntu machine to share the Ubuntu files with Win 7? if yes, that caused that problem in 11.04.

Nope, never installed Samba.

---

### Post by BertN45 on 2012-03-15
Xrdp has sometimes a timing problem, if you supply the password in the remote desktop form. You could try removing the password from the form in the Windows machine and type the password at the moment it is requested. At least you can see in this way what goes wrong.

---

