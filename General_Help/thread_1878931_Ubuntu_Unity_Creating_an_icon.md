---
title: "Ubuntu Unity: Creating an icon"
date: 2011-11-10
forum: General Help
---

### Post by Jary316 on 2011-11-10
Hi everyone,

I am looking for a tutorial to create my own icon.

I have created a program (binary file) that I would like to run with an icon. I have an image for the icon and I know the location of the binary, but I do not know how I can create an icon that I could put in the Unity launch bar.

I am running Ubuntu 11.10 but cannot find any tutorial for creating an icon (my searches only found how to modify the look and feel or update the launch bar).

Could anyone please link me to a tutorial to do that, or tell me how to create an icon from the image and put in the location of the binary please?

Thank you very much!

---

### Post by MG&amp;TL on 2011-11-10
Well, the essence of it is you copy the image to /usr/share/icons/hicolor, then the right size, then the right category - for instance, /usr/share/icons/hicolor/24x24/apps/ for a 24x24px icon for an application.

Then you create a .desktop file:

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html")

And fill in the fields as appropriate, then copy to /usr/share/applications. You should now see the launcher etc. in the Unity dash, complete with icon. This should work in all desktops, not just Unity.

---

### Post by MG&amp;TL on 2011-11-10
Example:

```
[Desktop Entry]
Type=Application
Name=Myapp
Exec=/usr/bin/myapp
GenericName=
Comment=
Icon=<your icon's name, e.g myicon, NOT /usr/share/icons/etc.>
Terminal=False (if it doesn't need a terminal)
Categories=<categories here>
```

You could test this using a pre-made icon from usr/share/icons and a .desktop entry. Try making one for firefox to get the feel of things. It will appear as a shortcut straightaway, but if you copy it to /usr/share/applications it will show up in Unity.

---

### Post by Jary316 on 2011-11-10
> **MG&TL said:**
> Example:

```
[Desktop Entry]
Type=Application
Name=Myapp
GenericName=
Comment=
Icon=<your icon's name, e.g myicon, NOT /usr/share/icons/etc.>
Terminal=False (if it doesn't need a terminal)
Categories=<categories here>
```

You could test this using a pre-made icon from usr/share/icons and a .desktop entry. Try making one for firefox to get the feel of things. It will appear as a shortcut straightaway, but if you copy it to /usr/share/applications it will show up in Unity.

Woo, thanks a lot!!! You helped me a lot.

I've got the icon on the desktop, with it's correct image and it launches the correct binary, yay! I am not sure I used the right thing for Icon because you say it should be the name.

I have one question, using ~ does not seem to work, I have to replace it with /home/..., is it normal please?

Here is my file (which seems to work, I would wish I could replace /home/rudys with ~)

```

[Desktop Entry]
Type=Application
Name=Remote
Exec=/home/rudys/project/bin/Host/clientToDevice 192.168.0.119 3333
TryExec=/home/rudys/project/bin/Host/clientToDevice
Terminal=false
Icon=/home/rudys/project/remote.png
GenericName=Remote Control
Categories=Application

```

Please let me know if you see any error in my file. I haven't completely grasped the difference between TryExec and Exec. I thought TryExec was just the path, and Exec the actual binary name, but when I do have it cannot find the file.

Thanks a lot for your help.

---

### Post by Jary316 on 2011-11-10
I have been reading that .desktop files only support absolute path and not relative path for security concerns, which is why '~' did not work.

Would anyone please confirm if this information is right? I have not found any good workaround that problem, please let me know if you know one.

---

### Post by 3rdalbum on 2011-11-10
Rather than craft a .desktop file by hand, why not use the Main Menu (alacarte) program in Ubuntu? Open up the Dash and type 'main menu' and then click on the first search result that appears. Create a menu item, specifying the icon, name, and command (path to the file you want to run).

This icon will appear in the Installed Applications part of the Dash, or you can search for it of course. Drag its icon from the Dash to the Launcher to store it in the Launcher.

---

### Post by Jary316 on 2011-11-10
> **3rdalbum said:**
> Rather than craft a .desktop file by hand, why not use the Main Menu (alacarte) program in Ubuntu? Open up the Dash and type 'main menu' and then click on the first search result that appears. Create a menu item, specifying the icon, name, and command (path to the file you want to run).

This icon will appear in the Installed Applications part of the Dash, or you can search for it of course. Drag its icon from the Dash to the Launcher to store it in the Launcher.

The problem is that I am currently actually including the launcher (or .desktop) inside a folder part of the project. This folder is shared with other people (via svn), so I wanted them to be able to start the binary just by opening the .desktop file.

It works fine on my machine and I can put it in the dash, the problem is when it comes to sharing it with other people.

---

### Post by MG&amp;TL on 2011-11-11
Yeah, as I understand it, not all shells/implementation of linux use ~/ as a shortcut to /home/$USER, so absolute paths are safest. Although 'security concerns'-really? I'm not sure how you would hack anything via a .desktop?

Wow, 3rdalbum, I didn't know that was possible. Something new every day.

---

### Post by MG&amp;TL on 2011-11-11
Because you would usually only include .desktop files when you are distributing it, (i.e via a deb package), it kinda assumes that you won't be using your home folder, more likely something in your $PATH like /usr/bin/ in your case (I suspect).

