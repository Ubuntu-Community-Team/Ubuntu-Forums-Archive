---
title: "passwords gone/ changed?"
date: 2009-10-18
forum: General Help
---

### Post by Birdomuerto on 2009-10-18
my system: a Pentium 4 processor and has 512MB of ram.

my personal unix/linux literacy: low-ish to nil.

Long story short:

GUI wont load- I get something that looks like this:
 
> chown: invalid group: `root:polkituser'
*Loading ACPI modules...
*Starting ACI services...
*Starting system log daemon...
FATAL: Error inserting battery (/lib/modules/2.6.24-19-rt/kernel/drivers/acpi/battery.ko): No such device
 * Starting systen log daemon...
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'

 * Starting kernel log daemon...
chown: invalid group: `klog:klog'
chown: invalid group: `klog:klog'

(after previewing my post: where the smiley face is equal to ': p' (without the space))

after a little bit of time, the computer continues on and I'm told that 'The GDM group 'gdm' dows not exist. Please correct GDM configuration and restart GDM.

a Google search suggested that my
a)my /etc/group file is either missing or corrupt or,
b)I have a postfix problem, solved by
# /etc/init.d/gdm stop
# apt-get -f install
# apt-get install --reinstall gdm
# apt-get install --reinstall postfix
# /usr/sbin/postfix check 
(using sudo before relevant commands)

tried (a), looks like this:
> root:x:0:
nogroup:x:65534:
brian:x:1000:

(after previewing my post: where the angry face is equal to ': x' (without the space))

which may or may not be kosher... looks like something is wrong...

trying (b), sudo asks for my password, which I give- I'm then told that I'm not in the sudoers file.

further Google searching reveals that I can add myself to the sudoers file by 
> su -
echo "brian ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

but when I try this permission is denied.

my system was working great up until a half hour ago. please help.

Thanks in advance,

---

### Post by Birdomuerto on 2009-10-19
Figured out how to get root privileges and did a partial revamp of my group file following the instructions found here 
[http://psychocats.net/ubuntu/sudo](http://psychocats.net/ubuntu/sudo)  

my ability to use sudo has been restored.

The group file shown is an example... as you can see from my previous post my old group file was decimated. I've written in lines 2,3,4,102,103 and 106 (following the name: x:##: format)... what else is essential to get my system up and running as it was before - as an internet and music box?


Thanks again...
-Brian

---

### Post by Birdomuerto on 2009-10-19
huh... turns out my group.bak file has been wiped as well.

I never arbitrarily fiddle around under the hood, so I don't think this is my doing... only thing I may have done is turn off the initial login to the GUI...  that was maybe a week ago... I don't know if I restarted the system between now and then.

...anyways: I'm slowly putting my group file back together.  I was really hoping someone could at least tell me what the basic elements of the group file are. Internet seems a little sparse on explaining what my options are...

...I mean, I could cut and paste, but running Linux is a bit like owning a VW bus: if you aren't interested in learning how to fix it, then why bother?

for example: right now I can get the GUI up and running, but the keyboard and mouse aren't working.  What are the groups that control those? Where's some documentation listing out what the various groups are and what they do? Can I just write in arbitrary group names and addresses? 

Looks like I'll find out what I need by trial and error... after I've done the legwork, I'll be sure to share.

Cheers

---

