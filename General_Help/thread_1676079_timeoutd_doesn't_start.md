---
title: "timeoutd doesn't start"
date: 2011-01-26
forum: General Help
---

### Post by ecowan on 2011-01-26
timeoutd doesn't start on boot.

I have Ubuntu 10.10 with timeoutd-1.5-10.1ubuntu1 installed.
It used to work up until a couple of weeks ago. The /etc/rc*.d/S20timeoutd pointers are there, but timeoutd does not show in ps aux|grep timeoutd after a boot. Neither dmesg nor syslog show any sign of an attempted start-up or a failure.

If I manually /etc/init.d/timeoutd start it does run and do it's job. Unfortunately our teenager has discovered that a reboot makes it go away.

Can anyone suggest a remedy? Thanks. - Erny

---

### Post by ecowan on 2011-01-31
I played with this a little more, and I have a couple of clues.

I thought that maybe init was trying to run /etc.init.d/timeoutd but that it fell over. So I put some logger statements in the script, one just after the first few initialization statements. Nothing showed up in syslog, so it seems that init is not even trying to run the script, even thought there are several S20timeoutd pointers in the rcn.d directories.

I used System>Preferences>Startup Applications to add timeoutd to the users' session startup sequence. This works. Unfortunately I have to do this for each user, and the user can easily remove the entry.

How can I get init to include the timeoutd script at boot time?

Thanks. - Erny

---

### Post by ElectronicCarpenter on 2011-03-27
Bump

---

### Post by tredegar on 2011-03-27
I think this is probably **upstart**'s fault. Ubuntu currently seems to he halfway between the "old" SysV init scripts and upstart - so some things sometimes break.

Why not try starting **timeoutd** by calling it from **/etc/rc.local** ?

---

### Post by ElectronicCarpenter on 2011-03-27
You know I have played around with ubuntu but this year I am serious about learning this thing.. 

I updated the sudo update-rc.d ssh defaults
I do not know what that does... it might not even matter..

What I was trying to do for a test was to have a user login and be denied. 

This does not do that; instead you are allowed to login, then the system logs you back out within a min. I thought because I was able to login it was failing. I am very accustomed to AD(windows control ship) :evil: no login means nolgin, no desktop, do not pass go..

When you create a new user or group a reboot is in order otherwise timeoutd dos not see that new user or group. Maybe a restart of x server would do the trick.. but Microsoft habits are so difficult to break ](*,) (can I double click this)


I am going to need help with a cronjob to verify user is allowed to login by timeoutd rules. 

Is that possible? 

I would also like to know how to use a cron job to turn the machine off at 8:00 am and let no users from group0 to login in again until 4:00pm so off to the forums I go.

Is that possible?



I just wanted to thank you for your help and I think the parental controls functionality lacks.. I am playing around with a lot of machines with various ubuntu installs and a smoothwall and dans gauridian. 

Like I said internetcafe here  I come. 

PJ

---

### Post by tredegar on 2011-03-27
This thread seems to be going ... nowhere.
The OP was **ecowan** and he hasn't (yet) replied to my post at #4.

@ElectronicCarpenter
You bumped this thread (not much point in doing that unless you have more information than just "Bump").
Now you say > You know I have played around with ubuntu but this year..
Well, no we don't know that from what you have posted to this thread.
> Like I said internetcafe here I come. 
"Like I said" ??? _Where?_

You seem to be having problems with "parental controls". Perhaps you should start a new thread with an an appropriate title to address your problem, and not hijack the OP's thread.

Best wishes.

---

### Post by ElectronicCarpenter on 2011-03-28
I bumped the thread because  I had the same issue.. Now  I have a different problem.. And it is in a different thread where someone else is having the same issue. Thank you

---

