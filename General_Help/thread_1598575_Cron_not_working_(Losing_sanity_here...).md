---
title: "Cron not working (Losing sanity here...)"
date: 2010-10-16
forum: General Help
---

### Post by thatsdaniel on 2010-10-16
Hi there, got myself a bit of trouble with cron here.

Ok, so I thought I'd make myself a wake up script fuelled by: [Death Metal Rooster]("http://www.youtube.com/watch?v=A43JOxLa5MM"). :guitar: (Ok, not really but..)
[URL="http://www.youtube.com/watch?v=A43JOxLa5MM"]
[/URL]I just:```
chmod a+x /usr/local/bin/wakeup
```Script works fine by just:
```
wakeup
```or```
/usr/local/bin/wakeup
```So I added it to my crontab:```
crontab -e
```with: ```
22 * * * * /usr/local/bin/wakeup
```Nothing happened, so I checked if I was in /etc/group in 'crontab', which I was'nt.
I added myself and checked /etc/cron.allowed and added myself there as well (new file, btw..)
Logged out an in. Still no joy.

Ladies, Gentlemen, in what manner do I not please cron in Ubuntu? :confused:

---

### Post by gnush on 2010-10-16
How about adding yourself to the group then? I'm not on Ubuntu atm. but you might be able to do it in System -> Administration -> Users and Group.

If you want to run the cronjob for every user, you could just move it to /etc/cron.daily, /etc/cron.hourly or whenever you want the script to run.

---

### Post by thatsdaniel on 2010-10-16
> **gnush said:**
> How about adding yourself to the group then? I'm not on Ubuntu atm. but you might be able to do it in System -> Administration -> Users and Group.

If you want to run the cronjob for every user, you could just move it to /etc/cron.daily, /etc/cron.hourly or whenever you want the script to run.Yes, I have added myself to the crontab group and looged in and out, as I stated in OP. Thank you kindly anyway for the swift reply! :)

---

### Post by The Cog on 2010-10-16
What does the script do? Does it need some environment setting up for it?

You could try writing any out put from the script (such as error messages) to a file, a bit like this:
22 * * * * /usr/local/bin/wakeup > /home/me/wakeup-out.txt 2>&1

Also note that cron uses sh to run the scripts, not bash. Some bash features aren't there in sh.

---

### Post by thatsdaniel on 2010-10-16
> **The Cog said:**
> What does the script do? Does it need some environment setting up for it?

You could try writing any out put from the script (such as error messages) to a file, a bit like this:
22 * * * * /usr/local/bin/wakeup > /home/me/wakeup-out.txt 2>&1

Also note that cron uses sh to run the scripts, not bash. Some bash features aren't there in sh.Its this script with a slight modification: [MPD-script 'GoodSleep]("http://mpd.wikia.com/wiki/Hack%3AGoodSleep")'.

Oh snap... lol I feel *a bit* daft now! :P
But hey, **thanks for the tip!** I had not put the full path in the executable 'wakeup':```
_/usr/local/bin/_[wakeup.sh]("http://wakeup.sh") -p SverigesRadioP1
```It should do what I want now: crontab -l```
59 05 * * 1-6 /usr/local/bin/wakeup
45 06 * * 0 /usr/local/bin/wakeup
```That is: load and play playlist: 'SverigesRadioP1' at 05:59 Monday till Saturday and then 06:45 on Sundays.

---

### Post by The Cog on 2010-10-18
Is that a GUI program it's trying to launch? If so, you need to set the DISPLAY variable first - try adding:
> export DISPLAY=:0.0
to the start of the script, but it still won't work unless the user is logged in on the GUI first.

If that's not it, try piping the output of the script to a file as I suggested, so you can see any error messages.

---

