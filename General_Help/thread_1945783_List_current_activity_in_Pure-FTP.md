---
title: "List current activity in Pure-FTP"
date: 2012-03-23
forum: General Help
---

### Post by MockY on 2012-03-23
when running pure-ftphwo, only the column headers are displayed. No connected users nor current transfers are listed. Docs say that pure-ftp has to be compiled with the --with-ftpwho flag for it to work, but I installed it from the repo. In other words, I did not compile it myself.
Is there a configuration file I can create for this to be enabled or do I simply have to remove it from the system and compile it from scratch? Pure-FTP is an awesome ftp server, but it would be nice to know what's currently going on as this server have quite some traffic going through it n a daily basis.

---

### Post by imachavel on 2012-03-23
pure-ftp isn't in the repository, you had to download it. Ok so here is my assumption because you need to provide more information. You are trying to ftp into a server, but not a web server because most web domain servers have ftp web interface compatibility, so my assumption is you set up a server, lan? Dhcp? Now does pure ftp work where the server uses recognizes the ftp port trying to connect, and the client computer you are on is trying to connect in through ftp and you downloaded and installed pure ftp?

remember ssh usually gives you the ability to ssh into a directory and ls what is in the directory, meaning you ssh man I believe it is, then enter user name and password but it'd be more like ssh man "username@urladdress" without the quotes

I've never used ftp man. But when using Linux created programs usually the site gives you several mirrors, if not the mirror will say it's alpha and needs to be compiled, or the auto install version. So I wouldn't know, please give me the link and I'll try and download and install it myself and see if I get the same problem, although I have no dhcp lan server set up, no vlan set up with any server or host, don't feel like checking my public i.p. address, and only have lamp back end server set up and am trying to learn local host a bit better, which should at the moment without an i.p. protocol information being received from a server computer, should only use two i.p. addresses, my own, as well as loop back (127.0.0.1)

reply if you are interested

---

### Post by MockY on 2012-03-23
> **imachavel said:**
> pure-ftp isn't in the repository, you had to download it. 
It most certainly is in the repo for 11.10. sudo apt-get install pure-ftpd installed it just fine. It's even available in the repos for 10.04, as I recently configured 5 VPS's earlier this week at MediaTemple. Come to think of it, neither of those installs lists current activities either, even though in those cases I had to compile it (as it has to be compiled with --without-capabilities). I did not add --with-ftpwho, so that would explain it however.

Also, none of your assumptions are correct. I have a publicly available server with pure-ftp installed and configured just fine. I use virtual users who are chrooted in their own directory. There are no issues what so ever for a client to connect with one of these accounts. However, the activities are only logged in the logfile and not displayed when using pureftp-who.
That leaves me to believe that it is not enabled when installing it from the repo which is why I wonder with there is a configuration file I can can create to tell pure-ftp to enable it on launch.

---

