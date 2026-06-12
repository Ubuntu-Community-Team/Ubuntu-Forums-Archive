---
title: "Shell Command to Identify Current Network"
date: 2012-04-05
forum: General Help
---

### Post by kevinfitch83 on 2012-04-05
Does anyone know of a shell command I could use to identify the network I am currently on?

Let me explain what I'm attempting to do. I'm writing up a shell script which will backup data from my laptop to a Linux box I have set up at home. This script will be setup as a cron job which will run every once in a while. I only want this script to attempt to perform the backup when I am at home so I'm looking for a way to make sure I'm on my home network before the backup begins.

I'm very much a noob when it comes to shell scripting so if I'm going about this the wrong way I would be happy to be corrected.

Thanks.

---

### Post by kazztan0325 on 2012-04-06
Hi kevinfitch83,

Actually I am not good at using Shell Commands and cannot write Shell Scripts, so I would have to apologize to you if my reply would be beside the point.

What about using **ifconfig** or **netstat**?

---

### Post by kevinfitch83 on 2012-04-06
It is true that I could use 'ifconfig' and pull my current ip. The only problem is that my home router does not support handing out static ip's so I couldn't use a particular ip as a indicator. However, one thing I could do is configure my router to hand out non-standard ip's (e.g. 192.168.48.X versus the typical 192.168.1.X) and then run the script if I'm on 48. I was just looking for a more elegant solution than that.

Either way it's not a huge deal. If I'm not on my network rsync will give a error message if it can't connect to the remote machine so it will be obvious what the issue is.

---

### Post by Cheesemill on 2012-04-06
If it is a wireless conection then you could use something along the lines of:
```
if [ "$(iwconfig wlan0 | grep ESSID | cut -d '"' -f 2)" = 'xxx' ] ; then echo "run backup" ; fi
```
Replacing xxx with your wireless network ESSID and the echo command with a call to your backup script.

---

### Post by kevinfitch83 on 2012-04-17
NIce. Thanks Cheesemill. I'll play around with this.

---

