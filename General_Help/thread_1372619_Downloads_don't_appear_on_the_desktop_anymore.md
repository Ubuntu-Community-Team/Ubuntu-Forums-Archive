---
title: "Downloads don't appear on the desktop anymore"
date: 2010-01-04
forum: General Help
---

### Post by dark_omega on 2010-01-04
I've been using Ubuntu 9.04 for a few months now after switching over from XP. I've figured most issues I've had via Google, but this problem is stumping me.

I guess about a week ago, everything I download whether it be from Firefox Or Transmissions won't show up on the desktop screen. When I few the folder in Nautilus, same thing. I can see the files with the 'dir' terminal command. I did try using 'sudo' to lauch Nautilus and was able to see my files. If I drag them out of the Nautilus window and on to my desktop, they appear.

Keep in mind, I know the files are in MY directory and are owned by me. Any clue to what is causing this and how to fix it?

Thanks.

---

### Post by jamesisin on 2010-01-04
What is the output from ls -a /home/[insert your user name]/Desktop ?

---

### Post by LuisGMarine on 2010-01-04
Also where exactly are you telling Firefox (which is the browser you must be using) to save all your files?

Check in Firefox by going to Edit > Preferences.  In the Main Tab, down at the bottom there is a section called Downloads.  If you have a tick next to "Save Files to" change it if its some directory other than "Desktop"

---

### Post by dark_omega on 2010-01-04
Desktop is my download folder in Firefox. When I run that command, all the files show up in the list. However, their icons don't show up on my desktop nor in the Nautilus view UNLESS the sudo command is used first.

---

### Post by mbeach on 2010-01-04
just a shot in the dark here, but if you run gconf-editor and navigate to apps > nautilus > preferences, what is your "show_desktop" option status (checked or unchecked)?

to run gconf-editor, either open a terminal and type "gconf-editor" or use Alt+F2 then type "gconf-editor".

---

### Post by jamesisin on 2010-01-04
Mbeach probably has this one.  If that doesn't work, then please post the output of ls -a as above so I can see your terminal output (cd into the Desktop and run the command).

---

### Post by a2z on 2010-01-04
I had this problem once. 


I would just open a terminal and type ls and then press enter.

This will show you the files you can't see. Because it's a different desktop a system desktop I guess. 

Then you can transfer copy/move your files from there to your visible Desktop. Look in Ubuntu help menu for commands to move files. 
It's really easy, If I can do it anybody can ;)

I wonder how many people actually see the life preserver up there:lolflag:

PS: keep in mind  a2z@a2z-desktop:~$ = system desktop
           while  a2z@a2z-desktop:~/Desktop = Your visible desktop

---

### Post by dark_omega on 2010-01-04
The option is checked.

I know all about moving the files. What I want to know is how to keep from having to do that. I know the commands, I took a Unix class in College. Besides, I've used DOS for years, similar commands.

As I said, I don't want to have to keep doing all that, if there is a way to fix the problem.

---

### Post by jamesisin on 2010-01-04
Look, in asking for the output from ls -a I am trying to determine if your working directory (pwd) is the same as the /home/[username]/Desktop directory you ought to be seeing under all your applications.  Can you help me help you?

---

### Post by dark_omega on 2010-01-04
Here is the output.
```
ryan@Nix_BoX_1:~/Desktop$ ls -a
.
..
100K3200
clk.htm
DARK WATERS
DEAD SILENCE
eBayISAPI.dll
Family.Guy.Blue.Harvest.2007.DVDRIP.Xvid.JUGGALOTUS420.avi
Family Guy - Something something something Darkside - XviD-Reward - A UKB Release
fdsrepair_files
fdsrepair.html
firefox.desktop
JBidwatcher-2.1pre5(2).jar
JBidwatcher-2.1pre5.jar
linux-wbfs-manager
Mega Man 9.wad
Michael Jackson This Is It (2009) DVDRip XviD-MAXSPEED
New_Super_Mario_Bros_Wii_req.ios.truncha_FiX_Wii-iND
open_emulation.iso
pidgin.desktop
Roms
Saves
snes9x.cfg
snes9x.exe
Snes9XW.dll
Start Apache.desktop
Tengen_Toppa_Gurren_Lagann_1-27-HD
ubuntulogo.png
Valid.Ext
Witchboard.1986.Tawny.Kitaen.DivX.DvdRip.NightSongz
ryan@Nix_BoX_1:~/Desktop$ 

```

The jar files don't appear on my desktop screen. Anything new I save to the directory never shows up except in directory lists.

---

### Post by jamesisin on 2010-01-04
What is the output of pwd also, please?

---

### Post by dark_omega on 2010-01-04
```
ryan@Nix_BoX_1:~$ cd Desktop
ryan@Nix_BoX_1:~/Desktop$ pwd
/home/ryan/Desktop
ryan@Nix_BoX_1:~/Desktop$ 


```

---

### Post by jamesisin on 2010-01-04
Well, Mr. Dark, you have a very interesting problem here.  I am not able to get my system be behave as you have described without doing what mbeach suggested above.  You might try unchecking and then rechecking the box to see if that will reset yours, though I am less convinced this is the source of the problem.

Do you have any other clues that might help?  Is this the only user account?  Can you create another account to see how it behaves?

---

### Post by jamesisin on 2010-01-04
I did have one other thought.  Is it possible that your application is saving the new files outside of the borders of your screen size?  You could test this, possibly, by altering your screen resolution to see if the other files are beyond the borders.  This would explain why you can drop them from the Desktop folder onto a visible location of the Desktop and have them show up.

---

### Post by mechro on 2010-01-04
By any chance, have you got "desktop_is_home_dir" checked in nautilus's gconf?

---

### Post by dark_omega on 2010-01-04
Well it appears to be working now. After I unchecked/rechecked the 'show_desktop' nothing showed up, no matter what I did. So I restarted and now things seem to be working.

Thanks for all the help.

---

### Post by jamesisin on 2010-01-04
Quirky.  Glad to hear it's functional for now.

---

### Post by mbeach on 2010-01-05
> **dark_omega said:**
> Well it appears to be working now. After I unchecked/rechecked the 'show_desktop' nothing showed up, no matter what I did. So I restarted and now things seem to be working.

Thanks for all the help.

Glad you got it sorted out even if it is not quite apparent as to what was causing the issue in the first place. I would suspect a restart of the gdm would would accomplish whatever happened during your restart (in case it happens again, and you don't want to restart).

```

sudo /etc/init.d/gdm restart

```

---

### Post by mbeach on 2010-01-05
> **dark_omega said:**
> I did try using 'sudo' to lauch Nautilus and was able to see my files

I wonder if you are seeing the same behaviour as described in the thread linked below - that user seems to be saying that if Nautilus is started with gksu then the root session is not released (ie even after closing Nautilus, you maintain admin access). If running nautilus with admin privileges is something you need to do, see the specific post linked for another gconf setting which may be of interest.

[http://ubuntuforums.org/showthread.php?p=8612956#post8612956](http://ubuntuforums.org/showthread.php?p=8612956#post8612956)

---

