---
title: "Problem with Samba"
date: 2012-09-02
forum: General Help
---

### Post by rickm1945 on 2012-09-02
I am having a problem accessing my desktop from my laptop. I have had a problem with the UFW and now I think it maybe be interfering again. here is out put from terminal:
```
richard@XPS8100:~$ sudo ufw allow samba
Skipping adding existing rule
Skipping adding existing rule (v6)
richard@XPS8100:~$ 

``` 
I'm don't know what this means.

---

### Post by 2F4U on 2012-09-02
My experience is that opening the firewall for the Samba application is not sufficient. So what I did is to explicitly open the port 135 tcp on the server.

On a client (given that the ufw rules are restrictive) I open the following ports:
- 137 udp
- 138 udp
- 139 tcp
- 445 tcp

---

### Post by AnotherMuggle on 2012-09-02
> **rickm1945 said:**
> I am having a problem accessing my desktop from my laptop. I have had a problem with the UFW and now I think it maybe be interfering again. here is out put from terminal:
```
richard@XPS8100:~$ sudo ufw allow samba
Skipping adding existing rule
Skipping adding existing rule (v6)
richard@XPS8100:~$ 

``` 
I'm don't know what this means.

Have you tried disabling the firewall temporarily to see if samba starts working as you expected?  It may or may not rule out the firewall as the cause of your problems.

Have you tried checking the status of the UFW firewall?  It may be skipping the rules because they are already active.

```
sudo ufw status
```

---

### Post by rickm1945 on 2012-09-02
> **2F4U said:**
> My experience is that opening the firewall for the Samba application is not sufficient. So what I did is to explicitly open the port 135 tcp on the server.

On a client (given that the ufw rules are restrictive) I open the following ports:
- 137 udp
- 138 udp
- 139 tcp
- 445 tcp
How do you do this?

---

### Post by rickm1945 on 2012-09-02
> **AnotherMuggle said:**
> Have you tried disabling the firewall temporarily to see if samba starts working as you expected?  It may or may not rule out the firewall as the cause of your problems.

Have you tried checking the status of the UFW firewall?  It may be skipping the rules because they are already active.

```
sudo ufw status
```
The status came up allow.
```
richard@XPS8100:~$ sudo ufw status
[sudo] password for richard: 
Status: active

To                         Action      From
--                         ------      ----
Samba                      ALLOW       Anywhere
Samba (v6)                 ALLOW       Anywhere (v6)

richard@XPS8100:~$ 

```With UFW disabled I still can't connect. Get this error ```
Unable to mount location
Failed to retrieve share list from server
```

Now on RichardM when I try to Browse Network, I get Windows Network, I click , and I get a blank page. I don't know what happened but I have lost part of my network from my laptop (RichardM) and can not see my desktop (XPS8100). I can access my laptop from my desktop but not the other way around. It was working perfectly.

---

### Post by Morbius1 on 2012-09-02
See if samba itself is working on XPS8100. OPen a terminal and type:
```
nautilus smb://192.168.0.100
```Change 192.168.0.100 to the ip address of XPS8100 itself.

If that works then run the exact same command with the exact same ip address from RichardM.

[COLOR=Blue]*BTW, When you do "sudo ufw allow samba" it points to: /etc/ufw/applications.d/samba. And in that file it opens the following ports so I think you're fine:*[/COLOR]
> ports=137,138/udp|139,445/tcp

---

### Post by rickm1945 on 2012-09-03
> **Morbius1 said:**
> See if samba itself is working on XPS8100. OPen a terminal and type:
```
nautilus smb://192.168.0.100
```Change 192.168.0.100 to the ip address of XPS8100 itself.

If that works then run the exact same command with the exact same ip address from RichardM.

[COLOR=Blue]*BTW, When you do "sudo ufw allow samba" it points to: /etc/ufw/applications.d/samba. And in that file it opens the following ports so I think you're fine:*[/COLOR]
I'm getting output back that says "Could not find "smb://192.168.1.142"
I checked my network connection and that is my IP address. This is on XPS8100. I can see my RichardM from XPS8100 but I can not see XPS8100 from RichardM

---

### Post by Morbius1 on 2012-09-03
So you ran "nautilus smb://192.168.1.142" on 192.168.1.142 and it could not find itself?

If you turn off the firewall completely do you get the same result?

---

### Post by rickm1945 on 2012-09-03
> **Morbius1 said:**
> So you ran "nautilus smb://192.168.1.142" on 192.168.1.142 and it could not find itself?

If you turn off the firewall completely do you get the same result?
Ok I just did it again and it shows all my shared files on XPS8100 with firewall on as well as off. I must have did something wrong the first time.

I just tried to browse Network from RichardM (my laptop) and got this error.
```
Could not display "network:///". 
 Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.
