---
title: "wheres my program"
date: 2011-06-15
forum: General Help
---

### Post by david.mann8 on 2011-06-15
Ive installed a windows cd rom, using crossover. It hasnt put a shortcut on desktop, and i cant find it anywhere else, not even under crossover tab. please help.. thanks

It seems my problem with the program i want to use needs a newer version of wine, meaning i need to remove the old one first, this is im stuck already. Info tells me to 

          
"Before installing Wine from source, make sure you uninstall any Wine            binary packages you may have on your system.  Installing from source            requires use of the terminal window as well as a full copy of the            Wine source code.  Once having downloaded the source from Git or            extracted it from an archive, navigate to it using the terminal and            then follow the remaining steps". 



Im no good using terminal window, any basic help would be very much appreciated


****

---

### Post by inameiname on 2011-06-15
Have you tried the /home/(your username)/.wine/drive_c folder? I know that's where all Windows programs I install go. I use Wine, not Crossover, but I think Crossover's does the same thing, IDK. Once you find the one you want there, just create a desktop shortcut to it, and voila.

---

### Post by david.mann8 on 2011-06-15
Thankyou very much for you reply.Please forgive my absolute ignorance...Is that a command or a list of drop down menus?

---

### Post by inameiname on 2011-06-15
First, ignore this:

"Before installing Wine from source, make sure you uninstall any Wine             binary packages you may have on your system.  Installing from  source            requires use of the terminal window as well as a full  copy of the            Wine source code.  Once having downloaded the  source from Git or            extracted it from an archive, navigate to  it using the terminal and            then follow the remaining steps". 

No need to build Wine from source. 


What I was talking about in my last post was just the folder where all applications are housed inside Linux. So just as you would in Windows, go to the file explorer, Nautilus in this case, and find: /home/(Your_Username)/.wine/drive_c. Not a terminal command. Inside the 'drive_c' folder it'll look famililar, much like a C:/ folder in Windows. See if the folder you want is there, and if so, see if the particular 'exe' file to run it is there (same as Windows).


And if it does turn out that you need a newer Wine, just install/upgrade it using a repository. For that, it'd be easiest to install it in the terminal. Just open a terminal window, found under the Main Menu > Accessories > Terminal, and copy/paste the following:

*sudo add-**apt*-*repository ppa:ubuntu-wine*/ppa[I]
sudo apt-get update
sudo apt-get install wine1.3

From what I recall, it'll automatically remove the older version of Wine and install this one for you.
[/I]

---

### Post by grahammechanical on 2011-06-15
I had a similar problem. The icon for my Windows program that I was running under Wine was in the list of installed programs in the Dash but not on the desktop and I could not transfer it on the Launcher. The Wine icon would appear there instead of the program icon and the link to the Windows program was broken. The solution?

I logged-in into Ubuntu Classic and installed the program from CD using wine. An icon was placed on the desktop which was still there when I logged-in into Unity. And it was now possible to place the icon in the Launcher and fix it there using Keep in Launcher when you right click the icon.

Regards.

---

### Post by david.mann8 on 2011-06-15
thanks again. im running the commands for updated wine as one of my programs only runs with it...
now showing
Setting up ttf-umefont (411-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
david@david-desktop:~$ 

Is that waiting for me?

Im very sorry to say that i still dont understand your instructions for finding installed software. I dont recognise nautilis that you mentioned, i have a search file tab but that didnt come up with any results. Im very sorry for my stupidity as im sure youve already made it easy to understand

---

### Post by inameiname on 2011-06-15
No worries. 

It looks like it installed correctly. Not waiting; done. Does it still ask you to upgrade Wine for whatever program is was that wanted that when you try to install it?

And as for finding the folder, did you first open Nautilus, the file browser. You can open it by double clicking your home folder on the desktop. Then you can either enter "/home/INSERT_YOUR_USERNAME_HERE/.wine/drive_c" into the field like you would in Windows, and click enter.....OR....on the left side of the screen where there are all of those shortcuts to folders, just click 'File System', and then inside the normal folder section on the right double click: "home" => "INSERT_YOUR_USERNAME" => ".wine" => "drive_c"


Finally, if that doesn't work out for you, another way is to open that folder directly through the terminal. Open a terminal window just as you did uprading Wine, and then enter:

nautilus /home/me/.wine/drive_c

---

### Post by david.mann8 on 2011-06-15
thanks for your help. Installing newer version of wine has brought up a new tab where i can see installed programs.

All the best

---

### Post by inameiname on 2011-06-15
Glad you got it sorted.

---

