---
title: "Encrypted Pen Drive Problem (Mounting &amp; Permissions)"
date: 2010-11-10
forum: General Help
---

### Post by Skavenger0 on 2010-11-10
Hi,

I wasnt sure where to post this so I think general is the closest thing really.

Ubuntu 10.10 fresh install

I am investigating into using Ubuntu as a corporate Desktop solution and trying to make sure everything is working so I can try to progress this project but I've hit a bit of a show stopper.

I'm a heavy Linux user at home so I have a fair amount of knowledge.

Our company uses Safestick Hardware encrypted pen drives. I have flashed the firmware to make them Linux compatible but I've got a small permission problem.

Basically the Safestick comes with a decryption program and you unlock the drive using: ```
sudo ./safestick -> [Enter Password]
```
This works fine and it can be re-locked with ```
sudo ./safestick lock
```

This works fine but I dont want to give normal users Sudo rights and can't get it to work without sudo.

In my attempts to fix this I tried changing the permissions on /dev/ to 777 using ```
sudo chmod -R 777 /dev
```

This then allowed me to unlock and lock the drive without sudo. I reset the permissions back to default and tried applying 777 just to the sdb and sdb1 files (The 2 Safestick partitions) and it didnt work. Any ideas which files I need to change permissions on to get this to work without opening up /dev/ to the world?

Thanks for any assistance, I'd like to have a good argument to try and get my company to start moving away from Windows

---

### Post by Hippytaff on 2010-11-10
> 
I'd like to have a good argument to try and get my company to start moving away from Windows

it's free is a good argument :-)
 
Can you change the ownership of the partitions (chown) and add users to a group that owns the partitions?
 
Edit -> just noticed... a fellow Taff, Croeso

---

### Post by Skavenger0 on 2010-11-10
Croeso - My Welsh isn't very good mind :P

While "Its Free" is one part of the argument its not going to be received well by either management or the end users if the functionality isn't available. Especially when there is thousands of pounds worth of safe sticks been purchased previously.

I don't think its a permission on the partition itself that is the issue as the user does have access to partition sdb and sdb1 but sdb1 is an encrypted partition that requires the tool to decrypt it. Its during that decryption process that the failure occurs.

As mentioned about I have tried setting permissions on 
/dev/sdb and /dev/sdb1 without success and the user can access /media/SafeStick Login to run the application without sudo.

If I run: ```
./safestick -> [Password]
``` without sudo then the program asks me for the encryption password then gives the error. ```
Failed to unlock SafeStick: 21.
```

What I am trying to do it put a script on the users desktop that either locks or unlocks the drive when run, to avoid the user having to use the terminal but I also dont want to hard code the sudo password or give the password to the user.

I'm pretty sure its a file permission on something within the /dev folder but I dont know what files are accessed when a mount operation is taking place.


For arguments sake. How/What precisely had you in mind on changing the partitions permissions?

---

### Post by Skavenger0 on 2010-11-10
Additional: The safestick application/firmware came from the company themselves however is not in final release. It is also the only file there is and it is a single compiled file so the source cannot be seen

---

### Post by Hippytaff on 2010-11-10
I see the dilemma. Why can't the user have the encryption password (not sudo one). We have usb's and the staff are given the password.
 
It's a difficult one.

---

### Post by Skavenger0 on 2010-11-10
The staff do have the encryption password. So thats not the problem.

When they run the script (Which is on the Desktop) it will ask for the encryption password. 
Unfortunately at the minute the application has to be run using sudo, so it also asks for the sudo password. Thats the bit I'm trying to avoid, only without giving the user 777 on /dev/.

---

### Post by Hippytaff on 2010-11-10
don't know...you could, as part of the script, have a different password which will trigger the sudo password, so the staff don't need the sudo password, but that doesn't get around having to hardcode the password in the script somewhere.

---

### Post by Skavenger0 on 2010-11-10
Im going to try and ask the developers (Safecom) if they will either divulge some source code or tell me which files I need to change permissions on or the application accesses.

Not sure if they will tell me though.

---

### Post by softek on 2010-11-11
Hi,

Softek are UK Distributors for hardware encrypted USB pen drives "SafeStick", and after contacting the vendors about Linux support for SafeStick we can offer the following information which may help.

For now (SafeStick firmware v4.03 - on later firmware this may change) libraries used to provide Linux support require sudo, Linux also requires sudo mode in order to enumerate USB-devices and USB-hubs with VendorID and ProductID (which we must have in order to find the SafeStick).

Softek's Linux support team also offer the following advice:

We recommend searching for sudo usage as there is  much information about it.  However, as a guide a line like this in your /etc/sudoers file should work:

%users  ALL = NOPASSWD: /media/safestick/safestick

That assumes that your users are in group called "users" which they may  not be, and the name of the CD partition is safetick. Just change as  needed.

You can change the user's group settings through the Ubuntu GUI tools or  using the gpasswd command.  You can even set up a group so that only  certain users can use the safesticks (again in GUI tools or gpasswd).

All the the commands have man pages installed on the system.  You can read these using the man command e.g.:

man sudoers
man gpasswd

We hope this helps.


Softek product info / downloads:  [http://www.softek.co.uk](http://www.softek.co.uk)
Softek KB's and self help:  [http://esupport.softek.co.uk](http://esupport.softek.co.uk)

---

