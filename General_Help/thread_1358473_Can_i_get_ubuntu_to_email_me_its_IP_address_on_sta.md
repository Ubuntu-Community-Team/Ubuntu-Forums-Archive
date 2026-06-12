---
title: "Can i get ubuntu to email me its IP address on startup?"
date: 2009-12-18
forum: General Help
---

### Post by geekyhawkes on 2009-12-18
Hi,

i have several ubuntu machines connected to one adsl/wifi router with the router acting as dhcp.  My ISP wont provide a free static IP address (and i will be damned if im going to pay £5 p/m for something that should be free!).  I have recently experienced a few power cuts at home, and while the rest of my network is robust i loose my external access to mythbuntu and my nas etc as the router has a new IP address one the power comes back on.

Is there a way i could get one of my ubuntu machines to email me the external IP address each time they power up?   THis would be most useful if i could get my mythbuntu box to do it so i can always have access to myth web.

I think this shouldnt be that difficult but would be grateful of the advice.

Thanks

---

### Post by StuartN on 2009-12-18
> **geekyhawkes said:**
> Is there a way i could get one of my ubuntu machines to email me the external IP address each time they power up?

You could obtain the external IP address from DynDNS or similar website of your choice, using wget, and email it with a command-line email application of your choice.

There are several permutations here [http://ubuntuforums.org/showthread.php?t=1284459](http://ubuntuforums.org/showthread.php?t=1284459)

---

### Post by mihamil on 2009-12-18
You can use curl to get your external IP address from [www.whatismyip.com](www.whatismyip.com)

try this command ( you may have to install the curl package)

curl [www.whatismyip.com/automation/n09230945.asp](www.whatismyip.com/automation/n09230945.asp)

This should output your ip address.  

Then you could set up a shell script in /etc/rc2.d retrieve the ip address and email it to you.  Read the README in that folder for some instruction on startup scripts.

MH

---

### Post by geekyhawkes on 2009-12-20
Thanks for the above links.  I went for the exim4 and cron job version and it is now working perfectly!

---

### Post by KeyserSoze93 on 2009-12-20
> **geekyhawkes said:**
> Thanks for the above links.  I went for the exim4 and cron job version and it is now working perfectly!

Yes, thats what I do, more or less.

Even though I have DynDNS too, I like to know when my IP changes and what it is.

---

### Post by geekyhawkes on 2009-12-21
The only thing i dont quite get is when i edit the cron file it seems to save as a fairly randomly names temp file.  If i crontab -l the job is listed but I am wondering if i should save the cron file somewhere else and point cron to it?  I am keen that the auto email still works post a powercut / system reboot.

---

### Post by StuartN on 2009-12-21
> **geekyhawkes said:**
> The only thing i dont quite get is when i edit the cron file it seems to save as a fairly randomly names temp file.

crontab -e will copy your existing user crontab file to a temporary file, which you can then edit and save, then it is verified and (if it passes the verification) copied to replace the previous crontab. The temporary file has a random-looking name. This afety feature reduces the chances of editing serious errors into a previously functional crontab.

---

### Post by geekyhawkes on 2009-12-21
Thanks very much for the explaination.  Makes sence!  I just need to decide what else to get my mythbox to email me now as well as its ip address when the cron job runs!

---

### Post by mihamil on 2009-12-22
Have it email you shows that it is going to record within the next 24 hours, or shows it has recorded since the last reboot.

---

### Post by geekyhawkes on 2009-12-23
mihamil, that sounds good but i havent a clue where to start!  Any chance you could point me the right direction please? 

Thanks

---

### Post by 03spirit on 2009-12-23
This is not a direct answer to your question I think it may help though.
 
You could use a UPS(battery back up) for just the router. It would literally last all day.
 
Mark..

---

### Post by mihamil on 2009-12-23
Actually the modem would need to be remain powered to keep the connection, but your ISP can still institute a max client lease time and force an IP change without you losing power.

Although I have never actually used mythtv or mythbuntu you could use something similar to this in your shell script.

```

#!/bin/bash

#Stores the contents of lastreboottime.txt into a variable named "var".  This file should ONLY contain a date/time stamp.  Aything else will cause this script to error out.

var=`cat lastreboottime.txt`

#executes a MySQL command.  Provides authentication and runs a query.  The output of the query is stored in output.txt

mysql -u MythMysqlUserAccount --password=MySQLPassword -D MythTVDatabaseName -e "SELECT title, starttime, endtime, description FROM recorded WHERE starttime > $var" > output.txt

#executes the date command and stored the output (The datetime stamp) in the file lastreboottime.txt.  Make sure permissions are set to allow the script to overwrite lastreboottime.txt.  Also you will have to research the date command and add some options to format the date correctly.  Take a look at the dates in the mysql table 'recorded' and format the output of `date` the same way.  This is so you only get updates when it reboots.

echo `date` > lastreboottime.txt

#your ip address and email script
#Place your IP address and email script here.  direct the output to output.txt.  Then you should be able to use your smtp server to send the email containing the contents of the output.txt file.  

```

I did install mythbuntu on a virtual machine but I have no data so I'm not sure how the date is formatted.  My guess would be something similar to this. '2009-12-22 11:30:00' but I can't be for sure.

---

