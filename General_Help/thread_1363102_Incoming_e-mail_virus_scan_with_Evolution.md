---
title: "Incoming e-mail virus scan with Evolution"
date: 2009-12-24
forum: General Help
---

### Post by dcstar on 2009-12-24
Ok, I am posting this here because my previous thread is in the old locked Desktop archive.

[SIZE="3"]You can have Evolution scan all of your incoming e-mails for viruses and notify you of any detected.[/SIZE]

First you have to install the following packages:

**clamav clamav-freshclam**

This should install the basic Clamav system that updates itself automatically (there are other clam packages you can install for extra functionality).

Then create a script in a convenient place (like your /home directory), I called mine **clam-filter** and it contains the following:

```
#!/bin/bash
# Fred Blaise <chapeaurouge AT madpenguin DOT org>
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA

FILE=/tmp/$$_outclam.tmp
# clamscan for non-daemon scanning - clamdscan when the daemon is installed
clamscan --no-summary --detect-pua=yes --detect-structured=yes - 1>$FILE

if [ $? -eq 1 ]; then
STRING=$(grep "FOUND" $FILE |cut -d: -f2)
zenity --warning --title="Evolution: Malware detected" --text="$STRING" &
logger -t clamav/Evolution <$FILE
exit 1
fi

exit 0
```

After you create it, make it executable:

```
chmod 777 **clam-filter**
```

Go into Evolution-Edit-Message Filters and create a new Incoming Filter called Virus scan with location of the **clam-filter** script in the Pipe to Program location and an Evolution folder to dump any e-mails with a virus into (I made one called "Virus Dump) - see attached screenshot.

Make sure that the filter is at the top of the list and all of you incoming e-mails should be checked by Clamav (so you know when you receive a Windows virus or other malware).

You can test the functionality by sending yourself an e-mail containing one of the Eicar test files:

[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

---

### Post by dcstar on 2010-03-16
> **dcstar said:**
> 
You can have Evolution scan all of your incoming e-mails for viruses and notify you of any detected.


Script updated to do more scanning and also to log an entry to the Syslog.

---

### Post by lz1dsb on 2010-03-16
Quite interesting. I think I'll give it a try. I didn't know that there're antivirus packages for Linux though... I thought that all viruses are written only for Windows...

Cheers, 
Boyan

---

### Post by dcstar on 2010-03-17
> **lz1dsb said:**
> Quite interesting. I think I'll give it a try. I didn't know that there're antivirus packages for Linux though... I thought that all viruses are written only for Windows...


Don't you want to see all the Windows malware that gets sent to you?

It also detects bogus e-mail links in messages that are there to deceive you, these things are platform independent and IMHO most people would rather be informed of them than risk clicking the link.

---

### Post by lz1dsb on 2010-03-17
You're right. I'll really try it out, that's really the point. I didn't mean to be sarcastic in any way though...

Cheers,
Boyan

---

### Post by dcstar on 2010-03-17
> **lz1dsb said:**
> You're right. I'll really try it out, that's really the point. I didn't mean to be sarcastic in any way though...

Cheers,
Boyan

Didn't take it that way, some people like seeing Windows malware that has no effect on their systems...... ;)

---

### Post by ImmaNoob on 2010-06-22
Hi, 

I followed everything you wrote and now that I have all setup, how can I test everything? 

Thx for your reply....oh btw.... YOU ROCK Dude:guitar:

OK i just missed the eicar part. sorry!!!

---

### Post by fimasava on 2010-06-24
Well... All done, but all my incoming emails now are moved to the tray "Virus-Dump"

???

---

### Post by Manyette on 2010-06-25
Hi DCSTAR,
Many thanks.  That is just what I've been looking for.  Well done indeed.  It works as advertised and thanks for adding the info on test files.  I don't worry about viruses, but I try to take pity on my friends who are locked into another OS.  Again, many thanks.:popcorn:

---

### Post by ussndmac on 2010-07-05
Followed all the setup steps, attempted to test it...

My provider won't send the email cuz it detects the virus sig in the test file.

:-&

Any way around that?

---

### Post by ckrodle on 2010-07-09
> **fimasava said:**
> Well... All done, but all my incoming emails now are moved to the tray "Virus-Dump"

???

I had the same thing happen to me.
Any suggestions for this???

---

### Post by dcstar on 2010-12-10
> **ckrodle said:**
> I had the same thing happen to me.
Any suggestions for this???

I can only suggest that you either carefully check the script for missing or incorrect characters. The easiest way to ensure that the script is correct is to "copy and paste" the complete content from the first post.

All the permissions must be set as well otherwise it just won't run correctly, and take not of the two different lines in the script for the slightly different clamav installations.

---

