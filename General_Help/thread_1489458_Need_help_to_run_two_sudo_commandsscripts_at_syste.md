---
title: "Need help to run two sudo commands/scripts at system startup"
date: 2010-05-21
forum: General Help
---

### Post by sirf.mein on 2010-05-21
Hi..!
I want to run two sudo commands at system startup,

1.   ```
sudo rfkill block bluetooth
``` to disable bluetooth.
2. ```
 sudo mount -t ntfs /dev/sda1 /mnt/windrive -o “umask=022&#8243;
``` to mount windows partition (C: drive)

Will I have to make scripts to run these commands at startup??
If yes, where to put these scripts?

I am a new ubuntu user and don't know how to make and run scripts. I just want to run the above mentioned commands at system startup to disable bluetooth and to maunt windows partition at system start. I have spent much time find it on internet but could not find anything helpful to me, so I posted my questions here..!
 Help me please..!
Thank you in advance.:)

Regards,
Brar

---

### Post by kerry_s on 2010-05-21
put the commands in /etc/rc.local, it runs as root so you don't need sudo.

make sure you put above the "exit 0"

---

### Post by sirf.mein on 2010-05-21
> **kerry_s said:**
> put the commands in /etc/rc.local, it runs as root so you don't need sudo.

make sure you put above the "exit 0"

This method is not working..:(
Below is the code for /etc/rc.local
I have added two commands in this scrips but it did not work for me.

```
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
sudo rfkill block bluetooth
sudo mount -t ntfs /dev/sda1 /mnt/windrive -o “umask=022&#8243;
exit 0
```i have just edited /etc/rc.local , Is there any need to enable this script ? If yes, then how to? 
 I am beginner with ubuntu ..! please do provide details to do any task. Thank you

---

### Post by kerry_s on 2010-05-21
> **sirf.mein said:**
> This method is not working..:(
Below is the code for /etc/rc.local
I have added two commands in this scrips but it did not work for me.

```
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
sudo rfkill block bluetooth
sudo mount -t ntfs /dev/sda1 /mnt/windrive -o “umask=022&#8243;
exit 0
```

i have just edited /etc/rc.local , How to enable this script?? or is it already enabled by just editing it? I am beginner with ubuntu ..! please do provide details to do any task. Thank you


i told you "**no**" sudo, it's already running as root.

```
sudo rfkill block bluetooth
sudo mount -t ntfs /dev/sda1 /mnt/windrive -o “umask=022&#8243;
```
to
```
rfkill block bluetooth
mount -t ntfs /dev/sda1 /mnt/windrive -o “umask=022&#8243;
```

---

### Post by WorMzy on 2010-05-21
You can add the mount command to fstab, which is a more correct way of mounting drives. Add this to the end of /etc/fstab, on it's own line:

```
/dev/sda1 /mnt/windrive ntfs defaults,umask=022 0 0
```


You'll need to use sudo/gksu to edit the file.

---

### Post by sirf.mein on 2010-05-21
this is also not working.!

```
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
rfkill block bluetooth
mount -t ntfs /dev/sda1 /mnt/windrive -o “umask=022&#8243;
exit 0
```

Is there any need to enable this script ? If yes, then how to?

---

### Post by sirf.mein on 2010-05-21
> **WorMzy said:**
> You can add the mount command to fstab, which is a more correct way of mounting drives. Add this to the end of /etc/fstab, on it's own line:

```
/dev/sda1 /mnt/windrive ntfs defaults,umask=022 0 0
```
You'll need to use sudo/gksu to edit the file.

Thank you for your help WorMzy...!:): 
It really worked...!
I can mount C: drive at system startup. :)

Now left with one problem only,  please help me to disable bluetooth at system start.

---

### Post by SlugSlug on 2010-05-21
```
sudo update-rc.d -f bluetooth remove
```


will remove bluetooth from auto loading

---

### Post by sirf.mein on 2010-05-21
> **SlugSlug said:**
> ```
sudo update-rc.d -f bluetooth remove
```
will remove bluetooth from auto loading
Hi SlugSlug..!

Will this turn off bluetooth hardware? or it will just remove bluetooth applet from my system. I want to turn off bluetooth hardware at system startup. I should be able to turn it on anytime when needed.

---

### Post by SlugSlug on 2010-05-21
you can turn it back on

---

### Post by donato roque on 2010-05-21
hi all
I am just posting this answer because there's an easier way to do this.  

1) prevent bluetooth service from starting.  Go to Panel>System>Preferences>Startup Applications.  Select Bluetooth. You can untick the box or Remove the service entirely. 

2) mounting any partition or drive on startup.  The partition or drive must be listed in your etc/fstab file.  See this manual 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by sirf.mein on 2010-05-21
> **donato roque said:**
> hi all
I am just posting this answer because there's an easier way to do this.  

1) prevent bluetooth service from starting.  Go to Panel>System>Preferences>Startup Applications.  Select Bluetooth. You can untick the box or Remove the service entirely. 

2) mounting any partition or drive on startup.  The partition or drive must be listed in your etc/fstab file.  See this manual 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Hi [donato roque]("http://ubuntuforums.org/member.php?u=644034")..!
If I am not wrong,  disabling bluetooth service will turn off bluetooth interface but it will not turn of bluetooth. Is nt it?

---

### Post by sirf.mein on 2010-05-21
> **SlugSlug said:**
> ```
sudo update-rc.d -f bluetooth  remove
```
will remove bluetooth from auto loading



**Not working...**:(

---

### Post by doas777 on 2010-05-21
JOC, what makes you believe that bluetooth is in fact running?

---

### Post by sirf.mein on 2010-05-21
> **doas777 said:**
> JOC, what makes you believe that bluetooth is in fact running?
  Bluetooth icon is the notification area notifies that the bluetooth is turned on. I can turn it off from that bluetooth icon, but it automatically gets turned on after every boot.

---

### Post by doas777 on 2010-05-21
> **sirf.mein said:**
> Bluetooth icon is the notification area notifies that the bluetooth is turned on. I can turn it off from that bluetooth icon, but it automatically gets turned on after every boot.
this is just a thought, but is teh tray applet listed in your Preferences->Startup Applications? the tray app may attempt start the service if it is not already loaded, and since that would execute after your kill command, it might restart it.

---

### Post by sirf.mein on 2010-05-22
> **doas777 said:**
> this is just a thought, but is teh tray applet listed in your Preferences->Startup Applications? the tray app may attempt start the service if it is not already loaded, and since that would execute after your kill command, it might restart it.
I can prevent bluetooth app from autoloading at syatem startup in peferences->Startup Applications, this will not turn off bluetooth hardware. I can't run kill command at system startup. this is what the problem is all about...

---

### Post by SlugSlug on 2010-05-22
> **sirf.mein said:**
> **Not working...**:(


In what way did this not work?

---

### Post by sirf.mein on 2010-05-22
> **SlugSlug said:**
> In what way did this not work?

I have tried the command that you told, but bluetooth icon is tray still notifies that bluetooth is turned on, after every startup.


Regards,
Brar

---

### Post by doas777 on 2010-05-23
> **sirf.mein said:**
> I can prevent bluetooth app from autoloading at syatem startup in peferences->Startup Applications, this will not turn off bluetooth hardware. I can't run kill command at system startup. this is what the problem is all about...
what I am saying, is that it may be, that you have to do both modifications to get it to work. if you kill command runs sucessfully, but then you load the notifier app (which restarts the service), then it would appear that the kill script is not working, when it is in fact working.

---

