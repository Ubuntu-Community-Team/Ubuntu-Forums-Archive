---
title: "how to automate  up vsftp?"
date: 2006-04-15
forum: General Help
---

### Post by lezz on 2006-04-15
hi there.

i just installed vsftp with apt-get install. read some guides on the net, but unfortunately those werent about the ubuntu distro. what should you write to bring up vsftpd every time you boot up ubuntu. in suse you just have to run:

chkconfig vsftpd on

do you really have to manually make a soft link to /etc/init.d/vsftpd to the rc.X directories?

EDIT: the headline should be like "how to automate vsftpd? my mistake"

---

### Post by taurus on 2006-04-15
I am not in front of my Ubuntu machine right now but can you at least check System -> Services to see if there is an option by placing a check next to it to start vsftpd upon boot!!!

---

### Post by lezz on 2006-04-15
[QUOTE=taurus]I am not in front of my Ubuntu machine right now but can you at least check System -> Services to see if there is an option by placing a check next to it to start vsftpd upon boot!!![/QUOTE]

Oh, I forgot to tell you that I rather want to do this at the console prompt. Just to learn things =)

Every time I install daemons with apt-get they automatically put the main scripts in /etc/init.d and I believe they also create soft links to these scripts in the /etc/rcx.d directories for autoloading the daemons at boot up time. In Suse its very convinient to use the chkconfig command for this purpose. What is the standard procedure when dealing with Ubuntu? Cause it's very annoying tampering with soft links all the time with:

ln -s /etc/init.d vsftpd /etc/rc2.d/S20vsftpd
ln -s /etc/init.d vsftpd /etc/rc2.d/K80vsftpd
rm....
ln -s /etc/init.d vsftpd /etc/rc5.d/S20vsftpd
ln -s /etc/init.d vsftpd /etc/rc5.d/K80vsftpd
and so on...

---

### Post by rvergara on 2006-04-15
lezz,

Just go to System->Services and activate the service "FTP service" (vsftpd)"

Regards

Ramiro

---

### Post by lezz on 2006-04-15
I dont want to use the gui-utilities for the learnings sake =) Now I know, you just use update-rc.d. That is all i had to know. Thx for myself =)

---

