---
title: "Possible to share application over LAN?"
date: 2009-09-30
forum: General Help
---

### Post by graylox on 2009-09-30
OK, here goes my first post:

I am running 8.10 Intrepid Ibex on a laptop. I use MySQL locally,  running in a Firefox interface. Is there a way to have this app shared across a LAN (Wireless even) with other Windows based PC's logging in via a web browser? I do not have Apache installed at this point.

What other information do I need to provide to get something worked out? I appreciate all suggestions.

---

### Post by akakingess on 2009-09-30
I am by no means an expert, but you may want to provide some more detail, like what exactly are you using MySQL for, and could you make it web-based (i.e. just install apache and have the other machines point to yours via a web interface? The more we know, the more we can help.

---

### Post by BQAggie2006 on 2009-09-30
There are a few ways you can do this.
 
1) On the Windows Machine, you can install the MySQL GUI Tools for Windows and configure it to connect to the database on your machine
 
2) Install PHPMyAdmin (though this requires a full LAMP install but that's easy) and point the browser on your Windows machine to [http://your.mysql.host.ip/phpmyadmin](http://your.mysql.host.ip/phpmyadmin)
 
3) Not quite sure about this, but I think SQuirreL SQL might be able to connect to a remote host. If that's the case, install SQuirreL SQL on the Windows machine, add the MySQL JDBC driver to and point it to your MySQL host

---

### Post by graylox on 2009-09-30
Here's the basic scenario:

This is an accounting database used by a non-profit. There is a server running with several construction projects being managed from users in various locations accessing the SQL system from the web. At times, a particular dataset is taken offline and it is moved using the backup/restore routine to the laptop, which has its own MySQL installation. On the construction site, the laptop is currently being used by a single user, but there is a need for as many as five users to be on the system at the same time. I was planning on a WAP deployment on the jobsite using the laptop with its current dataset active as a "local server" for lack of a better term. The main (stationary) server does have Apache installed and works nicely. 
Akakingess, you may have the best idea. If all I need to do is install Apache and then configure the WAP, then I'm set.
Thanks again!

---

### Post by graylox on 2009-10-01
Well, I still need some assistance. I should say that although the main server does indeed run Apache, I did not set it up. So...I need the idiot's guide to configuring Apache once I have it installed on the laptop so that a login for the MySQL app presents itself to the LAN users. And I am thinking that pointing the other browsers to the app is as simple as opening the browser of choice to the assigned ip. I would assume that the WAP should be set up to use DHCP for the users, but how is the connection set between the WAP and the laptop/server? Static IP assignment in the WAP? Then how to assign a static IP in the server?
I will admit to being a seasoned Windows user with some network experience, and perhaps I am just a bit timid with the foray onto the *.nix world. I like the way it works so far, and have a machine dedicated to schooling myself on this setup, besides the critical machine for the network I am servicing. 

Thanks yet again!

---

### Post by graylox on 2009-10-01
Anyone?

---

### Post by BQAggie2006 on 2009-10-01
If I understand correctly, you are looking for a way to do MySQL development via a web browser? If that is correct, check out PHPMyAdmin.
 
But if it doesn't necessarily have to be through a web browser, check out the MySQL GUI Tools (available for Windows, Linux, and Mac).
 
There is also a way to configure the OpenOffice.org Base data sources to point to a MySQL back end.

---

### Post by graylox on 2009-10-02
I guess I am not very good at describing the situation. I have an application that presents itself as sql-ledger, an acounting program, that users normally access on the web. It is hosted by a Ubuntu server running MySQL and Apache. It is administered with pgAdmin III. I do remote admin with NX Client on a windows machine. I have a virtually identical setup on an Ubuntu laptop, but originally with no intention to have it serve up the app via web. The idea was to place a copy of a single dataset derived from active data on the server, disable access to that dataset (on the server) via web, and have a single individual use the laptop for a short time. After a project was finished, the dataset from the laptop would be transfered back to the server for web access. 
Now the idea is to share the laptop with a wireless access point so that as many as five users could have access to the application (mimicking the main server). So far, I can see that Apache would be necessary to make the app available from the laptop (used as a server). But how to actually set up Apache to make the connection in Ubuntu to the application is my main question. 
I also need some guidance in configuring Apache (I suppose) to have the WAP connect. Some IP config info I don't have.  

I know, I know.....clear as mud.

---

