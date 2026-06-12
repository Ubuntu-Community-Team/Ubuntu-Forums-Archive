---
title: "cursor customising in ubuntu 11.10 wont work properlly"
date: 2012-02-12
forum: General Help
---

### Post by Yujo on 2012-02-12
hey all, ive recently been able to customise the themes in ubuntu 11.10 my problem is with the cursors im doing it correctly with the .icons folder and using the advanced settings but when i select the cursor the main cursor stays default ubuntu white one but the rest of the cursors used change according sutch as a hand on a link or button or the text cursor , can anybody help me figure out how to make the main cursor to what it should be in the cursor theme? 

thanks 

Yujo :)

---

### Post by fragos on 2012-02-12
This is a bug that has shown up with Unity. Changing cursor themes appears to take effect but only when the cursor is under the control of selected applications or libraries. I found no solution. Perhaps it relates to not all applications being upgraded from use of GTK 2 to GTK 3.

---

### Post by Yujo on 2012-02-13
ok thanks :) i did google it and i didnt find anything out either:(

---

### Post by stinkeye on 2012-02-14
After you have changed the cursor theme in advanced settings
run this command in terminal
```
sudo ln -fs /usr/share/icons/[COLOR="Magenta"]THEME[/COLOR]/cursor.theme /etc/alternatives/x-cursor-theme

```
Inserting the name of your cursor theme for [COLOR="Magenta"]THEME[/COLOR]

then run
```
sudo service lightdm restart
```

When you change your cursor theme using gnome-tweak-tool or Ubuntu-Tweak 
it changes the gsettings value but there is still another file that affects the cursor theme. 
ie **/etc/alternatives/x-cursor-theme**

This file links to the default **cursor.theme** file in **/usr/share/icons/DMZ-White**.
So as a work around, linking your cursor.theme file to  **/etc/alternatives/x-cursor-theme** appears to work.

 
I made this script which will list cursor themes in /usr/share/icons and allow you to choose by number.
It then runs 2 commands to change gsettings to your selection
and link your cursor.theme file to /etc/alternatives/x-cursor-theme file, with the option to restart lightdm.

Save as **change_cursor** and make executable.
To run, double click on file and choose **Run in Terminal**.
```
#!/bin/bash

### Script to change cursors in /usr/share/icons ###

#
## create installed cursor list text file
ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt

# 
## show a numbered list of cursors to choose from
cat -b ~/.cursorlist.txt 
 
	echo -e "\033[36mEnter your theme selection number:\033[0m"
	read CHOICE

#
## match the theme selection number to the cursor name
CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p') 
	echo -e "\n\033[36mYou have selected ...$CURSOR\nContinue?(y/n):\033[0m"
	read Ans
if  [ "$Ans" != "y" ]; then
exit
else

#
## Change to selected  cursor ###
	gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" &
	sudo ln -fs /usr/share/icons/$CURSOR/cursor.theme /etc/alternatives/x-cursor-theme
        # sudo sh -c "echo '[Icon Theme]\nInherits=$CURSOR' > /usr/share/icons/DMZ-White/cursor.theme"
fi

#
## Restart session to complete cursor change ###
	read -p "Do you wish to restartx? Save any work as you will now be logged out.(y/n):"
if  [ "$REPLY" != "y" ]; then 
	echo -e "\033[36m\nYou need to log out to complete cursor change.\033[0m";
else 
	sudo service lightdm restart
fi 
```

---

### Post by Yujo on 2012-02-15
sorry if i sound like an idiot lol im very greatful for your help but im new to linux and still getting the hang of things. when you said save the script save it how ? as a .txt file or something?

---

### Post by stinkeye on 2012-02-15
Open gedit and copy and paste the script into it.
Click on save and then name it **change_cursor** and save in your home folder.
Then right click on the saved file...Properties > Permissions
and mark the **Allow executing as program** box.
To run double click on **change_cursor** and choose **Run in Terminal**.

[SIZE="3"]**or**[/SIZE]

just download the attached archive and extract the change_cursor script.
Check it is executable and run as stated before.
 
*** The script will only list cursors in /usr/share/icons.
To install your cursor theme open the file browser to where your downloaded cursor theme is,
and then open nautilus with root permissions as below.
Enter in the terminal...
```
gksudo nautilus /usr/share/icons
```

Drag and drop your extracted cursor theme folder into **/usr/share/icons**

---

### Post by @lpha on 2012-02-16
> **stinkeye said:**
> After you have changed the cursor theme in advanced settings
run this command in terminal
```
sudo sh -c "echo '[Icon Theme]\nInherits=[COLOR=Magenta]THEME[/COLOR]' > /usr/share/icons/DMZ-White/cursor.theme"

```Inserting the name of your cursor theme for [COLOR=Magenta]THEME[/COLOR]

then run
```
sudo service lightdm restart
```When you change your cursor theme using gnome-tweak-tool or Ubuntu-Tweak 
it changes the gsettings value but there is still another file that affects the cursor theme. 
ie **/etc/alternatives/x-cursor-theme**

This file links to the default **cursor.theme** file in **/usr/share/icons/DMZ-White**.
So as a work around, editing the **/usr/share/icons/DMZ-White/cursor.theme** file to also reflect your selected theme appears to work.

 
I made this script which will list cursor themes in /usr/share/icons and allow you to choose by number.
It then runs 2 commands to change gsettings to your selection
and edit the /usr/share/icons/DMZ-White/cursor.theme file, with the option to restart lightdm.

Save as **change_cursor** and make executable.
To run, double click on file and choose **Run in Terminal**.
```
#!/bin/bash

### Script to change cursors in /usr/share/icons ###

#
## create installed cursor list text file
ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt

# 
## show a numbered list of cursors to choose from
cat -b ~/.cursorlist.txt 
 
    echo -e "\033[36mEnter your theme selection number:\033[0m"
    read CHOICE

#
## match the theme selection number to the cursor name
CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p') 
    echo -e "\n\033[36mYou have selected ...$CURSOR\nContinue?(y/n):\033[0m"
    read Ans
if  [ "$Ans" != "y" ]; then
exit
else

#
## Change to selected  cursor ###
    gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" &
    sudo sh -c "echo '[Icon Theme]\nInherits=$CURSOR' > /usr/share/icons/DMZ-White/cursor.theme"
fi

#
## Restart session to complete cursor change ###
    read -p "Do you wish to restartx? Save any work as you will now be logged out.(y/n):"
if  [ "$REPLY" != "y" ]; then 
    echo -e "\033[36m\nYou need to log out to complete cursor change.\033[0m";
else 
    sudo service lightdm restart
fi 
```


You're the best! You give some the clearest, most useful solutions in ubuntuforums. This script will save me lots of time, as I don't have to change themes manually anymore. Thank a bunch!

So the underlying problem is that the tweak tool fails to update the **/usr/share/icons/default/index.theme** file? Does Gnome plan on building a tool that will let us perform more customization in the future?

I hope this gets fixed soon somehow ..by someone. Although I enjoy finding fixes for problems, It's time consuming, sometimes inconvenient, and especially burdensome on newBuntu users that want to get things working. This thread is a perfect example of that.

---

### Post by stinkeye on 2012-02-16
> **@lpha said:**
> You're the best! You give some the clearest, most useful solutions in ubuntuforums. 
This script will save me lots of time, as I don't have to change themes manually anymore. Thank a bunch!
Thanks. Took me a while to write and test the script.
Don't really know bash scripting, just put it together by reading other scripts
and man pages and googling for sed snippets.
My evening hobby since switching from that other OS. :D

> **@lpha said:**
> 
So the underlying problem is that the tweak tool fails to update the **/usr/share/icons/default/index.theme** file? 
Does Gnome plan on building a tool that will let us perform more customization in the future?

You can also change cursors using gnome-tweak-tool
and then running **sudo update-alternatives --config x-cursor-theme** to also change to the same cursor
but it will only list cursors installed through the package manager,
not those you manually install.
I'm sure customizing will improve as gnome3 matures.

---

### Post by Yujo on 2012-02-23
thanks alot for this its saved me alot of hassle :)

---

### Post by cenaar on 2012-05-04
Thank you for your effort, stinkeye, it worked perfectly with 12.04 LTS as well.

---

