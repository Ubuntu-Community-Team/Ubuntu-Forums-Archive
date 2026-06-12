---
title: "trying to save power and avoid heating by powering server off durring day"
date: 2010-07-05
forum: General Help
---

### Post by thedrachen on 2010-07-05
I have a server that only runs durring the hours the house is asleep, to avoid bandwidth hogging. I know there are ways to prevent bandwidth hogging, but I figured I'd kill two birds with one stone. My other goal is also to reduce power and cooling costs. My two computers between them make a very nice space heater in the winter, in summer they make it sweltering in my room.
I'm sure it would be trivial to get the sever to power itself off every morning, but is it possible to get it to power itself on at bedtime? If not, I do have Wake on Lan working, is there a windows program that would allow me to send a wake on lan signal every day and then shutdown windows?
Thanks in advance.

---

### Post by btindie on 2010-07-05
Take a look at the following:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
[http://manpages.ubuntu.com/manpages/lucid/man8/rtcwake.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/rtcwake.8.html)

---

### Post by thedrachen on 2010-07-07
Many thanks, btindie.

For anyone following in my footsteps,  rtcwake would not work properly for me until I disabled HWclock updates,  per the mythtv link. I also could not get it to work  with the argument  "-m off."
 
I set up gnome-scheduler to run the command 
rtcwake  -m disk -s 68400
every day at 8AM. It should shut it down for  19hours, or until 3AM.

---

### Post by btindie on 2010-07-07
Only thing being with that approach is that the hwclock is not saved and I think over time it'll drift.
 
One way around it would be to create an upstart job that runs after hwclock-save to set the rtcwake up time from a config file using a similar method as described [here]("http://[http://ubuntuforums.org/forumdisplay.php?f=331&order=desc&page=5")(http://ubuntuforums.org/forumdisplay.php?f=331&order=desc&page=5"]here[/URL)] to set the RTC to an absolute time instead or relative.
 
Here's an example upstart script that would do just that. Save it to
 
*/etc/init/rtcwake.conf:*
```
 
description "RTC Wakeup Alarm"
 
start on (runlevel [06]
          and started hwclock-save)
 
task
 
script
    [ -f /etc/default/rtcwake ] || exit 0
    . /etc/default/rtcwake
 
    [ "$RTCWAKE" = "yes" ] || exit 0
    dt=$(date --date="$DATE $TIME" +%s)
 
    . /etc/default/rcS
    [ "$UTC" = "yes" ] && rtc="-u" || rtc="-l"
 
    exec /usr/sbin/rtcwake $rtc -m $MODE -t $dt
end script

```
 
*/etc/default/rtcwake:*
```

# Set to 'yes' to enable rtcwake anything else disables it
RTCWAKE=yes
# Can use any argument that can be passed to the date command, e.g.
#  tomorrow
#  2 days
#  this Friday
#  1 week
DATE="tomorrow"
# Time to wake up
TIME="03:00:00"
# rtcwake sleep mode
MODE="no"

```
 
Which if run would cause the system to wake up tomorrow at 3am.
 
EDIT: I found that with my development box that has the hwclock set to localtime (due to having Windows installed) and the timezone being set to London (BST/UTC+1) I had to add an hour to wake up time to get it to work correctly. Using *rtcwake* directly
 
```

rtcwake -l -m no -t $(date --date="5 min 1 hour" +%s) -v

```
 
with *hwclock-save* disabled and manually telling it to *poweroff* afterwards results in it waking up 5 minutes later.
After setting the wakeup time with rtcwake you can see the time it'll wakeup with
 
```

cat /proc/driver/rtc

```
 
with out the *'1 hour'* bit it sets the wakeup time to 1 hour in the past. But why??
 
EDIT2: It appears that after chaning the hwclock to use UTC instead of localtime the results are as expected. When using localtime the difference is between that and UTC. This problem only exists with Karmic, under Lucid it works fine.

---

