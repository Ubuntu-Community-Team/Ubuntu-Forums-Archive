---
title: "Run a script before shutting down or rebooting"
date: 2010-10-27
forum: General Help
---

### Post by CharlesA on 2010-10-27
Hi,

I wrote up a script to check to see if any VMs are running in VirtualBox, and if there are, it would save the state they are in and then reboot or shutdown the host.

Is there a way to make that script run outside of using an alias for "reboot" and "halt" when I run those two commands?

Here's the script:

```
#!/bin/bash

if [[ -n $(VBoxManage -nologo list runningvms) ]]
then
for runningvms in $(VBoxManage -nologo list runningvms | grep \" | cut -d \" -f 2)
do
VBoxManage -nologo controlvm $runningvms savestate
done
else
echo "No VMs running"
fi
```

It works fine when run from a terminal, but I'll probably forget to run it before rebooting.

Any ideas?

Thanks.

---

### Post by i.r.id10t on 2010-10-27
Put the script in /etc/init.d and link to them from within /etc/rc6.d and /etc/rc0.d

---

### Post by Hippytaff on 2010-10-27
Is /etc/rc.local editable to run the script on shutdown maybe !?

---

### Post by sikander3786 on 2010-10-27
> **i.r.id10t said:**
> Put the script in /etc/init.d and link to them from within /etc/rc6.d and /etc/rc0.d
Exactly.

Here is an explanation. Post # 3.

[http://ubuntuforums.org/showthread.php?t=185261](http://ubuntuforums.org/showthread.php?t=185261)

---

### Post by CharlesA on 2010-10-27
Thanks, that really helps explain it.

I guess I'll add an entry into cron with the @reboot time so that it'll start those saved VMs back up when the reboot is finished, unless there is a better way to go about it.

---

### Post by alienprdkt on 2010-10-27
> **CharlesA said:**
> Hi,

I wrote up a script to check to see if any VMs are running in VirtualBox, and if there are, it would save the state they are in and then reboot or shutdown the host.

Is there a way to make that script run outside of using an alias for "reboot" and "halt" when I run those two commands?

Here's the script:

```
#!/bin/bash

if [[ -n $(VBoxManage -nologo list runningvms) ]]
then
for runningvms in $(VBoxManage -nologo list runningvms | grep \" | cut -d \" -f 2)
do
VBoxManage -nologo controlvm $runningvms savestate
done
else
echo "No VMs running"
fi
```

It works fine when run from a terminal, but I'll probably forget to run it before rebooting.

Any ideas?

Thanks.

Thanks! 
Hope you don't mind sharing that script, could be very useful! any way to start a VM with virtualbox through a script?

---

### Post by Hippytaff on 2010-10-27
> **alienprdkt said:**
> Thanks! 
Hope you don't mind sharing that script, could be very useful! any way to start a VM with virtualbox through a script?

You could use an alias in .bashrc

alias vm='[I]the code to start vmbox'


[/I]

---

### Post by sikander3786 on 2010-10-27
I just found a ready made script. Me also needed one too ;-)

[http://en.gentoo-wiki.com/wiki/Virtualbox](http://en.gentoo-wiki.com/wiki/Virtualbox)

---

### Post by CharlesA on 2010-10-27
> **sikander3786 said:**
> I just found a ready made script. Me also needed one too ;-)

[http://en.gentoo-wiki.com/wiki/Virtualbox](http://en.gentoo-wiki.com/wiki/Virtualbox)
I looked thru that page but didn't really see anything about starting machines automatically on reboot.

Probably overlooked it, since it's been a long day.

---

### Post by sikander3786 on 2010-10-27
> **CharlesA said:**
> I looked thru that page but didn't really see anything about starting machines automatically on reboot.

Probably overlooked it, since it's been a long day.
Mentions how to start Virtualbox as a service.

Another one here.

[http://www.glump.net/howto/virtualbox_as_a_service](http://www.glump.net/howto/virtualbox_as_a_service)

I just had a look at both of them. Not gone in the details. I'll try them this weekend.

---

### Post by CharlesA on 2010-10-27
> **sikander3786 said:**
> Mentions how to start Virtualbox as a service.

Another one here.

[http://www.glump.net/howto/virtualbox_as_a_service](http://www.glump.net/howto/virtualbox_as_a_service)

I just had a look at both of them. Not gone in the details. I'll try them this weekend.
Yeah that's not what I want to do. I just want to start the VM up after a reboot. The VBox services are already running. :)

---

### Post by sikander3786 on 2010-10-27
> **CharlesA said:**
> Yeah that's not what I want to do. I just want to start the VM up after a reboot. The VBox services are already running. :)
Oh. My mistake.

Last Shot: There was something like vboxcontrol but that is not being developed any further. Here is an alternative.

[http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/)

---

### Post by CharlesA on 2010-10-27
Thanks for the help.

I did look into vboxtools before but since they aren't under development any longer I skipped over them.

It looks like the way the VBoxManage works, it won't find any running VMs under the username of "root"

It doesn't even find any VMs period.

I guess I'll just have to stick with an alias.

EDIT: Alias is out of the question as well, since I would be using ***sudo halt*** or ***sudo reboot***, and it won't find any VMs running. :|

EDIT2: Nevermind, got it to work, I had to tweak the alias command:

```
alias reboot='/path/to/stopvm.sh && sudo reboot'
```
```
alias halt='/path/to/stopvm.sh && sudo halt'
```

I'll just have to remember NOT to use sudo when running those, else it won't find any running vms and just reboot or power off the host. What a pain in the butt.

Also, for anyone who cares, here's the start script:

```
#!/bin/bash

###
### startvm.sh
### Script to start saved VMs up
### Created by CharlesA
### Tested 10/27/2010
### Updated 10/27/2010
###

BIN=/bin/
USR=/usr/bin/
HOME=/home/charles/
LOGS=${HOME}logs/

for vms in $(${USR}VBoxManage -nologo list vms | ${USR}awk -F \" '{ print $2 }';)
do
if [[ -n $(${USR}VBoxManage showvminfo $vms | ${BIN}grep saved) ]]
then
${USR}VBoxHeadless -s $vms > /dev/null &
fi
done
# eof
```

Stop script:

```
!/bin/bash

###
### stopvm.sh
### Script to save state of VMs
### Created by CharlesA
### Tested 10/27/2010
### Updated 10/27/2010
###

USR=/usr/bin/
HOME=/home/charles/
LOGS=${HOME}logs/

echo > ${LOGS}savevm.log
if [[ -n $(${USR}VBoxManage -nologo list runningvms) ]]
then
for runningvms in $(${USR}VBoxManage -nologo list runningvms | ${USR}awk -F \" '{ print $2 }';)
do
echo Saving state of $runningvms >> ${LOGS}savevm.log && ${USR}VBoxManage -nologo controlvm $runningvms savestate >> ${LOGS}savevm.log
done
else
echo "No VMs running"
fi
# eof

```

---

### Post by alienprdkt on 2010-11-01
Thanks Again.

---

