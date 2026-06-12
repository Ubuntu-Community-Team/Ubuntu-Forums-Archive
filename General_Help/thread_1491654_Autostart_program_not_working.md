---
title: "Autostart program not working?"
date: 2010-05-23
forum: General Help
---

### Post by bone2006 on 2010-05-23
I have a java application that is in this path:
java -jar /home/jbo10/.stuff/run.jar

If I type that command the gui comes up and it's ready to run.  I want this program to autostart with ubuntu, so I went into gnome-session-properties and put that command in there.

But it's not starting.  I'm not sure what I'm doing wrong or if there's another way to autostart programs?

---

### Post by gordintoronto on 2010-05-23
Preferences/Startup Applications might help.

---

### Post by inso_741 on 2010-05-24
> **gordintoronto said:**
> preferences/startup applications might help.

+1..:)

---

### Post by bone2006 on 2010-05-24
I don't mean to be rude, but did you guys read my post completely or try the command:
gnome-session-properties before replying if you were unfamiliar with the actual name of the application?  

As I stated it doesn't work maybe, because it's not an installed app or I'm really not sure why, but this was my original post.  I appreciate the effort in trying to help me though

Ubuntu's documentation seems to indicate I need to have the service run at the init.d level

If I run this command it starts up fine with gui and all
java -jar /home/jbo10/.stuff/run.jar

So I created a scripted called run and placed it here /etc/init.d

And this is the script
#!/bin/bash
java -jar /home/jbo10/.stuff/run.jar

then I ran:
sudo chmod +x /etc/init.d/run

Then:
sudo update-rc.d run start 51 S .

Which everything seems to work just fine, if I put this command in again I see that it's already been added as it warns me.  But no matter what this program doesn't start up.

---

### Post by Bobhuber on 2010-05-24
> **bone2006 said:**
> I don't mean to be rude, but did you guys read my post completely or try the command:
gnome-session-properties before replying if you were unfamiliar with the actual name of the application?  

As I stated it doesn't work maybe, because it's not an installed app or I'm really not sure why, but this was my original post.  I appreciate the effort in trying to help me though

Ubuntu's documentation seems to indicate I need to have the service run at the init.d level

If I run this command it starts up fine with gui and all
java -jar /home/jbo10/.stuff/run.jar

So I created a scripted called run and placed it here /etc/init.d

And this is the script
#!/bin/bash
java -jar /home/jbo10/.stuff/run.jar

then I ran:
sudo chmod +x /etc/init.d/run

Then:
sudo update-rc.d run start 51 S .

Which everything seems to work just fine, if I put this command in again I see that it's already been added as it warns me.  But no matter what this program doesn't start up.
My mistake .

---

### Post by bone2006 on 2010-05-24
Finally got it to work with a script

Thanks

---

