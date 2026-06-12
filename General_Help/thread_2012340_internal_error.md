---
title: "internal error???"
date: 2012-06-29
forum: General Help
---

### Post by Matrix01 on 2012-06-29
does anyone know what this message mean?
this message often shows up when Lubuntu gets booted.[ATTACH]220395[/ATTACH]

---

### Post by spikoley on 2012-06-29
Click "Show Details".  It should provide you with more information.

---

### Post by Matrix01 on 2012-06-30
i clicked details,
here's how this looks.
do u know what they mean?

[ATTACH]220472[/ATTACH]

[ATTACH]220473[/ATTACH]

[ATTACH]220474[/ATTACH]

---

### Post by spikoley on 2012-06-30
It looks like the Notification Daemon crashed.  This warning is asking if you want to send a report to the developers.  They only collect anonymous data, so there is no harm in sending it.  Sending the report will alert the developers to the issue and it will help with getting the issue resolved.  I personally send them.

---

### Post by houseworkshy on 2012-06-30
There should be some more detail in your system logs too.  You could also allow it to report and follow your report to see what others with the same problem have experianced and been advised.  Could be a bug and there may be a work around which hasn't made the repros yet.

---

### Post by Matrix01 on 2012-07-05
how do u check system logs?

> **houseworkshy said:**
> There should be some more detail in your system logs too.  You could also allow it to report and follow your report to see what others with the same problem have experianced and been advised.  Could be a bug and there may be a work around which hasn't made the repros yet.

---

### Post by Matrix01 on 2012-07-05
i clicked 'continue', and
this tab disappeared.
do u think the report has been sent?

> **spikoley said:**
> It looks like the Notification Daemon crashed.  This warning is asking if you want to send a report to the developers.  They only collect anonymous data, so there is no harm in sending it.  Sending the report will alert the developers to the issue and it will help with getting the issue resolved.  I personally send them.

---

### Post by spikoley on 2012-07-05
It sounds like it was sent.  I think the final dialog says bug report sent.

---

### Post by houseworkshy on 2012-07-06
I haven't used lubuntu recently so am very out of date on it's gui, system logs are usually in the administration section.  However, the terminal is always the same so open one of those and enter "apropos system-log"   that will list all the manual pages with the term system-log in them.  To read a manual page enter "man" in front of whatever looks like a likely command and it will tell you how to use it.  Then, when you've found the right one just use it.  To exit from the manual pages and get back to the terminal enter "q"; As this is an admin tool you will need to put "sudo"  in front of whatever the command is, then immediately after entering it you will be asked for your password ( the same one you use on booting up ).  

Definately worth getting used to the terminal as whatever linux system you happen to be on it will always be much the same and one can do almost everything through it.  No matter what system you encounter, if it's linux and you can get to the terminal you'll know your way around it at first sight.  Occasionally for tasks which don't depend on a gui ( a lot do ) it can be worth booting into a command line session without a gui in order to save memory and increace speed. Good for fast anti malware checking for example.  One of the terminals big pluses is the amazing built in help. "man man"  in the terminal for details on how to use it.  It's good to have all that available if one can't get online for example.  Also though I haven't seen it here yet some advise may be malicious, there's a sticky warning about that on this forum.  So doing a quick "man" on things people suggest you copy and paste into the terminal is a sensible just-in-case precaution as well as being a good way to learn.

 One can open any number of terminals so I tend to have one for the manual pages and another for doing things in, one can also copy and paste between the two.     It's not urgent as one could probably spend years just using a gui, so no need to overface onself thinking one has to know all of it right now, but it is very handy knowlage to slowly aquire as, unlike graphic user interphases, it never really goes out of date or becomes obsolete.  Occasionally new commands are created or replaced but total, bath and baby too, revamps simply don't happen.  Two terminal commands you should use immediately on a new 'buntu install is to set and enable your firewall "sudo ufw default deny"  followed byt "ufw enable" . Note that the second command doesn't have sudo in front of it.  This is because sudo grants admin rights for a default of 15 minets, and if you are using the same terminal and haven't waited longer than that the first sudo will still be running.  If you want to end this privalage early ( wise if one is browsing online ) "sudo -k"  will do it. "man ufw" will tell you what all that lot is about.

Another way of reading the system logs is to first find out where they are using the locate or find commands in the terminal and then opening them with gedit.  Because some of them are for admin eyes only you'll need to use sudo or gksu ( similar command to sudo for graphic applications ) to access the lot.

---

### Post by Matrix01 on 2012-07-07
here's an output,

k@ubuntu:~$ sudo apropos system-log
[sudo] password for k: 
k@ubuntu:~$ 

this did not work.

> **houseworkshy said:**
> I haven't used lubuntu recently so am very out of date on it's gui, system logs are usually in the administration section.  However, the terminal is always the same so open one of those and enter "apropos system-log"   that will list all the manual pages with the term system-log in them.  To read a manual page enter "man" in front of whatever looks like a likely command and it will tell you how to use it.  Then, when you've found the right one just use it.  To exit from the manual pages and get back to the terminal enter "q"; As this is an admin tool you will need to put "sudo"  in front of whatever the command is, then immediately after entering it you will be asked for your password ( the same one you use on booting up ).  

