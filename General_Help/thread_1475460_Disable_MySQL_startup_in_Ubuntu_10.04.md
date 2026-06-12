---
title: "Disable MySQL startup in Ubuntu 10.04"
date: 2010-05-06
forum: General Help
---

### Post by bryanhogan on 2010-05-06
Hi all,
  
I want to prevent MySQL from starting in Ubuntu 10.04
I have used
  
update-rc.d -f mysql remove
 
and confirmed that there is no link to the /etc/inid.d/mysql  script from any of the rc?.d directories.
  
I also ran sysv-rc-conf and it shows me that MySQL is NOT  being called as part of the rc.d scripts.
It is still starting on boot.
  
How do I disable it?
  
Regards,
  
Bryan

---

### Post by longanduselessname on 2010-05-06
> **bryanhogan said:**
> Hi all,
  
I want to prevent MySQL from starting in Ubuntu 10.04
I have used
  
update-rc.d -f mysql remove
 
and confirmed that there is no link to the /etc/inid.d/mysql  script from any of the rc?.d directories.
  
I also ran sysv-rc-conf and it shows me that MySQL is  being called as part of the rc.d scripts.
It is still starting on boot.
  
How do I disable it?
  
Regards,
  
Bryan


Hmm update-rc.d is not a command in my install of Lucid. Also I haven't heard of sysv-rc-conf... what is it and how do I use it?

As for your question, I would check each of the folders manually as well as rc.local. That is how I have always done it. I think you replace the "S" with a "K". There is a README in each folder.

---

### Post by bryanhogan on 2010-05-06
> **longanduselessname said:**
> Hmm update-rc.d is not a command in my install of Lucid. Also I haven't heard of sysv-rc-conf... what is it and how do I use it?

As for your question, I would check each of the folders manually as well as rc.local. That is how I have always done it. I think you replace the "S" with a "K". There is a README in each folder.


I did check all the rc1/2/3/4.... directories.

---

### Post by longanduselessname on 2010-05-06
> **bryanhogan said:**
> I did check all the rc1/2/3/4.... directories.

And rc.local?
Well something is starting it. If the following command doesn't return anything I have no ideas.

```
grep mysql `find /etc/ |grep "rc.\."`
```Oh yea besides if it is starting when you login. That is a different story.

---

### Post by bryanhogan on 2010-05-06
> **longanduselessname said:**
> And rc.local?
Well something is starting it. If the following command doesn't return anything I have no ideas.

```
grep mysql `find /etc/ |grep "rc.\."`
```Oh yea besides if it is starting when you login. That is a different story.


your command returns no files. I have manually checked all the directories too.

rc.local is effectively empty. 

I have checked System -> Preferences -> Startup Applications

---

### Post by longanduselessname on 2010-05-07
> **bryanhogan said:**
> your command returns no files. I have manually checked all the directories too.

rc.local is effectively empty. 

I have checked System -> Preferences -> Startup Applications

Well I just checked on a 9.10 server install I have (forgot about that thing) and my command turned up a hella lot of output. Mostly from rc2.d/S19mysql.

So if that didn't turn up anything then I think we can say it isn't starting on bootup. Maybe. Is it starting when you login?

Oh yea and what user does it run as?

---

### Post by bryanhogan on 2010-05-07
> **longanduselessname said:**
> Well I just checked on a 9.10 server install I have (forgot about that thing) and my command turned up a hella lot of output. Mostly from rc2.d/S19mysql.

So if that didn't turn up anything then I think we can say it isn't starting on bootup. Maybe. Is it starting when you login?

Oh yea and what user does it run as?


I removed all the rc?.d scripts using update-rc.d 

I will try booting into single user mode and using 
 init 2,3,4,5 and check if at each level

It is running as the mysql user

---

### Post by longanduselessname on 2010-05-07
> **bryanhogan said:**
> I removed all the rc?.d scripts using update-rc.d 

I will try booting into single user mode and using 
 init 2,3,4,5 and check if at each level

It is running as the mysql user

You probably didn't want to remove ALL of them but it seems you know what you are doing. I haven't done that before. 

Good luck.

---

### Post by bryanhogan on 2010-05-07
> **longanduselessname said:**
> You probably didn't want to remove ALL of them but it seems you know what you are doing. I haven't done that before. 

