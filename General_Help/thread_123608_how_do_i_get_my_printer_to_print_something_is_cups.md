---
title: "how do i get my printer to print something? is cups running???"
date: 2006-01-30
forum: General Help
---

### Post by ice60 on 2006-01-30
[color=blue]post #6 shows how i got it to work [here](http://ubuntuforums.org/showpost.php?p=704081&postcount=6)[/color]

hi, i am trying to get a HP PSC 1610 to work, i think all the software has been installed i followed instructions from [here](http://ubuntuforums.org/showpost.php?p=438985&postcount=4) but, i'm not sure how to get it to print a page :D 

when i goto System>Admin.>Printing> i see this...

[[IMG]http://img374.imageshack.us/img374/8505/screenshothppsc1600printingdef.th.png[/IMG]](http://img374.imageshack.us/my.php?image=screenshothppsc1600printingdef.png)

[[IMG]http://img353.imageshack.us/img353/1495/screenshotprinters0dk.th.png[/IMG]](http://img353.imageshack.us/my.php?image=screenshotprinters0dk.png)

does everything look OK? i haven't been asked to set my user name and password. i did come across it once and filled in my name and pw but it kept on popping back up and didn't look like it was accepting it.

when i look at running processes and look for cups all i can find is - cupsd and the argument is -F like this 
```
/usr/sbin/cupsd -F
```
does that look correct? how do i get it to print something :confused:  i think the printer's abit dim :lol:

---

### Post by l337killa07 on 2006-01-30
Everything seems good to me.  I just installed Ubuntu last night, and I just started using the printer when I got it yesterday.  I did the same you did, and it basically gave me a list of printers, I chose that which was most compatible, and it automatically installed my printer.  I printed a test page to make sure it worked, and it seemed fine.  Maybe someone with more knowledge of Ubuntu can help you..since I'm a newbie user :)

Killa

---

### Post by ice60 on 2006-01-30
hi, killa. did you see the window below? what did you do? do you just click on Forward, or did you do anything with the Printer Port?

[[IMG]http://img382.imageshack.us/img382/7696/screenshotaddaprinter6gc.th.png[/IMG]](http://img382.imageshack.us/my.php?image=screenshotaddaprinter6gc.png)

---

### Post by gslater on 2006-01-31
Have you tried the instructions from the HP website here:

[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

I have got to the point where I can set up the printer when connected via USB cable but still struggling to get it set up using my Belkin print server

---

### Post by ice60 on 2006-01-31
thanks, i just had alook and i did have to install afew extra packages i'd missed. but, what i'm confussed about is at no point in the installation was i asked for a root password. for all distros a password is asked for when you go to System>Administration>Printing>Add Printer. but i wasn't it just let me install the new printer.

also, i know cups is running, but there's an instruction for all distros to restart cups with this command
```
/etc/init.d/cups restart
```
but i don't have cups in init.d, i do have cupsys, but not cups.

```
~$ sudo  /etc/init.d/cups restart
sudo: /etc/init.d/cups: command not found

```

OK, i know those two things probably aren't important but it still doesn't work. i still have a window saying "Printing Jobs 2" :confused: and i have a printer constantly in the notification area but it doesn't print anything.

the printer works, it printed a page when it configured it self, when i clicked the scan button on it it used a piece of paper to scan nothing so it came out blank, but i suppose it works too. maybe i'll reboot and see if it works. if not i'll have a look in var at the logs.

oh, and when i goto [http://localhost:631/printers/HP-PSC-1600?which_jobs=completed](http://localhost:631/printers/HP-PSC-1600?which_jobs=completed)

i have this there
```
 	Description: HP-PSC-1600
Location: 
Printer State: processing, accepting jobs. 
"open device failed; will retry in 30 seconds..." 
Device URI: hp:/no_device_found
```

---

### Post by ice60 on 2006-02-03
thanks for the help. i got it all working after following the instructions from the pages below. then going into synaptic and installing - i found them after a search for hp psc
```
hpoj
hpoj-xojpanel
```

[http://ubuntuforums.org/showpost.php?p=438985&postcount=4](http://ubuntuforums.org/showpost.php?p=438985&postcount=4)

[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

i don't really know what did what but it all worked for me :) i can now use the HPLIP Toolkit at System>Preferences

---

