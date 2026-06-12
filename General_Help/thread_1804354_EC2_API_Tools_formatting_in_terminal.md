---
title: "EC2 API Tools formatting in terminal"
date: 2011-07-14
forum: General Help
---

### Post by brianjolly on 2011-07-14
The output of ec2 cli tools on my mac is nice and formatted like so:

RESERVATION     r-xxxx      xxxx    cl-xx
INSTANCE        i-xxxx      ami-xxx                  
TAG     instance        i-xxx      Name    xxxx
etc...

On my Ubuntu machine the output is very hard to read. I followed the instructions from the Ubuntu help here:
[https://help.ubuntu.com/community/EC2APITools](https://help.ubuntu.com/community/EC2APITools)

Does anyone know what I am missing to get better looking output than this?

+------------+--------------+----------------------+------------------------------------------+---------+--------------+--------------------------
------+----------------+-------------------------------------------------------------------------------------------------+--------------+---------
----------------------------------------------------------------------------------------------------------------------+--------------------+------
| instanceId |   imageId    |    instanceState     |                  reason                  | keyName | instanceType |        launchTime        
lId   |   monitoring   |                                           stateReason                                           | architecture | rootDevi
                                           blockDeviceMapping                                                         | virtualizationType |     
+------------+--------------+----------------------+------------------------------------------+---------+--------------+--------------------------
------+----------------+-------------------------------------------------------------------------------------------------+--------------+---------
----------------------------------------------------------------------------------------------------------------------+--------------------+------
| i-xxxxxxa | ami-xxxxxx | code=80 name=stopped | User initiated (2011-07-14 04:14:38 GMT) | somekey   | t1.micro     | 2011-07-14T03:46:43.000Z 
d9529 | state=disabled | code=Client.UserInitiatedShutdown message=Client.UserInitiatedShutdown: User initiated shutdown | i386         | ebs

---

### Post by Habitual on 2011-07-14
I have 211 binaries in my ~/bin/ec2/bin directory on version 1.3-62308 

what version are you running, which c-li tool and what terminal are you using?

---

### Post by brianjolly on 2011-07-14
My ec2-api-tools are version 1.4.3.0

The examples in my post were part of the output of ec2-describe-instances. Other commands are formatted in the same way though. It seems to be a general problem and not tied to a particular binary.  

I have tried both gnome-terminal and xterm in Ubuntu.  Both output exactly the same. On my mac I'm using iTerm2. 

In gnome-terminal $TERM=xterm-256color
in xterm $TERM=xterm
in iTerm2 $TERM=xterm-256color

---

### Post by Habitual on 2011-07-23
Brian:

I don't see any of the output you described (+------------+--------------+----------------------+------------------------------------------+---------+--------------+--------------------------) running ```
ec2-describe-instances -K /home/jj/.ssh/someclient/pem/pk.pem -C /home/jj/.ssh/someclient/pem/cert.pem --region us-east-1
``` here on my box. But then again, I am not using Ubuntu. Sorry.

I just see textual descriptions of the contents/structure of the instance.

GNOME Terminal 2.32.1
echo $TERM > xterm



What command are you running exactly? (sanitize the key) and show me. :)

---

