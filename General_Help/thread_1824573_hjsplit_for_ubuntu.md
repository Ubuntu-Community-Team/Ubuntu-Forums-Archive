---
title: "hjsplit for ubuntu"
date: 2011-08-14
forum: General Help
---

### Post by p3aul on 2011-08-14
Can someone please tell me how to install this thing? I downloaded the program forom the website. It is now a linux distro. I unpacked it as per instructions I double clicked on it to run it. dialog said couldn't execute it. No problem. I thought I just need to make it an executable. Right-clicked and selected properties =>permissions and checked the executable box. Clicked the file again. got the same message. Opened the terminal in the hjsplit folder Typed sudo chmod +x hjsplit This command gives no feedback so I assumed it worked. typed hjsplit at the terminal, Response: No such command. 

NOTE: I didn't need to type paths because the terminal was opened in the correct folder. A useful little utility I found on the net allows me to do this.

Please help
Thanks,
Paul

---

### Post by kyphi on 2011-08-14
1.  Download the file - most likely it will end up in your "Downloads" folder.
2.  Right click on the file and select "Extract here" which will untar and uncompress the package and create a folder in your Downloads folder.
3. In a terminal type ```
cd Downloads
``` (Enter) and then ```
./hjsplit
``` (Enter)

---

### Post by p3aul on 2011-08-14
Thanks, but here's what happened:

> p3aul@p3aul-Aspire-X3910:/media/Acer/HjSplit$ [COLOR=Red]./hjsplit[/COLOR]
bash: ./hjsplit: **[COLOR=DeepSkyBlue]Permission denied[/COLOR]**
p3aul@p3aul-Aspire-X3910:/media/Acer/HjSplit$ [COLOR=Red]sudo ./hjsplit[/COLOR]
[sudo] password for p3aul: 
sudo: ./hjsplit: [COLOR=SeaGreen]**command not found**[/COLOR]
p3aul@p3aul-Aspire-X3910:/media/Acer/HjSplit$ 
What does the "dot slash do anyway?
Thanks,
Paul

---

### Post by ofnuts on 2011-08-14
> **p3aul said:**
> Thanks, but here's what happened:

What does the "dot slash do anyway?
Thanks,
PaulYou have to make your file executable by turning the executable bit:
```

chmod +x hjsplit

```

If you use "hjsplit" without a path, the shell looks for an executable hjsplit in the PATH (and by default the PATH doesn't include the working directory). "./hjsplit" instructs it to run that very file so it doesn't search the PATH.

---

### Post by p3aul on 2011-08-14
> You have to make your file executable by turning the executable bit:

This was quoted from my first post

> Typed sudo chmod +x hjsplit This command gives no feedback so I assumed it worked.

> If you use "hjsplit" without a path, the shell looks for an executable  hjsplit in the PATH (and by default the PATH doesn't include the working  directory). "./hjsplit" instructs it to run that very file so it  doesn't search the PATH.     The dot slash should have worked because I was already in the directory I was trying to run hjsplit from. I use the bash script to do the same thing as the "Command Prompt Here" does in win7 so I don't have to type long path names. That just opens the way for typos to cause problemss.

Here is where I found my script: [http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/](http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/)

---

### Post by ofnuts on 2011-08-14
> **p3aul said:**
> This was quoted from my first post

The dot slash should have worked because I was already in the directory I was trying to run hjsplit from. I use the bash script to do the same thing as the "Command Prompt Here" does in win7 so I don't have to type long path names. That just opens the way for typos to cause problemss.

Here is where I found my script: [http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/](http://www.cyberciti.biz/faq/linux-gnome-open-terminal-shell-prompt-here/)

1) "permission denied" is what I get if I try to execute a script that isn't flagged as executable. To check yours is: 

 "ls -l hjsplit" and check for "x" flags (ie, should have "-rwxr-xr-x" and not "-rw-r--r--")

2) In Windows, the current directory is implicitly added to the path. In Unix, it's not, so you have to dot-slash any commands in the current directory, or add the current directory in your PATH. Better put your executables and little scripts  all in the same place  instead of having them in the "current directory", and add that  directory to the PATH. I use "~/bin".

3) If you know "command completion" you never have to type the names in full

4) At the risk of  starting a desktop war, FWIW the file explorer in KDE includes a shell window with a working directory synch'ed to the file display. Works wonders.

---

### Post by p3aul on 2011-08-14
Ok I tried it your way by cd /media/Acer/HjSplit I got the same prompt as when I opened the terminal window in the directory ie p3aul@p3aul-Aspire-X3910:/media/Acer/HjSplit$ It's the same thing I see no difference. In each case, the system is chmoding the file to an executable. 

That the whole I'm trying to make; The file is not being flagged as an executable. When I right click the file and select properties and try to check the box that says execute file as program, it just reverts back. However if I move the file to the home directory, it works just fine. Well in any case the program works and I don't care were it is.

UPDATE: With a little experimenting I found that the hjsplit will not work from any directory like it says. It will NOT work off any subdirectory of the media directory so I cant save it to any of the hard or removable drives, only off the home directory. I was able to change the permissions just fine when I put the file in several directories off the home directory.

---

### Post by ofnuts on 2011-08-14
> **p3aul said:**
> Ok I tried it your way by cd /media/Acer/HjSplit I got the same prompt as when I opened the terminal window in the directory ie p3aul@p3aul-Aspire-X3910:/media/Acer/HjSplit$ It's the same thing I see no difference. In each case, the system is chmoding the file to an executable. 

That the whole I'm trying to make; The file is not being flagged as an executable. When I right click the file and select properties and try to check the box that says execute file as program, it just reverts back. However if I move the file to the home directory, it works just fine. Well in any case the program works and I don't care were it is.

UPDATE: With a little experimenting I found that the hjsplit will not work from any directory like it says. It will NOT work off any subdirectory of the media directory so I cant save it to any of the hard or removable drives, only off the home directory. I was able to change the permissions just fine when I put the file in several directories off the home directory.
If the external media isn't using a Unix filesystem (FAT32, NTFS...) then it won't support the executable flag. However, there are usually mount options to handle this (use the "archive" flag as the "execute" flag, or report the "execute" flags as always set).

Also there is way to force bash to execute a script which is not executable: prefix it with a dot (but that only works for bash scripts, not binaries or other scripts (python, perl...). Note that this isolated dot is completely different from the "./"  prefix. Here it is just a shorthand for the "source" command. I.e.:
```
. hsjsplit {parameters}
```or```
source hsjsplit {parameters}
```

---

