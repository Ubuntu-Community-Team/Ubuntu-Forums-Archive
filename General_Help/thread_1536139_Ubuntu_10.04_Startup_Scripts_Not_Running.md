---
title: "Ubuntu 10.04 Startup Scripts Not Running"
date: 2010-07-21
forum: General Help
---

### Post by daneren2005 on 2010-07-21
I have just installed a fresh Ubuntu 10.04 x64 installation.  I have a script that I am added manually that is not starting on startup like it should, but I also have 2 normal startup scripts that are not running either.  Apache2 and mt-daapd are 2 applications that I installed with sudo apt-get install apache2 mt-daapd.  Neither application is starting during bootup.  I tried making sure there were in the rc.d by using update-rc.d but both said that they already existed.  Another script (mount_data) I made myself also has been added and is executable like it should be that isn't running at bootup.

---

### Post by AlphaLexman on 2010-07-21
Please note I am on 9.10 NOT 10.04 like you!
Go to System, Preferences, Startup Applications...
Click the 'Add' button, browse to your desired startup script(s)!

---

### Post by daneren2005 on 2010-07-21
I have already tried this.  Running scripts this way does not actually run them for some reason.

---

### Post by AlphaLexman on 2010-07-21
Have you double checked they are executable?
```
chmod +x filename.sh
```
Just a thought.

---

### Post by rubylaser on 2010-07-21
Do the startup scripts actually exist in /etc/init.d/ ? (They should, but just asking).  Also on your own script did you chmod +x it and update-defaults for it in /etc/init.d/?

---

### Post by bodhi.zazen on 2010-07-21
If you installed Apache via apt-get you should not need a start script.

Also , Ubuntu is transitioning to upstart, so boot scripts are more and more in /etc/init

Check you logs ...

---

### Post by daneren2005 on 2010-07-21
I have checked that they are executable.  Yes they do exist in /etc/init.d/ and I did update-defaults for the one that I manually added.

In the past /etc/init.d/apache2 script is how apache has been started.  I don't know why the script wouldn't be needed anymore but it appears to still be needed.  Is there anything special I have to do to get scripts in /etc/init/ running at bootup or just move them into that folder?

