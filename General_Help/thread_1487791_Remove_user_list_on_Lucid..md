---
title: "Remove user list on Lucid."
date: 2010-05-19
forum: General Help
---

### Post by anonymousturtle3 on 2010-05-19
I want to know if there is any way that one could remove the user list from the login screen requiring the user to type in their user name. I am not quite sure why this feature is not implemented and it is one of the very few things I don't like about Lucid but hopefully there is a fix for it.

---

### Post by dino99 on 2010-05-19
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

To remove:

sudo userdel -r <username>

---

### Post by 8Kuula on 2010-05-19
Just a hunch, but open gconf-editor and check does lucid have: /apps/gdm/simple-greeter/disable_user_list
(I do not have access to my ubuntu atm)

sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
if has then maybe this command would work, IT IS FOR KARMIC, but maybe works in lucid too.

source: [http://www.webupd8.org/2009/12/remove-user-list-from-ubuntu-karmic-gdm.html](http://www.webupd8.org/2009/12/remove-user-list-from-ubuntu-karmic-gdm.html)

---

### Post by revderek on 2010-08-13
DON'T use userdel unless you actually wish to delete a user from your machine. To stop the list of names (a pain in either a secure environment or when there are lots of users) follow this process:

Log out if you need to in order to reach the GDM login screen.
Go to a console screen (e.g. Ctrl-Alt-F1) and log in as someone entitled to use sudo.

Run "sudo -u gdm gconf-editor" in order to run gconf-editor as the gdm user. Go to the GDM login screen (Alt-F7 probably) and you will see the running instance of gconf-editor
navigate to apps - gdm - simple-greeter and tick the disable_user_list box
exit gconf-editor and return to the console (Ctrl-Alt-F1)
run the command "sudo /etc/init.d/gdm restart" to restart the logon screen

The new logon screen will appear. Go back to the console (Ctrl-Alt-F1) and log out. Alt-F7 to go to the logon screen and "voila".

:-)

8Kuula's method works, too, but I'm hesitant about editing when the manager is being used which is why I prefer to have GDM waiting for a logon (i.e. idle) and to work from a console, only personal bias, really.

---

### Post by RogerTX on 2010-10-10
Didn't seem to work... but most of the directories are owned by 'root' and not 'gdm' and are limited to owner-only access, so I'm not sure that the 'gdm' user can see the file I edited.

/root/.gconf is owned by 'root' and is 'rwx' to owner only
/root/.gconf/apps is owned by 'root' and is 'rwx' for owner only
/root/.gconf/apps/gdm is owned by 'root' and is 'rwx' for owner only
same for 'simple-greeter' and the %gconf.xml file.

Should any or all of these be owned by gdm or have different permissions?

---

### Post by jruberto on 2010-11-30
Have been looking into this for a while.

If you want a single user to disappear from the "simple greeter", just change their UID so it is less than 1000

[SIZE=2]**[FONT=Courier New][COLOR=Navy]sudo usermod -u 999 johnsmith[/COLOR][/FONT]**[/SIZE]

If you want to disable the userlist altogether, there is a setting in the gnome config editor to disable_user_list but if you use the gconf-editor it doesn't seem to work.  issue the following command and it will work.  Don't ask me why the GUI editor doesn't work and the cmdline does, but that seems to be the case.

[COLOR=Navy]**[FONT=Courier New][SIZE=2]sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gdm/simple-greeter/disable_user_list true[/SIZE][/FONT]**[/COLOR]

---

