---
title: "FFSAKE - router ftp setup"
date: 2006-04-04
forum: General Help
---

### Post by neoroses on 2006-04-04
i wana setup a ftp server on my ubuntu box to share files with friends over the internet, however i am behind a router an am finding this EXTREAMLY difficult and fustrating, i have read every relivent post on this board and it jsut doesnt work so can some one please help me set this up? thanks

sam

---

### Post by NewbieNik on 2006-04-04
OK, we need some info first. What router have you got? Have you installed any FTP software on the Ubuntu box?
There is plenty of people here waiting to help you, but give us something to work with.
Basics of FTP are:-
Opening FTP port on router/firewall and Server
Ensure server software is installed and running
triple check security.

---

### Post by MJN on 2006-04-04
Also, what exactly isn't working? It doesn't surprise me that it's not - FTP can be a bugger to configure - however it could be one of many things.
 
Have you checked out the thread at [http://www.ubuntuforums.org/showthread.php?p=680342]("http://www.ubuntuforums.org/showthread.php?p=680342") ? Ignore the SSH squabblings (although using it would likely help you out!!) - are the symptoms discussed along the lines of what you're seeing? That is, can you login okay but not do much else?
 
Mathew

---

### Post by neoroses on 2006-04-04
okies guys =) well im using the belkin f5d7632-4, works fine with windowz,,,dont wana use that tho lol. my ip atm is 88.109.28.26 , i have tryed almost every FTP sever there is for TUX, being unsucsessfull with all, i have open all the ports necissery and am compleatly stuck :P ,,, thanks guys 

neoroses, am currently looking at that post thank

edit - } after readin that post, it is not similar there isnt even a log in option, just doesnt work [ftp://88.109.28.26](ftp://88.109.28.26) nothing happens =( doesnt even work with LAN login

---

### Post by NewbieNik on 2006-04-04
If it works with windows then we will asume for the time that port 21 is open and fowarded to the PC (Check your PCs ip address against the ip address that the router is fowarding port 21 traffic to)
I have used PureFTP with the webmin module to configure it. (I'm no good at command line configurations and find webmin a vital piece of kit in the transition fom Win to Linux)
Ensure you have a folder for the FTP server to use and that FTP users and Groups have the appropriate permissions to read/write.
PureFTP is the easiest to configure that I have found so far.

---

### Post by neoroses on 2006-04-04
at the end of the day im just not top notch at comfiguring thigs,,,so could a simple step by step explination be given please =) thanks for your help guys -- okies got pure fpt up n running but how to i add usernames and allow internet acsess instead of jsut lan

---

