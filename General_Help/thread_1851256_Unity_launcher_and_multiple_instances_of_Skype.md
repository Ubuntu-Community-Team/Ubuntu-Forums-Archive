---
title: "Unity launcher and multiple instances of Skype"
date: 2011-09-27
forum: General Help
---

### Post by jamesgthang on 2011-09-27
I had a problem in using Skype with the Unity Launcher in Ubuntu 11.04.  The bug is logged on launchpad as bug #667050. ([https://bugs.launchpad.net/unity/+bug/667050](https://bugs.launchpad.net/unity/+bug/667050) )

 
The  problem is that when you close Skype, the launcher doesn't remember  that the instance of Skype is still running.  When you try to click the  Skype icon again to bring up the contact list in the Unity Launcher, it  tries to start a whole new Skype instance and fails.


I found a workaround on the old Skype forums that may be helpful.
[http://forum.skype.com/index.php?showtopic=332401](http://forum.skype.com/index.php?showtopic=332401)

Here's what I did:

[LIST=1]
[*]downloaded the python script in that post (ensures that only a single instance of skype is started)
[*] copied the script to /usr/local/bin
[*] edit the "Main Menu" and added a new item called skype-single-instance in the network category
[LIST]
[*]   also used the same skype icon (/usr/share/icons/skype.png)
[/LIST]
[*] started the skype-single-instance from the dash
[*] when the icon showed up in the launcher I right-clicked and selected "keep in launcher"
[/LIST]
 
now  I can close the skype contacts window with ALT-F4 or the close button and if I want Skype back I can click on the skype-single-instance icon in the launcher.

---

### Post by jamesgthang on 2011-09-27
Also found a discussion on here about the skype-single-instance python script.
[http://ubuntuforums.org/showthread.php?t=1011348](http://ubuntuforums.org/showthread.php?t=1011348)

---

### Post by dockalek on 2012-02-25
I have the same problem, but I don't really know how to do what you suggest. Step 3 is a problem for me, and I would need some more detailed instructions to step 3. 
I moved the python file to usr/local/bin, can run it from there, but the multiple instances problem is still there. How do I create the new item in the "main menu"?

---

### Post by jamesgthang on 2012-02-28
Step 3 is really specific to 11.04 which allowed users to edit the menu items using the alacarte program.  Now in 11.10 that doesn't work.   Adding new items to the unity launcher is a bit more difficult now.  You can try to follow the instructions in the following link:

[http://www.uptechtalk.com/?p=135](http://www.uptechtalk.com/?p=135)

You need to create those .desktop text files in ~/.local/share/applications/ to add Unity launcher items.  

Here is what I have for my Skype Single Instance which is called alacate-made-14.desktop:
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=skype
Exec=skype-single-instance
Icon=skype
Name[en_US]=Skype Single Instance
Name=Skype Single Instance

```

I am not sure if the initial "#!/usr/bin/env xdg-open" is needed.  I have it in mine, but the link I reference above does not use it.  I believe that is only needed if you want to make the .desktop file executable and want to click on it like an icon on the desktop.

---

### Post by dockalek on 2012-02-29
Hi, and thank you.
I created the ".desktop" file with a copy of the code you sent. There was no folder applications in ~/.local/share/ so I had to create one. When I tried to run it with "nautilus ~/.local/share/applications/" it only opens the folder, and nothing else happens.

What is it supposed to do actually? Run the python file from usr/local/bin ?

I am not really sure whether all the lines are correct for my case, but I don't know what shall I change. I tried to rename the python file also to skype-single-instance.py but it didn't help.

I'm a bit lost as you can see.

---

### Post by baumanno on 2012-02-29
Try this:

in ~/.local/share/applications, create a file **skype.desktop**. The contents of this would be along the lines of

```

[Desktop Entry]
Version=1.0
Type=Application
Name=Skype
Comment=Skype Internet Telephony
Exec=<your-script>
Icon=skype
Path=
Terminal=false
StartupNotify=false

```

with <your-script> being either the path to your Python-script, or, if its in /usr/bin, just the scriptname. 

Any luck?

FYI, [http://www.nautilus-actions.org/?q=node/377]("http://www.nautilus-actions.org/?q=node/377") does a great job of listing all the options for .desktop-files...

---

### Post by jamesgthang on 2012-03-02
dockalek,

Just curious what version of python and skype are you using?
```

$ python --version
Python 2.7.2+
$ skype --version
Skype 2.2.0.35
Copyright (c) 2004-2011, Skype Limited

```Here is where my skype-single-instance python script is and the permissions on it:
```

$ ls -la /usr/local/bin/skype-single-instance 
-rwxr-xr-x 1 james james 492 2009-02-28 14:28 /usr/local/bin/skype-single-instance

```What happens when you go to a terminal and try to run the skype-single-instance python script from your home directory?  Dose the skype application open up?
```

$ pwd; skype-single-instance
/home/james

```

---

### Post by dockalek on 2012-03-13
Baumanno and Jamesgthang,
Thank you, it is solved for me now too, I am very happy about it. It was really more about me not knowing how to creat python or desktop files and how to run it, than that my case would be somehow more complicated. So I am not even sending the requested information to Jamesgthang, since it is solved already. I learned a lot how to work in ubuntu (I didnt know anything at all before) while trying to fix this issue. And started really enjoying it. Thanx to both of you.

---

