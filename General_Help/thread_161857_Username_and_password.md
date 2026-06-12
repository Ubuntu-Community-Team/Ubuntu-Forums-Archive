---
title: "Username and password"
date: 2006-04-17
forum: General Help
---

### Post by Lamorue on 2006-04-17
Hello,
My first experience with Linux and I just compleeted the installation of ubuntu breeze badger 5.10 in french and everything went fine, but I cannot get to it because it does not reconnaise my username or my password maybe because I made a mistake. 
How can I review them or change them.
Thanks in advance 
Lamorue

---

### Post by aysiu on 2006-04-17
Boot into recovery mode (this should be between the normal boot option and "memtest").

I believe these are the commands you would type from there: ```
adduser lamorue admin
passwd lamorue
``` Then you can reboot into normal mode and log in as *lamorue*.

---

### Post by yangbin2590 on 2006-04-17
sudo root
then youcan input linux password

---

### Post by aysiu on 2006-04-17
[QUOTE=yangbin2590]sudo root
then youcan input linux password[/QUOTE] How would one who can't even log in be at a point to type ```
sudo root
```?

---

### Post by Lamorue on 2006-04-17
Thanks Aysius 
But I am realy novice in linux can you tell me how can I boot to recovery mode.
And also tell me how I can I ask my question into the forum, becaure I though I was asking my question into the forum.

Sorry for my inexperience 

Lamorue

---

### Post by bunnieofdoom on 2006-04-17
when grub loads(where you pick your kernel) you should see your kernel number with (recovery mode) after it

then you cad add usernames and passwords with the ccommands allready post i think

lemme know if it works if not ill boot my other box and try to help you :)

---

### Post by Lamorue on 2006-04-17
Sorry but how can I go to the screen to type the code.
Thanchs Lamorue

---

### Post by ncappel1 on 2006-04-17
> how I can I ask my question into the forum, becaure I though I was asking my question into the forum. Sorry for my inexperience 

you are asking your question in the forum!

we love helping people out so there's no need to apologize for being new at anything. If you feel confused, remember that you aren't the only one!

---

### Post by Lamorue on 2006-04-18
Went booting in recovery mode trhere is an error saying ( Temporary failure in name resolution ( FAILL ) in red ) then stop loading and ask for root password for maintenance which I found after comes Root@abuntublueberry:... and then I can type codes .
After typing sudo root the answer is :
unable to look up ubuntublueberry via gethost by name ()

Is there any codes to change name?In the documentation of ubuntu is trere any simple code table for debugging that I can print.

Thanks Lamorue

---

### Post by Lamorue on 2006-04-30
Problem solved

Thank you
Lamorue

---

### Post by xenmax on 2006-05-01
[QUOTE=Lamorue]Problem solved[/QUOTE]Lamorue, could you share with us the solution? That way, anybody who has a similar problem and comes across this thread can refer to your solution.

Also, i am glad you solved your problem. Now you can enjoy using Ubuntu!

---

