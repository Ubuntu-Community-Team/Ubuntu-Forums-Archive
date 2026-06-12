---
title: "How to get MythWeb working with SabNZBd+ in Ubuntu 9.10"
date: 2009-10-30
forum: General Help
---

### Post by Maybelline on 2009-10-30
OK, maybe I'm the only one.  But, I run a MythTV backend that records and serves up TV shows to my whole house.

I also run SABnzbd+ on this machine, and like to use the [nzbStatus addon]("https://addons.mozilla.org/en-US/firefox/addon/7617?src=external-bountysource") for Firefox so that I can monitor (and add to) the daemon.

I wanted to get SAB working with MythTV (and more specifically, the MythWeb plugin).  The MythWeb plugin uses Apache, while SABnzbd uses CherryPy.  For reasons unknown to me, Apache takes priority (as I believe it should).  But, once MythWeb is up & available on my internal network, SABnzbd is no longer available on the network.  Here's how to fix that.  I'm assuming you know that when you modify system files (in /etc) that you'll have to use sudo and enter your password.

[SIZE="5"]First[/SIZE], we need to set SABnzbd to use something we can find.  I set my ~/.sabnzbd/sabnzbd.ini file to have
```
host=cybertron #(my home server hostname)
port=8080
```
You can also set this via the SABnzbd+ webpage from the actual server machine -- I was able to get to this page, even when Apache2 would not let external machines in.

[SIZE="5"]Second[/SIZE], I set my /etc/apache2/httpd.conf file (which was blank, previously) to be:
```
ServerName      Cybertron

<Location /sabnzbd>
order deny,allow
deny from all
allow from all
ProxyPass http://Cybertron:8080/sabnzbd
ProxyPassReverse http://Cybertron:8080/sabnzbd
</Location>
```
[SIZE="5"]Then[/SIZE], I created symlinks to my proxy modules:
```
cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/proxy.conf ./
sudo ln -s ../mods-available/proxy.load ./
sudo ln -s ../mods-available/proxy_connect.load ./
sudo ln -s ../mods-available/proxy_http.load ./
```
[SIZE="5"]Finally[/SIZE], just restart SAB and Apache.
```
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/sabnzbdplus restart
```

Now, you should be able to access your MythWeb at [http://YourServer/MythWeb/](http://YourServer/MythWeb/) and your SABnzbd+ at [http://YourServer/sabnzbd/](http://YourServer/sabnzbd/)

I hope this helps someone.  At the minimum, I hope it pops up in Google for the next time I upgrade my home server! :D

---

