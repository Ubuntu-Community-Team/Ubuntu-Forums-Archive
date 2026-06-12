---
title: "How do I  install Teamspeak 3 (.run file)"
date: 2012-06-04
forum: General Help
---

### Post by colobix on 2012-06-04
Hello. I just downloaded TeamSpeak3-Client-linux_amd64-3.0.6.run from their website. How do I install it?
It's not a deb file, so I'm not sure what distro it's meant for.
But I'm not able to extract it either.

---

### Post by dino99 on 2012-06-04
googling a little will help

[http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/](http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/)

[http://support.teamspeakusa.com/index.php?/Knowledgebase/List/Index/10/english](http://support.teamspeakusa.com/index.php?/Knowledgebase/List/Index/10/english)

[https://help.ubuntu.com/community/TeamSpeak](https://help.ubuntu.com/community/TeamSpeak)

---

### Post by colobix on 2012-06-04
> **dino99 said:**
> googling a little will help



Thanks, but none of the links explained how to install it from the .run file.
And I've tried to google this.

---

### Post by blueshead on 2012-06-04
right click mouse/properties/permissions/ select -allow this file to run as program

---

### Post by hakermania on 2012-06-04
Hey, I just installed it yesterday!
Follow these steps:
1) Right click on the file->properties->permissions->allow executing file as program
2) Open a terminal with Ctrl+Alt+T. Probably you have the .run file in your Downloads folder.
Give the following command:
```

cd Downloads

```
so as to go to the Downloads folder and then give
```

./TeamSpeak3-Client-linux_x86-3.0.6.run

```
(or whatever the name of the executable is)
Press ENTER, after you start the above application, then Q, then type yes and press ENTER again. Some extraction will take place and a new directory will be created.
3) In order to launch the Teamspeak application, create this .desktop file at your desktop:
```

[Desktop Entry]
Type=Application
Exec=/home/alex/Documents/TeamSpeak3-Client-linux_x86/ts3client_runscript.sh
Name=Teamspeak
Version=3
Icon=/home/alex/Pictures/alien192.png

```
but, change the 'Exec' field to the one matching your ts3client_runscript.sh file's path and 'Icon' to one of your preference. Save the file as 'anything.desktop'
4) Give execution permissions to anything.desktop and run teamspeak :)

---

### Post by Steven D on 2012-06-05
Try this: 
[http://addons.teamspeak.com/directory/tools/miscellaneous/Teamspeak-3-Linux-GUI-Installer.html](http://addons.teamspeak.com/directory/tools/miscellaneous/Teamspeak-3-Linux-GUI-Installer.html)

---

### Post by colobix on 2012-06-05
Thank you guys. That was complicated. I can only imagine how painful it would be to remove it afterwords:)
Why can't people use .deb?

---

### Post by JLNemisis on 2012-06-22
> **Steven D said:**
> Try this: 
[http://addons.teamspeak.com/directory/tools/miscellaneous/Teamspeak-3-Linux-GUI-Installer.html](http://addons.teamspeak.com/directory/tools/miscellaneous/Teamspeak-3-Linux-GUI-Installer.html)

[SIZE=1]This is mainly for the people looking for help on this later.[/SIZE]

The above link, provided by Steven D [SIZE=1](thank you)[/SIZE] takes you to the TS3 addons directory information for the GUI based installation application. There you can read about what the GUI installer does.   While your reading you will need to *COPY*   the websites non-functioning link information found in the description of the installer. 
[SIZE=1](NOTE:  The download button there is for the *readme* file.  Which contains some information on installation )[/SIZE]
Next:
*PASTE* the address into the address bar of your browser.
You will be taken to the Source forge website with a download button for the 32 bit version and another link under the button called *browse all files.*
If your in need of the 64bit version.  You can select the link under the button[I].
[/I]This link will take you to all the files available for this program such as the 64bit version.

OR:
So you don't have to go through all that trouble to get what your looking for...
Here is a direct link to the GUI based installer files for _both_ [32bit or 64bit]("http://http://sourceforge.net/projects/ts3linuxinstall/files/") versions.

[http://sourceforge.net/projects/ts3linuxinstall/files/](http://sourceforge.net/projects/ts3linuxinstall/files/)


Or you can google all this for awhile.
I prefer yahoo, but this was my search term *"64bit teamspeak 3 linux gui installer files"*


Happy trails

---

