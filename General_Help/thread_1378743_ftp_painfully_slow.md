---
title: "ftp painfully slow"
date: 2010-01-11
forum: General Help
---

### Post by kpholmes on 2010-01-11
ftp from and from my home computers to 2 remote servers has become really slow over the past month. one of the remote servers i manage and the other one is taken care of by a hosting company, so im thinking the problem is residing on my end. it doesnt matter if im downloading 1 file or 10 files, they are all coming in at 9 kb/s which is really slow cause i have a 7 megabit connection. ive tried using multiple computers and still have the same problem

im using proftp for the ftp server and filezilla for the client

thanks!
kevin

---

### Post by kpholmes on 2010-01-26
anyone?

---

### Post by t4thfavor on 2010-01-26
Betting that if you have a consumer grade connection your provider has noticed your usage, and throttled FTP. Try it over SSH if possible and see if there are better results. also you could tunnel somewhere else and download a file.

Try another protocol such as http, or sftp. 

Providers are getting brave, mix it up a bit, and make them earn your money.

---

### Post by lisati on 2010-01-26
Another thought: how does your "upload" speed compare to your "download" speed? [www.speedtest.net](www.speedtest.net) might be able to provide some insight.

---

### Post by shields on 2010-03-30
Kevin -- did you ever solve this? 

I am forced to do my FTPing on a Windows machine until I resolve this. It's not my ISP. It's only happening with one PC on the network -- the Linux box using Filezilla.

---

