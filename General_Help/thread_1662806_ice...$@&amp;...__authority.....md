---
title: "ice...$*@&amp;...  authority...."
date: 2011-01-08
forum: General Help
---

### Post by JuicyCouture on 2011-01-08
what the hell do i do

every time i boot, before the desktop appears i get "could not update ICEauthority"

i know this is a common problem, yet there still seems to be no common solution

if i have to reinstall this thing again i might have to go back to windows


also another problem lie iceauthority to appear out of nowhere - all of a sudden, every application i have installed today via the software center - will not start. i download armagetron, click its icon in the games - nothing happeny, same with tank wars. anything i installed before today starts fine.

---

### Post by JuicyCouture on 2011-01-08
wow even under root in the freaking bootloader i dont have permission with that file

---

### Post by cariboo on 2011-01-08
Please watch your language, we have members as young as 8 years old.

To solve your problem. at the login screen, press Ctrl-Alt-F1, login at the prompt with your username and password, then type the following command:

```
chmod 600 .ICEauthority
```

and prees return.

Then press Ctrl-ALT-F7 to return to the login screen, you should now be able to log in without the .ICEauthority error message

---

### Post by drs305 on 2011-01-08
Starting at Post #43 of this thread people start discussing .IceAuthority problems. There are several solutions posted, none of which worked for all users.

If this is the thread that sent you 'round the bend I apologize, as it exactly matches your description of numerous solutions (which may not have worked for you) which are tried and work for some but fail for others.  ;-)

[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

---

### Post by JuicyCouture on 2011-01-08
this program not running problem is actually a bigger issue for me right now

i just remembered doing an apt-get aptitude today, it might have been since then that nothing i try to run (installed today) works

anyone know how to fix that, how to chang eit back to the old installer?

---

### Post by tgm4883 on 2011-01-08
> **JuicyCouture said:**
> this program not running problem is actually a bigger issue for me right now

i just remembered doing an apt-get aptitude today, it might have been since then that nothing i try to run (installed today) works

anyone know how to fix that, how to chang eit back to the old installer?

apt-get aptitude doesn't do anything. It's an invalid operation

---

### Post by JuicyCouture on 2011-01-08
seriously i dont think i have the authority right now to save anything anywhere

i just set up frostwire, its asking me where i want my save directory to be - NOTHING is permitted, anywhere in the home folder, root folders anything

im trying the stuff you guys are telling me - and in that guys thread, i just keep getting not permitted not permitted

thats gotta be why the games i've installed today arent running right? they probably werent even saved in there

btw where are games saved by default? which folder

im just gonna end up giving this thign another wipe tonight - and its been like 3 days since i've had a wireless problem, they're probably gonna start again after i reinstall
 
holy )#()# i cant even delete movies off my thumb drive nothing is happening

---

### Post by JuicyCouture on 2011-01-08
i just noticed something that might help you people

i found the games folder under /usr

for some reason, armagetron (the game i installed today thats not starting) has a .real extension after it, none of the other games do

could this mean something?

---

### Post by tgm4883 on 2011-01-08
> **JuicyCouture said:**
> i just noticed something that might help you people

i found the games folder under /usr

for some reason, armagetron (the game i installed today thats not starting) has a .real extension after it, none of the other games do

could this mean something?

No that doesn't mean anything in regards to your issues.

---

### Post by Lian Radu on 2011-01-13
Try change the owner of /home/username/.Iceauthority:
sudo chown username /home/username/.ICEauthority

sudo chown -R username /home/username
for the entire home folder

where username is, of course, your user name.

You can also open a folder in administrative mode like this:

sudo nautilus /home/username

Then you can change the owner of a file by right-clicking on it -> Properties -> Permissions.

You can install nautilus-gksu with:

sudo apt-get install nautilus-gksu

then you can open any folder with root privileges (right click on a folder -> Open as administrator).
To activate this feature, you might need to restart the computer after installing the above mentioned program.

Another user extension to nautilus is nautilus-open-terminal. You can install it by:

sudo apt-get install nautilus-open-terminal

This will allow you to open the terminal in any folder, including on the Desktop.
Right click on a folder or on the Desktop, then choose Open in terminal.
You will also need to reboot to activate this feature.

---

