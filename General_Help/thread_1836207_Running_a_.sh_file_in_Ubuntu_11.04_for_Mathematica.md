---
title: "Running a .sh file in Ubuntu 11.04 for Mathematica 8"
date: 2011-08-30
forum: General Help
---

### Post by pederbruusgaard on 2011-08-30
Hi,
I'm trying to install Mathematica 8, and downloaded it from their websites.
However, when I try to open the file I downloaded (which is named home/peder/Downloads/Mathematica_8.0.1_LINUX.sh) I get an error saying this: "gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

I'm running Ubuntu 11.04. Does anyone know how to get this to work?

Thanks!

---

### Post by decoherence on 2011-08-30
> **pederbruusgaard said:**
> Hi,
I'm trying to install Mathematica 8, and downloaded it from their websites.
However, when I try to open the file I downloaded (which is named home/peder/Downloads/Mathematica_8.0.1_LINUX.sh) I get an error saying this: "gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

I'm running Ubuntu 11.04. Does anyone know how to get this to work?

Thanks!

I assume you're trying to run it from the GUI? I seem to recall it's supposed to give you a choice between running it in a terminal or viewing it but for some reason, you computer is assuming you want to view it (gedit is a text editor)

A sure-fire way to run it is with the terminal. Try the following command
```

sh /home/peder/Downloads/Mathematica_8.0.1_LINUX.sh
```

you may have to preface the command with 'sudo' and type in your password if it complains about permissions or generally doesn't work.

---

### Post by pederbruusgaard on 2011-08-30
> **decoherence said:**
> I assume you're trying to run it from the GUI? I seem to recall it's supposed to give you a choice between running it in a terminal or viewing it but for some reason, you computer is assuming you want to view it (gedit is a text editor)

A sure-fire way to run it is with the terminal. Try the following command
```

sh /home/peder/Downloads/Mathematica_8.0.1_LINUX.sh
```

you may have to preface the command with 'sudo' and type in your password if it complains about permissions or generally doesn't work.

Man, that was quick! Thanks! Seems to work now! :)

---

### Post by pederbruusgaard on 2011-08-30
So, the installing worked perfectly as far as I can tell. Now there's another, slightly different issue (I guess you can tell now I'm new to Ubuntu :) )

The only way I know so far to open Mathematica is to go through all the folders (usr/local/Wolfram/Mathematica/8/Executables/Mathematica), which seems like a kinda tedious way of opening an application. So I was wondering if there's a way to make it look like all the other applications in my "dock"?

Also, when I open it the way I described above, in the top bar it doesn't say "Mathematica", only "Untitled 1", unlike my other applications. The same goes for the dock, where there's just a question mark with the name "Panel" or something.

Again, I'm all new to Ubuntu, so I'm sorry if this is a completely retarded question.

Thanks!

---

### Post by decoherence on 2011-08-30
Actually, that's a great question! I could've told you how to do this with an older version of Ubuntu, but I don't know if the process has changed now that they're using Unity.

If you right-click on the desktop, do you get a menu that says "Create Launcher" or something similar? If so, that's what you want. There should be a text field where you put in the command to execute. Put in

/usr/local/Wolfram/Mathematica/8/Executables/Mathematica

I think what you put in the other text fields is up to you. Keep in mind, I'm going by memory here as I don't have a running Ubuntu system at my disposal right now.

---

### Post by asomad on 2011-08-30
hey guys. thanks for the info. I'm actually (going to be) in the process of installing a .sh file later..

Another way to install .sh files from what I've read, (via the GUI i.e. gnome/kde) you right click on the .sh file, and change the properties to make it executable. then double click the .sh file and it should install. And @decohearence, good stuff. I not too long ago did not know how to make a launcher, I know the feeling.

about that launcher. In ubuntu there is a choice weather you want to run an application or command. YOU sir want to choose APPLICATION

Be well gentlemen.

---

### Post by pederbruusgaard on 2011-08-31
> **decoherence said:**
> Actually, that's a great question! I could've told you how to do this with an older version of Ubuntu, but I don't know if the process has changed now that they're using Unity.

