---
title: "Horrendous crash with black screen after upgrading ubuntu to the lastest version"
date: 2009-12-17
forum: General Help
---

### Post by clettier on 2009-12-17
[FONT=Arial][SIZE=2]Hello there. Please, notice that I am a beginner with linux and I am also really really desperate!
I have a Dell Studio XPS 13 with ubuntu. Yesterday I performed the upgrade of ubuntu to the latest version. Once the upgrade finished and the system restarted, the computer appeared to be frozen at the loading window. After a while the screen becomes completely white, then black with the cursor flashing on the upper left corner of the screen.
It gives no error and no info at all. It just stays like that forever :(.
I always had problem with this goddam laptop and ubuntu.
Actions I performed :
I initially thought it could be a graphic problem (I had something similar when I installed the graphic drivers). Therefore I typed:
[FONT=Times New Roman]**lspci | grep VGA**
having:[/FONT]
[/SIZE][/FONT]  **[FONT=Arial][SIZE=2][FONT=Courier New]02:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)[/FONT][/SIZE][/FONT]** **[FONT=Arial][SIZE=2][FONT=Courier New]03:00.0 VGA compatible controller: nVidia Corporation GeForce 9400M G (rev b1)[/FONT][/SIZE][/FONT]** 
[FONT=Arial][SIZE=2]
hence I[/SIZE][/FONT] edited the /etc/X11/xorg.conf file as follows:

 **[FONT=Courier New]Section "Device"[/FONT]** **[FONT=Courier New]        Identifier     "Default Device"[/FONT]** **[FONT=Courier New]        Busid   "PCI:3:0:0"[/FONT]** **[FONT=Courier New]        Driver  "nvidia"[/FONT]** **[FONT=Courier New]        Option  "NoLogo"       "True"[/FONT]** **[FONT=Courier New]EndSection[/FONT]** 

I had no improvement. After that I tried to delete any folder which could effect the graphic settings:

**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

Again this yielded no result. Finally I tried to restore the default graphic:

**sudo dpkg-reconfigure -phigh xserver-xorg**
Still nothing :(.

[B]Question: Is there any way to retrieve an error log, or any kind of information which can tell what the problem is? Also, I 'd really appreciate any suggestion, if you had or know about this bug before.

[/B]The worst part is that I am a PhD student at the final year with some important data and the thesis on my laptop. I have some backup but nothing extremely recent. 
If I load the system in 'safe mode' I can access to the terminal. I mounted an external hard drive, but when I copied the data, everything was copied with no writing/reading /execution rights. Hence, I have to go folder by folder, file by file and chmod a+w/r/x any single file!!!!
Also, if I boot the pc with the live cd I can see my data. However,  when I try to copy them, it just says I do not have the permission , without asking for any psw or anything.
It all looks like an horrible linux nightmare! It is a jungle of bugs, limitationa and permissions! ^^ I feel really frustrated!
The windows Vista partition works fine, but I can't download my data from there.


Thanks a lot for your help :D!!!!

---

### Post by amsterdamharu on 2009-12-17
I had a simular problem with fedora once, the nvidia card is not working well untull you install the drivers but to install the drivers you have to open synaptic package manager or something like this (in a gui).

In Fedora it was as easy as pressing control + alt + plus(+) to change resolutions untill you get a picture. In ubuntu this doesn't work I think.

You might try a low resolution changing the xorg.conf
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Just don't boot in a gui (use the restore from the boot menu and go to command line).

---

### Post by realzippy on 2009-12-17
*"The worst part is that I am a PhD student at the final year with some important data"*

you can start from Live CD and save your data.

"**rm** -rf .gnome .gnome2 .gconf .gconfd .metacity"

bad idea.Gnome is your desktop..maybe the deleted files are in trash,so you can copy them back.You should have deleted only your /etc/X11/xorg.conf file..

"sudo dpkg-reconfigure -phigh xserver-xorg"

does not work anymore since Karmic.With NVIDIA-drivers run:

sudo nvidia-xconfig

---

### Post by clettier on 2009-12-17
Hello there. First of all thanks to both for ur help :P
To realzippy:
Unfortunately, I already tried to backup data with live cd. As you can see in the main threat the problem is that doing so he does not allow me to backup, since it says I have no permission to copy the files.
sudo nvida-xconfig does not work. It says that the line Default Device in Screen is not a valid option...
To amsterdamharu:
We may have something here!!! Not exactly correlated to what you sent me... however going in one of the links posted in ur suggestion I found:
sudo xinit -- :2which is a great thing. It allows me to test xconf without restarting.
It comes out with the error:
Fatal server error:
no screens found

Can it be that after the update of ubuntu, now the system is not able to find the screen ? How can I fix it?

---

### Post by clettier on 2009-12-17
Maybe I can give some extra piece of information:

(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

This is the Xorg.2.log 

can this be the problem :P ?

Cheers

---

### Post by amsterdamharu on 2009-12-17
It might be a lot of trouble to fix this using editing text files. You can try renaming xorg.conf and see what happens.

In your start menu there should be an option ...(recovery mode) try that and go to command prompt (this still works doesn't it?). Log in as root (if root password is not set yet log in as normal user and do: sudo passwd to set it DO NOT FORGET THE PASSWORD).
Make sure xorg is installed
apt-get install xorg
rename the xorg.conf
mv /etc/X11/xorg.conf /etc/X11/xorg.origional

If all that doesn't give you gui back and you really want to back up then you can change file permission of your home folder to back it up:
chmod 777 -R /home/myUser/
or just copy it as root to some other location.
777 is all permission to all files, you might not need execute but I am a bit busy to look up the number for read write for everyone.

---

### Post by longtom on 2009-12-17
What about burning a Puppy iso file and try to access your files from there?

I have had success with that before.

---

### Post by Tavarid on 2009-12-17
Since you seem to be able to make it into a terminal... login and type: sudo nano /etc/X11/xorg.conf

After this keep going down until you find a line that looks something like this:
Driver    "nvidia"

What you are going to do there is change "nvidia" to "nv".  Seems the nvidia drivers you were using before either stopped working or are not installed into the newer kernel.

Hope that helps.

---

### Post by clettier on 2009-12-17
Heya guys. Again thanks for all the efforts u r making to help me out. :D
To amsterdamharu
chmod 777 -R /home/myUser/ is a life saver!!! :):):):)
I copied all the files on the hard drive and I can now access with another computer.
On the other side I am still far from recovering the system...
apt-get install xorg did something... it did not exactly give me back the graphic interface but now when i type
sudo xinit -- :2
the system gives a sort of white window and then crashes completely :P
Again the error is no screen found! the only error message I got is:
(EE) No devices detected

