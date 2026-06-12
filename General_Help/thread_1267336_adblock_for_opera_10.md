---
title: "adblock for opera 10?"
date: 2009-09-15
forum: General Help
---

### Post by sena_akada on 2009-09-15
the old blocker from 9.6 is gone?

[IMG]http://i32.tinypic.com/121vs5d.png[/IMG]

how do i get it back?

---

### Post by sena_akada on 2009-09-16
bump

---

### Post by bodhi.zazen on 2009-09-16
I suggest you use a proxy.

I personally like bfilter :

**[Adblock with bfilter]("http://blog.bodhizazen.net/linux/adblock-with-bfilter/")**

---

### Post by sena_akada on 2009-09-16
i dont want to have to use a proxy. is there any other way?

---

### Post by bodhi.zazen on 2009-09-16
> **sena_akada said:**
> i dont want to have to use a proxy. is there any other way?

Not that I know of. 

If you google. search adblock + opera the results all point you to proxy.

What is wrong with a proxy ?

---

### Post by sena_akada on 2009-09-17
> **bodhi.zazen said:**
> Not that I know of. 

If you google. search adblock + opera the results all point you to proxy.

What is wrong with a proxy ?

Bfilter can be run in two ways, as a service (started in /etc/init.d/bfilter) or as a GUI (graphical user interface).
Ubuntu &#8211; bfilter is in the repositories &#8211; install either bfilter (service, no gui) or bfilter-gui (gui) but NOT Both !!!
Other distros (Fedora) you will need to either compile bfilter or use the bfilter-gui which is available as an &#8220;Autopackage&#8221; (See the Bfilter Downloads page). Run the Autopackage on the command line (does not work when launched from a gui).
Windows &#8211; Obtain it from the Bfilter Downloads page. To run portable, download from here.
Using bfilter
Start bfilter
As a service (bfilter) &#8211; bfilter starts on boot. You can start or stop it manually with 

# Ubuntu
sudo /etc/init.d/bfilter start|stop|restart

# Fedora
su -c &#8217;service bfilter start|stop|restart&#8217;
As a gui - 
Windows &#8211; run (double click) the bfilter.exe .
Linux &#8211; You will find it easier to write a (short) script to autostart bfilter-gui when you log in. Save this script in ~/bin/bfilter-gui : 

#!/bin/bash
sleep 10
nohup /usr/bin/bfilter-gui > /dev/null &

Make it executable:

chmod a+x ~/bin/bfilter-gui

Now add to your autolauncher, go to Settings -> Sessions and Startup
Add an entry:
name: bfilter-gui
command: /home/you/bin/bfilter-gui

Configure your browser

One advantage of bfilter, it will work with any browser. The menus will vary with your browser, and on Windows you may need to edit your network configuration.

Friefox -
Open your options, navigate to the Advanced tab
Select the &#8220;network&#8221; tab and hit the settings button.

In the dialog box, set your proxy to 127.0.0.1 port 8080

Windows users &#8211; 
In your control panel, open your &#8220;Internet Options&#8221; , select the &#8220;connections&#8221; tab.

Hit the &#8220;LAN Settings&#8221; button and insert your proxy settings 127.0.0.1 port 8080


That is all there is to it, no need to re-boot or re-start your browser.
Power Tweaks
Import the Adblock Plus (Firefox extension) &#8220;blacklist&#8221;

This is not necessary as bfilter does just fine on it&#8217;s own. If you find there are some ads not blocked, you can try to add the Adblock Plus filter list.

See This Link for the original scripts. I modified them (fixed the paths and files, fixed the perl script with dos2unix) and re-posted them below.

Save this first one in /usr/local/bin/adblock2bfilter.pl

And the second one in /usr/local/bin/bfilterUpdateLists.sh

Make them executable :

sudo chmod a+x /usr/local/bin/*

Note: On the origional page there is a link to a windows script, but I used the above scripts on Linux, converted with tofrodos, and saved the urls.local to my flash drive. If you wish here is a link to a urls.local you may use on Windows (Note: the list in that link is unmaintained).

To use the script simply:

sudo /usr/local/bin/bfilterUpdateLists.sh

This will update your list in /etc/bfilter/urls.local
To use the list with the service, simply restart bfilter.
To use the list with bfilter-gui, copy 

sudo cp /etc/bfilter/urls.local /home/your_user/.bfilter/urls.local
sudo chown you:you /home/your_user/.bfilter/urls.local

Then quit and restart the bfilter-gui
Use a cache for bfilter
bfilter-gui uses a cache automatically. 
Linux it is located in ~/.bfilter/cache .
Windows it is in Program Files\BFilter\Cache
If you are using bfilter as a service you will need to make a (small) edit to /etc/init.d/bfilter. Using any editor, add &#8220;-C /tmp/bfilter&#8221; to /etc/init.d/bfilter on the &#8220;DAEMON_OPTS&#8221; line. It looks like this: 

# All one line:
DAEMON_OPTS=&#8221;-u nobody -g nogroup -p /var/run/bfilter.pid -C /tmp/bfilter $DAEMON_OPTS&#8221;
Use bfilter as a proxy server on your LAN

This is easy to do if you are running bfilter as a service.

Using any editor, open /etc/bfilter/config

Under the [global] section, at the top of the page, edit the &#8220;listen_address&#8221; line, use your ip address rather then 127.0.0.1

listen_address = 192.168.0.10:8080

You may wish to change the default port and firewall the connection.

Additional options are explained in the configuration file.

The advantage of running bfilter this way is that you then only need to maintain one set of config files for all clients on your LAN.

Assuming your LAN is 192.168.0.0/24 any your bfilter server is 192.168.0.10 , you can firewall the connection with ufw 

sudo ufw enable
sudo ufw default deny
sudo ufw allow from 192.168.0.0/24 to 192.168.0.10 port 8080

[SIZE="3"]**[COLOR="Red"][SIZE="2"]_that_[/SIZE][/COLOR] :/**[/SIZE]

---

### Post by NoaHall on 2009-09-17
Try reinstalling. It's still there for me.

---

### Post by sena_akada on 2009-09-17
> **NoaHall said:**
> Try reinstalling. It's still there for me.

are you using the qt3 or qt4 version?

---

