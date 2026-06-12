---
title: "Permissions for System-&gt;Preferences-&gt;Startup Applications"
date: 2009-06-26
forum: General Help
---

### Post by Sonthun on 2009-06-26
What permissions do startup applications run from System->Preferences->Startup Applications have?  I'm trying to run a script on startup that requires sudo permission.  Can I do that through the Startup Applications?  How?

Thanks.

---

### Post by wojox on 2009-06-26
Here's how I do it in Intrepid

System > Preferences > Sessions
Click Add to bring up new window where you can type the start up command.
Enter WhatEverName into the Name field.
Enter into the Command field  sudo /path/to/script
Click Add.

---

### Post by Sonthun on 2009-06-27
Does that give you sudo privilege in Intrepid?  In Jaunty it seems the equivalent is System->Preferences->Startup Applications.  There isn't a Sessions in Jaunty (as far as I can tell).  I can get the script to run, but I can't get it to do anything that would require a sudo.

---

### Post by bodhi.zazen on 2009-06-27
If you have a script that needs to run as root when you boot, put it in /etc/rc.local or write an init script.

If you have an application that need to run as root, consider configuring sudo to allow you to run the script with no password.

In start up you then sudo script.

What is it you are trying to configure exactly ?

---

### Post by alanwalterthomas on 2009-06-27
I have related problem. I want to run my UPS monitoring software with the command
sudo /opt/sms_power_view/powerview start -g
This works fine if I type it in a terminal. I created a new item in startup applications & entered this command, but the program doesn't run on startup.
Know of any reason why not? Thanks,

---

### Post by swisstone198 on 2009-06-27
> **alanwalterthomas said:**
> I have related problem. I want to run my UPS monitoring software with the command
sudo /opt/sms_power_view/powerview start -g
This works fine if I type it in a terminal. I created a new item in startup applications & entered this command, but the program doesn't run on startup.
Know of any reason why not? Thanks,

Add an script to /etc/init.d called powerview
in the script put

case $1 in 
start)
                 /opt/sms_power_view/powerview start -g
                 ;;
stop) 
                 /opt/sms_power_view/powerview stop (or however you stop it)
                 ;; 
*)
                  exit
                 ;;
esac



and make it executable and chown to root:root.  Then
sudo ln -s /etc/init.d/S99powerview /etc/rc2.d/S99powerview
sudo ln -s /etc/init.d/S99powerview /etc/rc0.d/K99powerview
sudo ln -s /etc/init.d/S99powerview /etc/rc6.d/K99powerview
I think this should work.

---

### Post by Sonthun on 2009-06-27
The basic purpose is to restart mythbackend after the hdhomerun is recognized (30-120 seconds after login).  The script works fine when I run it with sudo from terminal and it works fine if it is trying to do something that doesn't need sudo permission on bootup.  But, if I test it with something that needs permission (like writing a text file to the init.d directory) it won't work on startup.  I tried your suggestion and it didn't work.  Any other ideas?  Thanks.

---

### Post by swisstone198 on 2009-06-28
you could add an entry in /etc/sudoers so that sudo doesn't need a password to run the command.

---

### Post by Sonthun on 2009-06-28
Thank you.  I didn't realize I could do that.  It works now.

---

### Post by alanwalterthomas on 2009-11-06
The script solution above doesn't work anymore now that I've moved to karmic.
Just to check I did it right, I moved this script to /etc/init.d/ then made it owned by root & executable.

#!/bin/sh
echo Starting SMS Auto-Start
case $1 in
start)
/opt/sms_power_view/powerview start -g
;;
stop)
/opt/sms_power_view/powerview stop
;;
*)
exit
;;
esac
echo Finished

The service will still start if I run sudo /opt/sms_power_view/powerview start -g
If I run sudo sh /etc/init.d/powerview I get the first echo line "Starting SMS Auto-Start" but not the "Finished" so I think something's no longer right.
Note that I don't really understand scripts. If you have any idea how to make things right again, thanks a lot!

---

### Post by bodhi.zazen on 2009-11-06
> **alanwalterthomas said:**
> The script solution above doesn't work anymore now that I've moved to karmic.
Just to check I did it right, I moved this script to /etc/init.d/ then made it owned by root & executable.

#!/bin/sh
echo Starting SMS Auto-Start
case $1 in
start)
/opt/sms_power_view/powerview start -g
;;
stop)
/opt/sms_power_view/powerview stop
;;
*)
exit
;;
esac
echo Finished

The service will still start if I run sudo /opt/sms_power_view/powerview start -g
If I run sudo sh /etc/init.d/powerview I get the first echo line "Starting SMS Auto-Start" but not the "Finished" so I think something's no longer right.
Note that I don't really understand scripts. If you have any idea how to make things right again, thanks a lot!

In the second example, you are running "sudo sh /etc/init.d/powerview" ?
With no options ?

So in your case , it matches *) => exit

it should work just fine if you add an option

```
sudo sh "/etc/init.d/powerview **[COLOR=blue]start[/COLOR]"**
```the -g is unnecessary as you specified -g in your script (and you would need to work on your script to pass multiple options ... ).

---

