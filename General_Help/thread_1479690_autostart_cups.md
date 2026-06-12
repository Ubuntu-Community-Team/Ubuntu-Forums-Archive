---
title: "autostart cups"
date: 2010-05-10
forum: General Help
---

### Post by kentechy on 2010-05-10
How can I automate the sudo password and make the following command automatic?  It is for starting cups since it fails to start at times and I have been unable to find a fix anywhere...

sudo /etc/init.d/cups restart
Thanks..  :)

---

### Post by wojox on 2010-05-11
You could make an alias for it in .bashrc

```
alias cups='sudo /etc/init.d/cups restart'
```

Then just run

```
cups
```

---

### Post by kentechy on 2010-05-12
> **wojox said:**
> You could make an alias for it in .bashrc

```
alias cups='sudo /etc/init.d/cups restart'
```Then just run

```
cups
```

Thanks for the information.  I am just running it manually before I want to print since I am not advanced enough to know how to do what you describe.  If you're just meaning to edit the .bashrc file, I can handle that.  My question is, will I still be asked for my password because of the "sudo" command?  Thanks.

---

### Post by Snow986 on 2010-05-12
Yes it will still ask for your password.  The best option here is to figure out what is going on with CUPS.  Have you checked the error logs in /var/log/cups ?  You could always make a cron job that would auto restart every hour but that's a bit messy and shouldn't be necessary as CUPS should be reliable.

---

### Post by kentechy on 2010-05-13
> **Snow986 said:**
> Yes it will still ask for your password.  The best option here is to figure out what is going on with CUPS.  Have you checked the error logs in /var/log/cups ?  You could always make a cron job that would auto restart every hour but that's a bit messy and shouldn't be necessary as CUPS should be reliable.

True statement.  I will search the net again as I am not a programmer, just a techy...

I know many others are having this problem but have not found a fix.

Thanks.

---

### Post by kentechy on 2010-05-13
> **Snow986 said:**
> Yes it will still ask for your password.  The best option here is to figure out what is going on with CUPS.  Have you checked the error logs in /var/log/cups ?  You could always make a cron job that would auto restart every hour but that's a bit messy and shouldn't be necessary as CUPS should be reliable.

Here is a log.  There are lots of them and all the same.  See below..

E [05/May/2010:16:51:12 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:17:57:42 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:18:18 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:20:37 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:24:26 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:25:23 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:32:07 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:43:52 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:43:54 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:20:43:57 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:04:12 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:20:54 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:20:58 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:21:44 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:22:38 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:22:40 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:23:37 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [05/May/2010:21:41:43 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

:(

---

### Post by Snow986 on 2010-05-15
Let me point to you to something that might help.  It looks like HPLIP is causing issues.  You could try uninstalling it or try the workaround found at the bottom of this page:

[https://answers.launchpad.net/hplip/+question/89726](https://answers.launchpad.net/hplip/+question/89726)

---

### Post by kentechy on 2010-05-15
> **Snow986 said:**
> Let me point to you to something that might help.  It looks like HPLIP is causing issues.  You could try uninstalling it or try the workaround found at the bottom of this page:

[https://answers.launchpad.net/hplip/+question/89726](https://answers.launchpad.net/hplip/+question/89726)

Thanks for the information.  I will try some things...  :)

---

