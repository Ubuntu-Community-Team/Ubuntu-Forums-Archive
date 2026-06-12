---
title: "Shell file not running through crontab ???"
date: 2010-06-22
forum: General Help
---

### Post by tapobrata on 2010-06-22
HI ALL,
CAN ANY BODY HELP ME....?????
I HAVE WRITTEN A SHELL FILE THAT WILL STOP A JAVA (SOCKET PROGRAM)PORT LISTENER PROGRAM FROM CRON ON SCHEDULED BASIS.
BUT SOMETIMES IT IS NOT WORKING SOMETIMES IT WORKS.......
I AM POSTING THE SHELL FILE ---
 
StopPortReader6604.sh ----
 
#!/bin/bash
PID=$(ps -ef | grep "Gprs6604PortReader" | grep -v grep | awk '{print $2}')
echo $PID
kill -9 $PID
exit
 
After Stopping the shell file I have a shell file that will restart it...
 
StartPortReader6604.sh -----
 
#!/bin/bash
cd /APP/app/src/net/gprs/
/APP/jdk1.5.0_08/bin/java -classpath .:/APP/jdk1.5.0_08/lib:/APP/jboss-4.0.5.GA/server/default/lib/jboss-j2ee.jar:/APP/jboss-4.0.5.GA/server/default/lib/ojdbc14.jar:/APP/jboss-4.0.5.GA/server/default/lib/log4j.jar:/APP/jboss-4.0.5.GA/server/default/lib/mail.jar:/APP/jboss-4.0.5.GA/server/default/lib/activation.jar:/APP/jboss-4.0.5.GA/server/default/lib/dom4j.jar:/APP/jboss-4.0.5.GA/server/default/lib/javax.servlet.jar:/APP/app/src/net/lib/appvts.jar com.etrans.vts.datacollection.app.utility.Gprs6604 PortReader
exit
 
both the shell file having permission like ---
 
-rwxrwxrwx  1 root   root    925 Jun 18 12:04 StartPortReader6604.sh
-rwxrwxrwx  1 root   root    550 Jun 18 12:33 StopPortReader6604.sh
 
both the shell file run through crontab after each hour. The entry for both the shell file in crontab -e
 
11 * * * * /APP/app/cronjobs/net/StopPortReader6604.sh
12 * * * * /APP/app/cronjobs/net/StartPortReader6604.sh
 
It means cron invokes StopPortReader6604.sh and StartPortReader6604.sh for every 11th and 12th minute of an hour respectively.
 
The problem is sometimes it invokes correctly but sometime it does not.
Is it because I have mentioned #!/bin/bash at start of the shell file and the file having permission of Root????
 
Can anybody help me Please???? need suggestion........
Thanks,
Tapobrata

---

### Post by gmargo on 2010-06-22
A couple of ideas.
1. Take a look at the **killall** command. Send signals by process name instead of messing with **ps** output.
2. Never use kill -9 if you can avoid it.  At least try -15, -3, -2, -1 first.  This is because -9 (SIGKILL) cannot be caught by the targeted process, and so the process has no chance to clean up nicely.
3. You don't say what's "not working" but it's probably that the new process can't listen on the port?  Are you configuring the socket for address re-use?
4. Avoid the 11-minute/12-minute sequential nonsense by running a single script that calls both of the others.

---

### Post by gdonwallace on 2010-06-22
It could be that the commands are running into each other because they are scheduled to run at so close a time to each other.

Also, is this your user crontab or the root crontab?  That may also make a difference.  If the program that is listening on that port that you are trying to "kill" is called by "root" then it may take a "root" command to stop it.

You can create the same entry in the root crontab by typing "sudo crontab -e" and this will allow you to edit the root crontab file.  If you call just crontab-e as a normal user, it creates the crontab file for that user.

---

