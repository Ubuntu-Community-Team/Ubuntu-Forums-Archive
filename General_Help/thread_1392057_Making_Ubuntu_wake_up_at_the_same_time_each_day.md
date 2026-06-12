---
title: "Making Ubuntu wake up at the same time each day"
date: 2010-01-27
forum: General Help
---

### Post by hostilejosh on 2010-01-27
Hey,

I have managed to make ubuntu (9.04) turn itself on from being completely off with the following code:


```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 480 minutes'` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm

```

where 480 is replaced by however many minutes until I want it to turn on.

I then use

```
cat /proc/driver/rtc
```

to check the time/date of turning on is correct. This is from [this link]("http://www.mythtv.org/wiki/ACPI_Wakeup#Manually_test_wakealarm")

Now, this is fine and works perfectly, but obviously has the restrictions of having to enter the code every day.

My understanding of this stuff is quite limited, but is there a way to get the computer to wake up at the same time everyday? I can't work it out from the link provided.

Unfortunately there is not an option in my BIOS (dell) to make the computer turn on.

Thanks

josh

---

### Post by Devi1903 on 2010-01-27
You can set the code up as a cron job to run at a certain time everyday. I was looking into a solution for this a while bck. I was working on wake on ethernet

---

### Post by tgalati4 on 2010-01-27
Put your commands in a shell:

wakemeup.sh

```

#!/bin/sh
# Super cheesy script to wake my computer every day
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 480 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm > /var/log/last_known_wakeup_time

```

Save the file and give it executable permissions:

sudo chmod +x wakeneup.sh

sudo cp wakmeup.sh /root

Here's where it gets a little tricky.  You need to run this job as root.

man crontab  (so you can read up on the command)

sudo cp /etc/crontab /etc/crontab.bak
sudo nano /etc/crontab

Add your cron job at the bottom of the file and save.

```

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
30 11   * * *   root    /root/wakemeup.sh

```

This will run your wakeup script at 1130 AM every day that the computer is online.  Of course you can change it to whatever you want.  The script dumps the last wakeup time to /var/log/last_known_wakeup_time.  You can check it to make sure it's correct.  The timestamp on the file let's you know when the cron job ran.

---

### Post by t4thfavor on 2010-01-27
FWIW alot of decent BIOS's have automatic wakeup settings, I have a few that will allow you to specify date time, and day of week.

---

### Post by hostilejosh on 2010-01-27
thanks tgalati4 that is really helpful. 

if i changed the string

```
30 11   * * *   root    /root/wakemeup.sh
```

to

```
05 07   * * *   root    /root/wakemeup.sh
```

would it run the script at 7.05am?

also, i replaced the time in

```
#!/bin/sh
# Super cheesy script to wake my computer every day
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 480 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm > /var/log/last_known_wakeup_time
```

from 480, to 1170, meaning 19.5 hours from when the script runs at 11.30am, so that the computer wakes up at 7am, correct?

thanks again!

---

### Post by tgalati4 on 2010-01-28
You will have to test it to be sure.  Don't forget to turn off saving the Ubuntu clock to the BIOS clock at shutdown.  Instructions are included in the link that you provided.

What Dell computer do you have?  All Dells that I've played with have a wakeup time in the BIOS.  It's much easier that way.

---

