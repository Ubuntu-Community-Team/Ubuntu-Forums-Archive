---
title: "Samba"
date: 2012-08-05
forum: General Help
---

### Post by rickm1945 on 2012-08-05
I have Samba installed on my dual boot Windows/Ubuntu 12.04 laptop and on my desktop. I setup the files to share on both computers but I can not access files from one computer to the other. I need to be able to use my files both ways.
I clicked on browse network and got this error message.
```
Unable to mount location
Failed to retrieve share list from server
```
An
I would think this should be a simple process.How can i get samba setup to work properly?

---

### Post by raja.genupula on 2012-08-05
[https://help.ubuntu.com/community/Samba/](https://help.ubuntu.com/community/Samba/)

please read this

---

### Post by Morbius1 on 2012-08-05
First, I would suggest making sure Samba itself is working. Access the other machine directly by ip address:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the other machine.*[/COLOR]
You can also try to access it by a qualified hostname:
> nautilus smb://hostname.local[COLOR=Blue]*Changing hostname to the name you gave the other box.*[/COLOR]

If that works and you still want to browse to the other box instead of accessing it directly then I would suggest making the following modifications to your smb.conf:

[1] Run the following command and count the number of characters:
```
hostname
```If it's 15 characters or less in length then you are good to go. If it's more than that then add the following line to the [global] section of smb.conf- right under the workgroup line:
```
netbios name = something
```[COLOR=Blue]*Changing "something" to be 15 characters or less in length.*[/COLOR]

[COLOR=Black][2] Add one more line right under the workgroup line again:
[/COLOR]```
[COLOR=Black]name resolve order = bcast host lmhosts wins[/COLOR]
```[COLOR=Black]
Then restart samba:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]
Wait a few minutes for the network to settle down and try to access the share again.

These changes should be done on every Linux machine in your network.
[/COLOR]

---

### Post by rickm1945 on 2012-08-05
> **Morbius1 said:**
> First, I would suggest making sure Samba itself is working. Access the other machine directly by ip address:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the other machine.*[/COLOR]
You can also try to access it by a qualified hostname:
[COLOR=Blue]*Changing hostname to the name you gave the other box.*[/COLOR]

If that works and you still want to browse to the other box instead of accessing it directly then I would suggest making the following modifications to your smb.conf:

[1] Run the following command and count the number of characters:
```
hostname
```If it's 15 characters or less in length then you are good to go. If it's more than that then add the following line to the [global] section of smb.conf- right under the workgroup line:
```
netbios name = something
```[COLOR=Blue]*Changing "something" to be 15 characters or less in length.*[/COLOR]

[COLOR=Black][2] Add one more line right under the workgroup line again:
[/COLOR]```
[COLOR=Black]name resolve order = bcast host lmhosts wins[/COLOR]
```[COLOR=Black]
Then restart samba:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]
Wait a few minutes for the network to settle down and try to access the share again.

These changes should be done on every Linux machine in your network.
[/COLOR]
Evidently Samba is messed up along with several other things. Her is the out put of netbios name = something command.
```
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ hostname
richard-HP-Pavilion-g6-Notebook-PC
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ netbios name = RichardM
netbios: command not found
richard@richard-HP-Pavilion-g6-Notebook-PC:~$
```How can I change computer name? How do I edit smb.comf?

---

### Post by Morbius1 on 2012-08-05
Samba's not messed up it's the installer that defaults to a hostname that's longer than 15 characters long.

TO edit smb.conf:
```
gksu gedit /etc/samba/smb.conf
```netbios name isn't a command it's a parameter you add to smb.conf. Once you have smb.conf in an editor add the following lines right under the [COLOR=Blue]workgroup[/COLOR] line:
```
netbios name = RichardM
[COLOR=Black]name resolve order = bcast host lmhosts wins[/COLOR]
```Then save the file, exit gedit, and restart samba:
```
sudo service smbd restart
```

---

