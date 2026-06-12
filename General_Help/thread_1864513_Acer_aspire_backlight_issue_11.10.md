---
title: "Acer aspire backlight issue 11.10"
date: 2011-10-19
forum: General Help
---

### Post by techfighterminal on 2011-10-19
I've looked everywhere alas no luck. it seems to be a common problem with no solution.

my backlight just shuts off when Ubuntu boots. my external monitor works, just not my laptop screen. and my brightness/contrast is all the way up. it just doesn't work..

I would appreciate any help

---

### Post by techfighterminal on 2011-10-19
solved

sudo gedit /etc/default/grub

Edit the two lines
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor vga=792"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"  

sudo update-grub 

sudo reboot

---

### Post by EpicWorld on 2011-12-28
sorry for the huge bump but is not working for me, and i have same laptop :(

---

### Post by CoDelishus on 2012-01-01
I have an Acer 5334 and had the same problems.  Since then I just downgraded to 10.04 since I like that one more than the latter 11.10.   But to help you rather than just saying downgrade read my to do file I created for this very problem.
The Intel GMA 4500M video card does not play well with later distros (That's at least what video card I have with this Acer Aspire).   The back-light does not turn on properly so prepare to have a flash light next to you.   To fix this you'll have to open the terminal and type this: 

    ```
sudo setpci -s 00:02.0 F4.B=00
```I recommend if you want to install the later versions of ubuntu based OS's that you run the live cd first open terminal and enter the above statement then install.  Keep in mind that this is a temp fix at the moment.  I will share how to further fix permanently.  Once you have installed and rebooted.  Re-type 
```
sudo setpci -s 00:02.0 F4.B=00
```in the terminal so you can see without your trusty flash light/cellphone led flash light.  Now that you can see properly type in the terminal 
```
gedit ./etc/pm/sleep.d/9_lcd_backlight.sh
```(if not gedit then any other text editor) this will create the file 9_lcd_backlight.sh.  9 is the priority you can put any number through 99 I believe, but it doesn't matter in this case.  Paste the following below into the file you created, this will make sure when you boot from suspend or hibernate the back-light will be activated.

    ```
#!/bin/bash
    case $1 in
        thaw)
        setpci -s 00:02.0 F4.B=0
            echo "oh, suspend to disk is over, we are resuming..."
        ;;
        resume)
        setpci -s 00:02.0 F4.B=0
            echo "hey, the suspend to RAM seems to be over..."
        ;;
        *)  echo "here we GO!."
        ;;
    esac
```With the bash file in place you now need to make the file executable.  Make sure you are in the directory ./etc/pm/sleep.d/ and type this in the terminal:
```
chmod +x 9_lcd_backlight.sh
```Once the bash file is now executable lets make sure the back-light turns on when you boot up.  Input the next 2 lines in ./etc/rc.local file at the bottom line.  So type in the terminal:

    ```
gedit ./etc/rc.local
```This will open rc.local file.  Now at the bottom make sure it looks like below and save.

    ```
sudo setpci -s 00:02.0 F4.B=00
exit 0
```You should be fine, reboot and check it out.  :D

---

### Post by ambardeepdas on 2012-02-06
CoDelishus yours was the best answer. :KS   Thank you so so much. In tackling this backilight issue I, a very new ubuntu user, have learned much. In case you are a new user and are having these same problems the above answer might have a few hitches. 
For example 
>when i tried to save 9_lcd_backlight.sh to the sleep.d folder I was not allowed because i am not a root user. What I had to do was save a gedit file in the same name in the home folder and move (mv command) the file to sleep.d folder. Of course I had to prefix mv with sudo. 
>Even the chmod command needed to be prefixed with sudo. 
>There were problems again in editing the rc.local file. As with the  9_lcd_backlight.sh file i had to make a new gedit file with name rc.local01 name elsewhere(home folder), copy the lines from the actual rc.local file into the rc.local01 file, add the two lines at the end as instructed by CoDelishus and saved it. Move (sudo mv command) the file to the etc folder and rename the files. By this time you will have tested the changes and will see that when the computer comes out of sleep or hibernation it works just fine BUT startup after a shutdown is still not working. This took the longest time to solve... ;) All you have to do is right click on rc.local file you made, click on Permissions tab and check the box that says 'Allow executing file as program.

As a new user, the above is my way of solving the problem at hand. Might not be the most efficient. please try my solution ONLY if the above doesn't seem to be working. Thanks and good luck.

---

### Post by CoDelishus on 2012-06-28
> **ambardeepdas said:**
> CoDelishus yours was the best answer. :KS   Thank you so so much. In tackling this backilight issue I, a very new ubuntu user, have learned much. In case you are a new user and are having these same problems the above answer might have a few hitches. 
For example 
>when i tried to save 9_lcd_backlight.sh to the sleep.d folder I was not allowed because i am not a root user. What I had to do was save a gedit file in the same name in the home folder and move (mv command) the file to sleep.d folder. Of course I had to prefix mv with sudo. 
>Even the chmod command needed to be prefixed with sudo. 
>There were problems again in editing the rc.local file. As with the  9_lcd_backlight.sh file i had to make a new gedit file with name rc.local01 name elsewhere(home folder), copy the lines from the actual rc.local file into the rc.local01 file, add the two lines at the end as instructed by CoDelishus and saved it. Move (sudo mv command) the file to the etc folder and rename the files. By this time you will have tested the changes and will see that when the computer comes out of sleep or hibernation it works just fine BUT startup after a shutdown is still not working. This took the longest time to solve... ;) All you have to do is right click on rc.local file you made, click on Permissions tab and check the box that says 'Allow executing file as program.

