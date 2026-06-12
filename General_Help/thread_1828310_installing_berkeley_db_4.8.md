---
title: "installing berkeley db 4.8"
date: 2011-08-18
forum: General Help
---

### Post by smcrossman on 2011-08-18
I doubt this is the right forum, but I'm a little lost as to where to turn.  I am installing bogofilter to use with Clawes and Postfix. I've tried both bogofilter and spamassassin and neither worked properly because I didn't take time to sit down and do proper install, set up and teaching.

I'm doing this on a 64 bit desktop with NVidia drivers running 11.04.  This will be the mail server for a small local network as well as a client.

I have bogofilter 1.2.2 downloaded and extracted per instructions.  Configure does not complete exiting with an error about unable to link to libdb.  The suggestion is to make sure Berkeley DB developer is installed.  I've looked through Software manager and searched in Synaptic both are showing libdb installed.  I'm not sure that is what I"m really looking for here though... 

To complicate things just a little I currently only have mobile broadband access so Software, & Synaptic & UPdater all tell me to check my internet connection and EVERYTHING is classified as unauthorized.  I've been doing updates via apt-get update, apt-get dist-upgrade and apt-get upgrade.  If I actually need to download a package I have to look for someone's unsecured wifi in the complex I'm living in and steal some wifi time.

So what/how do I resolve the ./configure error to move on into compiling & installing bogofilter?

---

### Post by smcrossman on 2011-08-19
bump...

---

### Post by dino99 on 2011-08-19
[http://archpub20.cs.ccu.edu.tw/cgi-bin/dwww?type=file&location=/usr/share/doc/bogofilter-bdb/integrating-with-postfix](http://archpub20.cs.ccu.edu.tw/cgi-bin/dwww?type=file&location=/usr/share/doc/bogofilter-bdb/integrating-with-postfix)

[http://scalability.org/?p=1551](http://scalability.org/?p=1551)

---

### Post by smcrossman on 2011-08-19
Thank you! Those articles will both be very helpful when I actually get the darned packages installed.  From looking at the first one I see that they used a different location to install bogofilter than the install information provided with the package does. BUT the postfix is installed to the location that they give to install the bogofilter to. So I might need to change that pdq.  

I also guess I can go ahead and start cleaning things up and start the install of postfix while I hunt for the solution to my currently DB issue.  Unfortunately I'm doing things a little backwards since actually downloading and then compiling (if necessary) to install is easier due to my internet connectivity.

Any other links dealing specifically with using Berkeley DB and how to fine tune so that it is recognized and used by bogofilter would be appreciated as well!

---

### Post by smcrossman on 2011-08-19
Okay, I've found the postfix download & documentation. I'm comfortable with that since it is the actual postfix site (linked from Software Center)

I have found a site with download of Berkeley DB 4.8. It looks legit, but what do I know about such things? If I give a link to the page can someone make sure it's at least legit. I know you can't say safe since it isn't part of the repositories.  Also what is meant by the developer package? The bogofilter documentation specifically states that both the database and the developer be installed.

[http://www.linuxfromscratch.org/blfs/view/svn/server/db.html](http://www.linuxfromscratch.org/blfs/view/svn/server/db.html)

Yes, the best approach to this project would be to wait until I have full internet access again and can use the repositories, but due to my situation its this weekend or not again for quite a while and I won't have internet access before the end of the month.  Besides I have installed both postfix & bogofilter (and spamassassin) from repositories and haven't been able to get it to work. I personally need to go through each step in the build to understand what I've missed or what needs to be different for my system.

---