### Post by juancarlospaco on 2009-10-02
I dont understand, maybe... 

you can try** rsync**'ing the Server and the Laptop, to clone the data and use locally.
or
you can try** SSH**'ing the Server or the Laptop, to work locally with remote data.

*Apache2 has nothing to do with WAP or IP.*
:)

---

### Post by graylox on 2009-10-02
Using the laptop locally works like a charm. Moving the data back and forth is no problem. The main issue behind all this is a lack of internet access on a project location. I have been setting up the laptop to use with all necessary files to use the sql-ledger app locally. What I want to do is share the resources of this "offline" laptop wirelessly with a few other users. After the offline use session is over, of course the dataset on the laptop has been updated by the user and this is then moved back to the server (and hence is accessible via web).
All I need to do is set this up so that a few other wireless equipped laptops can log into this app in a similar manner to what the users are accustomed to seeing on the internet when they log into the main server.

Maybe?

---

### Post by graylox on 2009-10-02
Anyone? I know this seems trivial to some of you, but it is really important to me and I appreciate your help.

---

### Post by BQAggie2006 on 2009-10-02
The application that is accessed through the web, and that you are trying to share with the remote users, how is it developed (besides the MySQL backend)?

---

### Post by graylox on 2009-10-02
I'm not sure what you are asking. I do not know the author, nor did I set it up originallu. I inherited this project from someone else.

---

### Post by karlson on 2009-10-02
> **graylox said:**
> I guess I am not very good at describing the situation. I have an application that presents itself as sql-ledger, an acounting program, that users normally access on the web. It is hosted by a Ubuntu server running MySQL and Apache. It is administered with pgAdmin III. I do remote admin with NX Client on a windows machine. I have a virtually identical setup on an Ubuntu laptop, but originally with no intention to have it serve up the app via web. The idea was to place a copy of a single dataset derived from active data on the server, disable access to that dataset (on the server) via web, and have a single individual use the laptop for a short time. After a project was finished, the dataset from the laptop would be transfered back to the server for web access. 

I think that you are creating the problem more convoluted then it needs to be...

Create a second database either on the laptop or on the same server and do a dump and load from production to the second DB and have the user have at that database to his/her heart's content.

---

### Post by BQAggie2006 on 2009-10-02
So the users access this accounting app through a web browser right? Well how was the web interface developed (PHP/Java/ColdFusion/etc)?

If it's just a simple web interface (HTML/PHP/JavaScript/etc), then all you'll have to do is install the LAMP stack, mimic the main server's Apache configuration, and copy the web app's files over to /var/www.

---

### Post by graylox on 2009-10-02
Karlson,
 I probably am making this harder than it really is. The laptop is a virtual clone of the server. I already do that (dump and load with pgAdmin III) for local/offline use and it works fine. I want to share this laptop with a handful of other users while it is offline, and located nowhere near web access. I have at hand a WAP that something tells me I can use to bridge the other laptops to this one. That's where I am stuck in not knowing what to install (Apache??) and how to go from here.

Thanks!

---

### Post by BQAggie2006 on 2009-10-02
We probably won't be able to give specific instructions on how to configure the WAP since there are so many available, though you could probably find the manual online. Basically, you'll need to configure the AP's SSID, security (WPA2), and make sure it's giving IP addresses. After you have configured all this, you should be able to connect all the computers (including the host laptop) to the same network.

As far as hosting the application from you laptop, we need to know how the application was developed so we can give you the appropriate support. If it is just a simple page, then a simple Apache install will work. If it was developed in PHP, you'll need the LAMP install. If it was developed in Java... I'm sure you get the point.

---

### Post by graylox on 2009-10-02
It appears to be realitively simple HTML. Viewing page souorce, I see references to css and Javascript as the script language.

Where are the Apache config files located so that I can copy them?

---

