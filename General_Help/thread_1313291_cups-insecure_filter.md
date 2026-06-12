---
title: "cups-insecure filter"
date: 2009-11-03
forum: General Help
---

### Post by stephanosh on 2009-11-03
Hello,

After Installing my canon mp240 printer in ubuntu 9.10 and trying to print a test page I get this error saying "cups-insecure-filter". Please help! It worked with previous versions of ubuntu.

Stephanos

---

### Post by john_pollard on 2009-11-03
I had the same problem after upgrading, for my canon ip1800. Figured it out and registered just to post this. you need to find anything in /usr/lib/cups/filter and /usr/lib/cups/backend not owned by root, and chown and chgrp them to root

sudo chown root /usr/lib/cups/filter/whatever
sudo chgrp root /usr/lib/cups/filter/whatever
sudo chown root /usr/lib/cups/backend/whatever
sudo chgrp root /usr/lib/cups/backend/whatever

worked for me...

---

### Post by stephanosh on 2009-11-04
I also registered to post this :P

There are too many files. How can I make all the contents of these two folders to be owned by root by using the terminal?

---

### Post by stephanosh on 2009-11-04
thanks a lot mate!

Got into terminal and after asking it for help for these commands I solved my problem.

You actually have to type:

sudo chown -hR /usr/lib/cups/filter
sudo chown -hR /usr/lib/cups/backend
sudo chgrp -hR /usr/lib/cups/filter
sudo chgrp -hR /usr/lib/cups/backend

SOLVED

---

### Post by danmoo on 2009-11-05
Hmm, Terminal tells me that there's a missing operant.

I suppose the correct commands should rather be:

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

Anyway, even with "root" added to the commands, I am still experiencing the cups-insecure-filter message when I try printing from our network printers.

Removing and reinstalling cups as well as setting up the printers from scratch did not make any difference either.

---

### Post by stephanosh on 2009-11-05
Yes sorry about the mistake.

there should be a "root" there you are right.

Doing this solved my problem.

---

### Post by danmoo on 2009-11-05
And hey, I got good news, too: reinstalling the actual printer driver solved the problem in my case. Now our KONICA MINOLTA bizhub 250 is willing to print again =D>

---

### Post by Beansof57 on 2009-11-07
> **danmoo said:**
> Hmm, Terminal tells me that there's a missing operant.

I suppose the correct commands should rather be:

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

Anyway, even with "root" added to the commands, I am still experiencing the cups-insecure-filter message when I try printing from our network printers.

Removing and reinstalling cups as well as setting up the printers from scratch did not make any difference either.
I've tried all this, but my Brother MFC-3360C is still giving me back the same message. Anybody got any ideas?

I am very new to Ubuntu (and Linux), so please make the replies apt for chumps :-)

Thanks

---

### Post by beesblaas on 2009-11-08
I have an **Epson printer.**
This problem occurred after **upgrading to 9.10**, the printer worked fine before the upgrade.
I first tried the commands as described above but it would not work because the user did not have administrator rights.

Then I tried from another user account and the commands went OK but the printer had the same error message. 
[B]I then deleted and re-installed the printer, which fixed the problem.
[/B]
System > administration > printing.  
Inside this menu, delete the icon with your printer name.
Then (still inside this menu),  click "new", or Server > New > Printer
It will search for printers, will find your printer (if it is connected),
look for a driver and install it. This worked for me.

---

### Post by LequidMetal on 2009-11-25
> **danmoo said:**
> 

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend



Had the same problem with my canon mp140 series driver

executing these commands solved the problem .

---

### Post by fcorourke on 2009-11-27
Hi :-)  -- I have tried all the examples  & uninstalled and re-installed and still have "cups_insecure_filter"  is this just a Brother problem?? Does anyone know of a printer that will work my Brother MFC-465CN worked from 7.10 to 9.04 BUT the powers that be decided to cripple printing in 9.10 & move or delete the old fixes NO 666 to make it work, it would be too easy NO BUG REPORT UNDER THAT LISTING  -- MAYBE IS MY IMAGINATION. I guess I am too OLD and think that improving something that did work perfectly & now does not is way stupid, not that I am smart enough to fix it --- i love Ubuntu ------ but am amazed that every update kills all the things you fixed up & starts you all over I am building a new windows 7 machine now as I need a printer and scanner... & PUT Ubuntu away as I only have room to run one machine that can hook up & a week is long enough to read and try DIS & DAT -- on a problem that is minor or not important in the bug area. That makes Ubuntu a TOY as that is what a computer is that can not print. I am really sad  about this & will look this weekend

     Fred

---

### Post by Skinnybill on 2009-12-26
I have followed the steps... done the
sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend
with no errors
deleted and reinstalled my Lexmark X1270 with the z600 driver (that should work on ubuntu, following a post about installing x1270) and now when trying to print, immediatley i get 'stopped' on the document status

