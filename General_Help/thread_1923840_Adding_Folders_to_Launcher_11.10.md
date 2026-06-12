---
title: "Adding Folders to Launcher 11.10"
date: 2012-02-11
forum: General Help
---

### Post by Bill Gates Foundation on 2012-02-11
Is there a way to add folders to the launcher?   i can only get programs to work.....

technically, i can add the folder icon to the launcher, but the icon does not work in dash or launcher.......

Nothing would happen when icon is clicker.

I opened up Main Menu in the dash, and edited icon to launch in terminal.....

the error i get is this, by using icon in the dash or launcher......
 
> [SIZE=3][B]There was an error creating the child process for this terminal

Failed to execute child process "file:///host/Documents0and0Settings/BAD/My0Documents " (No such file or directory)[/B][/SIZE]this is a folder of my documents on XP.......but i think any folder will give me this problem...


.I have also tried making a link to folder, and then adding link to launcher but that still does not work

:popcorn:

---

### Post by duanedesign on 2012-02-11
One option is to add the folder to the Home Folder in the Launcher. If you right-click on the Home Folder icon you open various folders and add your own.

Copy 'Home Folder' launcher file to your home directory:

```
mkdir ~/.local/share/applications
cp /usr/share/applications/nautilus-home.desktop ~/.local/share/applications
```

Open the file for editing in gedit:

```
gedit ~/.local/share/applications/nautilus-home.desktop

```

Delete the following line from the file:
```
OnlyShowIn=GNOME;

```

Add this text to the bottom of the file. change the 'Name' and the folder you wish to open. Place the folder name/path after nautilus in the 'Exec' line. In this example I am opening the bzr folder in my Home directory. When done save and close:

```
Name=bzr
Exec=nautilus bzr
TargetEnvironment=Unity
```

Log out and log in again to see the changes.

[Here are more quicklists]("http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available") you can add to the launcher.

---

### Post by Bill Gates Foundation on 2012-02-12
[IMG]http://i.stack.imgur.com/VZoxi.png[/IMG]


ok, i got that to work, but i tried to get My Documents from XP install in there......it does not appear.....

> [Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.0.0
X-Ubuntu-Gettext-Domain=nautilus

X-Ayatana-Desktop-Shortcuts=Videos;Documents;Music;Pictures;Downloads
[Videos Shortcut Group]
Name=Videos
Exec=nautilus Videos
TargetEnvironment=Unity

[Documents Shortcut Group]
Name=Documents
Exec=nautilus Documents
TargetEnvironment=Unity

[Music Shortcut Group]
Name=Music
Exec=nautilus Music
TargetEnvironment=Unity

[Pictures Shortcut Group]
Name=Pictures
Exec=nautilus Pictures
TargetEnvironment=Unity

[Downloads Shortcut Group]
Name=Downloads
Exec=nautilus Downloads
TargetEnvironment=Unity
[COLOR=Red]
[My Documents Shortcut Group]
Name=My Documents
Exec=nautilus/host/Documents and Settings/BAD/My Documents
TargetEnvironment=Unity[/COLOR]
[COLOR=Red]
not working


edit:

working[COLOR=Black]
had to edit file and add "my documents"
[/COLOR][/COLOR]> X-Ayatana-Desktop-Shortcuts=Videos;Documents;Music;Pictures;Downloads;[COLOR=Red]My Documents[/COLOR]also i got a lot of errors.....after it appeared in task bar
> [COLOR=Red] Could not find "/home/bad/My."
Please check the spelling and try again.
.[/COLOR]All I had to do was, create a shortcut to my documents and I choose to put it in /home/{your computer name}/
I then renamed the folder to "My" becuase there error it gave me....(error was that [COLOR=Red]/home/bad/My Documents [COLOR=Black]is too long[/COLOR][/COLOR]!!!!!!!)

---

### Post by Bill Gates Foundation on 2012-02-12
works like a champ......


rename My Documents Link to My, (glitch if too long)

then put link in_   home/(computer name)/_

 > X-Ayatana-Desktop-Shortcuts=Videos;Documents;Music;Pictures;Downloads;MyDocuments

[MyDocuments Shortcut Group]
Name=MyDocuments
Exec=nautilus My Documents
TargetEnvironment=Unity
notes: make sure you have no spaces beofre or after "My" link  after you change the name from "My Documents".......example: " My " is  incorrect, "My" is correct........

---

### Post by yetiman64 on 2012-02-12
The name (title) "My Documents" should be ok there, but to get the Exec= line to work try it as ```
Exec=nautilus file:///home/<yourusername>/My\ Documents
``` The exec line is what is failing because of the space in the Foldername,  the \ symbol in the code above is an escape sequence for the space in the path.

I tend to avoid using spaces in foldernames instead replacing them with a dash (-) to avoid this style of problem.

> (glitch if too long) no, just doesn't tolerate spaces in the path, typical of the terminal as well. You can retain the full folder title "My Documents" with the space if you use the escape sequence in the exec line, if you wish to.

Edit: just tested further and the escape sequence in the exec line allows nautilus to open the My Documents folder here from the Unity Launcher. The "X-Ayatana-Desktop-Shortcuts=" entry and the shortcut group ([My Documents Shortcut Group]) tolerate the space in them ok.

---

### Post by Bill Gates Foundation on 2012-02-12
ok....thanks........did not know the proper format......by the way, they way i had, would cause two folders to pop up when i click my doucments......


> 
Exec=nautilus My Documents
this causes documents, and my documents to open at the same time....

> 
Exec=nautilus My
fixed

---

### Post by yetiman64 on 2012-02-12
> **Bill Gates Foundation said:**
> Quote:
                                                 Exec=nautilus My Documents                      
The folder Documents already exists as a System provided user folder and if you created a folder "My" (? did you ?) then I would expect that command to try opening 2 folders both in your home folder (where the system defaults the terminal to.)

Try it just as 

```
Exec=nautilus My\ Documents
```and this should call only one folder. My previous post included the absolute path for "My Documents", I expect it should work from here, that is how you escape a space in a path in terminal. This should integrate your folder "My Documents" in your home folder.

Edit: checked and it works here.

---

