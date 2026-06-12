---
title: "Problem with ubuntu or Windows option screen"
date: 2011-09-02
forum: General Help
---

### Post by mawsoft on 2011-09-02
I've recently installed Ubuntu 11.04 alongside Windows7. I downloaded the image file from the ubuntu website and burned it to CD. The install appeared to go fine and I got the Installation Complete/Restart Now screen which I clicked for Restart. On the Reboot, the screen goes purple as expected and an OS selection screen appears listing options as follows :-
 
 **ubuntu with Linux**
** ubuntu with Linux recovery**
** memcheck**
** memcheck**
** Windows7**
 
Each of the options has a variety of figures & letters after them. 
 
With **ubuntu with Linux** highlighted I press Enter.
 
The screen goes blank purple for about 10 seconds then goes black. And thats it !
No curser or anything. I have to power off.
 
 Selecting the **Windows7** option works fine.
 
Can anyone help please. Nothing too technical as "Computers for Dummies" was written for my benefit !!

---

### Post by searchfgold6789 on 2011-09-02
Try to set the "nomodeset" option:

[LIST=1]
[*]Go to the menu of boot options. Go to the ubuntu one and press the "E" on your keyboard.
[*]Press the Down Arrow until you get to the line that begins with "linux /boot".
[*]The line ends with "quiet splash". Press the "END" key to position the cursor right after "quiet splash".
[*]Modify the end of the line so that instead of "quiet splash" it says "quiet splash **nomodeset**".
[*]Press ctrl + x to boot.
[/LIST]
Then, if it works, go to System>Administration>Additional Drivers to see if your graphics card shows up.

---

### Post by mawsoft on 2011-09-02
Thanks for your quick reply. I've tried what you suggested. At the end of the line which contains "quiet splash" is the expression "vt.handoff=7". I deleted this before adding "nomodeset" and rebooted. Just got a text screen requesting my ID & password which I entered. I then got a command promp but could get no further. Should I have deleted the "vt.handoff=7" bit ?

---

### Post by searchfgold6789 on 2011-09-02
I would try it again, except this time do not delete that one boot option (vthandoff=7). Also, adding the nomodeset is just non-permanent, which means that every time you reboot you'll have to add the nomodeset option again until we get it fixed.
If you get to a Command Line (text-only) screen like this:
```
name@user login:
```Then type in your username, press enter, type in your password, press enter, then type:```
startx
```

---

### Post by mawsoft on 2011-09-02
Thanks again for quick response. I tried editting the line again without deleting the **vt.handoff=7 **but I'm afraid that just returned to the original problem - blank purple screen then black screen. I went back in to edit the Grub screen and removed the **vt** bit before adding the **nomodeset.** This time I got back into the text screen, signed in and typed in **startx.**
A screenful of text appeared showing when the system was built etc etc, but I guess the significant part was as follows :-
 
**Log file:- "/var/log/Xorg.O.log", Time : Fri Sep 2 ......2011**
 
**Using system config directory "/usr/share/X11/xorg.conf.d"**
**(EE) Failed to load module "fglrx" (module does not exist,0)**
**(II) [KMS] drm report mode setting isn't supported.**
**(EE) RADEON(0): Chipset: "CAICOS" (ChipID=0x6779) requires KMS**
**(EE) Screen(s) found, but none have a usable configuration.**
 
I'm afraid this doesn't mean very much to me, but hopefully you will be able to shed some light on it.
Thanks again for your help.

---

### Post by searchfgold6789 on 2011-09-02
OK, now when you get to the prompt, type in:```
lspci
```And look where it says "VGA Compatible Controller". Can you post the contents of that line?
Also, if you need to reboot your computer in a more safe fashion, you can use the command ```
sudo reboot
```

---

### Post by mawsoft on 2011-09-02
Have done. That line reads :-
**VGA ****Compatible Controller: ATI Technologies Inc NI Caicos[AMD RADEON HD 6450]**

---

### Post by searchfgold6789 on 2011-09-02
OK, now when you get to the prompt can you type in the following one last command and post the output? I will then make commands for you to run that will install drivers for the card and it will work.```
uname -m
```

---

### Post by mawsoft on 2011-09-02
Have done. Output from the **uname-m **command is **i686. **Hope we're on the last lap !
Thanks again.

---

### Post by searchfgold6789 on 2011-09-02
Run the following commands and then reboot:
```

sudo apt-get install -q=2 linux-libc-dev linux-headers-generic
mkdir ~/Graphics
cd ~/Graphics
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run
chmod +x ati-driver-installer-11-8-x86.x86_64.run
ati-driver-installer-11-8-x86.x86_64.run
```
Don't worry; if all goes well this problem should be very nearly resolved.

---

### Post by mawsoft on 2011-09-02
I've put in all the code and everything went fine until the very last line :
 
**ati-driver-installer-11-8-x86.x86_64.run**
 
to which the response came back :
 
**ati-driver-installer-11-8-x86.x86_64.run : command not found**
 
As its getting a bit late in this part of the world, would it be ok to resume this tomorrow ?

---

### Post by searchfgold6789 on 2011-09-02
By all means.
When you are ready to resume, I will have to say, I typed the wrong command. It is not:```

ati-driver-installer-11-8-x86.x86_64.run
```but```
./ati-driver-installer-11-8-x86.x86_64.run
```
Sorry! :(

---

### Post by mawsoft on 2011-09-03
Please don't apologise. I'm grateful for your time and expertise.
 
I've re-entered all the commands(except the mkdir line) including the modified last line but unfortunately it still hasn't solved the problem.
I'm beginning to think that I've got a corrupt download/CD burn and it might be as well to start from scratch and burn a new CD. What do you think ?

---

### Post by searchfgold6789 on 2011-09-03
When you reboot, you only need to type in the 'cd' command, and then the very last one...
I'm surprised the last command did not work, that is, "./ati-driver-installer-11-8-x86.x86_64.run". What about ```
sudo sh ~/Graphics/ati-driver-installer-11-8-x86.x86_64.run
```?
The reason you are having trouble is because Ubuntu cannot find the software needed to run your graphics card, that is, the thing that runs your screen as well as processes all of the graphics. All of these commands are installing a driver Ubuntu can use to run graphics on your computer.

---

### Post by mawsoft on 2011-09-05
**Yipee !!! We have lift off**. Everything appears to have installed ok. I got the message :-

[B]For further configuration of the driver, please run aticonfig from a terminal window or AMD CCC:LE from the Desktop Manager Menu.
Removing temporary directory : fglrx-install.CzoOKC

[/B]I rebooted, got the grub screen, selected** ubuntu** and hey presto here we are in the desktop with Firefox running !
Do I need to further configure the driver or can I just let things go now ?

Thanks again for all your help and patience

---

### Post by searchfgold6789 on 2011-09-05
> For further configuration of the driver, please run aticonfig from a terminal window or AMD CCC:LE from the Desktop Manager MenuI am happy to say that the 'aticonfig' command should only need to be used if you run into further problems. *You're all set.*
Have fun with Ubuntu, I think you'll find it to be a very usable and superior computing experience.
Don't forget to mark this thread as solved under the 'thread tools' menu.
 - search

---