```

---

### Post by Morbius1 on 2012-09-03
>  I just tried to browse Network from RichardM (my laptop) and got this error.And what about running this from richardM:
```
nautilus smb://192.168.1.142
```The could not display error usually means a missing package(s):
```
sudo apt-get install gvfs-backends
sudo apt-get install gvfs-fuse
```It's also possible you are not a member of the fuse group:
```
 sudo gpasswd -a your-user-name fuse
```Then logout and login again for the group to change.

---

### Post by rickm1945 on 2012-09-03
> **Morbius1 said:**
> And what about running this from richardM:
```
nautilus smb://192.168.1.142
```The could not display error usually means a missing package(s):
```
sudo apt-get install gvfs-backends
sudo apt-get install gvfs-fuse
```It's also possible you are not a member of the fuse group:
```
 sudo gpasswd -a your-user-name fuse
```Then logout and login again for the group to change.
I entered:```
 sudo nautilus smb://192.168.1.143
```and returned this error
```
Could not display "smb://192.168.1.142".
Nautilus cannot handle "smb" locations.
```Samba was working well for me until a few days ago. this is really strange.
Now I have lost the the connection between XPS8100 and RichardM. would the apt-get gvfs-fuse caused that.

---

### Post by rickm1945 on 2012-09-03
> **rickm1945 said:**
> i entered:```
 sudo nautilus smb://192.168.1.143
```and returned this error
```
could not display "smb://192.168.1.142".
Nautilus cannot handle "smb" locations.
```samba was working well for me until a few days ago. This is really strange.
Now i have lost the the connection between xps8100 and richardm. Would the apt-get gvfs-fuse caused that.
1

---

### Post by rickm1945 on 2012-09-03
> **rickm1945 said:**
> 1
This is the pop-up I got from ```
sudo nautilus smb://198.168.1.143
```

---

### Post by Morbius1 on 2012-09-03
I don't know who 198.168.1.143 is and I can’t imagine why you want to run nautilus as sudo to get to it. 

Sorry but I can't follow your posts any longer.

---

### Post by Mintnacho on 2012-09-03
alt +f2 nautilus smb://192.1xx.x.x/directory

---

### Post by rickm1945 on 2012-09-04
> **Morbius1 said:**
> I don't know who 198.168.1.143 is and I can&#8217;t imagine why you want to run nautilus as sudo to get to it. 

Sorry but I can't follow your posts any longer.
Sorry Morbius1, but if you scroll up you will see that you are the one who said to use nautilus command. I'm new to this and I certainly didn't invent the command. After doing exactly what you suggested I do, nothing from RichardM in browse Networks works. Thank you.

---

### Post by rickm1945 on 2012-09-04
> **Mintnacho said:**
> alt +f2 nautilus smb://192.1xx.x.x/directory
This is what I have been doing.```

