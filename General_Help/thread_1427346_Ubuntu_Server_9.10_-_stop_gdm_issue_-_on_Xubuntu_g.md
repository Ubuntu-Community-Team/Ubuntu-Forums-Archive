---
title: "Ubuntu Server 9.10 - stop gdm issue - on Xubuntu gui"
date: 2010-03-11
forum: General Help
---

### Post by gottijr on 2010-03-11
I figured to disable the gdm boot so i can boot to console with
 ```

  vi /etc/init/gdm.conf
  start on (runlevel [3]
 
```

  i start gdm now with 
  ```

  gdm start
  
```

  the only problem i have with stopping gdm to get back to console
  ```

  gdm stop
  /etc/init.d/gdm stop
  
```

  does now work.

  any suggestion pls?

---

### Post by gottijr on 2010-03-11
I will post the resolve for me!

  I disabled the boot in gdm with
 "vi /etc/init/gdm.conf"

> **sisco311 said:**
> 
```

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

#start on (filesystem
#          and started hal
#          and tty-device-added KERNEL=tty7
#          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0**2**16]

```



  than i can start and stop service gdm without a problem

```

  sudo service gdm start
  sudo service gdm stop

```

  the other options didn't allowed me to start stop service because of errors!

---

### Post by bodhi.zazen on 2010-03-11
First, to stat / stop gdm (or any service) you need to run the following commands as root, meaning sudo :

```
service gdm stop
```

NOT 

gdm stop

Or

```
sudo /etc/init.d/gdm stop
```

When you stop gdm from within X you are left with a balnk screen, to switch to a console use

```
Ctrl-Alt-F1
```

To start gdm use

```
sudo service gdm start
sudo /etc/init.d/gdm start
```

With either command you will be brought to X

====

Otherwise, yes Ubuntu is moving to upstart, so you need to modify the upstart script in /etc/init as you indicated, but with updates your changes may be over written.

When making edits to system files , make comments with #
# Changed from ... to ... 
# To disable GDM
# name / date

and back up the file in say /root (I use /root/etc). This way if the config scripts are updated, you can review your changes and update the new scripts if needed.

Of course during the update process, you can elect to keep your current script, but if you do so you run the risk of breaking the boot scripts do to your option to not update the scripts. This would be rare, but can happen.

---

### Post by gottijr on 2010-03-11
> **bodhi.zazen said:**
> First, to stat / stop gdm (or any service) you need to run the following commands as root, meaning sudo :

```
service gdm stop
```

NOT 

gdm stop

Or

```
sudo /etc/init.d/gdm stop
```

When you stop gdm from within X you are left with a balnk screen, to switch to a console use

```
Ctrl-Alt-F1
```

To start gdm use

```
sudo service gdm start
sudo /etc/init.d/gdm start
```

With either command you will be brought to X

====

Otherwise, yes Ubuntu is moving to upstart, so you need to modify the upstart script in /etc/init as you indicated, but with updates your changes may be over written.

When making edits to system files , make comments with #
# Changed from ... to ... 
# To disable GDM
# name / date

and back up the file in say /root (I use /root/etc). This way if the config scripts are updated, you can review your changes and update the new scripts if needed.

Of course during the update process, you can elect to keep your current script, but if you do so you run the risk of breaking the boot scripts do to your option to not update the scripts. This would be rare, but can happen.

  ok!

  it looks like you know more and it's good i've got someones attention!

  my way to disable was wrong?  

  i'm a newbie to linux just installed a few days ago - week

  i tried to disable gdm inserting runlevel (3) or in grub insert "text" for quiet splash

  both worked with this issue:

  when i wanted to start gdm it worked!

  but i couldn't stop it with any of:

  sudo service gdm stop
  sudo gdm stop
  sudo /etc/init.d/gdm stop

  none worked...! gave me some errors .. .like unable to find, unknown job etc.

  the present disable was the only that i could

  sudo service gdm start
  sudo service gdm stop

  if i'm doing it wrong ... pls advice in more explicit steps ... so i could change it....

  already spend ed too much time trying to fix this

---

### Post by bodhi.zazen on 2010-03-11
You are fine with what you have done.

The only thing you might want to add is comments in the config file and back it up. It is a small edit, but if the upstart scripts are updated you will be given a choice to install the new (package maintainers) script, keep the old, ore review the differences.

IMO, with such a small edit, I would install the package maintainers.

In that event, it is nice if you can review the old script.

```
sudo mkdir ~/etc
sudo cp /etc/initd/gdm.conf /root/etc
```

I do not know why those commands did not work, if you are getting error messages copy - paste the command and output here so we can review it.

Otherwise, if it not broken, don't fix it.

---

### Post by gottijr on 2010-03-11
this is the error that i'm getting

  on both ubuntu server (virtual and phisic)

  ```

root@UbuntuSV1:/home/gottijr/Desktop# gdm stop

** (gdm-binary:1990): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:1990): WARNING **: Could not acquire name; bailing out
root@UbuntuSV1:/home/gottijr/Desktop# service gdm stop
stop: Unknown instance: 
root@UbuntuSV1:/home/gottijr/Desktop# /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
root@UbuntuSV1:/home/gottijr/Desktop# 


```  thanks


 also sometimes when i tried to service gdm start
 i got: gdm stop/waiting

  something like that.

---

### Post by bodhi.zazen on 2010-03-11
oops ...

Wrong syntax

gdm stop 

will not work.

I do not know why 

service gdm stop

will not work, all I can say is that it works here just fine.

---

### Post by gottijr on 2010-03-11
> **bodhi.zazen said:**
> oops ...
I do not know why 

service gdm stop

will not work, all I can say is that it works here just fine.

  And same thing on 2 Ubuntu Server 9.10 with xubuntu. (one physical one virtual) ...

  if anyone has same problem pls post.

---

### Post by HappyTimeHarry on 2010-05-10
Is service new? I can't find a man entry for it on Ubuntu 8.04.

Instead I've just used "sudo /etc/init.d/gdm stop" when needed (from console mode). However I've only used this method on Xubuntu 8.10.

---

