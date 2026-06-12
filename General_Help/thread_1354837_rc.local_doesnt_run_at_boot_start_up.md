---
title: "rc.local doesnt run at boot start up"
date: 2009-12-14
forum: General Help
---

### Post by mikecarlone on 2009-12-14
**rc.local doesnt run at boot start up** 			
 			 			 		   		 		 		if i run the command  " update-rc.d rc.local defaults "

then i get 

" update-rc.d: warning: rc.local stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
System start/stop links for /etc/init.d/rc.local already exist.

 "

how can i start rc.local at boot up

---

### Post by SPr on 2009-12-14
If you have only edited /etc/rc.local you don't need to run update-rc.d It is only used if you have created a script in /etc/init.d/

---

### Post by mikecarlone on 2009-12-14
firstly thx for replaying, yes i just editet rc.local  and added things for trackpoint speed and sensitivity, everything worked well but now rc.local is not automaticly stared at boot/start up.
if i start it  sudo /etc/rc.local then track point has the setting which i gave there. hence i think rc.local is not added to start up. also it doesnt boot with. 

any ideas?
thx

---

### Post by mikecarlone on 2009-12-14
still no help?

---

### Post by bodhi.zazen on 2009-12-14
Post the contents of rc.local

You can test if it runs with a simple comment

echo "rc.local runs" >> /root/rc.txt

I would bet your commands are off, most common you list the command when you should be using the full path.

---

### Post by mikecarlone on 2009-12-14
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
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select
exit 0



also there is no output i added it to rc.local echo "rc.local runs" >> /root/rc.txt and there was no rc.txt file created. only after i run it manually sudo /etc/rc.local then the file was created.

---

### Post by mikecarlone on 2009-12-14
why doesnt help anybody?
how can i start rc.local automaticly on start up?

---

### Post by SPr on 2009-12-14
```

su - root -c "echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity"
su - root -c "echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed"
su - root -c "echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select"

```
Also make sure those paths already exist.

Edit:
```

su - root -c "echo -n 255 2> /home/USER/rc.local.log 1> /sys/devices/platform/i8042/serio1/serio2/sensitivity"
su - root -c "echo -n 255 2>> /home/USER/rc.local.log 1> /sys/devices/platform/i8042/serio1/serio2/speed"
su - root -c "echo -n 1 2>> /home/USER/rc.local.log 1> /sys/devices/platform/i8042/serio1/serio2/press_to_select"

```

They will be better because errors will be sent to /home/USER/rc.local.log. Change USER to your user name else it wont work.

---

### Post by bodhi.zazen on 2009-12-14
> **SPr said:**
> ```

su - root -c "sudo echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity"
su - root -c "echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed"
su - root -c "echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select"

```Also make sure those paths already exist.

you do not need "su - root -c " as rc.local is run by root already.

@mikecarlone

What makes you feel rc.local is not running ?

Did you add my echo ?

```
echo "rc.local" > /root/rc.txt
```boot and run 

sudo cat /root/rc.txt

---

### Post by JBAlaska on 2009-12-14
@ bodhi.zazen, small typo in your last post, I think:

Should be:
```
echo "rc.local runs" >> /root/rc.txt
```

---