nautilus smb://192.168.1.143 This is IP for my Laptop named RichardM 
```
I got the pop-up that I posted. Sudo was not in the command that I typed,I evidently typed suso in my post by mistake. I'm about ready to get rid of all Linux and delete partitions and go back to Windows 7. I have had nothing but one problem after another running Ubuntu 12.04 on my laptop. The screen resolution has never been correct since first time I installed it and there has been no resolve for that. At least MS has and uses drivers for all Intel graphics cards. I must say I do like Ubuntu, but I'm 67 and not in the mood to be in constant repair of my OS. This is just plain maddening. Samba was working perfectly then it just quit. This is the second time I asked for help here and didn't get it, or the help was wrong. So because of a word I put in the post, which I didn't use in my command Morbious1 gets ticked. If he would have bothered to scroll up he would have seen the screen shot I posted.  I didn't get the screen shot by using sudo. He being a avid and experienced user should have realized that My posting a sudo command wouldn't get such results.

---

### Post by Morbius1 on 2012-09-04
*** I have a fully functional samba setup here. If I run the following command: "sudo nautilus smb://192.168.0.100" I will get the following error:
> Could not display "smb://192.168.0.100". Nautilus cannot handle "smb" locations.This will always happen when you try to use nautilus as root to access samba. This is the exact error message you received after running nautilus as root.

** What I wanted to establish was whether or not Samba itself was working. So first I wanted you to access the XPS8100 samba server from the XPS8100 samba client by running the following command on XPS8100: 
```
nautilus smb://192.168.1.142
```- and it appeared to work:
> Ok I just did it again and it shows all my shared files on XPS8100 with firewall on as well as off.** Then I wanted you to access XPS8100 from RichardM the exact same way by running the exact same command on RichardM:
```
nautilus smb://192.168.1.142
```That's the part that's missing in your posts so far. Can the laptop access the desktop by ip address or not?

---

### Post by rickm1945 on 2012-09-04
> **Morbius1 said:**
> *** I have a fully functional samba setup here. If I run the following command: "sudo nautilus smb://192.168.0.100" I will get the following error:
This will always happen when you try to use nautilus as root to access samba. This is the exact error message you received after running nautilus as root.

** What I wanted to establish was whether or not Samba itself was working. So first I wanted you to access the XPS8100 samba server from the XPS8100 samba client by running the following command on XPS8100: 
```
nautilus smb://192.168.1.142
```- and it appeared to work:
** Then I wanted you to access XPS8100 from RichardM the exact same way by running the exact same command on RichardM:
```
nautilus smb://192.168.1.142
```That's the part that's missing in your posts so far. Can the laptop access the desktop by ip address or not?

```
 I an nautilus smb://192.168.1.142 on XPS100 and it brought up my shared files. So Samba is working on XPS8100. 
When I ran nautilus smb:192.168.1.142 on my Laptop which is RichardM I get an error message, but it brought up the shared files also. See screen shot attached.
```

---

### Post by rickm1945 on 2012-09-04
> **Morbius1 said:**
> *** I have a fully functional samba setup here. If I run the following command: "sudo nautilus smb://192.168.0.100" I will get the following error:
This will always happen when you try to use nautilus as root to access samba. This is the exact error message you received after running nautilus as root.

** What I wanted to establish was whether or not Samba itself was working. So first I wanted you to access the XPS8100 samba server from the XPS8100 samba client by running the following command on XPS8100: 
```
nautilus smb://192.168.1.142
```- and it appeared to work:
** Then I wanted you to access XPS8100 from RichardM the exact same way by running the exact same command on RichardM:
```
nautilus smb://192.168.1.142
```That's the part that's missing in your posts so far. Can the laptop access the desktop by ip address or not?

```
 I an nautilus smb://192.168.1.142 on XPS100 and it brought up my shared files. So Samba is working on XPS8100. 