If you right-click on the desktop, do you get a menu that says "Create Launcher" or something similar? If so, that's what you want. There should be a text field where you put in the command to execute. Put in

/usr/local/Wolfram/Mathematica/8/Executables/Mathematica

I think what you put in the other text fields is up to you. Keep in mind, I'm going by memory here as I don't have a running Ubuntu system at my disposal right now.

Launchers are still here in 11.04, and they work perfectly! :) Thank you so much!

The only thing I'm struggling with now (which is really a minor issue) is that the icon I found on the internet and set as the launcher's icon changes to one of the pre-made icons when I place the launcher in the dock. There are like 50 or so pre-made, but I thought it would be nice to have the real ones, and they work on the desktop but not in the dock. Kinda strange, but no big deal, I guess.

Again, thanks for the help! :)

---

### Post by decoherence on 2011-09-01
> **pederbruusgaard said:**
> ...they work on the desktop but not in the dock. Kinda strange, but no big deal, I guess.

That is kinda strange. I would call that a bug. Perhaps the Unity dock only looks in specific locations for icons? But ideal behavior would be having consistent icons between the desktop and the dock.

Anyway, glad I could be of some help. :)

---

### Post by pederbruusgaard on 2011-09-02
> **decoherence said:**
> That is kinda strange. I would call that a bug. Perhaps the Unity dock only looks in specific locations for icons? But ideal behavior would be having consistent icons between the desktop and the dock.

Anyway, glad I could be of some help. :)

Yeah, I thought that might be it, so I found the folder, but I'm not allowed to put stuff there. I tried to move it there using terminal and the mv command, and thought about using sudo, but I didn't get that far. It says:

```
peder@peder-ThinkPad-X220:~$ mv ~/Downloads/M8 usr/shared/icons/hicolor/scalable/apps
mv: cannot stat `/home/peder/Downloads/M8': No such file or directory
```

Is that the correct way to use the command (I guess not, since it's not working :) )?

---

### Post by decoherence on 2011-09-06
A couple of tips -- 

1. use cp rather than mv. If it's just an icon you're moving, you might as well copy it rather than move it in case M8 is expecting to find it in the original directory. Also, it looks like you were trying to move the entire M8 directory. Just copy the icon file (wherever that is)

2. use tab completion. Type in part of the path to the file, then hit 'tab' which will complete as much of the path as possible, then give it another 'hint' by typing whatever letter it is missing, press tab again (twice) and repeat until you have the entire path. It's kinda hard to explain so just experiment with the technique. Once have a feel for how it works, you can use it to combine the function of the basic 'ls' command with whatever other command you are running. It also prevents typos.

3. in your command you have "usr/shared/icons/hicolor/scalable/apps" which I doubt exists. You want "/usr/shared/icons/hicolor/scalable/apps" -- note the leading forward slash. Paths that start with a leading slash are absolute. They describe the location of something relative to the root directory (that initial "/"). If you leave out the first forward slash, the path described is relative to the current working directory. 

For instance, if you opened up a terminal and immediately typed "cd usr/shared/icons/hicolor/scalable/apps" the shell would try to change directory to /home/peder/usr/shared/icons/hicolor/scalable/apps (/home/peder is your working directory when you first open a shell) which probably doesn't exist. Put in the leading forward slash to indicate the path is relative to the root directory (aka "/") and you'll get where you want.

I can't be more specific than that without actually having the mathematica package to examine. I hope this helps.

---

### Post by mooto85 on 2011-09-07
Hi guys,

I tried to use the sh Mathematica_8.0.1_LINUX.sh command and I get the following:

Mathematica Secured 8.0.1 for LINUX Installer Archive

Verifying archive integrity.
Extracting installer................
Extraction failed. No space left on .1797
Removing temporary files.

What can I do? I definitively have enough hard drive space...
Any help would be appreciated.

---

### Post by tom67 on 2011-12-09
answer to problem of mooto85:

Hi,
I've run into the same problem with 'no space left' during extraction a while ago. 
Then I copied the installer file from usb stick to HDD and retried installation. Passed well. 
Hope to help someone (just don't panic).
Tomas

---

