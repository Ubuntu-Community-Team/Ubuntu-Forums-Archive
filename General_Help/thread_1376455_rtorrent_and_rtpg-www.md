---
title: "rtorrent and rtpg-www"
date: 2010-01-09
forum: General Help
---

### Post by dpg77 on 2010-01-09
have setup new ubuntu server install with rtorrent and rtpg-www (all from standard repo's) on ubuntu 9.10 server.
just want to know how to access webinterface on it.
cannot find any info anywhere on getting rtpg-www usage.

---

### Post by dpg77 on 2010-01-13
> **dpg77 said:**
> have setup new ubuntu server install with rtorrent and rtpg-www (all from standard repo's) on ubuntu 9.10 server.
just want to know how to access webinterface on it.
cannot find any info anywhere on getting rtpg-www usage.


Anyone help with this.
Have got rtorrent working now.
configured it fine.
installed apache and all its stuff but still no idea how to finish the setup of rtpg-www

what url do i need to go to to finish the setup.
someone out there should know it a repo package but cannot find anything on how to config it.

eg is the url [http://server.ip/install:8080](http://server.ip/install:8080)

or something like this please help 

all i can get on apache server is the test page that is installed by default.
this is headless server so also need to make sure have configured to be able to access from a remote machine. as no firefox installed on this machine.

Please help.

Cheers Damien.

---

### Post by aimpau on 2010-01-18
bump. I also need an answer for this one. Thanks!

---

### Post by silver1499 on 2010-01-18
I'm in the same boat as you guys.

Installed rtorrent & rtpg-www from repos. 

Did this additional configuration, which may be useful: [http://www.debianblogs.com/rtpgwww_please_your_dearest_with_rtorrent’s_power]("http://www.debianblogs.com/rtpgwww_please_your_dearest_with_rtorrent’s_power")

But still can't access remotely.

[http://serverip:8080/](http://serverip:8080/) is my XBMC frontend, maybe I have some conflict? I dunno much about apache.

Any help would be much appreciated.

---

### Post by dpg77 on 2010-01-19
Strange thing happened was playing with rtorrent and apache web site.
still was not able to get working.

changed the rtpg website and copied over the 000-default website and opened up to all locations and it didn't work 2 days ago

tried getting rutorrent working but no sucess there either 

today tried and guess what it is working.
so not sure of which other step got it working 

now this is my 000-default in sites-enabled 

# NameVirtualHost *:80  # this record exists in /etc/apache2/ports.conf
                        # by default (Debian system)

<VirtualHost *:80>
    ServerName rtpg
    DocumentRoot /usr/share/rtpg-www/

    AddHandler cgi-script .cgi
    SetEnv RTPG_CONFIG /etc/rtpg/rtpg.conf
    <Directory /usr/share/rtpg-www/>
        DirectoryIndex index.cgi
        Options FollowSymLinks ExecCGI
        AddDefaultCharSet utf-8
        AllowOverride All

            Order deny,allow
            allow from all
           #  deny from all
    </Directory>
</VirtualHost>

<VirtualHost *:80>
    ServerName rtpg-scgi.localhost
    SCGIMount /RPC2 127.0.0.1:5000

    <Location /RPC2>
            Order deny,allow
            allow from all
            #deny from all
    </Location>
</VirtualHost>
                                           
this is by browsing straight to [http://IP_OF_SERVER/](http://IP_OF_SERVER/)

can someone else test this out and let me know if only the change to the website is required if not will keep digging to see what else i changed.

and in .rctorrent.rc is 

scgi_port = localhost:5000

---

### Post by hypestar on 2010-01-23
Hi

I've got rtpg and rtorrent working by doing the following steps:


Install rtorrent and rtpg frontend
```
sudo apt-get install rtorrent rtpg-www
```

Enable the scgi module:
```
sudo a2enmod scgi
```

Enable the virtual server in apache:
```
a2ensite rtpg.apache.conf
```
 
Reload Apache to activate the new configuration:
```
invoke-rc.d apache2 reload
```

Add scgi_port = localhost:5000 to your .rtorrent.rc file
```
echo “scgi_port = localhost:5000&#8243; >> ~/.rtorrent.rc
```

I've got the above instructions from this blog [http://www.debianblogs.com/rtpgwww_please_your_dearest_with_rtorrent%E2%80%99s_power]("http://www.debianblogs.com/rtpgwww_please_your_dearest_with_rtorrent%E2%80%99s_power")


I hope that this helps.

Jacob

---

### Post by dpg77 on 2010-01-24
> **hypestar said:**
> Hi
 
I've got rtpg and rtorrent working by doing the following steps:
 
 
Install rtorrent and rtpg frontend
```
sudo apt-get install rtorrent rtpg-www
```
 
Enable the scgi module:
```
sudo a2enmod scgi
```
 
Enable the virtual server in apache:
```
a2ensite rtpg.apache.conf
```
 
Reload Apache to activate the new configuration:
```
invoke-rc.d apache2 reload
```
 
Add scgi_port = localhost:5000 to your .rtorrent.rc file
```
echo “scgi_port = localhost:5000&#8243; >> ~/.rtorrent.rc
```
 
I've got the above instructions from this blog [http://www.debianblogs.com/rtpgwww_please_your_dearest_with_rtorrent%E2%80%99s_power](http://www.debianblogs.com/rtpgwww_please_your_dearest_with_rtorrent%E2%80%99s_power)
 
 
I hope that this helps.
 
Jacob
 
 
This only works if you access the machine from the local host we are trying to get it so we can access from another machine. eg that machine it is on is a headless server no GUI or Firefox installed on machine.
 
the webpage hack i have posted may work but need someone else to test it.

---

### Post by ramomamo on 2010-03-25
What I did to make it work is, after following the steps provided by hypestar:

On rtpc.apache.conf
Modify
```
ServerName rtpg
```
By
```
ServerName rtpg.yourserverdomainname
```
And comment the following lines
```
#Order deny,allow
#allow from 127.0.0.1
#deny from all
```
Restart apache and you should be able to connect to
[http://rtpg.yourserverdomainname/](http://rtpg.yourserverdomainname/)

I forgot to mention that with this, you will open the rtpg to the whole world as it has no user authentication. You probably want to use apache authentication for this page.

---

### Post by thomas.mcmahon on 2010-05-31
I got stuck at this step as well, as rtorrent resides on a headless server on my network too. The fix is simple, you just need to add an entry in the client you're using's hosts file (/etc/hosts) for the server.

So in my case on the windows machine that is accessing the web front end, I have the following in the hosts file, the same syntax will work for ubuntu:

192.168.1.10 rtpg

Then when I type [http://rtpg](http://rtpg) in the address bar in chrome, it accesses the rtorrent front end.

Hope this helps anyone else who stumbles across here. If you're still having trouble, the following article might help:

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