When I ran nautilus smb:192.168.1.142 on my Laptop which is RichardM I get an error message, but it brought up the shared files also. See screen shot attached.
```When I do nautilus smb://192.168.1.143 on RichardM I get see screen shot attach.
If I enter password nothing happens the same pop-up keeps repeating.

---

### Post by rickm1945 on 2012-09-04
Now I just ran nautilus smb://192.168.1.142 and it brought up the shared folder on XPS8100. See Attach

---

### Post by rickm1945 on 2012-09-04
If I  try to use Browse Network, it brings up Windows Network, when I  click Windows Network, it brings up Work Group folder. When I click  WORKGROUP, After a minute or so it gives me error message, see attach.

---

### Post by Morbius1 on 2012-09-04
**Phase II**: I want you to access XPS8100 from RichardM by name. So on RichardM run the following command from the terminal:
```
nautilus smb://xps8600.local
```If that works bookmark it: Bookmarks > Add Bookmark.

If not, make sure that all firewalls are off and try it again.

If your heart is set on browsing to this machine instead of using a bookmark then we need to edit smb.conf . It's only one line you need to add ( name resolve order ) but I'm trying to keep that as a last resort.

---

### Post by rickm1945 on 2012-09-04
> **Morbius1 said:**
> **Phase II**: I want you to access XPS8100 from RichardM by name. So on RichardM run the following command from the terminal:
```
nautilus smb://xps8600.local
```If that works bookmark it: Bookmarks > Add Bookmark.

If not, make sure that all firewalls are off and try it again.

If your heart is set on browsing to this machine instead of using a bookmark then we need to edit smb.conf . It's only one line you need to add ( name resolve order ) but I'm trying to keep that as a last resort.

It brought up my shared file and I booked marked it. I will be happy to use bookmark. Thank you I do appreciate your help. Sorry to have ticked you off


i just ran the same command nautilus smb://RichardM.local and it brings up a password pop-up. I entered my password and it just keeps looping back to password pop-up. I was going to book mark RichardM on XPS8100.

---

### Post by Morbius1 on 2012-09-04
> **rickm1945 said:**
> It brought up my shared file and I booked marked it. I will be happy to use bookmark. Thank you I do appreciate your help. Sorry to have ticked you off


i just ran the same command nautilus sm://RichardM.local and it brings up a password pop-up. I entered my password and it just keeps looping back to password pop-up. I was going to book mark RichardM on XPS8100.
Did you add the user "richard" to the samba password database? 

**[COLOR=Blue]On RichardM[/COLOR]** add your user to the database:
```
sudo smbpasswd -a richard
```It will ask you first for sudo's password then it will ask you what password you want to use for samba. It can be the same as the login password for that user but it doesn&#8217;t have to be.

If that doesn't fix it by itself then we will need to dig into what's going on with RichardM. To do that we need the output of the following commands:
```
testparm -s
``````
net usershare info --long
```

---

### Post by rickm1945 on 2012-09-04
> **Morbius1 said:**
> Did you add the user "richard" to the samba password database? 

**[COLOR=Blue]On RichardM[/COLOR]** add your user to the database:
```
sudo smbpasswd -a richard
```It will ask you first for sudo's password then it will ask you what password you want to use for samba. It can be the same as the login password for that user but it doesn&#8217;t have to be.

If that doesn't fix it by itself then we will need to dig into what's going on with RichardM. To do that we need the output of the following commands:
```
testparm -s
``````
net usershare info --long
```

```
richard@RichardM:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[Music]"
Processing section "[Pictures]"
Processing section "[Public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
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

[Documents]
    path = /home/richard/Documents
    read only = No
    guest ok = Yes

[Music]
    path = /home/richard/Music
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

``````
richard@RichardM:~$ net usershare info --long
richard@RichardM:~$ 

``` Output of the two queries.

I read some articles about Samba and Encrypt passwords needs to be set to yes in the Samba, Preferences, security. set Encrypt password- yes. Everything is working very well now.  This thread will be marked as solved.

---

### Post by Morbius1 on 2012-09-04
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Search through the file until you see this line:
> encrypt passwords = NoAnd change it to Yes:
> encrypt passwords = [COLOR=Blue]**Yes**[/COLOR]Then restart samba:
```
sudo service smbd restart
```It's that last command that I've been trying to avoid in this thread. Your network seems to be very slow between machines and every time you restart smbd it has a fit. Wait a few minutes - like 5 or so minutes before you try to access the shares on RichardM.

---

