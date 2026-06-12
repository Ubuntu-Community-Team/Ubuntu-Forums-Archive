---
title: "Sudo in script -- How do I do it?"
date: 2010-11-20
forum: General Help
---

### Post by dorlow on 2010-11-20
Ok, so I'm trying to setup a backup script.  This is what I have so far...

echo "**my password**" | su

sudo tar -z --create \
           --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Desktop_Backup.tgz \
           --listed-incremental=/var/log/usr.snar \
           /home/david/Desktop/

sudo tar -z --create \
           --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Filing_Cabinet_Backup.tgz \
           --listed-incremental=/var/log/usr.snar \
           /home/david/Filing\ Cabinet/


sudo tar -z --create \
           --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Pictures_Backup.tgz \
           --listed-incremental=/var/log/usr.snar \
           /media/0A2E27592E273D57/Pictures/

sudo tar -z --create \
           --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Videos_Backup.tgz \
           --listed-incremental=/var/log/usr.snar \
           /media/0A2E27592E273D57/Videos/

It's working fine except when it runs, it prompts for a password.  I've been searching around the web and I can't find a good answer.  

Please when replying, just tell me really easy how to do it.  Don't assume I know anything.  I've found lots of solutions and they all say sudo in a script is bad.  I don't care... it's just my laptop.  If the right way is easy, then I'm up to it.  I was trying to figure out if I could pipe the password into the sudo command and that didn't work.  I tried adding my user to the root and sudo user groups and it still prompts.

---

### Post by Crusty Old Fart on 2010-11-21
Howdy dorlow:

Edit the sudoers file with the following command:
```

sudo visudo

```Add the following two lines to the bottom of the file, assuming your username is: dorlow
```

# Allow dorlow to run any commands anywhere without a password
dorlow       ALL=(ALL)       NOPASSWD: ALL

```Make sure you save the file as: [COLOR=Green]**/etc/sudoers**[/COLOR] and _NOT_ [COLOR=Red]**/etc/sudoers.tmp**[/COLOR] as the editor will suggest.

After you do this, you'll be able to use sudo in your scripts...and...you'll never need to enter your password when you use sudo in the shell.

Enjoy.

---

### Post by v1ad on 2010-11-21
kinda suicidal, imo

---

### Post by bananas4370 on 2010-11-21
> **dorlow said:**
> 
I've found lots of solutions and they all say sudo in a script is bad.  I don't care... it's just my laptop. 

If you don't care, then ...

```
echo password | sudo -S program
```

---

### Post by Crusty Old Fart on 2010-11-21
> **v1ad said:**
> kinda suicidal, imo
How is it suicidal, vlad?

---

