---
title: "Webmin login"
date: 2011-08-23
forum: General Help
---

### Post by LatencyRemix on 2011-08-23
Hi all, Been trying to set up a mumble server for the past week.  Went and got the 64bit ubuntu v11.4 i think it is and have been trying to figure out webmin.

Getting it installed is fine but when i head to the web address to log in i get stumped.  I use my login creds but it says that its invalid.

"webmin install complete. you can now login to (url) as root with your root password"

now i assumed that this was my ubuntu user details that i use for sudo login but that doesn't work for me.  I've tried a few variants like using admin as a user and pass but nothing happens.  

I've been locked out and restarted installs from fresh so many times.


Anyone able to help me out so i can get my murmur up and running??

Cheers

LatencyRemix

---

### Post by LatencyRemix on 2011-08-23
problem sorted. was nice to see all the helpful reply's i got on the topic -_-'

---

### Post by crazyness003 on 2011-08-24
Sorry, I just stumbled onto your problem.

What did you do to fix the problem?

---

### Post by LatencyRemix on 2011-08-24
I had to re-enter a webmin password.  After i added webmin to the repository (sudo gedit /etc/apt/sources.list) it was a lot easier to install.  Then i had to re-enter an admin password for the root user. (sudo /usr/share/webin/changepass.pl /etc/webmin root "newpassword")

After that was done installing mumble and murmur was easy enough, now the next hurdle is trying to get others to connect to it.

It works fine over network but people cant join over the internet.  Don't know where to go from there.  My static ip is getting changed next month but even with out it yet they should be able to connect.

---

### Post by crazyness003 on 2011-08-24
Sounds like that may be attributed to a NAT issue. Are you behind a router or firewall?

I dont know what ports mumble/murmur use, but I've had that issue with many-a services hosted from my box

Also, thank for clarifying. I'm sure this info will make someone's life a whole lot easier in the future.

---

### Post by LatencyRemix on 2011-08-25
Yeah, i had a look through my virtual server on my router and i had put XXX.XXX.1.5 instead off XXX.XXX.1.6 

Moments like that deserve a sticker

---

### Post by crazyness003 on 2011-08-26
That actually made me laugh. Congratulations though. May I suggest you mark this thread as solved for future generations to learn.

---

