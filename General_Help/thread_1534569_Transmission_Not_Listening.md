---
title: "Transmission Not Listening"
date: 2010-07-19
forum: General Help
---

### Post by jessemillar on 2010-07-19
I'm trying to set up a web server for a friend.  I got Apache working fine, but I can't seem to get Transmission or Webmin to work.  Both are installed and running, but netstat claims they're not listening on their ports which means I can't get to the web interfaces.  Is there a firewall I need to fiddle with or some way to open ports?

---

### Post by bodhi.zazen on 2010-07-19
With transmission you need to enable the web interface.

[http://www.associatedcontent.com/article/1166282/control_your_bittorrent_downloads_remotely.html](http://www.associatedcontent.com/article/1166282/control_your_bittorrent_downloads_remotely.html)

With Webmin, see : [Detailed Debian + Webmin  (web based graphical interface) guide, with screen shots]("http://woodel.com/")

The firewall in Linux is iptables and by default is permissive.

You may need to forward ports from your router.

---

### Post by jessemillar on 2010-07-20
I'm trying to install Transmission on a headless server.  You don't enable the web interface in that case, it should just run when transmission-daemon starts.

I read through that Debian tutorial.  I couldn't find anything about port issues with Webmin though.  I've already installed Webmin in exactly the way mentioned on that site.

I just don't get it.  Apache is working and I can serve web files with no problem, but the server refuses to do anything when I navigate to [https://my_server_ip:10000/](https://my_server_ip:10000/) (for Webmin) or [http://my_server_ip:9091/](http://my_server_ip:9091/) (for Transmission).

**Edit**: It should be noted that SFTP works fine through port 20 with the help of an FTP client.  Also, Transmission and (to the best of my knowledge) Webmin are running with root privileges.

---

