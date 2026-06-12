---
title: "need a script to turn off a program, check for rsync"
date: 2011-07-16
forum: General Help
---

### Post by plecebo.mc on 2011-07-16
Hello I need to make an automated server backup for my ubuntu 10.04.2 server

It is a samba server via hamachi.

I plan on using cron to automate rsync once a month but before rsync runs i need a script of some kind to disconnect hamachi and then wait until rsync completes to turn hamachi back on.

How would i do this?  

Someone said i need my rsync job to touch a file when it starts and remove it when it finishes im not to sure what he meant by that.

---

### Post by conradin on 2011-07-16
I dont know what hamachi is but does it run as a process?
expect and TCL/Tk scripting might make you very happy. 
else i would assume to use bash and do a kill command for samba,
then run the back up script, then reconect (init) samba when the back up completes. 

is that an accurate psudo-code of what you want to do?
(I'll help you script it if it is.)

---

### Post by atca on 2011-07-16
In your cron script something like this should work..

> #!/bin/bash
#Stop hamachi
sudo hamachi -c /etc/hamachi stop
#Wait for hamachi to stop
sleep 15

#insert your rsync commands

#Wait for xx seconds after rsync has completed
sleep 30
#Restart hamachi
sudo hamachi -c /etc/hamachi start




Why do you need to take hamachi down, to stop people writing to the samba shares?

---

### Post by plecebo.mc on 2011-07-16
atca: yes i would like to keep people from writing to the samba folder while it backs up. but are you saying that i can kill samba and not worry about hamachi. I would assume that i should not have anyone using my shares while its backing up unless im totally wrong. Is there a better way at doing that.

Thank you for the script

---

### Post by plecebo.mc on 2011-07-16
so i would do this then 

$ sudo crontab -e
______________________________________

# m h  dom mon dow   command
0 0 * * * /usr/bin/clamscan -v -r /srv

0 9 1 * *  
#!/bin/bash
#Stop hamachi
sudo hamachi -c /etc/hamachi stop
#Wait for hamachi to stop
sleep 15

sudo rsync -g -o -p -a /srv/samba/ /media/Backup/

#Wait for xx seconds after rsync has completed
sleep 30
#Restart hamachi
sudo hamachi -c /etc/hamachi start
_______________________________________________


it doesnt seem right to me :/

---

### Post by plecebo.mc on 2011-07-16
nvm i found out

---

### Post by atca on 2011-07-16
I'd probably create a shell script with it in and use cron to call out to the shell script.

Something along that principle should work it depends how you run hamachi really. 

Personally I think you'll find it easier not to mess with the networking but to take samba down instead. Using the follow repectively, I usually have awful issues bringing hamachi down and up cleanly.

/etc/init.d/samab stop

/etc/init.d/samba start

---

### Post by linuchsan on 2011-07-17
You don't need the sleep command.
It is better to use ps for example. If the service is really down,
than proceed.

---

### Post by mikejonesey on 2011-07-17
hmmm sleep is cool no point in processing an if a zillion times whilst copying...

lock files are more for when you have multiple processes though; ie you which to determine if a group of processes launched from another script are running...

what you want to do is create a function called i'm done; create a trap which launches the funtion which lanches hanachi again...

eg
```

/etc/init.d/hama stop
rsync files...
rsync files...
rsync files...

function imDone()
{
   echo "starting hamacho again all done..."
   /etc/init.d/ham start
}

trap imDone EXIT

```lemmie kno if you need help with this :)

---

### Post by plecebo.mc on 2011-07-18
Well when I bash the script samba_back that i made I get back an error stating samba is not installed and if I meant to install samba4 after that rsync goes to work and then i get the error after thats done... expected

I checked under the dir /etc/init.d/samba  but there is no samba directory under /etc/init.d/   maybe I needed to install samba4 ??!! :/

When I do an aptitude install for samba it says I already have it installed along with samba-common and so forth.

This seems very disturbing because I used to be able to use samba start ... stop 
Maybe that was on my first install this is my second go at samba im doing much better
__________________________________

Now getting back to what mikejonesey said:
I am a little confused as to what this does and why I need it done this way. How exactly would I go about using this and whats the benefits of this method.

I will start doing some research on i'm done functions.

O_o

---

### Post by plecebo.mc on 2011-07-19
this is my script i made

#!/bin/bash
#Stop samba
sudo /etc/init.d/samba stop
#Wait for samba to stop
sleep 15

sudo rsync -v -g -o -p -a /srv/samba/ /media/Backup/

#Wait for xx seconds after rsync has completed
sleep 30
#Restart samba
sudo /etc/init.d/samba start


if its any help

does it use smbd instead of samba cause i think i read some where it does ill check this

---

### Post by plecebo.mc on 2011-07-19
ok i figured it out you have to use this:

#!/bin/bash
#Stop samba
sudo stop smbd
#Wait for samba to stop
sleep 15

sudo rsync -v -g -o -p -a /srv/samba/ /media/Backup/

#Wait for xx seconds after rsync has completed
sleep 30
#Restart samba
sudo start smbd

---

### Post by mikejonesey on 2011-07-19
if rsync takes longer;
```
#!/bin/bash
#Stop samba
sudo stop smbd
#Wait for samba to stop
sleep 15

sudo rsync -v -g -o -p -a /srv/samba/ /media/Backup/

function meFinshed()
{
    #Restart samba
    sudo start smbd
}

trap meFinshed EXIT
```

---