And no, for the same reason as above (inconsistency across distros/shells) you need an absolute path even if it's in your $PATH.

To find stuff in your path, do:

```
echo $PATH
```

---

### Post by MG&amp;TL on 2011-11-11
> **Jary316 said:**
> Woo, thanks a lot!!! You helped me a lot.

 ...thing for Icon because you say it should be the name.



Please let me know if you see any error in my file. I haven't completely grasped the difference between TryExec and Exec. I thought TryExec was just the path, and Exec the actual binary name, but when I do have it cannot find the file.

Thanks a lot for your help.

No problem-I meant you only need the absolute path if you're *not* saving to anywhere with /usr/share/icons. Otherwise, normally you put it in /usr/share/icons, and just use the name.

Difference between exec and Tryexec-absolutely no idea. I assume 'tryexec' this, and if it works, do 'exec' this. I think it should be in the freedesktop spec link I gave.

---

### Post by Jary316 on 2011-11-11
> **MG&TL said:**
> No problem-I meant you only need the absolute path if you're *not* saving to anywhere with /usr/share/icons. Otherwise, normally you put it in /usr/share/icons, and just use the name.

Difference between exec and Tryexec-absolutely no idea. I assume 'tryexec' this, and if it works, do 'exec' this. I think it should be in the freedesktop spec link I gave.


Thanks a lot.

Yea it is in the link, but they say "Path to an executable file on disk used to determine if the program is actually installed. If the path is not an absolute path, the file is looked up in the $PATH environment variable. If the file is not present or if it is not executable, the entry may be ignored (not be used in menus, for example)." for TryExec. And for Exec: "Program to execute, possibly with arguments."

I tried just having the path in TryExec and the executable name for Exec but it doesn't work. I'll just keep the path for both. I feel like their explanations is incorrect or I don't understand it.

Quick question MG&TL, if you distributed an application but let the users compile it anywhere they want. You only know where it will be once in the root of your directory, ie:

User can put the folder anywhere, but they type "make" and it creates a "bin/" folder. This "bin" folder may not be part of their path. How would you make sure the .desktop entry always work (if the file were to be inside the root of your directory).

Is there anyway or this will not work because of absolute path?

I hope my question makes sense. I guess I'm trying to have an icon always pre-generated for a binary where I don't really know where it will be located, so maybe it's actually not doable as it could only rely on relative path.

Thank you.

---

### Post by MG&amp;TL on 2011-11-11
I think tryExec is a 'all-singing' Exec, but Exec is simpler and faster.

In your situation, what you would do is have the ```
make
``` rule as-is, (to compile into bin/) but then also a 

```
make install
``` rule to install the program into the right places. Where you CAN predict where they go. :)

Like so (roughly, in the makefile):

```

install: <files needed to install>
    install (see man install) files <places to go>
    install morefiles <moreplaces to go>
    install bin/myprog /usr/bin/
    install myicon /usr/share/icons/24x24/apps
    install myshortcut.desktop /usr/share/applications
``` 

I don't know much about makefiles, you might be better looking it up on the internet. Just google 'GNU make tutorial' and you should be laughing. *make* has loads of useful utilities like variable substitution. If you're distributing your package, consider making OS-specific packages like a .deb for ubuntu/debian/mint , an rpm for yum-based distros (fedora, red hat, CentOS, SUSE) and possible setup.exe or something for windows and a diskimage for mac? I can point you to the 'how-tos' for debian packaging:

[https://wiki.ubuntu.com/PackagingGuide/Complete]("https://wiki.ubuntu.com/PackagingGuide/Complete")

I hope this helps.

---

### Post by Jary316 on 2011-11-12
> **MG&TL said:**
> I think tryExec is a 'all-singing' Exec, but Exec is simpler and faster.

In your situation, what you would do is have the ```
make
``` rule as-is, (to compile into bin/) but then also a 

```
make install
``` rule to install the program into the right places. Where you CAN predict where they go. :)

Like so (roughly, in the makefile):

```

install: <files needed to install>
    install (see man install) files <places to go>
    install morefiles <moreplaces to go>
    install bin/myprog /usr/bin/
    install myicon /usr/share/icons/24x24/apps
    install myshortcut.desktop /usr/share/applications
``` 

I don't know much about makefiles, you might be better looking it up on the internet. Just google 'GNU make tutorial' and you should be laughing. *make* has loads of useful utilities like variable substitution. If you're distributing your package, consider making OS-specific packages like a .deb for ubuntu/debian/mint , an rpm for yum-based distros (fedora, red hat, CentOS, SUSE) and possible setup.exe or something for windows and a diskimage for mac? I can point you to the 'how-tos' for debian packaging:

[https://wiki.ubuntu.com/PackagingGuide/Complete]("https://wiki.ubuntu.com/PackagingGuide/Complete")

I hope this helps.

Ok thanks a lot, I got it to work with a Makefile.

Thanks a lot! :)

---

### Post by MG&amp;TL on 2011-11-12
No problem, always happy to help if I can. I hope I saved you some time, you can imagine how long it took me to find that on my own.

---