As a new user, the above is my way of solving the problem at hand. Might not be the most efficient. please try my solution ONLY if the above doesn't seem to be working. Thanks and good luck.

Hey thanks for the kudos, you are correct ambardeepdas.  Before this code

```
gedit ./etc/pm/sleep.d/9_lcd_backlight.sh 
``` you should be in root.  I apologize for the confusion and late response.

---

### Post by duncanmaybury on 2012-08-15
Hi, am I missing something here.
I have followed the steps above and still know back light on restart.
When I sudo setpci.... I can get the backlight up and running, but the rc.local file doesn't seem to do it buisness, it is set as executable. This is on a upgrade to 12.04.
Can anyone think of why the rc.local file is not doing what it should?
I am fairly novice at ubuntu.
Thanks

---

### Post by isa.dsouza on 2012-10-07
Just use hot-keys when grub loads. I have been using the hot-keys to increase brightness, for a year or more now. Should work on any machine, I hope.

---

### Post by vampiro809 on 2012-12-05
> **techfighterminal said:**
> solved

sudo gedit /etc/default/grub

Edit the two lines
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor vga=792"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"  

sudo update-grub 

sudo reboot

HI. excuse me, but, how can edit if the screen in black????

---

### Post by Colabear8900 on 2013-06-01
> **techfighterminal said:**
> solved

sudo gedit /etc/default/grub

Edit the two lines
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor vga=792"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"  

sudo update-grub 

sudo reboot

CONFIRMED this method WORKS for Acer Aspire V3-771G-6485 on Ubuntu 13.04 64-bit (UEFI mode). Backlight turns ON during BOOT.

---

### Post by lawrencecar on 2013-06-23
> **CoDelishus said:**
> [U][COLOR=#000000]I have an Acer 5334 and had the same problems.  Since then I just downgraded to 10.04 since I like that one more than the latter 11.10.   But to help you rather than just saying downgrade read my to do file I created for this very problem.
The Intel GMA 4500M video card does not play well with later distros (That's at least what video card I have with this Acer Aspire).   The back-light does not turn on properly so prepare to have a flash light next to you.   To fix this you'll have to open the terminal and type this: 

    ```
sudo setpci -s 00:02.0 F4.B=00
```I recommend if you want to install the later versions of ubuntu based OS's that you run the live cd first open terminal and enter the above statement then install.  Keep in mind that this is a temp fix at the moment.  I will share how to further fix permanently.  Once you have installed and rebooted.  Re-type 
```
sudo setpci -s 00:02.0 F4.B=00
```in the terminal so you can see without your trusty flash light/cellphone [/COLOR][[COLOR=#000000]led light[/COLOR]]("http://www.niceledlights.com")[COLOR=#000000] .  Now that you can see properly type in the terminal 
```
gedit ./etc/pm/sleep.d/9_lcd_backlight.sh
```(if not gedit then any other text editor) this will create the file 9_lcd_backlight.sh.  9 is the priority you can put any number through 99 I believe, but it doesn't matter in this case.  Paste the following below into the file you created, this will make sure when you boot from suspend or hibernate the back-light will be activated.

    ```
#!/bin/bash
    case $1 in
        thaw)
        setpci -s 00:02.0 F4.B=0
            echo "oh, suspend to disk is over, we are resuming..."
        ;;
        resume)
        setpci -s 00:02.0 F4.B=0
            echo "hey, the suspend to RAM seems to be over..."
        ;;
        *)  echo "here we GO!."
        ;;
    esac
```With the bash file in place you now need to make the file executable.  Make sure you are in the directory ./etc/pm/sleep.d/ and type this in the terminal:
```
chmod +x 9_lcd_backlight.sh
```Once the bash file is now executable lets make sure the back-light turns on when you boot up.  Input the next 2 lines in ./etc/rc.local file at the bottom line.  So type in the terminal:

    ```
gedit ./etc/rc.local
```This will open rc.local file.  Now at the bottom make sure it looks like below and save.

    ```
sudo setpci -s 00:02.0 F4.B=00
exit 0
```You should be fine, reboot and check it out.  :D[/COLOR][/U]
Hello friend i am just facing similar problem with my acer laptop.. I will surely follow above mentioned steps and try to solve it.. Thanks for sharing information and i will post my experience very soon

---

### Post by klaus-3 on 2013-08-20
> **techfighterminal said:**
> solved

sudo gedit /etc/default/grub

Edit the two lines
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor vga=792"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"  

sudo update-grub 

sudo reboot

This Solution works for Acer Aspire 5332

---

