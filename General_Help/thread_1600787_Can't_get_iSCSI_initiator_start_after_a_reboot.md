---
title: "Can't get iSCSI initiator start after a reboot"
date: 2010-10-19
forum: General Help
---

### Post by twotone2 on 2010-10-19
[COLOR=#000000][SIZE=3]I am currently wanting to connect to an NAS unit that I have. I have installed open-iSCSI and have made the following changes to the iscsi_conf file:

[/SIZE][/COLOR]> 
# To set a CHAP username and password for initiator 
# authentication by the target(s), uncomment the following lines: 
node.session.auth.username = "user"
node.session.auth.password = &#8220;12 digit pass&#8221; 

# To set a discovery session CHAP username and password for the initiator 
# authentication by the target(s), uncomment the following lines: 
discovery.sendtargets.auth.username = "user"
discovery.sendtargets.auth.password = &#8220;12 digit pass&#8221; 

[COLOR=#000000][SIZE=3]With these setting I can run the following command:[/SIZE][/COLOR]


> 
sudo iscsiadm --mode node --targetname pmi.ctl:ultrastorage --portal 192.168.50.6:3260 --login
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]It connects with no issue I then have to mount the drives to view the them. Once I have the initiator working properly I plan on having it auto mount after a reboot.
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]When I change : 

[/SIZE][/COLOR]> 
# To request that the iscsi initd scripts startup a session set to "automatic". 
# node.startup = automatic 
# 
# To manually startup the session set to "manual". The default is manual. 
node.startup = manual 

[COLOR=#000000][SIZE=3]

to: 

[/SIZE][/COLOR]> 
# To request that the iscsi initd scripts startup a session set to "automatic". 
node.startup = automatic 
# 
# To manually startup the session set to "manual". The default is manual. 
#node.startup = manual 
[COLOR=#000000][SIZE=3]I get this error after restarting open-iSCSI: 

[/SIZE][/COLOR]> 
* Disconnecting iSCSI targets [ OK ] 

* Stopping iSCSI initiator service [ OK ] 

* Starting iSCSI initiator service iscsid [ OK ] 

ln: target `/lib/init/rw/sendsigs.omit.d/' is not a directory: No such file or directory 

* Setting up iSCSI targets [ OK ] 

[COLOR=#000000][SIZE=3]


My goal is to get the iSCSI initiator to connect after a reboot. Mounting after connecting I am sure this will be another challenge. 
[/SIZE][/COLOR]


Please help!!!!!!!!!!!!!!!!:(

[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Thanks in Advanced[/SIZE][/COLOR]

---

### Post by shigeo_savant on 2011-01-11
bump.

I can confirm this behaviour.

the following bugs have been posted about this:
414986
306678
412186
541512

the first three mentioned bugs seem closed with "fixed in <version>" and "status: triaged" (which doesn't quite hit the nail on the head ). the last bug 541512 seems to get it right. the status as of now is "fix released".

maybe anyone else has anything on this issue?

---

