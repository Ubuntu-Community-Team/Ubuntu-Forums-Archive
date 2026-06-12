---
title: "KMyMoney 1.0 package"
date: 2009-08-23
forum: General Help
---

### Post by arch0njw on 2009-08-23
KMyMoney has released their 1.0 version.  Who should I bribe to get an package built and updated into the repositories?

---

### Post by aharown07 on 2009-09-23
Yes, please! I'm googling alot but not finding info on how to install the new release in Ubuntu.

---

### Post by arch0njw on 2009-09-23
> **aharown07 said:**
> Yes, please! I'm googling alot but not finding info on how to install the new release in Ubuntu.

I should have updated this.  Thank you for replying and reminding me.  You can get the packages from the PPA.  You need to be forewarned that this is a *Personal Package Archive* and is so named for a reason.  These packages can become unstable (though the KMyMoney2 folks are pretty good about that).

[https://launchpad.net/~claydoh/+archive/ppa]("https://launchpad.net/%7Eclaydoh/+archive/ppa")

You can either update your sources, or you can download the DEBs and install them manually (sudo dpkg -i *deb-file-1 deb-file-2*).  Personally, I recommend the latter so you remain in control and don't get any kind of nightly build that you don't want.

If you download, you need to get the proper architecture "kmymoney2 - 1.0.1-0ubuntu1~jaunty5" package _*and*_ the "kmymoney2-common_1.0.1-0ubuntu1~jaunty5_all.deb" package.  Of course, get the proper hardy package if you are using hardy.  You can install them both at once with the following command (assuming jaunty and amd64 -- edit the command as appropriate for your version and architecture):  *sudo dpkg -i kmymoney2_1.0.1-0ubuntu1~jaunty5_amd64.deb kmymoney2-common_1.0.1-0ubuntu1~jaunty5_all.deb*

---

### Post by aharown07 on 2009-09-23
Thanks. I think I'd rather install the debs. I'm not entirely clear on that process--never done it--but will give it a go. There are just some KmyMoney annoyances that are driving me nuts in my 0.9 and I'm hoping they are corrected in 1.0.1.

Edit: I'm not seeing where to download these files manually. Where would I find them?
Edit; nevermind, found them.

---

### Post by aharown07 on 2009-09-23
OK, done. That wasn't so bad.:)

But they haven't fixed my annoyances list... so, maybe in a couple more releases!

---

### Post by Hei Ku on 2009-09-23
What are your annoyances? Perhaps I can help

---

### Post by aharown07 on 2009-09-24
Funny you should mention that. I posted a wishlist at the KMyMoney website and someone on the development team responded very quickly (which is kind of amazing to me in itself.. I'm impressed).

What was driving me nuts was the apparent requirement to move from keyboard to mouse in order to use the split transaction function.. and then lots of double clicking in the split form to open new rows for keying in data.

What they pointed out to me was...
1. If you're tabbing through the main transaction form/grid, you can tab to the split button then hit **spacebar** to activate the splits form

2. Once on the splits form, you can just start typing. It doesn't *look* like you can (you're not visibly in a field w/a cursor), but you can.

3. When you finish a row, you can tab to the green check then hit **spacebar** again to get a new row.

So, most of my annoyances gone right there.  There remains some work to be done on the splits interface, though. It's not apparent at all that you can do these things. I probably overlooked it in the manual, but you shouldn't have to read a manual to figure out how to enter data from the keyboard... in what is basically a data-entry application.

Another annoyance is that the **accounts tree does not stay expanded.** It's pretty useless until you expand some part of it. I suppose some like it that way, but I submitted on my wishlist an option to have the tree always expanded.

Also suggested ability to **change the tab sequence** in the transaction form. I split *alot* (goes w/shopping at Walmart I guess) and prefer to enter the total amount first, then the splits. The current tab order goes to the amount field *after* the category and split fields. So I have to go to the amount, then backtab to the split button. Slows entry down a bit. (And that matters since my wife manages to spend money at 300 different places every day! ... where's that marital counseling thread? :) )

---

### Post by Hei Ku on 2009-09-24
Yes, there are some things to be improved on the interface. Noted for the next release but I can't make any promises.

The accounts tree, I think I can find a way to make it stay like the last time you used it. Maybe.

The tab sequence. Can't you just enter the splits before the amount? Is there something that makes it better to enter the amount first?

---

### Post by arch0njw on 2009-09-24
> **Hei Ku said:**
> Yes, there are some things to be improved on the interface. Noted for the next release but I can't make any promises.

The accounts tree, I think I can find a way to make it stay like the last time you used it. Maybe.

The tab sequence. Can't you just enter the splits before the amount? Is there something that makes it better to enter the amount first?

It is nice to have the total entered first so when entering splits you can verify that the splits add up correctly.  You can easily see any discrepancy as the split view does the math for you.

That's my two shekels...

---

### Post by aharown07 on 2009-09-24
Splits... yes, dittos there. What I like to do is divide up the transaction into budget categories and it's just easier if the correct total is in place to ensure everything "goes somewhere." 
Seems like I remember having some trouble w/Quicken once upon a time because I kept ending up w/the wrong total and not noticing.

In a better world, I'd always remember to check the splits total against the receipt or whatever I'm using but... seems more intuitive to get it in there first.

Also, about accounts tree... maybe the trick is to make the expand button that's already there sticky or add a checkbox by it to make it sticky... of course, that's just interface talk and I have no idea what would be required under the hood.

I appreciate how responsive you guys have been!

---

### Post by Hei Ku on 2009-09-24
Ok. I understand now. The main issue is having the total splits checked against the transaction total, right?
So, either you have to enter the amount first, and then go back to splits, or you go into splits first, but then the application does not check the total.

---

### Post by aharown07 on 2009-09-24
Yep. 
Of course, there may be zillions of users who would *hate* to have the total first, so that's why I'm thinking "option."

---

### Post by Hei Ku on 2009-09-24
Or perhaps a total amount field inside the splits dialog?

---

### Post by aharown07 on 2009-09-24
That's thinking outside the box. Can't think of any reason why that wouldn't work... assuming you come to it before the first split row.

---

### Post by Hei Ku on 2009-09-25
Ok. For now, there is a config option to change the tab order. This is in CVS.

---

### Post by aharown07 on 2009-09-25
Yes, I heard from Thomas over there also... says the tab order will be changeable via a config file edit. And also it looks like 1.0.2 will make the acct tree setting stick between sessions.
=D>

---

### Post by Hei Ku on 2009-09-25
Yes, I pointed him to this thread and he got to work before I even noticed. :D

Now I have to port that over to the KDE4 version.

---

### Post by shainkeit on 2009-10-17
Hi 

I'm new to Linux and is trying to install Kmymoney. i used the following command "sudo dpkg -i deb-file-1 deb-file-2" and got the error below. Im running a 64 bit Ubuntu 9.04.

Any help would be kindly apreciated.

dpkg: error processing deb-file-1 (--install):
 cannot access archive: No such file or directory
dpkg: error processing deb-file-2 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 deb-file-1
 deb-file-2

Thank you

---

### Post by Hei Ku on 2009-10-17
you have to replace deb-file1 and deb-file2 with the full name of the .deb files you are trying to install.

---

### Post by shainkeit on 2009-10-17
soory for sounding like a complete idiot but i trying to install kmoney. I have downloaded the stable version from there site. the file I have is kmymoney2-1.0.2.tar.bz2.

Thank for your time

---

### Post by shainkeit on 2009-10-18
I need help I have tried every thing and cannot seem to get this to install. I treid the net but there not a lot available on .deb ubuntu 9.04 64 kmymoney installations.

Thank you for your time and passions

---

### Post by Hei Ku on 2009-10-18
You have a PPA with the latest version: [https://edge.launchpad.net/~claydoh/+archive](https://edge.launchpad.net/~claydoh/+archive)

Please uninstall any version you have, then follow the instructions there.  If you can't, wait for Karmic, which ships with version 1.0.2. and it's less than a couple of weeks away.

---

