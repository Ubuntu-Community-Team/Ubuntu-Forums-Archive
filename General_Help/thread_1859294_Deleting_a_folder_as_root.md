---
title: "Deleting a folder as root"
date: 2011-10-13
forum: General Help
---

### Post by Mikeb85 on 2011-10-13
So I installed a .jar file, I installed it as root, but it's buggy and I want to get rid of it, but I can't figure out how to log in as root with the GUI, and the terminal commands keep on denying me.  Need some help.  I'm assuming it's very basic, but it keeps on confounding me...

---

### Post by Karlchen on 2011-10-13
Hello, Mikeb85.

Launch the a terminal session. Inside the terminal run the commandline
**sudo rm /full/path/to/name_of_jar_file**
(Replace /full/path/to/name_of_jar_file by the full pathname and filename of the jar file which you want to delete.)
**sudo **will ask you for _your password_, your password, not the root password.
Provided you enter the correct password and provided you are entitled to run commands with root privileges using **sudo **and provided you have not mistyped /full/path/to/name_of_jar_file, the **rm **command will delete the file. Else you will receive the appropriate error message.

Kind regards,
Karl

---

### Post by effenberg0x0 on 2011-10-13
BE CAREFUL WHEN USING THESE COMMANDS. YOU MIGHT DELETE IMPORTANT THINGS.

- Open a Terminal
- Use the "**cd**" command to navigate to the folder. Ex:
```

cd my_stuff/MyPrograms/files
```Notice that folders in Linux are Case Sensitive (**/ThIs/** is different than **/THIS/** and is different than /**this/**)[B].

[/B]The command **pwd** show you in each folder you are.
The command **ls -lah** shows you the files in the folder you are.

Once you have located the file and you are absolutely sure that you want to delete it, run:
```
rm NameOfTheFile
```If you get permission errors, run:
```
sudo rm NameOfTheFile

```**Again,** **be very careful when deleting files.**

Regards,
Effenberg

---

### Post by Hugh971 on 2011-10-13
Hi,

In the terminal run

```
sudo rm /path/to/file
```alternatively if you would rather run a file browser to delete it try 

```
gksu nautilus
```That will give you a file browser with root privileges.


Hugh

edit: looks like I got beaten to it.

---

### Post by Mikeb85 on 2011-10-13
Ok, I figured it out.  (How do you change thread heading to solved?)  I wound up simply opening the uninstaller that came with it, and figured out what I was doing wrong with the java commands...  

gksu nautilus was strange though, it didn't let me access any of my normal folders in my /home.

---

### Post by pretty_whistle on 2011-10-13
> **Mikeb85 said:**
> Ok, I figured it out.  (How do you change thread heading to solved?)  I wound up simply opening the uninstaller that came with it, and figured out what I was doing wrong with the java commands...  

gksu nautilus was strange though, it didn't let me access any of my normal folders in my /home.
To change this thread as solved go to the top of the thread on the right side.  It says "Thread Tools".  Click this and a drop down menu appears-it's on there, just click that.

Edit:

Be sure you're logged in though or you won't see the option.

---

