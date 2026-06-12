---
title: "Date &amp; Time Issue with installing 10.04 to PPC"
date: 2010-08-19
forum: General Help
---

### Post by releach on 2010-08-19
I'm trying to install Ubuntu 10.04 to my ibook g4 and am coming up against a problem I've seen some documentation for in these forums. 

I booted to a live cd, was able to install Ubuntu from it. On the required restart, however, I am not able to log in to my account using the username and pw I set during installation. I get an "authentication failed" error message each time. 

I've had a longstanding problem with my ibook with the date and time--the computer thinks it's 1969, which, well, it's not. I tried to change the date using open firmware using instruction from a Swiss Ubuntu forum post I found. Basically, at the open firmware prompt I'm entering: 

decimal dev rtc 23:33:22 08/19/2010 set-time

and then, at the ok prompt, 

mac-boot

This, according to the post I found, should reset the date to the approx right time period and allow me to log in to my account (not sure what the genesis of this problem is, but that's what I was 'told' to do in that post to fix this problem). 

It's not working. I am still getting the "authentication failed" error message when I try to log in to Ubuntu with my username and password. I really want to make this work; please help! Any guidance or suggestions much appreciated. The live cd I am using to do my Ubuntu install appears to be clean and error-free.

---

### Post by silbak04 on 2010-08-19
I'm not sure what the date and time has anything to do with your authentication, but I would just try resetting the password.

This may help

[http://www.cyberciti.biz/faq/linux-reset-forgotten-root-password/](http://www.cyberciti.biz/faq/linux-reset-forgotten-root-password/)

[http://www.linuxclues.com/articles/11.htm](http://www.linuxclues.com/articles/11.htm)

---

### Post by anirudhtomer on 2010-08-19
I think what you can do is open the ubuntu in recovery mode from your grub.
then add a new user from the command line.
the command is "useradd"....u can check more about it as linux man pages are available...just google them...& once you create a user this way don't forget to create a password too else you won't be able to login with a null password & the next time u start your ubuntu via the GUI just type the new user name & password.
I hope this solves your problem....

---

