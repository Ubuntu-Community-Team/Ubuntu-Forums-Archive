---
title: "klamav the database directory must be writable for UID 1000 or GID 1000"
date: 2010-08-07
forum: General Help
---

### Post by wandalalakers on 2010-08-07
When I used 8.04, I used klamav and never go this error.  Does anyone know how to fix this for kubuntu 10.04?  I'd rather use klamav (the gui) instead of clamav since I'm using kde.  Thx.

---

### Post by dino99 on 2010-08-07
check the Users & Groups klamav settings: might be some missing checkboxes

my clamav settings: id group is 125, group member is my user

---

### Post by wandalalakers on 2010-08-08
Klamav database directory was set to /var/lib/clamav
Here's three fixes:

Don't delete the /var/lib/clamav folder
Open klamav, click on the update tab, click cancel and type in the virus database directory area:
/home/username/.klamav/database 
and then click update now

or

open terminal
sudo dolphin /var/lib
delete clamav folder
open klamav
database folder becomes /home/username/.klamav/database and new virus signatures will be downloaded
I guess the uid 1000 or gid 1000 error occurs when clamav and klamav are installed on the same system when using kubuntu 10.04.

or

open terminal
sudo konqueror /var/lib
delete clamav folder
open klamav
database folder becomes /home/username/.klamav/database and new virus signatures will be downloaded
I guess the uid 1000 or gid 1000 error occurs when clamav and klamav are installed on the same system when using kubuntu 10.04.

---

### Post by NuahHuan on 2010-09-19
Many thanks for this post - I had the same problem on UBUNTU Netbook Remix latest version seems to have resolved the problem - thank you  

> **pcdoctor said:**
> Klamav database directory was set to /var/lib/clamav
Here's my fix:
open terminal
sudo dolphin /var/lib
delete clamav folder
open klamav
database folder becomes /home/username/.klamav/database and new virus signatures will be downloaded
I guess the uid 1000 or gid 1000 error occurs when clamav and klamav are installed on the same system when using kubuntu 10.04.

---

### Post by tarzan11234 on 2010-10-28
> **NuahHuan said:**
> Many thanks for this post - I had the same problem on UBUNTU Netbook Remix latest version seems to have resolved the problem - thank you

When i insert " sudo dolphin /var/lib" i have  an error message saying " command not found" . can you please help me . I have a virus .

---

### Post by wandalalakers on 2010-10-29
Here's another fix.
I got this error on a secondary computer later on and tried this just for giggles.
On this other computer I didn't delete the /var/lib/clamav folder.
I simply opened klamav, clicked on the update tab, clicked cancel and typed:
/home/myusername/.klamav/database
and then clicked update now
I'll modify my older post and add this to the fix also.

---

### Post by RT236 on 2010-11-10
> **pcdoctor said:**
> Klamav database directory was set to /var/lib/clamav
Here's three fixes:

Don't delete the /var/lib/clamav folder
Open klamav, click on the update tab, click cancel and type in the virus database directory area:
/home/username/.klamav/database 
and then click update now

or

open terminal
sudo dolphin /var/lib
delete clamav folder
open klamav
database folder becomes /home/username/.klamav/database and new virus signatures will be downloaded
I guess the uid 1000 or gid 1000 error occurs when clamav and klamav are installed on the same system when using kubuntu 10.04.

or

open terminal
sudo konqueror /var/lib
delete clamav folder
open klamav
database folder becomes /home/username/.klamav/database and new virus signatures will be downloaded
I guess the uid 1000 or gid 1000 error occurs when clamav and klamav are installed on the same system when using kubuntu 10.04.

:)Worked Perfectly!!!
THANKS!!!

---

### Post by jchw on 2010-11-21
I tried all the fixes and they came up 'command not found'. I have been trying to make Klamav work since I installed Ubuntu 10.4 six months ago without success. On the other hand I do not have any viruses so does it matter other than my sense of failure at making this thing work.

---

### Post by Wretched Tundra on 2011-01-14
> **jchw said:**
> I tried all the fixes and they came up 'command not found'. I have been trying to make Klamav work since I installed Ubuntu 10.4 six months ago without success. On the other hand I do not have any viruses so does it matter other than my sense of failure at making this thing work.

I am using 10.4 and had to do the follow to get it to work.

open terminal 
mkdir /home/(whatever your username is)/.klamav/database

after that just follow this step from pcdoctor

Don't delete the /var/lib/clamav folder
Open klamav, click on the update tab, click cancel and type in the virus database directory area:
/home/username/.klamav/database 
and then click update now

should be good to go after that but none the less hope it works for you.

---

### Post by Wretched Tundra on 2011-01-14
duplicate of above message

---

### Post by jchw on 2011-01-15
Many thanks for this as it worked very well. I am not sure what I did wrong the first time but it worked immediately. Thanks again.

---

### Post by bartekklimczak on 2011-01-16
for ubuntu10.04 you need to replace dophin with 'nautilus' and complete the steps ie delete clamav etc

well thats what worked for me to not get the command not found problem

---

### Post by bartekklimczak on 2011-01-16
for ubuntu10.04 you need to replace dophin with 'nautilus' and complete the steps ie delete clamav etc

well thats what worked for me to not get the command not found problem

---

### Post by bartekklimczak on 2011-01-16
for ubuntu10.04 you need to replace dophin with 'nautilus' and complete the steps ie delete clamav etc

well thats what worked for me to not get the command not found problem

---

### Post by bartekklimczak on 2011-01-16
for ubuntu10.04 you need to replace dophin with 'nautilus' and complete the steps ie delete clamav etc

well thats what worked for me to not get the command not found problem

---

### Post by Ubuntered on 2011-01-19
Thanks for this, it worked great for me. I think the other fixes didn't work for me because I'm running Ubuntu with Kubuntu packages. 

version: 10.04 LTS The Lucid lynx 64-bit

---

### Post by marklusty on 2011-03-07
> **bartekklimczak said:**
> for ubuntu10.04 you need to replace dophin with 'nautilus' and complete the steps ie delete clamav etc

well thats what worked for me to not get the command not found problem

this is the way forward,cheers     :guitar:

---

### Post by Racket on 2011-04-17
OK, I had the same issues and it worked out by doing the following:

First of all, don't delete the /var/lib/clamav folder.

Open terminal, write:
mkdir /home/username/.klamav/database

Open KlamAV, click on the Update tab, click Cancel and type in the virus database directory area:
/home/username/.klamav/database 

and then click Update now.

This should work.

---

### Post by dustrho on 2011-06-10
> **Wretched Tundra said:**
> I am using 10.4 and had to do the follow to get it to work.

open terminal 
mkdir /home/(whatever your username is)/.klamav/database

after that just follow this step from pcdoctor

Don't delete the /var/lib/clamav folder
Open klamav, click on the update tab, click cancel and type in the virus database directory area:
/home/username/.klamav/database 
and then click update now

should be good to go after that but none the less hope it works for you.

Just wanted to say THANK YOU!!!! Your instructions helped me finally get this damn thing working. Great job and thanks!

---

### Post by leram12 on 2011-07-11
:PThanks, after trying other fixes, this is the only one that worked. Kudo:Ps:P.
> **Wretched Tundra said:**
> I am using 10.4 and had to do the follow to get it to work.

open terminal 
mkdir /home/(whatever your username is)/.klamav/database

after that just follow this step from pcdoctor

Don't delete the /var/lib/clamav folder
Open klamav, click on the update tab, click cancel and type in the virus database directory area:
/home/username/.klamav/database 
and then click update now

should be good to go after that but none the less hope it works for you.

---

