---
title: "Upstart and Sudo - Emails from Root"
date: 2010-08-31
forum: General Help
---

### Post by Johnnytk36 on 2010-08-31
I am getting a weird issue.

I am running 10.04 of Ubuntu. I have Postfix mail server installed and set to send alerts.

When I have the following script in the in a /etc/init/airvideo.conf file as described here [http://wiki.birth-online.de/know-how/hardware/apple-iphone/airvideo-server-linux](http://wiki.birth-online.de/know-how/hardware/apple-iphone/airvideo-server-linux).


```
start on runlevel [2345]
stop on shutdown
respawn

exec sudo -H -n -u johnnytk36 /usr/bin/java -jar /home/johnnytk36/AVS/AirVideoServerLinux.jar /home/johnnytk36/AVS/avs.properties
```When i boot up the Air Video server starts perfectly and i have no issues with it. What im having a issue with is that IF i have the airvideo.conf file in the etc/init/ folder like it needs to be to boot i receive a email from my Postfix server with the subject. 
```
*** SECURITY information for Server ***
```& a body  of ```
Server : Aug 30 18:30:30 : root :  ***

```The *** in the body is usually some random strange combo of a few characters.

I think it has to do with permissions, i just don't know where the issue is. I think the email is trying to tell me that something tried to guess my root pass.


I know this said it was for Karmic Linux and it I'm using Lucid. That might be the issue, i don't know.
[B]
UPDATE:[/B] After spending 6 hours debugging this all i could, i cant figure it out. I have narrowed it down to the fact that we are using the sudo command while already in root. I think that triggers the email to be sent. It seems to be bypassing any setting i can think of to stop this. I have tried to edit the sudoers file to not allow email sent, but no matter what i did. It didn't work.

This is what i added to the sudoers file:

```
Defaults    mail_always=off
Defaults    mail_badpass=off
Defaults    mail_no_user=off
Defaults    mail_no_host=off
Defaults    mail_no_perms=off
```Here is the auth log output:

```
Aug 31 02:05:21 Server sudo:     root : TTY=unknown ; PWD=/ ; USER=johnnytk36 ; COMMAND=/bin/bash -c /usr/bin/java -Djava.awt.headless=true -jar /opt/AVS/AirVideoServerLinux.jar /opt/AVS/avs.properties
```Could if be the fact that the sudeurs file is only readable by root?

Any help is appreciated. 

I've given up for now and I'm just going to do a filter in Gmail to delete the email as soon as it comes in. This might be a true bug, but i dont care anymore. If anyone else using 10.04 sees this, let me know, so i know i'm not alone.

[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)
[B]
UPDATE 2: Fixed[/B]

It was my hostname in the host files and real hostname didn't match. I had changed it a few weeks ago. I still dont know why the sudeors file ignored my settings not to send emails though.

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/530073](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/530073)

---

