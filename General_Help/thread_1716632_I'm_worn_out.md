---
title: "I'm worn out"
date: 2011-03-28
forum: General Help
---

### Post by Ziton on 2011-03-28
Why is mythtv such a boy dog
I just did an install of Ubuntu 10.10 and mythtv.
I have worked for several hours to get the front end to connect to the backend.
Nothing works.
[B]No UPnP backends found
[/B]**[SIZE=1]Unable to connect to the master backend[/SIZE]**


I believe its permissions. Maybe somethings wrong with Mysql. Mybe firewall blocked. Does ubuntu  10.10 have a  bultin firewall or does it have to be installed?  I know I set up the front end and backend right.
I watched all the utube videos on setting up mythtv. Just won't fly
I have the Hdhomerun. I can watch tv on HDHR config GUI.
Can't even watch on Mythtv.
If I get help with this I'll donate to the forum.
I've still got a foot in the windows 7 grave if I cant get it to fly.

---

### Post by uRock on 2011-03-28
What have you tried? What are your hardware specs?

I doubt your thread title will draw much help.

---

### Post by Ziton on 2011-03-28
> **uRock said:**
> What have you tried? What are your hardware specs?

I doubt your thread title will draw much help.
I've tried every possible ip address that's possible .
I had it working to some degree on ubuntu 10.4
Now I can't get it to do anything.
I have a ASUS mb 3.5ghz duel core 2 gigs memory, onboard ethernet and sound
nvidea graphics,64bit ubuntu 10.10.
I get channels when scanned.
The only snag now is connecting the front to the back.
It must be the firewall, permissions or mysql.
I cant get to mysql.txt says permission denied.
I can't get to the root folder permission denied

---

### Post by wt8008 on 2011-03-28
Is there a reason you choose Ubuntu instead of Mythbuntu?

Did you configure your mythtv backend yet? Do you get any error messages when you try to start the backend?

I also recommend you give your thread a better title, and more information if you want help.

---

### Post by wt8008 on 2011-03-28
> **Ziton said:**
> I've tried every possible ip address that's possible .
I had it working to some degree on ubuntu 10.4
Now I can't get it to do anything.
I have a ASUS mb 3.5ghz duel core 2 gigs memory, onboard ethernet and sound
nvidea graphics,64bit ubuntu 10.10.
I get channels when scanned.
The only snag now is connecting the front to the back.
It must be the firewall, permissions or mysql.
I cant get to mysql.txt says permission denied.
I can't get to the root folder permission denied

Verify that your backend is running, you can use
```
ps aux | grep myth
```
to see if it is up.

---

### Post by Ziton on 2011-03-28
> **uRock said:**
> What have you tried? What are your hardware specs?

I doubt your thread title will draw much help.
How do you change the title?

---

### Post by Ziton on 2011-03-28
> **wt8008 said:**
> Verify that your backend is running, you can use
```
ps aux | grep myth
```to see if it is up.
 What am I looking for?

---

### Post by wt8008 on 2011-03-28
Paste that code into a terminal and post the output, so we can see if the backend is running, since if it is not running, you will not be able to connect to it.

---

### Post by Ziton on 2011-03-28
> **wt8008 said:**
> Is there a reason you choose Ubuntu instead of Mythbuntu?

Did you configure your mythtv backend yet? Do you get any error messages when you try to start the backend?

I also recommend you give your thread a better title, and more information if you want help.
I like ubuntu better than mythbuntu, I've got both.
Tried to change the title.

---

### Post by Ziton on 2011-03-28
It would be great if I could install and get working my second nic card.
So I can run the HDHR and and hughesnet at the same time.

---

### Post by wt8008 on 2011-03-28
It appears the backend is running. The next thing I would try is verifying your frontend settings to make sure they are correct for connecting to the backend. Verify the IP address, and database information. If you have the front and backends on the same machine, then the IP is 127.0.0.1 for localhost. The default database name is mythconverg, username is mythtv, and the password is located in a file /etc/mythtv/mysql.txt; it sounds like you are having issues accessing this file. You need administrator access so use "sudo" in front of the command. If you wanted to do this on the terminal:
```
sudo cat /etc/mythtv/mysql.txt
```
It will show the password that you should use in the frontend configuration.

If the problem isn't there, then we would have to take a look into the backend settings.

---

### Post by Ziton on 2011-03-28
What's wrong with the title?:confused:
I've been trying to get this working all day. 
I'm bushed

---

### Post by Ziton on 2011-03-28
How do I change administrator access?

---

### Post by wt8008 on 2011-03-28
Are you getting the cannont connect to backend error message with those settings?

If yes, start to describe what you have done with the backend settings/setup.

---

### Post by Ziton on 2011-03-28
Ive changed everything over again.
I had it running on mythbuntu 10.4 yesterday.
I cant even get to the backend now.
Is there some way to reset the frontend and or backend?

---

### Post by Ziton on 2011-03-28
Myth could not connect to the database. Please verify your database settings below. Required fields are marked with *

**No UPnP backends found**

---

### Post by Ziton on 2011-03-28
This installment of mythtv has    not even connected once.I know the IP setting were correct. Must be a firewall,permissions or mysql bug.

---

### Post by wt8008 on 2011-03-28
> **Ziton said:**
> Myth could not connect to the database. Please verify your database settings below. Required fields are marked with *

**No UPnP backends found**

It appears your MySQL password is incorrect. Try running:
```
sudo dpkg-reconfigure mythtv-common
```
to reset the password.

---

### Post by Ziton on 2011-03-28
> **wt8008 said:**
> It appears your MySQL password is incorrect. Try running:
```
sudo dpkg-reconfigure mythtv-common
```to reset the password.
I set the password to mythtv.
Host mysql server resides in:
What goes here?
127.0.0.1 
or 
localhost
or 
ip address: 169.254.132.68

---

### Post by wt8008 on 2011-03-28
Also make sure mysqld is running with:
```
ps aux | grep mysql
```

127.0.0.1 and localhost are the same thing, which means the computer that mythtv is running on.

---

### Post by Ziton on 2011-03-28
what else can be checked?

---

### Post by wt8008 on 2011-03-28
Try to login to mysql with
```
mysql -u mythtv -p
```
it will ask you for the database password. If successful you will see the mysql prompt, to exit type `quit'
```
mysql> quit
```

If you can login and your frontend settings are good, then it is time to focus on the backend settings.

---

### Post by Ziton on 2011-03-28
I think this may be the problem.

---

### Post by wt8008 on 2011-03-29
Read the section "Access denied for user: 'mythtv@localhost' at [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

Document what happens/you saw for each case if you need additional help.

---

### Post by Ziton on 2011-03-29
I reinstalled Ubuntu 10.10 and mythtv. That didn't solve it bit I had enough confidence in it to fix the password error in mysql.
Thanks

---

### Post by wt8008 on 2011-03-29
Unforutnely, I am not in front of your computer, and only can tell you to try different things to help you figure out the solution yourself.

Glad that you were able to fix it.

---

### Post by bance on 2011-03-29
Check your hostname/ IP address in the following files:-


[LIST]
[*]~/user/.mythtv/config.xml
[*]~/user/,mythtv/mysql.txt
[*]~/.mythtv/config.xml
[*]~/.mythtv/mysql.txt
[*]/etc/mythtv/config.xml
[*]/etc/mythtv/mysql.txt
[*]/etc/hosts
[/LIST]
they should all match what you have in your backend setup

---

