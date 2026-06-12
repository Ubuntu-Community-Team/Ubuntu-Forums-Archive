---
title: "unable to update and download"
date: 2011-08-22
forum: General Help
---

### Post by gaurav.iit on 2011-08-22
My connection to internet requires a username and password..but when i update ubuntu software or try to download nything ..it doesnt ask for any username and password...also it doesnt download the update or software....plz help...

---

### Post by gaurav.iit on 2011-08-22
doesnt anybody know ???

---

### Post by drpjkurian on 2011-08-22
Are you the root user to the OS ?
If not you cannot update or install anything

---

### Post by drpjkurian on 2011-08-22
Try```
sudo apt-get update

```

---

### Post by Wim Sturkenboom on 2011-08-22
> **gaurav.iit said:**
> doesnt anybody know ???Give it a bit of time to go around the world. Bumping a thread (on any forum) within 24 hours is impolite.

Having said that:

Can you explain a little more? Where do you usually enter your username and password? In the browser? If so, are you behind a proxy? If so

For synaptic, there is a configuration option in there that applies both to software downloads and software updates.

For downloads and updates via command line, see e.g. [http://ubuntuforums.org/showthread.php?t=1802306](http://ubuntuforums.org/showthread.php?t=1802306)

---

### Post by Overcast32 on 2011-08-22
Try opening a terminal and running 'ifconfig' without quotes - see if you are even getting an IP address from DHCP (unless it's static). 

If not, try to force one and see if it works. 

```
sudo dhclient
```

Then see if you can ping your default gateway (probably the router).

---

### Post by docbop on 2011-08-22
> **gaurav.iit said:**
> My connection to internet requires a username and password..but when i update ubuntu software or try to download nything ..it doesnt ask for any username and password...also it doesnt download the update or software....plz help...
 
A bit confusing how you explained it.  First your username and PW for internet is just for internet nothing to do with ubuntu other than it need access the net to download files.

You are probably logging into ubuntu with your personal user account, but to install/update software you need to be root.   That can be done a couple of ways.
Either su - to root or use sudo to run a command as root.

Ubuntu has a tools in the menus for updating the system and installing files, most of them use sudo and will prompt you for your user password that sudo needs.

if you want to manually install software with apt-get or dpkg then you need to open a terminal window and su - to root and it will prompt for the root password.  If you are new to Linux/Unix I would say stick to the GUI tools in the menu for now.

Steve B.

---

### Post by gaurav.iit on 2011-08-22
see connecting to internet requires using username and password....
so when i open my browser to browse net it asks for my username and password..i enter it and the net runs...
but for updating when i use sudo command...it fails ....(i am the root user)...probably it needs username and password to connect to internet..but it doesnt asks for it....
when i try to update using ubutnu software center...then also it fails and doesnt ask for ny username or password to connect to internet...
also there is iron port installed in my college net...it might be happening due to this iron port....

 plz help..... i need g++ compiler and i cant get a way to install it....

---

### Post by Script Warlock on 2011-08-22
wow you have a super protected internet connection..

---

### Post by Wim Sturkenboom on 2011-08-23
1)
Check your browser settings

menu edit->preferences
select advanced on top, next select tab network and click settings

Is there a proxy configured? If so, write down the details or ask your system administrator for them. Continue with 2 below
If there is no proxy configured, skip the rest as I don't know the answer


2)
Next
2a)
Start synaptic (if you use a GUI, else go to 2b)

menu settings -> preferences,
select the tab network and configure the proxy server in there

These settings will also apply to the update manager

2b)
For the command line,
create / edit a file /etc/apt/apt.conf with the following content
```

Acquire::http::Proxy "http://myname:mypassword@theproxyaddressorname:theproxyport/";

```
As the file is in a system directory, you need root permissions for the above. Next you can run *sudo apt-get update*, *sudo apt-get upgrade* etc.

---

### Post by docbop on 2011-08-24
If you're logging in as root (a bad idea) then you don't need sudo, you are already root.  Just apt-get the programs you want.

---

