---
title: "veetle tv, malicious???"
date: 2010-11-24
forum: General Help
---

### Post by pavankumarl73 on 2010-11-24
Hello everyone,
               Today I installed veetle tv by executing .SH FILE. When I re-logged in it took about 30 sec for the desktop to load with error "CANNOT UPDATE IE.AUTHORITY" and there was NO SOUND. When I opened my home directory it was LOCKED and when I checked its permission it was set to some user group with ID 1016 (my USER ID IS 1000). But I'm the only user in my system. But other folders like DOCUMENTS,MUSIC,VIDEOS N DOWNLOADS weren't locked. But with successive relogins they were locked too with permission set to USER ID 1016. 

I googled about that application but found nothing about its malicious behavior.  

Any idea what might have happened?

---

### Post by Swagman on 2010-11-24
I installed that on my mates laptop last weekend.. He loves it.

Says it's better than Sopcast

I'll check with my mate tonight if he has had any permissions issues

[Edit]

These are the destructions I followed

> 
In the terminal first cd to the directory where you have the Veetle file.
Then do this: chmod +x veetle-0.9.17-linux-install.sh
Then do this: sh veetle-0.9.17-linux-install.sh
The install will start.
You will have to go through the terms of agreement by hitting 'enter' about a dozen or more times and then it will finish up.
Exit out, start Firefox and enjoy.
The above is the latest version of Veetle that I used. Any newer versions should make the necessary changes but the steps should be the same.


---

### Post by endotherm on 2010-11-24
what are teh current permissions for your home dir?
```
sudo ls -al /home/<username>/
```

---

### Post by pavankumarl73 on 2010-11-24
> **endotherm said:**
> what are teh current permissions for your home dir?
```
sudo ls -al /home/<username>/
```

I did i mistake, I deleted that user id and created new one

---

### Post by pavankumarl73 on 2010-11-24
I found the solution. Actually I ran the script as root. As per the forums of veetle if we run as root the permission of home directory changes to user id 1016 as I mentioned above. Running the script as normal user solves the problem

---

### Post by c.webster on 2011-07-28
>>>> I found the solution. Actually I ran the script as root. As per the forums of veetle if we run as root the permission of home directory changes to user id 1016 as I mentioned above. Running the script as normal user solves the problem <<<

? What does that mean?  

I have the same error of user 1016 apparently 'owning' my home drive.  I have no idea what the above statement means as I'm a complete Ubuntu numpty.  Can anyone tell me how I wrestle control of my home drive back from Veetle?  I want to keep Veetle though...

---

### Post by c.webster on 2011-07-28
Ok, fixed it after reading how to on another thread.

I followed this advice:

sudo chown <user>:<user> /home/<user>
sudo reboot 

(where user is your username)

this prevented an ICEauthority problem from occurring and also seemed to resolve some Sound issues I was having.

---

