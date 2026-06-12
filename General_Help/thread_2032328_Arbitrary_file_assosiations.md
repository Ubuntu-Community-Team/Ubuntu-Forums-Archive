---
title: "Arbitrary file assosiations"
date: 2012-07-23
forum: General Help
---

### Post by kill o matic on 2012-07-23
Is there a way to associate file types to applications other than through the nautilus menu, since it's not a complete list and all the wine applications are named "program files"?

---

### Post by papibe on 2012-07-23
Hi kill o matic.

On Nautilus:
```
Right click -> Open with -> Other Application...
```
A new window will open with lots of applications. If you don't see the one you want, expand (+) 'Use custom command' to write the path to the app you want.

Hope it helps, and let us know how it goes.
Regards.

---

### Post by kill o matic on 2012-07-23
I'm not seeing a 'Use custom command' anywhere.

---

### Post by kill o matic on 2012-07-24
Does anyone know how to make wine applications show up in the Open With... menu with the proper name and icon? It's kind of hard to tell them  apart when they are all called "program files" with a wine glass icon.

---

### Post by oldos2er on 2012-07-24
Post merged. Please keep to one thread per question, it's less confusing for you as well as those trying to help you.

---

### Post by Morbius1 on 2012-07-24
The "use custom command" option was removed in Nautilus because it was a feature, therefore declared a bug, and hence removed.

For that kind of advanced functionality you need to install the Thunar filemanager from Xubuntu:
```
sudo apt-get install thunar
```Once set by Thunar it will work everywhere.

---

### Post by kill o matic on 2012-07-24
> **oldos2er said:**
> Post merged. Please keep to one thread per question, it's less confusing for you as well as those trying to help you.

Sorry, wouldn't have started a new thread if I knew about the other one.

Anyhow, the 'Use custom command' has disappeared from the recent releases, which kind of baffles me, since I thought Linux was all about easy customization, but whatever. The other thread says to add more applications to the list I now have to find their .desktop files and add '%f' to the end of the 'Exec=' line. And while that does make them show up in the list, the wine apps give me errors saying they can't find the file or just open with no file loaded. They don't get added to the context menu afterwards either. Their execution commands are a lot more complex, so they probably need a different approach.

---

### Post by kill o matic on 2012-07-24
> **Morbius1 said:**
> The "use custom command" option was removed in Nautilus because it was a feature, therefore declared a bug, and hence removed.

For that kind of advanced functionality you need to install the Thunar filemanager from Xubuntu:
```
sudo apt-get install thunar
```Once set by Thunar it will work everywhere.

That command doesn't seems to accept exe files, so still no wine apps. :(

---

### Post by Morbius1 on 2012-07-24
> **kill o matic said:**
> That command doesn't seems to accept exe files, so still no wine apps. :(
I don't know what you're saying. 

** Install thunar with the command I gave you.
** Once installed open thunar and right click on a *.exe file
** Select "Open With" > "Open with Other Application"
[COLOR=Black]** At the bottom you will see "Use a custom command"

Type in whatever command starts wine - i would guess it's just:
[/COLOR]```
wine
```[COLOR=Black]
Then when you double click something.exe in Thunar or Nautilus it will run: wine something.exe
[/COLOR]

---

### Post by LewisTM on 2012-07-24
If you want certain files to open in a windows application by clicking on them, the best way is to create a script. For example I want Adobe Flash project files (*.fla) to open in Adobe's Flash editor if I double click it.

You can for example create a file using this terminal command. 
```
gedit ~/.wine/Flash\ 8
```
Now paste the following example script in it, save and close gedit.

Example script:

```
 #!/bin/sh

QUICKPARLOCATION="c:\\Program Files\\Macromedia\\Flash 8\\Flash.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0
```

The wine program location can also be in the format [FONT="Courier New"]"/home/user/.wine/drive_c/Program\ Files\Macromedia\ Flash 8\ Flash.exe"[/FONT]

Make sure the file is executable with this command.
```
chmod +x ~/.wine/Flash\ 8
```
After you completed this go to an *.fla file in Thunar, right click it, go to “Open with other application”, click "Use Custom Command", add this command
```
/home/<yourusername>/.wine/Flash 8
```
Now if everything went ok, you can launch the file and it will be openend in Flash 8.

