---
title: "Package Operation Failed on update"
date: 2012-07-22
forum: General Help
---

### Post by etphoto on 2012-07-22
I have 197 updates waiting to be installed but every time I click install on the update manager I eventually get a "package operation failed" message and the updates don't get installed.  I have 12.04 installed.  Any one able to point me in the right direction to get the updates installed?
 
I get the following message when I click on details:

installArchives() failed:  Extracting templates from packages: 13%% Extracting templates from packages: 27%% Extracting templates from packages: 41%% Extracting templates from packages: 55%% Extracting templates from packages: 69%% Extracting templates from packages: 82%% Extracting templates from packages: 96%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 13%% Extracting templates from packages: 27%% Extracting templates from packages: 41%% Extracting templates from packages: 55%% Extracting templates from packages: 69%% Extracting templates from packages: 82%% Extracting templates from packages: 96%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 13%% Extracting templates from packages: 27%% Extracting templates from packages: 41%% Extracting templates from packages: 55%% Extracting templates from packages: 69%% Extracting templates from packages: 82%% Extracting templates from packages: 96%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 13%% Extracting templates from packages: 27%% Extracting templates from packages: 41%% Extracting templates from packages: 55%% Extracting templates from packages: 69%% Extracting templates from packages: 82%% Extracting templates from packages: 96%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'libgtk-3-0': Input/output error 
Error in function:

---

### Post by plucky on 2012-07-23
Open a terminal and run ```
sudo apt-get clean
sudo apt-get install -f
``` and see what that shows you.

If you still get the error,post to the forum.

Good luck

---

### Post by etphoto on 2012-07-23
Thanks for the reply.

I did what you suggested.  After entering 
sudo apt-get install -f
I get the following;

Reading package list . . . Done
Building Dependency Tree
Reading state information . . . Done
0 upgraded, 0 newly installed, 0 to remove and 212 not upgraded.

I then ran upgrade manager again and eventually received the same message "Package operation failed"  and when clicking details get the same list as I posted in my original message.  Help!!

ET

---

### Post by plucky on 2012-07-23
> reading files list for package 'libgtk-3-0': Input/output error
Error in function: 

Try changing the Download Server using the Settings button in the update manager and then running ```
sudo rm /var/lib/apt/lists/* -vf
``` then run the two commands again ```
sudo apt-get clean
sudo apt-get update
```

Good Luck

---

### Post by etphoto on 2012-07-24
Thanks for the help Plunky.  Worked on it for several days.  Searched these forums along with google.  Nothing I did worked.  I ended up just reformatting my hard-drive and re-installing 12.04.  Works now.  (crossing fingers).

---