### Post by BQAggie2006 on 2009-10-02
The Apache documentation in the Ubuntu Server Guide does a good job of describing the different configuration files and what they contain: [https://help.ubuntu.com/9.04/serverguide/C/httpd.html](https://help.ubuntu.com/9.04/serverguide/C/httpd.html)

Once you have copied the configuration, you'll need to copy the pages from the main server to your laptop. These are usually located in /var/www, though it might be in a different location. To determine where they are, look in the /etc/apache2/sites-available/default file on the main server.

---

### Post by graylox on 2009-10-02
Thanks for the help. I still must be leaving out some things (and misspelling others). The laptop currently has the full application installed and can be used by opening a browser and pointing to itself. 

As far as the WAP, I can handle getting it connected. I guess my question on it revolves more around using a specific port or allowing sharing or any known issues related to that when connecting via LAN to a "server" hosting this app.

---

### Post by BQAggie2006 on 2009-10-02
Unless you specifically set up a firewall to block port 80, then you should be okay. Since it's already hosted (confirmed when you point a browser to the local machine), then you don't have to "allow sharing".

>  any known issues related to that when connecting via LAN to a "server" hosting this app

Not quite sure what you mean by this.

---

### Post by graylox on 2009-10-02
I think at this point, I am asking after I set up and configure Apache, etc. (the link to the guide is helping) is it as simple as using the LAN IP assigned to the laptop/server to open a browser on the other machines?

This is all getting clearer, and yes, I have been making this altogether more complex than it really is. I guess that comes from all this being relatively new. Last time I played with Linux, it was RedHat, and I gave it up. PC's have been fun since way back when. Been playing with computers long time and still have my TRASH 80. Guess I'm just intimidated and spoiled just a bit by M$.

---

### Post by BQAggie2006 on 2009-10-02
> is it as simple as using the LAN IP assigned to the laptop/server to open a browser on the other machinesYes, it should be (unless you have to point it to a sub-folder such as [http://1.2.3.4/application](http://1.2.3.4/application))

Yeah, it's always fun diving into something new, even though it can be intimidating at first. I too was apprehensive at first when I started playing with Linux. I guess something I did to over come it was just to play around with it in virtual machines. That way if you break something you can just start over.

Since you're used to MS products and you will feel more comfortable around a GUI, you might want to check out the following options: Webmin, eBox, GADMIN.

---

### Post by graylox on 2009-10-02
Well, so much for simplicity. I am thinking that it is in fact pointing to a subfolder. I can ping the server/laptop from another machine on the network. Browsing to the IP of the server, I am directed to a URL (it is resolving, so where is the DNS coming from??) such as [http://XXXX-laptop/sql-ledger/login.pl](http://XXXX-laptop/sql-ledger/login.pl)
There it dies and is unable to open the login to the app.

BQAggie....CLI is no problem, I learned long ago in BASIC and DOS, so I'm not THAT spoiled yet!

Still reading how-to's

Thanks!

---

### Post by graylox on 2009-10-03
End result for those interested:

Laptop running the sql-ledger app is obtaining an ip from a dhcp enabled router. Router hands out ip also to the wap. Wireless users obtain connection also using dchp from wap. Users point their browsers to the ip issued by the router to the host-laptop. There is no dns running, so the users must use the ip/app interface i.e. [http://192.168.1.100/sql-ledger.login.pl](http://192.168.1.100/sql-ledger.login.pl) ( I set the range of ip numbers in the router to start there)

I guess the issuance of the ip from the router to the laptop is the only downside here. The laptop/server must be powered up first to obtain the same ip from the pool every time, or someone has to determine the proper ip to give to the users. If any user were to log onto the wireless network, or power up the wap, they would get the first ip from the pool and spoil the plan. I didn't mention that this all will be run while I am not close by, but supplying phone support only. If there is a way to use a partially static/partially dynamic ip scheme in the router so it would connect for sure without worrying what ip was actually issed to it, it would be nice, but I don't see it. More research.

Anyway, it works well enough to meet my needs for now. 

Thanks again for all the assistance, it did help.

---

### Post by unutbu on 2009-10-03
> I set the range of ip numbers in the router to start there

If you assign the laptop a static IP address that is before or after the range used by DHCP, then you'd be all set. 

To setup a static ip, simply edit /etc/network/interfaces and put in something like this:
```

auto eth0
iface eth0 inet static
address 192.168.1.81
netmask 255.255.255.0
gateway 192.168.1.1
```

This assigns 192.168.1.81 as the static ip. 
In the example above, 192.168.1.1 is the router's ip address.
You may need to add a bit more if you are using WEP or WPA wireless encryption.

See also:
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by graylox on 2009-10-03
Done that and.....done!

Thanks, Unutbu....I knew that, lol. I was just lost in thought on all the rest and couldn't get my focus back on regular networking stuff.  It would probably have dawned on me....after I dropped this pakage of equipment off at the site. The link is good reading also.

Anyway, thanks again. It works as desired!

---

