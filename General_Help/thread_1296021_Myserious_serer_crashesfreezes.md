---
title: "Myserious serer crashes/freezes"
date: 2009-10-20
forum: General Help
---

### Post by andyb88 on 2009-10-20
Recently my Ubuntu Server (9.04) has been crashing rather frequently and I havent got a clue why. It seems to be completely random, sometimes during bootup sometimes after boot. Its a simple server running Apache, Sendmail and a few other standard network services. 

Can anyone suggest a place to start looking to find the cause of the crashes? I have had a look at a few logs but since Ive only recently begun using Linux OSes Im abit lost. I have also had a look at several posts on the forums but nothing seems to be similar to my problem.

Thanks in advance.

Andy

---

### Post by Lars Noodén on 2009-10-20
try this on the off chance it was recorded

```

# display all *faillog* records 
faillog -a

```

It will be hard or impossible to fix until you can figure out what causes the crash and can [reproduce the bug each time](http://catb.org/jargon/html/B/Bohr-bug.html)

Other places to look would be 
[INDENT]
/var/log/messages
/var/log/daemon
/var/log/syslog
/var/log/kern.log[/INDENT]

Try to keep track of the exact time the bug occurred so that your search through the logs can take advantage of the time stamps.  If your clock is not already synchronized with the rest of the world, consider installing openntpd.

---

### Post by andyb88 on 2009-10-21
Lars,

Thanks for the quick reply. Unfortunately 'faillog -a' is completely empty.

I know the server wasnt working at 7 this morning and have had a look at the logs you suggested. The last entry in /var/log/messages was '-- MARK --' at 4.53 and the last entry in /var/log/daemon was a cron job 'CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)' at 4.50.

Other than those lines nothing seems to point towards and error and all I know is it has crashed between 4.50 and 7.00. Also when it 'crashes' it is completely unresponsive, the mouse and keyboard dont work, the screen is black and it doesnt accept any remote ssh connections.

---

### Post by egalvan on 2009-10-21
Run a memory test. At least twenty-four hours.

Make sure the insides are clean. Really clean. No dust-bunnies anywhere.
Don't forget the insides of the power supply.

If it was dirty, then one by one, remove components such as RAM, add-on cards, power connections, data cables.
Remove and replace each one, one at a time, so you don't get mixed up.
(Corrosion can build up on connections, and they can also work loose.
The older the machine, the worse this can be.
Humidity can also wreak havoc on metal.)

Run a memory test. At least twenty-four hours. Yes, again.

Just my opinions here.

---

### Post by Lars Noodén on 2009-10-21
Hmm.  Is the same log entry present before each and every crash.  

Is there anyway you can get it to crash on demand?

---

### Post by andyb88 on 2009-10-21
I cant seem to get it to crash on demand, sometimes its during bootup other times its while its just 'ticking over'. Ill have a look next time it crashes and keep a record of the last lines before the crash.

I will run a memory test as egalvan suggested. Dust shouldnt be a problem as I just spent £400 on new hardware, case etc.

Would changing from one set of hardware to another without reinstalling cause any major problems? I had a look on google before migrating to the new hardware and didnt find any cause for concern.

---

### Post by egalvan on 2009-10-22
> **andyb88 said:**
> 
I will run a memory test as egalvan suggested.
 Dust shouldnt be a problem as I just spent £400 on new hardware, case etc.

OK, new componets mean clean components.
But something could still be defective, or mis-connected.

> 
Would changing from one set of hardware to another without reinstalling cause any major problems?
 I had a look on Google before migrating to the new hardware and didn't find any cause for concern.

Did you in fact swap the drive from one machine to another?

While Linux is MUCH more tolerant than Microsoft about this,
it could still present some problems.
Not very likely, though.

BUT, if you continue to have "mysterious crashes", you should re-consider.

---

### Post by andyb88 on 2009-10-22
Ok so its crashed again. This time I set up several ssh terminals to monitor what the server was doing: watch date, watch sensors, top, and tail -f for all the logs suggested by Lars and nothing strange seems to happen.

[I]Oct 22 20:10:01 helios /USR/SBIN/CRON[9359]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 22 20:17:01 helios /USR/SBIN/CRON[10874]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 20:20:01 helios /USR/SBIN/CRON[11518]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 22 20:20:01 helios /USR/SBIN/CRON[11519]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
[/I]
is the last 4 lines of messages (i think) all the other logs have events a while before the crash time. The temperature is still low and top didnt suggest anything was using alot of cpu or anything.

> Did you in fact swap the drive from one machine to another?
I did just swap the hard drive, if nothing seems to work in the next few days I think ill just wait until the new release comes out and do a fresh install with that.

I also tried running memtest, well i got someone to do it for me as im admining from 600miles away at uni, and it failed with "selected item doesn't fit into memory". Any suggestions?

Also when it was rebooted it hung on "reading files needed to boot", does this suggest anything? Maybe a dodgy hdd?

---

### Post by egalvan on 2009-10-23
> **andyb88 said:**
> 
 The temperature is still low and top didnt suggest anything was using alot of cpu or anything.

probably not heat-related, then.

> I did just swap the hard drive, if nothing seems to work in the next few days I think ill just wait until the new release comes out and do a fresh install with that.

You can wait for the results of the tests below.
Or you can schedule a  clean install of the new Karmic.

Personally, I wait a month after a new release is out to let others iron out bugs, if using it on an important machine.
Only you can decide how important this is.

> I also tried **running memtest, it failed **with "selected item doesn't fit into memory". Any suggestions?

Also when it was **rebooted it hung** on "reading files needed to boot", does this suggest anything? Maybe a dodgy hdd?

These can be indicative of bad RAM, or a bad copy of the CD.
Dodgy HDD?. How would that impact the memtest?
Yes, it's possible you also have a dodgy HDD.
Get the other problems squared away first.

Test the CD on another computer.
Run the "test media for errors" to make sure it is a good copy.

If the media tests good, I'd be looking hard at the hardware.
if the media tests bad, check the ISO md5, or download a new copy.
Use torrent if possible... it checks the file far better than a direct download.
But still check the md5.

---

### Post by andyb88 on 2009-10-23
> Personally, I wait a month after a new release is out to let others iron out bugs, if using it on an important machine.
If i can get it sorted ill wait, but since its a web server for small business thats just starting up I need to get it sorted pretty soonish.

> These can be indicative of bad RAM, or a bad copy of the CD.
I ran memtest from the hdd (pressing esc at grub boot menu). Could this be why it failed? Im in the process of downloading the iso so ill try again from cd.

> Dodgy HDD?. How would that impact the memtest?
I meant the hang at "reading files needed to boot". Sorry, i didnt make that clear.

Is there anything else I can have a look at to trace the crashes?

---

### Post by egalvan on 2009-10-23
> **andyb88 said:**
> If i can get it sorted ill wait, but since its a web server for small business thats just starting up I need to get it sorted pretty soonish.

This a critical piece of machinery, then.
You should be running a stable version of Linux.
Such as Hardy Heron 8.04 LTS.
Is there a valid, real, NEED
such as "8.04 does not have support for a critical piece of hardware"
to run a newer Linux?

When the business is on the line, is NOT the time to be experimenting.
You need stability, not flash.

> I ran memtest from the hdd (pressing esc at grub boot menu). Could this be why it failed?

Absolutely, yes.

>  Im in the process of downloading the iso so ill try again from cd.
I meant the hang at "reading files needed to boot". Sorry, i didnt make that clear.

Is there anything else I can have a look at to trace the crashes?

Need to isolate the cause to hardware or software.

---

### Post by andyb88 on 2009-10-25
> This a critical piece of machinery, then.
You should be running a stable version of Linux.
Such as Hardy Heron 8.04 LTS.
Is there a valid, real, NEED
such as "8.04 does not have support for a critical piece of hardware"
to run a newer Linux?
There isnt a need to run the newest version, It was just the version I downloaded when i set the server up. Im relatively new to Linux and am learning as I go along. If I cant fix the problem soon Ill install the 8.04 LTS.

The server hasnt crashed for a day and a half, but when it was restarted by a weekly cron job last night it crashed. So its still crashing on start up. Im going to run a memtest during the night when theres no demand for the website and Ill let you know the outcome.

---

