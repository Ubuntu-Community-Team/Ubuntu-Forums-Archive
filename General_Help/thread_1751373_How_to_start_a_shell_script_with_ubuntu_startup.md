---
title: "How to start a shell script with ubuntu startup?"
date: 2011-05-06
forum: General Help
---

### Post by thexnightmare on 2011-05-06
Dear,
I wrote a script, and what to make it surring with ububtu as startup shell.
how can I do that?
Thx

---

### Post by matt_symes on 2011-05-06
Hi

> I wrote a script, and what to make it surring with ububtu as startup shell.

Don't really understand this. It depends on when you want the script to start and what the script does.

You could add it to /etc/rc.local, add it to your auto start applications, add it to your ~/.bashrc or create an upstart script (or a couple of other things).

Please be clearer. What does the script do and when do you want it to start ?

Kind regards

---

### Post by compmodder26 on 2011-05-06
Essentially, do you want it to run when the system boots up, or when you log in?

---

### Post by thexnightmare on 2011-05-06
Dear,
this is my script.sh content :
{
#!/bin/bash
rm -rf /media/FLASHMEMORY
cp -r /media/cdrom1/* /media/FLASHMEMORY
reboot
}
My ubuntu is set up my user "XXX" to auto login, so the dektop appears after booting up my PC.
All what I want is when Desktop appears, this script will run, do it's job {erase flash memory, copy blu ray disc contents to flash memory, then restart}.
I hope to help me.

---

### Post by matt_symes on 2011-05-06
Hi

> **thexnightmare said:**
> Dear,
this is my script.sh content :
{
#!/bin/bash
rm -rf /media/FLASHMEMORY
cp -r /media/cdrom1/* /media/FLASHMEMORY
reboot
}
My ubuntu is set up my user "XXX" to auto login, so the dektop appears after booting up my PC.
All what I want is when Desktop appears, this script will run, do it's job {erase flash memory, copy blu ray disc contents to flash memory, then restart}.
I hope to help me.

This certainly is achievable. 

A couple of points though. 
 
1. The script will have to run as root for the reboot.
2. The script will have to run after the FLASHMEMORY has been mounted.

I have a couple of questions first though.

1. How are you mounting the flash drive ? From fstab ?
2. Surely each time you run the script it will just run, reboot and run, reboot and run, reboot..... and long as you log in as user XXX, until you hit the power. Is that really what you want ?

Anyways, one option is to add the script to the auto start options and run it as sudo <script_name>. Add the script to the sudoers file so it does not require a password for your user XXX.

Kind regards

---

### Post by thexnightmare on 2011-05-06
Now, After loading my Ubuntu now (with automatic user login option), I run my script, it runs perfectly, all what I want to make is to run it after ubuntu starting up.
Your Questions:
1. FLASHMEMORY and BD-ROM are mounted automatically, when ubuntu starts up, I see them on the desktop.
2. Yeah I am sure, Power up my PC, ubuntu start and user auto login, script must run automatically, remove all things from FLASHMEMORY, copy all BD-DISC Data, and restart.
Concerning your solutions, can you give me more details on how to do it please?
Thx in advanced

---

### Post by matt_symes on 2011-05-06
Hi

> **thexnightmare said:**
> Now, After loading my Ubuntu now (with automatic user login option), I run my script, it runs perfectly, all what I want to make is to run it after ubuntu starting up.
Your Questions:
1. FLASHMEMORY and BD-ROM are mounted automatically, when ubuntu starts up, I see them on the desktop.
2. Yeah I am sure, Power up my PC, ubuntu start and user auto login, script must run automatically, remove all things from FLASHMEMORY, copy all BD-DISC Data, and restart.
Concerning your solutions, can you give me more details on how to do it please?
Thx in advanced

Ok. 

I am not sure you understand what is going to happen here.

You will start your PC. It will boot into your desktop and run the script and restart your PC which will boot into your desktop and run the script which will restart your PC which will boot into your desktop which will.......

Unless i am missing something here.

Anyways, from the menu..

System->Preferences->Startup applications. Select the Add button. Enter a name and in the command text field enter

```
gksudo /path/to/script
``` 

where /path/to/script is the, obviously, the path to your script. Click the ADD button.

Reboot your PC.

Enter your password when prompted.

After that you will have to edit the sudoers file but try that first.After that you will have to edit the sudoers file but try that first.

Kind regards

---

### Post by thexnightmare on 2011-05-06
I did exactly what u said sir, however, after restarting my ubuntu, nothing appear on scrin (Just normal Desktop), and when I go to my FLASHMEMORY, i found that delete procedure didn't work.
So the script didn't started.
Any solution?

---

### Post by matt_symes on 2011-05-06
Hi

> **thexnightmare said:**
> I did exactly what u said sir, however, after restarting my ubuntu, nothing appear on scrin (Just normal Desktop), and when I go to my FLASHMEMORY, i found that delete procedure didn't work.
So the script didn't started.
Any solution?

I have just ran a modified version of your script and it worked on my machine. I modified it to just echo your commands to three files on my root directory.

Here's my modified version

```
matthew@matthew-laptop:~$ cat temp_script 
#!/bin/bash
echo "rm -rf /media/FLASHMEMORY" > /file1
echo "cp -r /media/cdrom1/* /media/FLASHMEMORY" > /file2
echo "reboot" > /file3
matthew@matthew-laptop:~$
```

This will write three files to the root directory. This also requires admin permissions.

These are the files generated.

```
matthew@matthew-laptop:~$ ls /fil*
/file1  /file2  /file3
matthew@matthew-laptop:~$ 
```

and here is the contents of the three files

```
matthew@matthew-laptop:~$ cat /fil*
rm -rf /media/FLASHMEMORY
cp -r /media/cdrom1/* /media/FLASHMEMORY
reboot
matthew@matthew-laptop:~$
```

so the procedure does work.

My script is in my home directory

```
matthew@matthew-laptop:~$ ls -l /home/matthew/temp_script 
-rwxrwxrwx 1 matthew matthew 134 2011-05-07 00:08 /home/matthew/temp_script
matthew@matthew-laptop:~$
```

as you can see i made it executable by all (overkill but hey)

```
chmod 777 /home/matthew/temp_script
```

I added it to the startup applications and added this as the command

```
gksudo /home/matthew/temp_script
```

See screenshot. Compare and contrast what i have done again what you have.

1. Make sure the script is executable. 
2. Make sure the full path to the script is added to the start up applications.
3. Make sure the script is ticked in the startup applications.

Try to get it working and check out the scripts behaviour.

Kind regards

---

### Post by thexnightmare on 2011-05-06
Dear sir,
Thx alot for detailed explanation.
I did what you proposed and it operates 100%.
However,
1- when run, it asks for password, I dont want to ask for password, how to do that?
2- I wrote second example with simple echo "ttt" command, but when restarting, nothing shown on screen.
3- I wrote third example with 2 simple rm-rf command, but when restarting, the first command which delete a folder from Desktop operate successfully, but nothing is deleted from my FLASHMEMORY.
Any suggestions?

---

### Post by matt_symes on 2011-05-06
Hi

> **thexnightmare said:**
> Dear sir,
Thx alot for detailed explanation.
I did what you proposed and it operates 100%.


That's good. Now you know how to start a script from the auto start option.

> 
However,
1- when run, it asks for password, I dont want to ask for password, how to do that?


To do this you need to edit your sudoers file. Open a terminal and type 

```
sudo visudo
```

Enter your password. It will not be echoed to the screen. This is normal. If given the option to select an editor select nano.

Scroll down to the bottom of the file and add this line

```
user_name ALL = (ALL) NOPASSWD: /path/to/script
```

Change user_name to your user name and /path/to/script to the full path to your script. To give you an example mine would look like...

```
matthew ALL = (ALL) NOPASSWD: /home/matthew/temp_script
```

Press ctrl + o to save and ctrl + x to exit. It will tell you if you have made any errors.

> 
2- I wrote second example with simple echo "ttt" command, but when restarting, nothing shown on screen.


The echo command will not display anything on your desktop. That's not how it works. I suggest you read up on bash scripting.

> 
3- I wrote third example with simple rm-rf command, but when restarting, nothing is deleted from my FLASHMEMORY.
Any suggestions?

The command is not rm-rf but rm -rf. Notice the space.

**This is a very very dangerous thing to do as your script will be running with root privileges and can delete any file on the system forced and recursively. _MAKE SURE YOU ADD THE CORRECT PATH_**

What i would try to do first is add a file to the flash drive from your script to make sure the path is correct. You can then check the file was created on the flash drive. It it is you have the correct path and you can change the command to an rm command.

**I would also not use rm -rf but **

```
rm /path/to/flash/drive/*
```

This is much safer if there are no sub directories on the flash drive. It's not recursive and not forced.

Make sure you get this right.

Kind regards

---

### Post by matt_symes on 2011-05-06
Hi

If it keeps rebooting and rebooting and rebooting (as i think it might) from the grub menu  select the recovery menu option. When it brings up the dialog scroll down to root console and select that option.

This will log you into a root console. From that root console type

```
rm /path/to/your/script
```

This will remove your script file.

Then type

```
shutdown -r now
```

to reboot your system.

Tell me how it goes.

Kind regards

---

### Post by thexnightmare on 2011-05-07
You are the best, and the most experienced guy in Linux I ever saw . Thx alot in your help.
Now my script is working exactly how I want.
However still most simple thing, how can I let it pring on screen what I want with echo.
If you can help me with that, I will be very thankful.
And I hope from you of you can help me with my other questions in the forum, if you have time.

---

### Post by matt_symes on 2011-05-07
Hi

> **thexnightmare said:**
> However still most simple thing, how can I let it pring on screen what I want with echo. If you can help me with that, I will be very thankful.

To display something to the screen i would use Zenity if you are using Gnome.

Make sure it's installed (It should be under Gnome but just in case)

```
sudo apt-get install zenity
```

Open a terminal and type

```
zenity --info --text "Something displayed on the screen"
```

```
man zentiy
```

to get a list of all the options. 

You can also search the web. Here is one such link.

[http://library.gnome.org/users/zenity/stable/](http://library.gnome.org/users/zenity/stable/)

> And I hope from you of you can help me with my other questions in the forum, if you have time.

If i'm online i will try to help. There are many others here who can help as well.

Kind regards

---

### Post by thexnightmare on 2011-05-08
Dear my friend,
All things working in a very good way, but, this part of script dont run
{
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/picture.png"
}
If I run the entire script directly it runs very well, but this portion of the script dont.
I tried to make 2 scripts where 1 call 2, and this part of the script is in 2, both 1 & 2 works perfectly, just this portion dont work.
Any idea?

---

### Post by matt_symes on 2011-05-08
Hi

Try using the full path to gconftool-2

```
/usr/bin/gconftool-2
```

If that does not work post the full script here and i will take a look.

Kind regards

---

### Post by thexnightmare on 2011-05-09
tried, not working.
thx for ur help in advanced:
{
#!/bin/bash
sleep 10
echo -e "\a"
echo -e "\007"
clear
echo "Welcome to DVD Copier"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/Welcome.png"
sleep 1
cdname=`volname`
cdname=${cdname%% *} #trim white space from variable holding cd name
cdname=${cdname#* }
if [ "$cdname" = "BackupData" ]
then
{
echo "Backup Found"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/BackupFound.png"
sleep 1
echo "Clearing the Flash Memory"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/ClearingFlashMemory.png"
sleep 1
rm -rf /media/FlashMemory
echo "Clearing Completed"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/ClearingDone.png"
sleep 1
echo "Copying Backup Disc"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/CopyingDisc.png"
sleep 1
cp -r /media/cdrom1/* /media/FlashMemory/
echo "Copying Completed"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/CopyingDone.png"
sleep 1
}
else
{
echo "No Backup Found"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/NoBackupFound.png"
sleep 1
echo "System will restart now"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/Restarting.png"
sleep 1
}
fi
echo "Ejecting the Disc"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/EjectingDisc.png"
sleep 1
eject
echo "Ejecting Completed"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/EjectingDone.png"
sleep 1
echo "Restarting"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/Restarting.png"
sleep 1
echo "Welcome to DVD Copier"
/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/Welcome.png"
sleep 1
reboot
}

---

### Post by matt_symes on 2011-05-09
Hi

What version of Ubuntu are you using ?

Open a terminal and copy and paste

```
gconftool-2 -g /apps/nautilus/preferences/show_desktop
```

Post back results.

Kind regards

---

### Post by thexnightmare on 2011-05-09
Ubuntu 9.10 - the Karmic Koala.
true.
I dont think that this is a ubuntu version problem, as the script works perfectly when running it by double click or from terminal, just changing desktop is not working from run as startup.

---

### Post by matt_symes on 2011-05-09
Hi

> **thexnightmare said:**
> Ubuntu 9.10 - the Karmic Koala.
true.
I dont think that this is a ubuntu version problem, as the script works perfectly when running it by double click or from terminal, just changing desktop is not working from run as startup.

I assume that *true* value is the value returned from the gconftool-2 command ? If so then that is correct.

I am not sure why is not changing the wallpaper at the moment. I assume either gconfd is not running or there is a dbus issue.

You're using Karmic. I am currently running Lucid (amongst others). I will download Karmic and install it in a VM and test your script to see what is wrong.

Kind regards

---

### Post by thexnightmare on 2011-05-09
yeah ot is, and I dont thinkl that it is a problem with the script or karmic, as the script working perfeclty when running it manually, it is only dont run in calling it: however from another script or startup.
Thx for your help, appreciated,

---

### Post by matt_symes on 2011-05-09
Hi

Well i managed to get this script working on 9.10 working in virtual box.

```
matthew@matthew-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
matthew@matthew-laptop:~$
``````
matthew@matthew-laptop:~$ cat test_wallpaper.sh 
#!/bin/bash

/usr/bin/gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/usr/share/backgrounds/Butterfly.jpg"
matthew@matthew-laptop:~$ 
```I made sure the script was executable

```
chmod 755 test_wallpaper.sh
``````
matthew@matthew-laptop:~$ ls -l test*
-rwxr-xr-x 1 matthew matthew 129 2011-05-09 22:10 test_wallpaper.sh
matthew@matthew-laptop:~$ 
```I added it as a startup application. See screen shot below 

Then i rebooted and the screen was changed to the butterfly.

To double check, i set the wallpaper back to nothing.

```
/usr/bin/gconftool-2 -t string -s /desktop/gnome/background/picture_filename ""
```and rebooted again. It changed the wallpaper again. 

Check your script is added correctly as a start up application. Check your script is executable.

If you want, try with my script above and follow my steps to see if my script above changes your wallpaper.

Kind regards

---

### Post by thexnightmare on 2011-05-09
Just a quik question, does the script requires .sh extension?
and concerning the startup applicaiton, do I write only the path or add gksudo before the path?
Thx

---

### Post by matt_symes on 2011-05-09
Hi

> **thexnightmare said:**
> Just a quik question, does the script requires .sh extension?

No. As long as it has the **#!/bin/bash as the first line of the script** and **it is executable** it will work. 

Check that #!/bin/bash is the first line of your script. I think you might have had a { as the first line.

BTW: You can also use

```
#!/usr/bin/env bash
```as the first line. This is more portable.

Kind regards

---

### Post by thexnightmare on 2011-05-09
I was searching for a while, and I think I found the problem.
I removed sudo from from the command line in startup application, and by then, when I restarted the system, the background did changed very well.
I think this command can't start with sudo or gksudo.
Now the script runs, but some functions like rm s not working because rm needs sudo. 
Do u have a solution for this?

---

### Post by thexnightmare on 2011-05-09
BTW, I tried to make the rm command in a seond script, and call it from the first script.
It runs perfectly from terminal, but from startup dont work.
ohhhhh this will make me crazy

---

### Post by matt_symes on 2011-05-09
Hi

I have just ran my test scrip with gksudo and you are correct. It does not change the wallpaper. In my test i did not use gksudo.

You will need to use gksudo to reboot the system.

Let me have a play and i will get back to you.

Kind regards

---

### Post by matt_symes on 2011-05-09
Hi

The reason why the wallpaper is not changing with gksudo is because the script runs as root when using gksudo.

Therefore the gconftool-2 commands are updating the configuration settings for root and not your user.

I am looking for a solution at the moment for this.

Kind regards

---

### Post by thexnightmare on 2011-05-09
I never saw experts like you, really ubuntu world looks very good to move to instead of windows 7 hell, lol.
but, iif this is related to what u said abput updating the configuration settings for root and not your user, so why calling the rm command from script 1 as sudo dont work?
or even calling script 2 whoch contains sudo rm from script1 dont work?

---

### Post by matt_symes on 2011-05-09
Hi

Sorry for the late reply. I was on the phone. Anyway as i said the script needs to run as root because the reboot command needs to run with admin privileges.

Adding the script to the /etc/sudoers file allowed the script to run as root at startup without entering a password.

However, if the script is running as root, when gconftool-2 is called it will update roots configuration settings and not yours. 

So what you need to do is make all the calls to gconftool-2 run under your user account. You can do this with su. Have a look at this.

```
echo "Welcome to DVD Copier"
**su xxx -c  '**/usr/bin/gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/xxx/script/Welcome.png"**' **
```This is part of your script but slightly modified. What you need to do is prefix the call to gconftool-2 with

_**su xxx -c '**_  [SIZE=1]your old command[/SIZE]   _**'**_  <-!!Don't forget the single quote at the end!!

The single quotes around your old command are very important. The xxx would be your user name.

Update each of your calls to gconftool-2 this same way. Then we will look at your rm command issues.

Kind regards

---

### Post by thexnightmare on 2011-05-09
i tried this now, however, after terminal running, it give me "sudo xxx" command not found"

---

### Post by Dave_L on 2011-05-09
I think that should be su, not sudo.

```
su xxx -c '...'
```

(where ... is the command, and xxx is the username under which the command should run)

---

### Post by matt_symes on 2011-05-09
Hi

@DaveL just beat me to it.

It should have been su <user-name> -c 'command'. I have got to used to typing sudo ;)

I will amend my last post. It's late here.

Kind regards

---

### Post by thexnightmare on 2011-05-09
Ok done, now works from terminal, but asks for password each time it runs this command.
and when restarting nothing done.

---

### Post by matt_symes on 2011-05-09
Hi

Blimy. We seem to be going around in circles here.

Give me ten minutes to run some checks in the VM.

We will get there.

Kind regards

---

### Post by matt_symes on 2011-05-09
Hi

I have just tested my small script and this is what i have noticed.

I start off with no background wallpaper. I reboot and get no background wallpaper. If i reboot again i get background wallpaper.

If i then clear the wallpaper again i have to reboot twice to get the wallpaper to change.

Does this happen to you ?

Kind regards

---

### Post by thexnightmare on 2011-05-09
yes, but what does this help in?

---

### Post by matt_symes on 2011-05-09
Hi

> **thexnightmare said:**
> yes, but what does this help in?

I'm not sure yet. I'm trying to find out why.

Kind regards

---

### Post by matt_symes on 2011-05-09
Hi

It's now very late/early here. We will have to continue this tomorrow.

Kind regards

---

### Post by thexnightmare on 2011-05-09
ok sir, here 2 it's 4am, lol. thx anyway

---

### Post by matt_symes on 2011-05-10
Hi

I have just ran a couple of interesting tests on the VM. 

If you blank the wallpaper and reboot the PC so the script runs, you will get no wallpaper.
If you then remove the start up script and reboot the PC again you *do* get wallpaper. This ensures the script is only called once; on the first reboot.

What i think this shows is that on the first reboot the script is updating the gconf database but either not passing the message to gconfd or nautilus.

I think this maybe a dbus session issue. I will continue to investigate later.

Kind regards

---

### Post by thexnightmare on 2011-05-10
Thx in advanced.
BTW, as the script is working perfectly without gksudo, and just rm and reboot functions dont work, I think if we find a way to run those 2 commands from the script as sudo will be mych easier than the solution of running the entire script with gksudi.
What do you think?

---

### Post by matt_symes on 2011-05-11
Hi

> BTW, as the script is working perfectly without gksudo, and just rm and  reboot functions dont work, I think if we find a way to run those 2  commands from the script as sudo will be mych easier than the solution  of running the entire script with gksudi.
What do you think?There is a way to do this but it is a very dangerous solution because you remove the protection requiring admin privileges gives you.

This is especially important when it comes to the rm command where one mistyped command can wipe your entire hard drive.

I am looking into getting gconftool-2 working correctly. I know what the problem is and i am currently looking for a solution.

Kind regards

---

### Post by thexnightmare on 2011-05-11
can u tell me how to fix it by the non secure solution?
I will use it now, till finding other solution, if didn't find then will use it.

---

### Post by matt_symes on 2011-05-11
Hi

I will PM you the solution after i have eaten because i know why you need it. 

Kind regards

---

### Post by thexnightmare on 2011-05-11
ok waiting it, but do u think I need it? tell me in PM

---

### Post by matt_symes on 2011-05-11
Hi

I have PM'ed you the unsafe solution. The only reason i have done this is because i am also helping you on another thread and i know what you are trying to do.

I will post the safe solution when i get time to test it in my VM. This will be either tonight or tomorrow. I highly advise you to use that solution when i post it.

Kind regards

---

### Post by thexnightmare on 2011-05-11
Recieved and testing it out, but why do u think I need it? tell me in PM
I think it is working very good now. thx alot.
I will continue testing and get back to you.
BTW, as I am disabling keyboard, mouse, and all shotcuts, plus to tty access, so why the solution u mentioned in PM still unsafe?

---

### Post by matt_symes on 2011-05-11
Hi

> **thexnightmare said:**
> Recieved and testing it out, but why do u think I need it? tell me in PM
I think it is working very good now. thx alot.
I will continue testing and get back to you.
BTW, as I am disabling keyboard, mouse, and all shotcuts, plus to tty access, so why the solution u mentioned in PM still unsafe?

It's not so much unsafe for you as i know what you are trying to achieve.

As a general solution it is very unsafe. This is why i PM'ed you and did not post it on the forums. It's a bad habit to use that type of solution when there are safer method availiable.

As i said, i will post a safe solution when i get time.

Kind regards

---

### Post by matt_symes on 2011-05-11
Hi

> **thexnightmare said:**
> Recieved and testing it out, but why do u think I need it? tell me in PM
I think it is working very good now. thx alot.
I will continue testing and get back to you.
BTW, as I am disabling keyboard, mouse, and all shotcuts, plus to tty access, so why the solution u mentioned in PM still unsafe?

It's not so much unsafe for you as i know what you are trying to achieve.

As a general solution it is very unsafe. This is why i PM'ed you and did not post it on the forums. It's a bad habit to use that type of solution when there are safer method availiable.

As i said, i will post a safe solution when i get time.

Remember, you are not the only person reading this thread.

Kind regards

---

### Post by thexnightmare on 2011-05-11
ok will use it fornow till getting safer method.
BTW, I found something weired in the script.
volname returns the volume name for cd and dvd, but dont return volumename for blu ray disc. Do u have an idea?

---

### Post by matt_symes on 2011-05-11
Hi

> **thexnightmare said:**
> ok will use it fornow till getting safer method.
BTW, I found something weired in the script.
volname returns the volume name for cd and dvd, but dont return volumename for blu ray disc. Do u have an idea?

From 

```
man volname
```

> DESCRIPTION
       Volname returns the volume name for a device formatted with an ISO-9660 file system, typically a CD-ROM. It also works with normal files that contain a ISO-9660 file system.

I believe blue ray uses UDF 2.50 encoding. You will need to double check that though.

Kind regards

---

### Post by thexnightmare on 2011-05-11
Yes you are right, it uses UDF 2.5 FS.
So, do u know a command which returns blu ray disc volume?

---

### Post by matt_symes on 2011-05-11
Hi

> **thexnightmare said:**
> Yes you are right, it uses UDF 2.5 FS.
So, do u know a command which returns blu ray disc volume?

No. You will have to google that. I don't own a blue ray player.

If you find a solution post back the answer.

Kind regards

---

### Post by thexnightmare on 2011-05-11
yeah sure

---