### Post by rickm1945 on 2012-08-05
> **Morbius1 said:**
> Samba's not messed up it's the installer that defaults to a hostname that's longer than 15 characters long.

TO edit smb.conf:
```
gksu gedit /etc/samba/smb.conf
```netbios name isn't a command it's a parameter you add to smb.conf. Once you have smb.conf in an editor add the following lines right under the [COLOR=Blue]workgroup[/COLOR] line:
```
netbios name = RichardM
[COLOR=Black]name resolve order = bcast host lmhosts wins[/COLOR]
```Then save the file, exit gedit, and restart samba:
```
sudo service smbd restart
```

I can access the browse Network from my laptop but I can only see the printer. How do I access files on either computer?
I edited the smb.conf file on my desktop computer also. I can now see both computers on the network, but I can;t see any files except for the printer. I got a error message saying:
```
Unable to mount location
Failed to retrieve share list from server
```

---

### Post by Morbius1 on 2012-08-05
I have a feeling you don't have anything shared. It's just like Windows - you have to share something first. Post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by rickm1945 on 2012-08-06
> **Morbius1 said:**
> I have a feeling you don't have anything shared. It's just like Windows - you have to share something first. Post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```
This is the out put from my desktop computer:
```
richard@XPS8100:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[Pictures]"
Processing section "[Public]"
Processing section "[Downloads]"
Processing section "[Templates]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    read only = No
    guest ok = Yes

[Documents]
    path = /home/richard/Documents
    read only = No
    guest ok = Yes

[Pictures]
    path = /home/richard/Pictures
    read only = No
    guest ok = Yes

[Public]
    path = /home/richard/Public
    read only = No
    guest ok = Yes

[Downloads]
    path = /home/richard/Downloads
    read only = No
    guest ok = Yes

[Templates]
    path = /home/richard/Templates
    read only = No
    guest ok = Yes
richard@XPS8100:~$ net usershare info --long
richard@XPS8100:~$ 

```
This is the return from my Laptop:
```
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[Pictures]"
Processing section "[Public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = RICHARDM
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast host lmhosts wins
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Documents]
    path = /home/richard/Documents
    read only = No
    guest ok = Yes

[Pictures]
    path = /home/richard/Pictures
    valid users = richard
    read only = No

[Public]
    path = /home/richard/Public
    read only = No
    guest ok = Yes
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ net usershare info --long
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 