Definately worth getting used to the terminal as whatever linux system you happen to be on it will always be much the same and one can do almost everything through it.  No matter what system you encounter, if it's linux and you can get to the terminal you'll know your way around it at first sight.  Occasionally for tasks which don't depend on a gui ( a lot do ) it can be worth booting into a command line session without a gui in order to save memory and increace speed. Good for fast anti malware checking for example.  One of the terminals big pluses is the amazing built in help. "man man"  in the terminal for details on how to use it.  It's good to have all that available if one can't get online for example.  Also though I haven't seen it here yet some advise may be malicious, there's a sticky warning about that on this forum.  So doing a quick "man" on things people suggest you copy and paste into the terminal is a sensible just-in-case precaution as well as being a good way to learn.

 One can open any number of terminals so I tend to have one for the manual pages and another for doing things in, one can also copy and paste between the two.     It's not urgent as one could probably spend years just using a gui, so no need to overface onself thinking one has to know all of it right now, but it is very handy knowlage to slowly aquire as, unlike graphic user interphases, it never really goes out of date or becomes obsolete.  Occasionally new commands are created or replaced but total, bath and baby too, revamps simply don't happen.  Two terminal commands you should use immediately on a new 'buntu install is to set and enable your firewall "sudo ufw default deny"  followed byt "ufw enable" . Note that the second command doesn't have sudo in front of it.  This is because sudo grants admin rights for a default of 15 minets, and if you are using the same terminal and haven't waited longer than that the first sudo will still be running.  If you want to end this privalage early ( wise if one is browsing online ) "sudo -k"  will do it. "man ufw" will tell you what all that lot is about.

Another way of reading the system logs is to first find out where they are using the locate or find commands in the terminal and then opening them with gedit.  Because some of them are for admin eyes only you'll need to use sudo or gksu ( similar command to sudo for graphic applications ) to access the lot.

---

### Post by houseworkshy on 2012-07-09
That's a puzzler.  You shouldn't need sudo in front of apropos as it isn't  an admin command.  Could be that it isn't installed in Lubuntu ( there are hundreds of commands ), all it does is riffle through the manual pages for installed commands looking for whatever word you followed it with which is handy but not crucial.  If you were to try apropos with a known command which should be any distro ( eg "cd" "cp" "rm" "grep" standard things like that ) you'd know if it was in or not  If it isn't and you wanted it just "sudo apt-get install apropos" and you've got it.   Also "system-logs" was only a guess based on what they are called in Ubuntu.  Could try just "log" or "logs".  Most graphic user interphases sitting on the ubuntu familly linux will have, somewhere in the administration section, a log viewer.  So look for something like "administration tools" or "administration" in the system menues. Some gui's have them as a tab in the system monitor. Perhaps I shouldn't have tried to answer this one, if all I've done is muddy the waters then I'm sorry. Late weekend babble perhaps.  You could also look in the preconfigured bookmarks in your browser for a help/tutorial  section.

---

### Post by Guilden_NL on 2012-07-11
This is a very common bug for Lubuntu 12.04.  I have submitted no less than 1,000 reports from many systems, yet it doesn't get much attention from the Lubuntu team.

I've messed around with various themes but have yet to find one that prevents this particular crash.

I configure many systems for senior citizens (over 75 yrs old) and this problem pushed me away from Lubuntu as my favorite.

It appears that the Lubuntu team is suffering from lack of resources.  I would truly like to help them, but I just started a new company and am up to my eyebrows in staying on top of the new business.

I am re-thinking my use of Lubuntu on all systems as a result of this problem that hasn't been acknowledged by the Lubuntu team.

---

### Post by Rodney9 on 2012-07-11
View log files in Ubuntu Linux
by VIVEK GITE 

Q. Can you explain me log files in Ubuntu Linux and how do I view logs?

A. All logs are stored in /var/log directory under Ubuntu (and other Linux distro).

Linux Log files and usage

=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file

To view log files at shell prompt

Use tail, more, less and grep command.
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot



For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by houseworkshy on 2012-07-11
So it's a bit of an established bug, pity.  However as the above post shows that logs are in the same place on all 'buntu systems, I wasn't sure, it's not crucial.  As some logs are for admin eyes only I'd suggest using "gksu gedit" to look at them, with the caution that one doesn't edit anything unless you are sure and really want to as the editor would be working with full privalages.  
To Guilden_NL I've found that Mepris is the least buggy system I've ever used, it's based on Debian stable, and very fast.   The only downside for older users is that the default GUI is KDE and the workspace switchers can be fiddly for those with small screens and poor eyesight.  But one can put Gnome2 on it instead as that is still in the stable debian repros.  Debian itself would be another good choice but it takes a little more time to set up, Mepris is basically a debian stable disto pre-configured for novices so, especially if maintaining several machines, saves time.

---