### Post by mikecarlone on 2009-12-14
[[COLOR=#980101]**@bodhi.zazen **[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")
yes i added you echo. and the file was not created. also rc.local not working at start up. it is fix.

how can i run rc.local automatically at start up
[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

---

### Post by bodhi.zazen on 2009-12-14
Problems with rc.local are almost never due to rc.local "not running' at boot.

You may have errors in your script, in which case it exits. You also say you made updates with update-rc.d, so, really, hard to tell what your current problem may be.

How about if you :

```
ls -la /etc/rc2.d
```Is rc.local listed ?
Is rc.local executable (ls -la /etc | grep rc.local ) ?

---

### Post by mikecarlone on 2009-12-14
yes it is listed and executable

total 20
drwxr-xr-x   2 root root  4096 2009-12-14 16:07 .
drwxr-xr-x 150 root root 12288 2009-12-14 23:20 ..
lrwxrwxrwx   1 root root    19 2009-12-14 01:10 K20rc.local~ -> ../init.d/rc.local~
lrwxrwxrwx   1 root root    20 2009-12-11 19:03 K20trackpoint -> ../init.d/trackpoint
-rw-r--r--   1 root root   677 2009-11-10 10:44 README
lrwxrwxrwx   1 root root    20 2009-10-31 14:56 S20kerneloops -> ../init.d/kerneloops
lrwxrwxrwx   1 root root    23 2009-11-15 13:20 S20openbsd-inetd -> ../init.d/openbsd-inetd
lrwxrwxrwx   1 root root    15 2009-12-13 21:12 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root    27 2009-10-31 14:56 S20speech-dispatcher -> ../init.d/speech-dispatcher
lrwxrwxrwx   1 root root    20 2009-10-31 15:55 S20sysfsutils -> ../init.d/sysfsutils
lrwxrwxrwx   1 root root    13 2009-12-13 21:12 S23ntp -> ../init.d/ntp
lrwxrwxrwx   1 root root    19 2009-10-31 14:56 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root    14 2009-10-31 14:56 S50cups -> ../init.d/cups
lrwxrwxrwx   1 root root    17 2009-11-15 13:20 S50proftpd -> ../init.d/proftpd
lrwxrwxrwx   1 root root    20 2009-10-31 14:56 S50pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root    15 2009-10-31 14:56 S50rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root    15 2009-10-31 14:56 S50saned -> ../init.d/saned
lrwxrwxrwx   1 root root    19 2009-10-31 14:56 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx   1 root root    18 2009-10-31 14:56 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx   1 root root    24 2009-10-31 14:56 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root    22 2009-10-31 14:56 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2009-10-31 14:56 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx   1 root root    21 2009-10-31 14:56 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2009-10-31 14:56 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx   1 root root    18 2009-12-14 16:07 S99rc.local -> ../init.d/rc.local

---

### Post by mikecarlone on 2009-12-14
but if i typ ctrl+alt+f8 rc.local not seem there.

---

### Post by bodhi.zazen on 2009-12-14
> **mikecarlone said:**
> yes it is listed and executable

total 20
drwxr-xr-x   2 root root  4096 2009-12-14 16:07 .
drwxr-xr-x 150 root root 12288 2009-12-14 23:20 ..
lrwxrwxrwx   1 root root    19 2009-12-14 01:10 K20rc.local~ -> ../init.d/rc.local~
lrwxrwxrwx   1 root root    20 2009-12-11 19:03 K20trackpoint -> ../init.d/trackpoint
-rw-r--r--   1 root root   677 2009-11-10 10:44 README
lrwxrwxrwx   1 root root    20 2009-10-31 14:56 S20kerneloops -> ../init.d/kerneloops
lrwxrwxrwx   1 root root    23 2009-11-15 13:20 S20openbsd-inetd -> ../init.d/openbsd-inetd
lrwxrwxrwx   1 root root    15 2009-12-13 21:12 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root    27 2009-10-31 14:56 S20speech-dispatcher -> ../init.d/speech-dispatcher
lrwxrwxrwx   1 root root    20 2009-10-31 15:55 S20sysfsutils -> ../init.d/sysfsutils
lrwxrwxrwx   1 root root    13 2009-12-13 21:12 S23ntp -> ../init.d/ntp
lrwxrwxrwx   1 root root    19 2009-10-31 14:56 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root    14 2009-10-31 14:56 S50cups -> ../init.d/cups
lrwxrwxrwx   1 root root    17 2009-11-15 13:20 S50proftpd -> ../init.d/proftpd
lrwxrwxrwx   1 root root    20 2009-10-31 14:56 S50pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root    15 2009-10-31 14:56 S50rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root    15 2009-10-31 14:56 S50saned -> ../init.d/saned
lrwxrwxrwx   1 root root    19 2009-10-31 14:56 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx   1 root root    18 2009-10-31 14:56 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx   1 root root    24 2009-10-31 14:56 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root    22 2009-10-31 14:56 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2009-10-31 14:56 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx   1 root root    21 2009-10-31 14:56 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2009-10-31 14:56 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx   1 root root    18 2009-12-14 16:07 S99rc.local -> ../init.d/rc.local

You have a few bad links there :

> lrwxrwxrwx   1 root root    19 2009-12-14 01:10 K20rc.local~ -> ../init.d/rc.local~
lrwxrwxrwx   1 root root    18 2009-12-14 16:07 S99rc.local -> ../init.d/rc.local

First, rc.local~ is probably a back up file, and so no need for a link.

Otherwise, looks good.

Make a simple script, with say and echo statement, and NOTHING ELSE.

My guess is that either your path is wrong or rc.local is running too early ( /sys is not yet mounted). You can try adding a sleep, or testing for the existence of the file.

---

### Post by mikecarlone on 2009-12-15
please can you give me how i cann add sleep or other think. i dont know it as good as you.
 please help me. and how can i remove the link for rc.local~

thank you

---

### Post by Slim Odds on 2009-12-15
Can we see your rc.local?

That might tell us what's wrong.

---

### Post by mikecarlone on 2009-12-15
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

echo "rc.local runs" >> /etc/rcsuat.txt

echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select




exit 0

--------------------

and here are the permission of the rc.local 

-rwxr-xr-x 1 root root 598 2009-12-15 00:14 rc.local



as i said if i type "ctrl+alt+f8"  rc.local is not there also that means it doesnt boot up with.

thx

---

### Post by bodhi.zazen on 2009-12-15
> **mikecarlone said:**
> please can you give me how i cann add sleep or other think. i dont know it as good as you.
 please help me. and how can i remove the link for rc.local~

thank you

use unlink to remove links to rc.local~

```
sudo unlink /etc/rc2.d/rc.local~
```

remove with 

```
rm /etc/rc.local~
```

sleep is, well sleep

```
sleep 30
echo "it works" > /root/rc.txt
```

---

### Post by fibercode on 2009-12-15
Run this:

ls -l /etc/rc?.d/*rc.local

You should get back this:

lrwxrwxrwx 1 root root 18 2008-11-09 06:59 /etc/rc2.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2008-11-09 06:59 /etc/rc3.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2008-11-09 06:59 /etc/rc4.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2008-11-09 06:59 /etc/rc5.d/S99rc.local -> ../init.d/rc.local

I did not see any of your run levels posted before (those are the rc?.d).

To be sure, first remove rc.local by doing this:

sudo update-rc.d -f rc.local remove

And then add it back in with this:

sudo update-rc.d rc.local defaults

---

### Post by mikecarlone on 2009-12-15
hey thx after adding sleep time i works. why it works now? what happens when rc.local sleeps?
thx

---

### Post by mikecarlone on 2009-12-15
lrwxrwxrwx 1 root root 18 2009-12-14 16:07 /etc/rc2.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2009-12-14 16:07 /etc/rc3.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2009-12-14 16:07 /etc/rc4.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 18 2009-12-14 16:07 /etc/rc5.d/S99rc.local -> ../init.d/rc.local




root@sc:/etc# sudo update-rc.d -f rc.local remove
 Removing any system startup links for /etc/init.d/rc.local ...
   /etc/rc2.d/S99rc.local
   /etc/rc3.d/S99rc.local
   /etc/rc4.d/S99rc.local
   /etc/rc5.d/S99rc.local



root@sc:/etc# sudo update-rc.d rc.local defaults
update-rc.d: warning: rc.local stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
 Adding system startup for /etc/init.d/rc.local ...
   /etc/rc0.d/K20rc.local -> ../init.d/rc.local
   /etc/rc1.d/K20rc.local -> ../init.d/rc.local
   /etc/rc6.d/K20rc.local -> ../init.d/rc.local
   /etc/rc2.d/S20rc.local -> ../init.d/rc.local
   /etc/rc3.d/S20rc.local -> ../init.d/rc.local
   /etc/rc4.d/S20rc.local -> ../init.d/rc.local
   /etc/rc5.d/S20rc.local -> ../init.d/rc.local

---

### Post by mikecarlone on 2009-12-15
for exampel, if i add sleep 10, it is okey. but if i add sleep 3 it is not ok.  what makes these 7 seconds here the diffrent?

---

### Post by fibercode on 2009-12-15
rc?.d is the run level,
The "S" and "K" mean "Start" and "Kill" respectively and then the number after S and K is the priority.

What concerns me is that you have kill events in run levels 0, 1 and 6.

Can you do the following?

sudo update-rc.d -f rc.local remove

and then:

sudo update-rc.d rc.local start 99 2 3 4 5 .

The "." at the end of the command is important.

This should solve your issue.

---

### Post by bodhi.zazen on 2009-12-15
Well, to be honest, you are messing with system files without knowing what you are doing.

I always assume anyone who runs update-rc.d knows what that command is doing , so my mistake, I should not have assumed you know what you are doing.

Your other mistake is to have assumed rc.local was not running, it is running, it is exiting with an error.

If you want to debug, you need to post the contents of rc.local ;)

From your previous post I assume you are wanting to adjust ststem settings, specifially files such as /sys/devices/platform/i8042/serio1/serio2/sensitivity .

If these commands are running too soon, before /sys is mounted, your command would fail with an error message, such as no such file (or similar) and rc.local will exit with an error code.

The sleep allows time for /sys to mount. 

Cut the sleep as low as possible, 10, 5, 2 sec, whatever works.

Last, to fix your links, you can run :

```
sudo update-rc.d -f rc.local remove
sudo ln -s /etc/init.d/rc.local /etc/rc2.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc3.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc4.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc5.d/S99rc.local
```This restores the defaults of rc.local

---

### Post by fibercode on 2009-12-15
> **bodhi.zazen said:**
> 

```
sudo update-rc.d -f rc.local remove
sudo ln -s /etc/init.d/rc.local /etc/rc2.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc3.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc4.d/S99rc.local
```



@bodhi.zazen

Is there a particular reason why you are omitting run level 5?

---

### Post by bodhi.zazen on 2009-12-15
No. Ubuntu really does not use runlevels any longer and honestly I doubt the Op needs any but the link in rc2.d anyway :p

I will add it in

---

### Post by mikecarlone on 2009-12-15
no, no success.  it is the same no changes. there is no effect like sleep 10

sudo update-rc.d -f rc.local remove
sudo ln -s /etc/init.d/rc.local /etc/rc2.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc3.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc4.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc5.d/S99rc.local
or 
sudo update-rc.d -f rc.local remove

and then:

sudo update-rc.d rc.local start 99 2 3 4 5 .


always as before

 Removing any system startup links for /etc/init.d/rc.local ...
   /etc/rc2.d/S99rc.local
   /etc/rc3.d/S99rc.local
   /etc/rc4.d/S99rc.local
   /etc/rc5.d/S99rc.local
suat@sc:~$ sudo update-rc.d rc.local defaults
update-rc.d: warning: rc.local stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
 Adding system startup for /etc/init.d/rc.local ...
   /etc/rc0.d/K20rc.local -> ../init.d/rc.local
   /etc/rc1.d/K20rc.local -> ../init.d/rc.local
   /etc/rc6.d/K20rc.local -> ../init.d/rc.local
   /etc/rc2.d/S20rc.local -> ../init.d/rc.local
   /etc/rc3.d/S20rc.local -> ../init.d/rc.local
   /etc/rc4.d/S20rc.local -> ../init.d/rc.local
   /etc/rc5.d/S20rc.local -> ../init.d/rc.local

---

### Post by bodhi.zazen on 2009-12-15
Why do you keep running this command ?

> sudo update-rc.d rc.local defaults

---

### Post by mikecarlone on 2009-12-15
because i truned off the laptop. and after that my tackpoint has no setting which i gave in rc.local.

only after i did defaults. but no success. it only helps sleep 10.

---

### Post by bodhi.zazen on 2009-12-15
update-rc.d does not do what you think it does.

Follow the instructions in either my post or fibercode's post to restore your defaults.

Then if it is not working, re-post the contents of you file , rc.local

---

### Post by mikecarlone on 2009-12-15
no success. i did your way. but the content of rc.local is not running.


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

echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select




exit 0

---

### Post by bodhi.zazen on 2009-12-15
There is no sleep in that file.

Add sleep before those commands.

---

### Post by mikecarlone on 2009-12-15
if i add sleep it is always ok as i said. without sleep it is not runnig. with sleep ok.

it was okey before dooing it also in condution with adding sleep.

sudo update-rc.d -f rc.local remove
sudo ln -s /etc/init.d/rc.local /etc/rc2.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc3.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc4.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc5.d/S99rc.local

---

### Post by bodhi.zazen on 2009-12-15
> **mikecarlone said:**
> if i add sleep it is always ok as i said. without sleep it is not runnig. with sleep ok.

it was okey before dooing it also in condution with adding sleep.

sudo update-rc.d -f rc.local remove
sudo ln -s /etc/init.d/rc.local /etc/rc2.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc3.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc4.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc5.d/S99rc.local

As I have indicated, you need to add a sleep to allow the system to mount /sys , lol

---

### Post by mikecarlone on 2009-12-15
thats ok. but why should i run this command because it didnt  help me.

but thank you your help. thank you very much. with sleep it is working.

sudo update-rc.d -f rc.local remove
sudo ln -s /etc/init.d/rc.local /etc/rc2.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc3.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc4.d/S99rc.local
sudo ln -s /etc/init.d/rc.local /etc/rc5.d/S99rc.local

---

### Post by fibercode on 2009-12-15
I agree with bodhi.zazen.

You have to allow for the /sys to mount first before you can even create and write to those files.

1. Stop removing and adding the rc.local to the run levels.
Just restore the defaults like in previous posts. 

Obviously if it creates these files after the sleep command it is actually getting executed.

So no need to tinker with update-rc.d once you restore the defaults. No matter how many times you reboot.

2. Put the sleep command in the rc.local script.

---

### Post by renkinjutsu on 2009-12-15
By default, rc.local should be the last script to be executed. So The problem is not with sleep, but rather, it's a workaround until the actual fix comes along.. i think your rc.local maybe being executed too soon.

it should be the LAST script that executes. Anyone who's update-whatever-savvy able to get this behavior back?

---

### Post by mikecarlone on 2009-12-15
> **fibercode said:**
> I agree with bodhi.zazen.

You have to allow for the /sys to mount first before you can even create and write to those files.

1. Stop removing and adding the rc.local to the run levels.
Just restore the defaults like in previous posts. 

Obviously if it creates these files after the sleep command it is actually getting executed.

So no need to tinker with update-rc.d once you restore the defaults. No matter how many times you reboot.

2. Put the sleep command in the rc.local script.

no i restored it by typind " sudo update-rc.d rc.local defaults " but no success. the only way is adding " sleep 10 "

---

### Post by Morientes on 2009-12-16
Yeah, adding sleep 10 seems like a hack, am I right?

I have the same problem...

---

### Post by mikecarlone on 2009-12-17
yes youre right, i tried typing init 2 ,3 ,4 ,5 to change the run revel. but no success. this is the only way adding sleep.

---

### Post by bodhi.zazen on 2009-12-17
> **mikecarlone said:**
> yes youre right, i tried typing init 2 ,3 ,4 ,5 to change the run revel. but no success. this is the only way adding sleep.

It is because things such as /proc and /sys are virtual file systems, and are created as the system boots.

In order to decrease boot time, various processes are being run simultaneously, and so rc.local is running before /sys is mounted, thus your commands fail, and rc.local exits with an error code.

The sleep allows time for /sys to be mounted, lol

---

### Post by mikecarlone on 2009-12-17
youre right too. your way helpt me thx again.

---

### Post by dcstar on 2009-12-17
> **bodhi.zazen said:**
> It is because things such as /proc and /sys are virtual file systems, and are created as the system boots.

In order to decrease boot time, various processes are being run simultaneously, and so rc.local is running before /sys is mounted, thus your commands fail, and rc.local exits with an error code.


Ahh, the pursuit of "fast boot time" claims another victim.....  ;)

BTW, great work on this thread, I certainly would not have that much patience with people who blatantly refuse to follow (repeated) good advice.

---

### Post by sisco311 on 2009-12-17
How about an Upstart job?

/etc/init/myjob.conf:
```

description     "set TrackPoint sensitivity and speed & simulate left click"
author          "sisco311"

start on virtual-filesystems

script
  echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
  echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed
  echo -n   1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select
end script
```

---

### Post by mumi on 2009-12-20
Hallo. I had same problems with the rc.local not running. After the MANY good advises i found here, i was digging deeper and deeper and found the solution. It WAS concurrency!!!!

At some time i had changed the concurrency field in /etc/init.d/rc from "none" to "shell". This lead to the same conclusion as you guys had... the system was to fast and the rc.local was runing way before the /sys folder was ready. Thats why the 10 seconds made the difference.

I hope this could help the case...

ps: The sleep command... THX a lot for that.. helped me with other issues :0)

---