Adapted from [https://help.ubuntu.com/community/Wine#To_start.2BAC8-run_Windows_programs_using_Wine](https://help.ubuntu.com/community/Wine#To_start.2BAC8-run_Windows_programs_using_Wine)

---

### Post by kill o matic on 2012-07-24
I don't want to open .exe files with wine (why would I need to change associations for that), I want to open files with wine apps directly in nautilus, like say PDFs with Adobe Reader.[COLOR=Black]

I was mistaken about the command not accepting windows binaries, rather it doesn't understand the concept of spaces so it chucks out any part of the filepath after one. This is a problem for all wine applications, because they reside in a folder called "Program Files (x86)".

Anyhow, when you rename everything without spaces it does launch [/COLOR]Adobe Reader, but it still has the same problem as the nautilus workaround - it gives an error saying "There was an error opening this document. This file cannot be found." and it doesn't remember the file association afterwards.

Also, unrelated, but any time I run [COLOR=Black]Thunar, it hangs for a good minute, keeping one CPU thread at a 100% before it starts responding.

Edit: I really shouldn't start replying then stop for 30 minutes to try something before posting. Gonna try to figure out [/COLOR][]("http://ubuntuforums.org/member.php?u=680986")LewisTM's suggestion now.

---

### Post by kill o matic on 2012-07-24
All right, the scripts do work and the association even remain after uninstalling [COLOR=Black]Thunar. Just had to make sure there were no spaces in their names/paths and that the always use this application box was checked, otherwise it doesn't stick (you can change it later in nautilus from the file properties). Also, when the applications are started this way they seem to show a blank spot where the launcher wine icon should be, but that's hardly worth complaining about.

Still, having to install a separate file manager just for this is a rather ridiculous workaround. If this isn't going to be properly supported, we need a third-party tool that can easily add (and remove, since [/COLOR][COLOR=Black]there are [/COLOR][COLOR=Black]a lot of duplicates [/COLOR][COLOR=Black]for some reason) items from the full "open with" list.[/COLOR]

---

### Post by LewisTM on 2012-07-24
The scripts should support spaces without modification, did you try it?

I fully agree with you, we need a GUI for editing file associations. I find myself in the reverse situation: I use Thunar routinely but need Nautilus if I want to **delete** associations.

Cheers!

---

### Post by kill o matic on 2012-07-25
The path *in the script* can have all the spaces you like, but if the path *to the script *or the name has any the custom command interpreter will get confused. You may be able to get around it if you add backslashes before each space, but for some reason my keyboard interprets '\' as '<', so I have to copy the character from somewhere every time, which is a pain.

Now that I had time to think about it, there was really no need to use Thunar, just make a new .desktop file in ~/.local/share/applications/

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
NoDisplay=true
Exec=path to wine script **%f**
Name=whatever you want to see in the open with menu
```If you're going to write one script, might as well write two. That removes any limitations for the name and you can give them the proper icons by copying the "Icon=" line from the appropriate .desktop files in ~/.local/share/applications/wine to your new .desktop files. This of course makes me wonder why launching from the original .desktop files always displays the same wine icon, when they have the correct icon path? Probably a bug they'll fix eventually.

---

### Post by Morbius1 on 2012-07-25
Perhaps LewisTM can correct me on this but the difference with using Thunar is that it does 2 things:

** It creates the *.desktop file for you in ~/.local/share/applications/

** It updates the ~/.local/share/applications/mimeapps.list file. Just adding the desktop file doesn't do that.

---

### Post by LewisTM on 2012-07-25
> **Morbius1 said:**
> Perhaps LewisTM can correct me on this but the difference with using Thunar is that it does 2 things:

** It creates the *.desktop file for you in ~/.local/share/applications/

** It updates the ~/.local/share/applications/mimeapps.list file. Just adding the desktop file doesn't do that.
I guess both methods are imperfect, which is why a better tool would be welcome. Thunar will work well but will not
1) Allow to name the custom command
2) Assign an icon to it.
3) Remove (forget) associations

As for adding .desktop files to ~/.local/share/applications/ , it's non trivial which is why it wasn't my first recommendation. Once the launcher is present, Nautilus can detect it and you're good to go.

In the wine-related .desktop files located in the applications directory, we most often see a command like 
```
wine start /ProgIDOpen <progid> %f 
```
In other words Wine launches the file with the associated Windows application, which is simpler than finding it yourself and converting all file names in a script. You can find the progids by launching ```
wine start regedit.exe
``` and going under HKEY_LOCAL_MACHINE\SOFTWARE\Classes\
So for example 
```
wine start /ProgIDopen txtfile logfile.log
```
will open the log file in Notepad.
Since .txt files are already associated with Notepad in Wine, this will do
```
wine start textfile.txt
```

---

### Post by kill o matic on 2012-07-25
> **Morbius1 said:**
> 
** It updates the ~/.local/share/applications/mimeapps.list file. Just adding the desktop file doesn't do that.

It's not like you need to do it manually though. The nautilus open with dialogue updates it for you. But yeah, need some kind of all-in-one solution, preferably one that works with wine programs too.

---

