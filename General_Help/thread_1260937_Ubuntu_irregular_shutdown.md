---
title: "Ubuntu irregular shutdown"
date: 2009-09-08
forum: General Help
---

### Post by hbbst on 2009-09-08
Dear Ubuntu Users!

I'm developing a digital information helpdesk system under Delphi with a touchscreen, and I run this application under Ubuntu/Wine. The problem is, when the shop closes, the employee does not make normal shutdown, he just pulls out the wire from the wall.
So how can I prepare my Ubuntu for this event? Will this action harm my Linux installation or not? Have I got chance that the computer won't start after an irregular shutdown? -- greets from Hungary! :)

---

### Post by Joshua Lückers on 2009-09-08
Pulling the plug when a computer is running is never good for a system (it can damage your hardware). A clean shutdown is always preferred. 
What you could do is using a crontab to shutdown the computer after the shop closes. 
All that has to be done is turn the computer on when opening the shop.

---

### Post by wojox on 2009-09-08
I think you need to hire a new employee.

---

### Post by hbbst on 2009-09-08
Lot of shops, very flexibe opens. I cannot make different timetable for every system, it has to be the same configuration.

**wojox**, they are not my employees, I will sell systems to shops. ;)

---

### Post by Joshua Lückers on 2009-09-08
Why don't they leave it on then? That way it causes less damage to the hardware.

---

### Post by hbbst on 2009-09-08
I would like to prepare the system for all event. I do not know the habits for the shops where I sell the system. If I make a user manual, it is not sure they are read it.

---

### Post by 3rdalbum on 2009-09-08
You can modify the /etc/fstab to mount the drive as "sync", which means that all data will be written to disk immediately rather than waiting in a buffer.

I imagine the reduced writing speed will not cause too many problems for your clients. If it does, then tough - they can either shut their machines down properly, or suffer reduced speed.

If you want to change the employee's behaviour, then you could write a script that runs on shutdown, that creates a file. Then write a script that starts on login and checks for the presence of the file, and if the file is not there, then the machine has been incorrectly shut down and it displays a warning message like:

"Warning: This computer was not turned off correctly. If it is not turned off correctly, it can lose important company data. In future, shut down the computer by doing xyz".

If the file has been found, then remove the file.

The possibility of losing important company data will probably be a big enough incentive for your clients to track down the irresponsible employee. But in the meanwhile you can mount the filesystem as sync.

---

### Post by hbbst on 2009-09-08
The computer doesn't store important data. I don't afraid about loss of any data, but I'm afraid that the operating system will harm.
So you think I should change every option in /etc/fstab to "rw, suid, dev, exec, auto, nouser, **sync**" in hdxx entries?
And what about swap file? I see "pri=42" option. Do I have to change it or not?

---

