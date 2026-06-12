---
title: "startup script help"
date: 2011-05-26
forum: General Help
---

### Post by scottsp64 on 2011-05-26
I have officially pulled all my hair out. 

I have been toying with linux for years but have now implemented multiple headless servers and am still learning the process of doing everything via the command line. 

I just have to yell this -- IT SHOULD NOT BE SO HARD TO GET S SCRIPT TO RUN AT STARTUP. OK, now that I have that off my mind, I will describe my problem.

I have working script, pingstorage, that I want to run at boot, after everything else loads is fine. The purpose of the script is to PING an interface on my storage network and alert me if it stops responding. It works beautifully when I execute it myself. But it is NOT working properly when I try to run it at startup.

BTW, my method of testing the script is to disable the pinged interface and see if I get some emails and TXTs.

I spent a good deal of the day yesterday trying to implement this in UPSTART. I created a PINGSTORAGE.CONF file (below) and placed it into the /etc/init folder.

Here it is.

*************MY PINGSTORAGE.CONF FILE************
# myservice - myservice job file

description "Script that pings the iSCSI backend and alerts me if it goes downn"
author "Scott <scott.blah@blahblah.com>"

# Stanzas
#
# Stanzas control when and how a process is started and stopped
# See a list of stanzas here: [http://upstart.ubuntu.com/wiki/Stanzas#respawn](http://upstart.ubuntu.com/wiki/Stanzas#respawn)

env MYSCRIPTHOME=/home/administrator/scripts

# When to start the service
start on started network-services

# When to stop the service
stop on stopping network-services

# Automatically restart process if crashed
respawn

# Essentially lets upstart know the process will detach itself to the background
expect fork

# Start the process

script
	chdir $MYSCRIPTHOME
	exec ./pingstorage
end script

******************END pingstorage.conf file********

I also tried this with it less complicated.  didnt create the nv variable and and just tried to execute it directly from /etc/init.d/pingstorage. That didn't work. 

So this morning I gave up on UPSTART and decided to go old school. I removed my pingstorage.conf file from the /etc/init. I then modified my /etc/rc.local file thusly:

**********MY /etc/rc.local file *********
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/etc/init.d/pingstorage 2>/dev/null 1>/dev/null&

exit 0
************END of MY RC.LOCAL***********

after editing rc.local, I changed the execution bits with: 
chmod u+x /etc/init.d/init.d/pingstorage
and update the boot by running:
update-rc.d pingstorage default 90 10

When I reboot my system hangs during both bootup and shutdown and I don't get a prompt at any tty. I had to boor into recovery mode and run:
rm /etc/rc*/*pingstorage to fix everything.

WHAT HAVE  I DONE WRONG?
WHY IS THIS SO HARD? 
Is there a clear and foolproof way to get a script to run at boot without a problem?

This server is a new one, 11.04 32 bit. 

Help.

---

