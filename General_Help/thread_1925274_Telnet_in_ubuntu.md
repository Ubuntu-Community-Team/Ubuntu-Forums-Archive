---
title: "Telnet in ubuntu"
date: 2012-02-14
forum: General Help
---

### Post by achuth on 2012-02-14
I have a server class machine.
I want to install some software in all the connected client computers.
Can I use telnet at the server for connecting to the individual clients and then install the softwares?

If it is not possible, how can I connect to the ubuntu clients for software installation while sitting at the server?

---

### Post by MG&amp;TL on 2012-02-14
Of course. Follow [this]("http://www.cyberciti.biz/faq/ubuntu-linux-enable-telnet-service/") guide to install a telnet server on the client machines, then you can simply:

```
telnet mymachineip
```

from your server.

However, telnet is extremely insecure, you should really use ssh instead.

---

### Post by perspectoff on 2012-02-14
Or use SSH, which is secure telnet.

---

### Post by Lars Noodén on 2012-02-14
Though mentioned several time, it's worth repeating that it is a good idea to use [SSH](https://en.wikibooks.org/wiki/OpenSSH/Overview) and avoid telnet.  You can get the SSH server as the package [openssh-server](apt://openssh-server) and it provides SSH and SFTP.  You can then connect to the server with SSH or your favorite SFTP client like Nautilus or FileZilla.

Here is some reading on FTP but it applies equally to Telnet.  The time to use telnet for remote logins passed some 15 years ago.

[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

[http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)

---