Good luck.

Sorry, I meant to say that I removed all mysql links from the rc?.d directories :)

---

### Post by bryanhogan on 2010-05-07
> **bryanhogan said:**
> Sorry, I meant to say that I removed all mysql links from the rc?.d directories :)

I've put in kill scripts in all run levels - K20mysql...it is still running after boot!

---

### Post by longanduselessname on 2010-05-07
> **bryanhogan said:**
> I've put in kill scripts in all run levels - K20mysql...it is still running after boot!

Ah so there is a mysql script... wonder why my command didn't return it. 

If it is running as another user, it might be getting triggered somewhere else... 

Check if there are .rc files in /root/

Check out the init.d mysql sh script to see how mysql operates. 

Find out more about the mysqld user and how it gets started. 

Maybe run my grep command with the username instead of mysql.

That's all I got mate gl.

---

### Post by bryanhogan on 2010-05-07
> **longanduselessname said:**
> Ah so there is a mysql script... wonder why my command didn't return it. 

If it is running as another user, it might be getting triggered somewhere else... 

Check if there are .rc files in /root/

Check out the init.d mysql sh script to see how mysql operates. 

Find out more about the mysqld user and how it gets started. 

Maybe run my grep command with the username instead of mysql.

That's all I got mate gl.


The mysql script is in /etc/inid.d

---

### Post by bryanhogan on 2010-05-08
> **bryanhogan said:**
> The mysql script is in /etc/inid.d


Removed the mysql script in /etc/inid.d

I have checked the /root/ for any start up files. 

The home directory of the mysql user has no scripts that start on login. 

I'm at the stage where I'll have to rename/move the mysqld.

Where else can this be loading from on boot?

---

### Post by Ramage21 on 2010-05-08
> **bryanhogan said:**
> Removed the mysql script in /etc/inid.d

I have checked the /root/ for any start up files. 

The home directory of the mysql user has no scripts that start on login. 

I'm at the stage where I'll have to rename/move the mysqld.

Where else can this be loading from on boot?


Lucid uses upstart to launch mysql. All the files are in /etc/init  (not init.d).  Open the mysql.conf script.  The instructions for starting mysql are at the top.  As a test, you can # the "start on" line to prevent the service starting on boot up.

I am still looking at this to see how I can properly modify the script to do what I want.

See this for more info on upstart [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by bryanhogan on 2010-05-08
> **Ramage21 said:**
> Lucid uses upstart to launch mysql. All the files are in /etc/init  (not init.d).  Open the mysql.conf script.  The instructions for starting mysql are at the top.  As a test, you can # the "start on" line to prevent the service starting on boot up.

I am still looking at this to see how I can properly modify the script to do what I want.

See this for more info on upstart [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

Wow, I just figured that out in the last 10 minutes too :) 

Found this link quite useful - [http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/)

I had done exactly what you suggest, comment out the two lines connected with the "start on".

---

### Post by Ramage21 on 2010-05-08
> **bryanhogan said:**
> Wow, I just figured that out in the last 10 minutes too :) 

Found this link quite useful - [http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/)

I had done exactly what you suggest, comment out the two lines connected with the "start on".

What I have now done is add runlevel 2 to the stop line of the script which stops mysql prematurely

```
# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up
          and local-filesystems)
stop on runlevel [0126]
```I can then start and stop mysql manually using the service command

Thanks for the info ref

---

### Post by longanduselessname on 2010-05-09
> **bryanhogan said:**
> Wow, I just figured that out in the last 10 minutes too :) 

Found this link quite useful - [http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/)

I had done exactly what you suggest, comment out the two lines connected with the "start on".


I've always wondered how ubuntu started my network card, since /etc/network/interfaces by default doesn't have any configuration for eth0.

Showing my noob colors for not thinking about upstart, or really understanding how it works!

EDIT: Sorry for leading you on wrong track bryanhogan ;_;

---

### Post by TrombaMarina on 2011-08-11
Thanks!  To summarize:

sudo vim /etc/init/mysql.conf

Edit it to say the following (I move the 2 from the first set of numbers to the second):

start on (net-device-up and local-filesystems and runlevel [345])
stop on runlevel[0126]

Works like a charm!

reboot
...

initctl list
...
mysql stop/waiting

---

