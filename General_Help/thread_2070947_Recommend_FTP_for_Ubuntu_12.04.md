---
title: "Recommend FTP for Ubuntu 12.04"
date: 2012-10-14
forum: General Help
---

### Post by pbryd on 2012-10-14
I have an Ubuntu 12.04 box at home.

I'd like to be able to connect to it via FTP and drop in NZB files, where SABNZBD will then pick them up.

I've tried vsFTPd but can't connect to it from my local network because of iptables.

The only way I can connect is to flush the iptables.

I've tried to solve this [here]("http://ubuntuforums.org/showthread.php?t=2068591") and [here]("http://www.linuxquestions.org/questions/linux-networking-3/timing-out-when-using-filezilla-to-connect-to-vsftpd-4175431724/")

Can anyone recommend a FTP program that is more suitable.

P

---

### Post by Lars Noodén on 2012-10-14
You might consider leaving FTP behind and using SFTP instead.  That only needs one port, 22, open to work.

[list]
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

---