Fatal server error:
no screens found

Also the suggestion of Tavarid did not work. Same error... no screens!

I also performed the following actions:
sudo apt-get remove --purge nvidia* 
which should have deleted any driver. Then again I did a reset of the xconf, praying God to have agraphic interphace! :( Same problem:( ... no screen

Question:
The bloody live cd works! How on earth is that possible? How can it find the screen while the System can't? Does this thing have a safe mode ? Is there a way to display a simple low resolution screen.... is there any default option???
I am really puzzled here! I feel like back in 1970! I just update the OS and I can't even access to my data. Talking about stability I think this is the pre-history of computers!

---

### Post by amsterdamharu on 2009-12-17
It must be a configuration error, I think with some default config it might work therefore try to rename xorg.conf. When there is no xorg.conf the system will make one and use some low res no 3d driver that will work.
After renaming try this command:
dpkg-reconfigure xserver-xorg
This will create a new xorg.conf in any case keep trying to edit this file is a lot of trouble I think that ubuntu can fix this automatically for you and after you can upgrade to a better video driver.
When you have your gui (desktop) you can install the correct nvidia drivers of your choise.
system -> administration -> hardware drivers

---

### Post by amsterdamharu on 2009-12-17
> I feel like back in 1970
I agree, using Linux is frustrating because it's a lot of different little programs knitted together by configuration text files and going into there is like going into regedit to fix a windows problem.
Ubuntu is a distro that tries to stabilize these programs running together and fix problems that a normal person like you and me won't bother to look into automatically. 
In my opinion Ubuntu has done a pretty good job of it but as this forum proofs it is never perfect.

---

### Post by spiderbatdad on 2009-12-17
Have you tried booting into Recovery, then selecting resume normal boot?

---

### Post by clettier on 2009-12-17
Hello there!!!
Still no luck. I renamed the xorg.conf, then I tried dpkg-reconfigure xserver-xorg.
However, we had an improvement... it's like a ubuntu loading bar appeared for a while, then the screen went mad with letters everywhere.
I have an idea.... could it be one of the splash screen I installed some months ago ? In particular I had one to make the loading bar more smooth and nice!
Do you have any idea how to uninstall them from terminal ?
Thanks again

---

### Post by clettier on 2009-12-17
> **spiderbatdad said:**
> Have you tried booting into Recovery, then selecting resume normal boot?

yep, it's what I am actually using 
Cheers

---

### Post by amsterdamharu on 2009-12-17
While booting press control alt and F1 this should give you tty1 which is non graphic. It will automatically switch to tty7 when the grapic login screen comes.
Or just start a command prompt, log in as normal user and type
startx

---

### Post by clettier on 2009-12-17
It actually... I have no mouse... but I am in :D

---

### Post by clettier on 2009-12-17
> **amsterdamharu said:**
> While booting press control alt and F1 this should give you tty1 which is non graphic. It will automatically switch to tty7 when the grapic login screen comes.
Or just start a command prompt, log in as normal user and type
startx
Astonishing!
It worked!
I am in!!!!!!!!!!!!!
What did we just do :D ?
I'll try to install the drivers now
I am so scared I am not going to reboot the system anymore!

---

### Post by amsterdamharu on 2009-12-17
It must have been the splash screen then. Ubuntu has several tty you can log in as another user by pressing control + alt + f1 and log in as root, then control + alt + f2 and log in as another user.
tty1 to 6 are usually non graphic tty1 is used at boot up and tty7 is your desktop login thing.
I would be careful logged in as root, maybe remove your splash first.

---

### Post by clettier on 2009-12-17
Thanks a lot!
I am still far from solving the problem, since I deleted splash screens and every screenlet I installed, but still I can't boot the system normally. I'll try to manually install the nvidia graphic drivers and see what happens.
Anyway, now that I can at least log in I can save all the data I have!
Cheers!!!!

---

### Post by amsterdamharu on 2009-12-17
System -> administration -> hardware drivers 
There you should be able to activate/install nvidia drivers.
Maybe in System -> administration -> software sources
Activate the multiverse packages (under Ubuntu software)

---

