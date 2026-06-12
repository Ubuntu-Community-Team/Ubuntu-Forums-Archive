---
title: "How to keep process running in backgroud?"
date: 2012-01-03
forum: General Help
---

### Post by thomo2710 on 2012-01-03
Hi all,

I have a daemon that i need running 24/7 but at the moment when its not doing anything it stops itself.

Is there a command or a file i can edit that will check to see if its running and if nor run it?

The plugin i need running lives in /usr/bin

Thanks

---

### Post by sj1410 on 2012-01-03
> **thomo2710 said:**
> Hi all,

I have a daemon that i need running 24/7 but at the moment when its not doing anything it stops itself.

Is there a command or a file i can edit that will check to see if its running and if nor run it?

The plugin i need running lives in /usr/bin

Thanks

Hope this helps

[http://blog.swapnil.me/2012/01/howto-run-process-in-background.html](http://blog.swapnil.me/2012/01/howto-run-process-in-background.html)

---

### Post by btindie on 2012-01-03
Are you sure it's been written as a daemon if it fails to run continuously?

Is there an option you can pass to it that puts it into daemon mode? What exactly does it do.. it may be possible to run it under xinetd.

You could use [monit]("http://mmonit.com/monit/") to monitor your process and restart it if it dies. Then there's also [daemontools]("http://cr.yp.to/daemontools.html") that might do what you want.

---

### Post by thomo2710 on 2012-01-03
@sj1410 - thanks ill look at that now.

@btindie - the file is called gammu-smsd
Its an SMS Daemon (part of the Gammu package) that scans a MYSQL database for text messages inserted from Nagios. The Daemon then forwards the messages from the database to the recipients mobile phones. 

The messages only leave the database though when i run the command gammu-smsd.

If this isnt running in a terminal windows continuously the messages stay in the DB and dont get forwarded.

So i need to get this gammu-smsd process runnind continuously 24/7/365

Is it a Daemon? Honestly dont know my linux knowledge is not great. Presumed it was as its called SMS Daemon?

Thanks

---

### Post by MartijnNL on 2012-01-03
When you run a program in terminal and then close the terminal the program stops. You could perhaps simply start it using Alt+F2 instead. Adding it to the start-up applications in your preferences is probably also useful.

If this doesn't work you could try starting it every few minutes or so using a [cron job]("https://help.ubuntu.com/community/CronHowto").

---

### Post by btindie on 2012-01-05
It sounds like you're running it as a foreground process. Having looked at the application it appears you need to pass it the '--daemon' option to tell it to run in the background and detach itself from the controlling terminal. However, the package *gammu-smsdcomes with it's own init.d script to there's no need for you to manually invoke the program directly from the terminal, you'd only do that if you wanted to debug the process. Instead use the [I]service* command to control the process.
```
sudo service gammu-smsd restart
```
You can see the installed files for that package with
```
dpkg -L gammu-smsd
```
If you need to pass any additional options to the process then set them in /etc/default/gammu-smsd which is sourced by the init script /etc/init.d/gammu-smsd

When it's run that way you don't need a terminal open or even to be logged in for it to run. It'll also start automatically when the system is booted.

[/I]

---

