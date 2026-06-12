---
title: "How do I use .sh / shell script files?"
date: 2006-02-07
forum: General Help
---

### Post by Clams on 2006-02-07
Hey.  I tried downloading the Cedega Timed Demo but it came as a shell script (.sh?) file, and for the life of me, I can't figure out how I go about using this. 

Sorry if this is the wrong place  to ask this, but thanks!!

---

### Post by Protex on 2006-02-07
Hey.

I'm fairly new to Linux but I think it's a simple, "sh filename.sh" in your terminal. (of course 'cd' to the directory first).

---

### Post by Clams on 2006-02-07
Okay, I did sh <filename> and it "verified archive integrity....all good." and "uncomrpessed cedega timed demo", yet it leaves nothing else for me.

Sorry if this is horrenously newb-like, but I'm stumped. Thanks for the SUPER fast reply though!!

---

### Post by Protex on 2006-02-07
I'm stumped. Sorry, maybe someone who installed the Time Demo can help out.

Sorry buddy. =(

---

### Post by Protex on 2006-02-07
[QUOTE=Protex]I'm stumped. Sorry, maybe someone who installed the Time Demo can help out.

Sorry buddy. =([/QUOTE]

*edit* Umm, just an idea. Run it as a super-user (sudo sh install.sh) and make sure you are running the correct .sh file.

---

### Post by Clams on 2006-02-07
Well here's how it is: The file is called a "shell script" and it has an SH on its icon, yet it's apparently NOT a .sh file.

The command I used to get a reaction from it was "sh cedega_timedemo_installer", and got the whole "verifying archives, uncomrpessing" message. I just tried adding sudo in front of it to no avail. Thanks for your help though!

---

### Post by Sutekh on 2006-02-07
[QUOTE=Clams]Well here's how it is: The file is called a "shell script" and it has an SH on its icon, yet it's apparently NOT a .sh file.

The command I used to get a reaction from it was "sh cedega_timedemo_installer", and got the whole "verifying archives, uncomrpessing" message. I just tried adding sudo in front of it to no avail. Thanks for your help though![/QUOTE]

Here's how you should install the cedega time demo
```
chmod +x ./cedega_timedemo_installer
sh ./cedega_timedemo_installer
```
This makes the installer executable, and then executes the installer.

Once its done you can run a program using cedega from the folder with the program executable (.exe) you want to run
```
cedega <name_of_file>.exe
```
Just substitute the name of the program in, you can also include the path, for example
```
cedega /media/cdrom0/swkotor.exe
```
will use cedega to run the file swkotor.exe (Knights of the Old Republic) in /media/cdrom0 (my CD-ROM drive)

---

### Post by Lews Therin on 2006-02-07
Running it with sh is the correct action. I downloaded and ran it with "sh cedega_timedemo_installer", and it uncompressed itself and created a window to continue the installation process.

If yours didn't, try looking in /tmp for a directory named "selfgz[bunch of numbers]". Inside, try to run setup.sh with "sh setup.sh"

The GUI setup screen appears to be a GTK 1.2 app. If running setup.sh didn't work, you can try "setup.data/bin/Linux/x86/glibc-2.1/setup.gtk".

If none of these work, it is doubtful Cedega will.

---