```

I can access the files on my laptop from my desktop computer. I can not access files on my Desktop from my laptop.

---

### Post by Morbius1 on 2012-08-06
You are missing the following line in XPS8100:
```
name resolve order = bcast host lmhosts wins
```Add it in and restart samba:
```
sudo service smbd restart
```If that doesn't resolve it post the output of this command from XPS8100:
```
smbtree
```

---

### Post by rickm1945 on 2012-08-06
> **Morbius1 said:**
> You are missing the following line in XPS8100:
```
name resolve order = bcast host lmhosts wins
```Add it in and restart samba:
```
sudo service smbd restart
```If that doesn't resolve it post the output of this command from XPS8100:
```
smbtree
```
```
richard@XPS8100:~$ smbtree
Enter richard's password: 
WORKGROUP
    \\XPS8100                XPS8100 server (Samba, Ubuntu)
        \\XPS8100\HP-Officejet-6500-E709n    HP Officejet 6500 E709n
        \\XPS8100\HPPrinter6500      HP Fax
        \\XPS8100\IPC$               IPC Service (XPS8100 server (Samba, Ubuntu))
        \\XPS8100\Templates          
        \\XPS8100\Downloads          
        \\XPS8100\Public             
        \\XPS8100\Pictures           
        \\XPS8100\Documents          
        \\XPS8100\print$             Printer Drivers
    \\RICHARDM               richard-HP-Pavilion-g6-Notebook-PC server (Samba
        \\RICHARDM\HP-Fax             HP Fax
        \\RICHARDM\HP-Officejet-6500-E709n    HP Officejet 6500 E709n
        \\RICHARDM\print$             Printer Drivers
        \\RICHARDM\Documents          
        \\RICHARDM\Pictures           
        \\RICHARDM\Public             
        \\RICHARDM\IPC$               IPC Service (richard-HP-Pavilion-g6-Notebook-PC server (Samba, Ubuntu))
richard@XPS8100:~$ 

```

I can see XPS8100 on my laptop but can't connect. I get the same error message  about can not mount

---

### Post by Morbius1 on 2012-08-06
My guess is that you either encrypted your home directory when you did the initial install or the target folders or the path to them is sitting at "drwx------".

Try this to bypass either of those conditions by adding yet another line to the smb.conf of XPS8100 - right under the workgroup line again:
```
force user = richard
```Then restart samba:
```
sudo service smbd restart
```

---

### Post by rickm1945 on 2012-08-06
> **Morbius1 said:**
> My guess is that you either encrypted your home directory when you did the initial install or the target folders or the path to them is sitting at "drwx------".

Try this to bypass either of those conditions by adding yet another line to the smb.conf of XPS8100 - right under the workgroup line again:
```
force user = richard
```Then restart samba:
```
sudo service smbd restart
```
This didn't work either. Would removing Samba and then installing it again maybe fix this, on XPS8100??

---

### Post by Morbius1 on 2012-08-06
The output of testparm on the XPS8100 ( once you add the name resolve order ) is textbook correct. If there was a remaining issue with name resolution the output of smbtree would have given you error messages. There's nothing to fix on the Samba end of this from my perspective. It all points to a Linux permissions problem.

Try using SSH to access the desktop:

[1] Install openssh:
```
sudo apt-get install openssh-server
```[2] From the laptop access the desktop this way:
```
nautilus ssh://192.168.0.100
```Or this way:
```
nautilus ssh://xps8100.local
```When it asks you for a user name and password on the laptop give it **richard** with richard's login password.

---

### Post by rickm1945 on 2012-08-06
> **Morbius1 said:**
> The output of testparm on the XPS8100 ( once you add the name resolve order ) is textbook correct. If there was a remaining issue with name resolution the output of smbtree would have given you error messages. There's nothing to fix on the Samba end of this from my perspective. It all points to a Linux permissions problem.

Try using SSH to access the desktop:

[1] Install openssh:
```
sudo apt-get install openssh-server
```[2] From the laptop access the desktop this way:
```
nautilus ssh://192.168.0.100
```Or this way:
```
nautilus ssh://xps8100.local
```When it asks you for a user name and password on the laptop give it **richard** with richard's login password.
  Getting errors:
```
Could not display "sftp://192.168.1.139/".
Error: ssh program unexpectedly exited
Please select another viewer and try again.
```

```

Could not display "sftp://xps8100.local/".
Error: ssh program unexpectedly exited
Please select another viewer and try again.
```

---

### Post by rickm1945 on 2012-08-08
> **rickm1945 said:**
> Getting errors:
```
Could not display "sftp://192.168.1.139/".
Error: ssh program unexpectedly exited
Please select another viewer and try again.
``````

Could not display "sftp://xps8100.local/".
Error: ssh program unexpectedly exited
Please select another viewer and try again.
```

I did the hostname in terminal a the out put is:
```
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ hostname
richard-HP-Pavilion-g6-Notebook-PC
richard@richard-HP-Pavilion-g6-Notebook-PC:~$
```
this is only happening on my laptop. I checked the smb.conf file and under WorkGroup it still list host name as RichardM.

```
Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup
XPS8100
    netbios name = RichardM
name resolve order = bcast host lmhost wins
```

---

### Post by davidvandoren on 2012-08-08
I haven't seen this anywhere in this thread yet but in case you missed it .

```
sudo ufw allow samba
```Or if you are not online 

```
sudo ufw disable
```Then see if you can get it to work.
If yes, ```
sudo gfw enable
```and try the first one ```
sudo ufw allow samba
```You'll have to do this on both pc


If the firewall stands in your way for configuring samba and the last command isn't enough getting it to work.

Here is the hack to make it work anyway.

```
sudo ufw allow proto udp to 10.42.43.10/24 port 137 from any
sudo ufw allow proto udp to 10.42.43.10/24 port 138 from any
sudo ufw allow proto tcp to 10.42.43.10/24 port 139 from any
sudo ufw allow proto tcp to 10.42.43.10/24 port 445 from any

sudo ufw status gives

Your inbound rules
sudo ufw allow proto udp from 10.42.43.10/24 port 137 to any
sudo ufw allow proto udp from 10.42.43.10/24 port 138 to any
sudo ufw allow proto tcp from 10.42.43.10/24 port 139 to any
sudo ufw allow proto tcp from 10.42.43.10/24 port 445 to any


sudo ufw allow proto udp to any port 137 from 10.42.43.10/24
sudo ufw allow proto udp to any port 138 from 10.42.43.10/24
sudo ufw allow proto tcp to any port 139 from 10.42.43.10/24
sudo ufw allow proto tcp to any port 445 from 10.42.43.10/24
```You'll have to do this on both pc changing the IPs accordingly. 


Always turn your internet and firewall off when configuring Samba. Once you got it to work, turn it back on and see how it works.


Another thing I think is the Ip range between ubuntu and windows should be the same. 
Your windows machine is on 192.168.0.100

as you can see my ubuntu machines are on 10.42.43.10 and the other machine is 10.42.43.1

Set your wired connection on Ubunt to be on  192.168.0.1 or something like that .
Do you have two network cards or how do you go internet with you machines?

---

### Post by rickm1945 on 2012-08-09
> **davidvandoren said:**
> I haven't seen this anywhere in this thread yet but in case you missed it .

```
sudo ufw allow samba
```Or if you are not online 

```
sudo ufw disable
```Then see if you can get it to work.
If yes, ```
sudo gfw enable
```and try the first one ```
sudo ufw allow samba
```You'll have to do this on both pc


If the firewall stands in your way for configuring samba and the last command isn't enough getting it to work.

Here is the hack to make it work anyway.

```
sudo ufw allow proto udp to 10.42.43.10/24 port 137 from any
sudo ufw allow proto udp to 10.42.43.10/24 port 138 from any
sudo ufw allow proto tcp to 10.42.43.10/24 port 139 from any
sudo ufw allow proto tcp to 10.42.43.10/24 port 445 from any

sudo ufw status gives

Your inbound rules
sudo ufw allow proto udp from 10.42.43.10/24 port 137 to any
sudo ufw allow proto udp from 10.42.43.10/24 port 138 to any
sudo ufw allow proto tcp from 10.42.43.10/24 port 139 to any
sudo ufw allow proto tcp from 10.42.43.10/24 port 445 to any


sudo ufw allow proto udp to any port 137 from 10.42.43.10/24
sudo ufw allow proto udp to any port 138 from 10.42.43.10/24
sudo ufw allow proto tcp to any port 139 from 10.42.43.10/24
sudo ufw allow proto tcp to any port 445 from 10.42.43.10/24
```You'll have to do this on both pc changing the IPs accordingly. 


Always turn your internet and firewall off when configuring Samba. Once you got it to work, turn it back on and see how it works.


Another thing I think is the Ip range between ubuntu and windows should be the same. 
Your windows machine is on 192.168.0.100

as you can see my ubuntu machines are on 10.42.43.10 and the other machine is 10.42.43.1

Set your wired connection on Ubunt to be on  192.168.0.1 or something like that .
Do you have two network cards or how do you go internet with you machines?

I got it to work with only using the first solution. It was the fire wall on my desktop pc preventing the share.  I now works on both machines. I didn't even think of the obvious, being the firewall. Thanks again for you help

---