Whether or not Ubuntu is moving to Upstart is irrelevant.  It shouldn't be breaking the old way to add startup scripts since this is the first version I've had problems with this :(

PS which logs exactly should I be checking?

---

### Post by bodhi.zazen on 2010-07-21
> **daneren2005 said:**
> I have checked that they are executable.  Yes they do exist in /etc/init.d/ and I did update-defaults for the one that I manually added.

In the past /etc/init.d/apache2 script is how apache has been started.  I don't know why the script wouldn't be needed anymore but it appears to still be needed.  Is there anything special I have to do to get scripts in /etc/init/ running at bootup or just move them into that folder?

Whether or not Ubuntu is moving to Upstart is irrelevant.  It shouldn't be breaking the old way to add startup scripts since this is the first version I've had problems with this :(

PS which logs exactly should I be checking?

First, what makes you think Apache is not running ?

What is the output of ```
sudo service apache2 status
sudo ps aux | grep apache
```Second what makes you think it is a problem with the init scripts ?

The init script for apache in 10.04 is indeed in /etc/init.d/apache2

To start or stop a service use

```
sudo service apache2 start
sudo service apache2 stop
```What happens when you manually start apache ?

```
sudo service apache2 start
```And what, if anything, is in your error log ?

```
tail /var/log/apace2/error.log
```

Last, although I understand it is frustrating, it really does not help to come across as ranting that Ubuntu is broken or that it should not migrate to upstart or well whatever you seem to be ranting about.

---

### Post by daneren2005 on 2010-07-22
> **bodhi.zazen said:**
> First, what makes you think Apache is not running ?

What is the output of ```
sudo service apache2 status
sudo ps aux | grep apache
```Second what makes you think it is a problem with the init scripts ?

The init script for apache in 10.04 is indeed in /etc/init.d/apache2

To start or stop a service use

```
sudo service apache2 start
sudo service apache2 stop
```What happens when you manually start apache ?

```
sudo service apache2 start
```And what, if anything, is in your error log ?

```
tail /var/log/apace2/error.log
```Last, although I understand it is frustrating, it really does not help to come across as ranting that Ubuntu is broken or that it should not migrate to upstart or well whatever you seem to be ranting about.
I know apache isn't running at bootup because when I try to load a page hosted on the web server I get a error.  After starting apache manually it works just fine.  I think its a problem with the init script because it doesn't run at bootup but it works just fine if I manually run it.  I don't know what is in the error log because I'm done trying the newest version of Ubuntu.  I've just run into too many problems for it to be worth it (especially when I can't really see any real improvement over Ubuntu 9.04 for example).  I don't know how you figure a one line sentence is a rant, but I think its a valid concern that this latest version seems to have broken several things that worked just fine in the last version.  Breaking the standard init.d scripts was just the last straw.

---

### Post by bodhi.zazen on 2010-07-22
> **daneren2005 said:**
> I don't know how you figure a one line sentence is a rant, but I think its a valid concern that this latest version seems to have broken several things that worked just fine in the last version.  Breaking the standard init.d scripts was just the last straw.

I am sorry you had problems. But you are jumping to conclusions without knowing what the problem is. It may or may not be a problem with the init script. Furthermore, just because it is not working for you does not mean it is a problem for everyone or that "his latest version seems to have broken several things".

Jumping to conclusions and making such sweeping generalizations does not identify or solve the problem with 10.04. Since downgrading has fixed the problem there is nothing more to be done at this time, but for next time it may help you to learn how to trouble shoot such issues. /var/log/apache./error.log and other log files should get you started. I suggest you take the time to review the logs at your convenience rather then if (when) you have a crisis.

---

### Post by olokki on 2010-08-18
bodhi.zazen ubuntu 10.04 upstart scripts DO have many problems, with the highlight of mysql upstart script. (U can look at lanchpad for the numerous bug reports). Ppl don't rant for nothing. Although i support transition to upstart as a better solution for the boot sequence, i believe that releasing an LTS with a so obvious problem (knowing so many ppl would dist-upgrade and as a result breaking their systems)is at least bad for ubuntu.  I wish i could help daneren but my upstart knowledge is non-existent.  peace and good luck to anyone trying to make 10.04 upstart work as it should :)

---

### Post by bodhi.zazen on 2010-08-18
> **olokki said:**
> bodhi.zazen ubuntu 10.04 upstart scripts DO have many problems, with the highlight of mysql upstart script. (U can look at lanchpad for the numerous bug reports). Ppl don't rant for nothing. Although i support transition to upstart as a better solution for the boot sequence, i believe that releasing an LTS with a so obvious problem (knowing so many ppl would dist-upgrade and as a result breaking their systems)is at least bad for ubuntu.  I wish i could help daneren but my upstart knowledge is non-existent.  peace and good luck to anyone trying to make 10.04 upstart work as it should :)

I agree that the upstart scripts have issues, if you search LP you will find I have filed my share of bugs against upstart.

I also tend to agree, personally I expected more of a LTS release (10.04) and 10.04 would not run on one of my boxes, I had issues on two others.

BUT ... The "solution" is to be active in the development / testing phase (report bugs before the release so hopefully they can be addressed)  and to use Launchpad.

Rants do not really help much, although they can relieve frustration.

---

### Post by darkscout on 2010-10-24
After trying to debug my system, I finally turned to google and found this thread.

I'd just like to toss in my 2c, same thing is happening to me, NUMEROUS things aren't starting.

First I just noticed sabnzbd, couchpotato and sickbeard. Then in the process of debugging. Cron, zfs-utils and who knows what else isn't starting either.

---

### Post by mpentney on 2011-05-12
I've also found this problem. I have a simple script which reconfigures my Logitech trackball to make is easier for left-handed use. I (try to) run this script from the "Startup Applications" menu. It worked well in Ubuntu 9.10, but has stopped working in 10.04. I've done a bit of playing around and tried to incorporate simple logging output. From this it seems that the script does not run on boot. If I run it manually it works as expected and swaps the trackball buttons for me.

The script lives in ~/settings/setupTrackball.sh, and is executable. Do I need to move it to /etc/init or /etc/init.d? I've not done "update-defaults" - but surely this is not necessary for scripts run via the "Startup Applications" menu?

Any suggestions?

---

### Post by robjlucas on 2012-02-09
Did anyone get anywhere with this problem? I had the same problem after moving up from 9.10 to 10.04: 
[LIST]
[*]Apache2 fails to start automatically on a system reboot
[*]There is no question that it is not running, since there is no process for Apache2
[*]However, it runs fine manually using /etc/init.d/apache2 start
[*]There are no signs in the obvious logs of anything going wrong
[*]There is no indication of any attempt to start Apache in the boot log
[*]The majority of other startup tasks are being run fine from upstart, but Apache is still done the old-fashioned way
[*]&#8756; doesn't it look like the old way of running startup scripts is just not happening in 10.04?
[/LIST]

---

