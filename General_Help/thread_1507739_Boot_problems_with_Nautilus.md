---
title: "Boot problems with Nautilus"
date: 2010-06-12
forum: General Help
---

### Post by espressobeanie on 2010-06-12
Hi all,

I'm stumped. I have the following error messages on my computer after I enter my password and boot into gnome:

Could not update ICEAuthority file /home/sam/.ICEauthority

Then:

There is a problem with the configuration server, /usr/lib/libconf2-4/gconf-sanity-check-2 (exited with status 256)

Finally:

Nautilus could not create the following required folders:
/home/sam/Desktop, /home/sam/.nautilus

Before running nautilus, please create these folders or set permissions such that Nautilus can create them.





Solutions I've tried:

sudo chmod 700 /home/


Can someone tell me what to do to repair nautilus and graphically boot into gnome?

---

### Post by chayzer on 2010-06-12
chown sam:sam /home/sam/.ICEauthority
chown -R sam:sam /home/sam/.nautilus
chmod -R 755 /home/sam/.nautilus

Remember to use gksudo when running graphical apps that require sudo elevation and be VERY careful chmodding /home stuff. Especially with -R option (recursive)

---

### Post by Coastalguy on 2011-02-21
I am having the same problem, however after going through all of the errors, I am stopped at a blank desktop background. How do I get from there into Terminal or something where I can enter the commands that you specified?

Thanks, sort of new at Ubuntu..

:(

---

### Post by Coastalguy on 2011-02-21
Regarding my prior reply, I discovered the recovery boot that takes me to the Terminal entries. I then tried the commands provided above, however in all instances, I received an error that the directory does not exist. I assume that "sam" means my login ID, however not sure what "sam" stands for (a new one on me)?

Apparently, permissions of these files are not the problem, rather it is that it has never created these files which is why I am getting a "no directory found"?? Haven't a clue on how to get my gnome back??

Boot up errors after entering password:
1. Could not update ICEauthority file home/my_id/.ICEauthority
2. Problem with configuration server /usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256.
3. Nautilus could not create the following required folders;
/home/my_id/Desktop
/home/my_id/.nautilus
Before running Nautilus, please create these folders or set permissions such that Nautilus can create them...

Stops at a blank desktop background screen...

thanks,

Thanks,

---