---

### Post by jeff21 on 2010-01-18
> **LequidMetal said:**
> Had the same problem with my canon mp140 series driver

executing these commands solved the problem .

The filter is no longer insecure, after changing the owner and group, but it still doesn't print the test page.  It prints about 1/4 or the test page and stops.

---

### Post by Cringer on 2010-01-25
This is starting to drive me nuts. I have done all that is in this thread, still can not get my printer to work. I have the warning gone, and then it could not locate my printer. It now seems to locate my printer but it just starts processing and does nothing. Bravo Ubuntu 9.10 is much more user friendly it seems since I had no problem with this in 9.04. I really had two hours to waste today though just so I could end up having to go back to sending a file to a Windows box so I can print from there. 

I do appreciate the help in this thread though. I got some of my printer problems fixed.

---

### Post by ghostwug on 2010-02-04
Thanks, had similar problem printing to PDF. Now solved.

---

### Post by CMEPTb on 2010-02-05
Confirmed with cups-pdf package (to print to pdf file). Changing everything in /usr/lib to root fixed it. Thanks!

---

### Post by Azati Prime on 2010-02-12
Thank you!  Thank you!  Thank you!  Thank you!  Thank you! I had completely given up hope on this printer.

---

### Post by nuchdog on 2010-03-08
I also had to:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend

also for those trying to get cups-pdf to work, you might have to manually create the folder ~/PDF

mkdir ~/PDF

---

### Post by creatorbri on 2010-07-08
> **nuchdog said:**
> I also had to:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend


This is what worked for me. Thanks for your help! I noticed the permissions on the file were:
```
-rws--S---
```

Once I changed that to:
```
-rwx------
```
via the commands listed above, it started working.

---

### Post by vibra on 2010-10-09
> **john_pollard said:**
> I had the same problem after upgrading, for my canon ip1800. Figured it out and registered just to post this. you need to find anything in /usr/lib/cups/filter and /usr/lib/cups/backend not owned by root, and chown and chgrp them to root

sudo chown root /usr/lib/cups/filter/whatever
sudo chgrp root /usr/lib/cups/filter/whatever
sudo chown root /usr/lib/cups/backend/whatever
sudo chgrp root /usr/lib/cups/backend/whatever

worked for me...



Thanks a lot mate! This solved my problem with my Lexmark z517 (Ubuntu 10.04) :P

---

### Post by knezmej on 2010-11-01
thanks!

cups-insecure-filter

---

### Post by najevi on 2011-03-21
This thread also helped me get my Canon MX700 printing successfully after first following advice from [http://ubuntuforums.org/showpost.php?p=7994228&postcount=1](http://ubuntuforums.org/showpost.php?p=7994228&postcount=1)

It seemed prudent to first check for any files/directories that were not owned by root viz.
```
ls -lR /usr/lib |grep -ive " root " |grep -ive "^$" |grep -ive "^/usr/lib" |grep -ive "^total"

```In my case this revealed files/directories in places other than the /usr/lib/cups directory tree but each one was related to a bubble jet printer and the "insecure" owner was my personal username instead of root.

So the recursive chown and chgrp fix was applied to /usr/lib rather than /usr/lib/cups viz.
```
sudo chown -hRv root /usr/lib
sudo chgrp -hRv root /usr/lib

```... and now the test page prints successfully.

---

### Post by Pogo1 on 2011-04-16
Thank you thank you thank you! My Canon mp240 now prints as it did before the 'upgrade' to 10.04.

In response to #3, I used Nautilus to view the files in list display and from the View -> Visible Columns menu I selected Owner and Group. Then I knew which files to change.

---

### Post by ntlsm on 2011-06-03
Thanks, this works for cups-pdf printer!

---

### Post by konnn on 2011-12-26
> **danmoo said:**
> Hmm, Terminal tells me that there's a missing operant.

I suppose the correct commands should rather be:

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

Anyway, even with "root" added to the commands, I am still experiencing the cups-insecure-filter message when I try printing from our network printers.

Removing and reinstalling cups as well as setting up the printers from scratch did not make any difference either.
Thank you , I solved the issue with those commands.
The point is why these archives had no root rights?

---

### Post by Orbital_sFear on 2012-03-14
I had the same error message, however my solution was different.

cd /usr/lib/cups/filter
sudo chmod 755 *
cd ../backned
sudo chmod 755 *

After that my insecure message was removed and things worked.
-Orbital

---

### Post by afrodeity on 2012-03-26
/usr/local/lexmark/lxk08/bin/printerdriver has insecure permissions (0100777/uid=0/gid=2)

I've tried everything here, nothing seems to work.

I've tried chmod 777, chmod 775 and chmod 700

---

