---
title: "Starting programs after in ubuntu 10.10"
date: 2011-06-14
forum: General Help
---

### Post by phampson on 2011-06-14
Hello

I have 3 programs webmin zabbix-client and simplehelp which I cant get to start when the server reboots

All of 3 of them start after the machine has started using the respective scripts in /etc/init.d. EG to start zabbix you run 
sudo /etc/init.d/zabbix-agent start.

They are linked into /etc/rc2.d rc3.d etc

I have placed echos in each script so i can tell when they run

None of them are called when going into run level 2.

I also added the calls into /etc/rc.local and this doesnt seem to run either.

Finally i created a file called paul which echos the time and test to a logfile. I then linked this into rc2.d

This doesnt run either.

Am I missing something very basic here. I know the init process has changed but you should according to what Ive read still be able to use the old method of starting programs. Others are started here and work fine.

Could someone point me in the right direction.

I also installed Boot-Up Manager (bum) which lists zabbix-agent and simplehelp as services but doesnt know if they are running. It doesnt list webmin at all

Thanks

Paul

---

### Post by phampson on 2011-06-15
I beginging to think I am missing a step. Do you need to switch on the rc style of starting programs. Is there another file needed to allow them to run.

Or how can i add the programs into the init startup.

Done some more work and have added an echo into jtrac which does start. Its does using the script in /etc/rc2.d.

Ive also put the script /etc/init.d/rc into debug mode and then run it. It lists all the scripts in the /etc/rc2.d directory.

But its no running some of them. As i said before it doesnt run /etc/rc.local all the files have 755 permissions.

---

### Post by phampson on 2011-06-17
Well using upstart Ive managed to get zabbix-agent starting auto

Will try and use for simplehelp and webmin now

Couldnt see any reason why zabbix wasnt starting under /etc/init.d

---

