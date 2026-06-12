---
title: "Add an Executable Bit??"
date: 2011-01-28
forum: General Help
---

### Post by the wolfe on 2011-01-28
IS there a way to add to the list of executable bits in ubuntu? Right now it is my only OS, And I know that I must have at least 1 game that can be run via WINE, but all of the setup.exe files give a notice saying "The file '/media/VIETNAM /SoNow/Acrobat/Setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.". 
Thanks for the help.

---

### Post by J V on 2011-01-28
You obviously didn't read about the executable bit did you? I'm tempted to tell you to RTFM but I was once this bad too...

There is an executable bit on every file. It is either marked executable or not. Just right click the file go to properties > permissions and check the executable button.

---

### Post by blueridgedog on 2011-01-28
Alternatively, type "man chmod" in a terminal and absorb.

---

### Post by the wolfe on 2011-01-28
i read it, it just didn't make sense to me. Not everyone is a comp genius. 

When right clicked it has several options. 
1. open with wine windows program loader
2. open with Archive Manager 
3. open folder 
4. move to trash 
5. save results as. 

NO properties tab. Id take a screen shot, But I have no clue how to.

---

### Post by linuxman94 on 2011-01-28
You can take a screenshot with the Print Screen button on the keyboard (sometimes labeled PrntScrn).  Another way to mark it as executable is to open a terminal (Applications -> Accessories -> Terminal) and change to the directory the file is in by using the cd command. like this:

```
cd /media/VIETNAM/SoNow/Acrobat/
```

Once in the directory, type this:
```
chmod +x Setup.exe
```

---

### Post by wojox on 2011-01-28
You need to copy the Acrobat folder into your /home/user directory. For security reasons you can't run executables from a CD.

---

### Post by the wolfe on 2011-01-28
seems that it won't let me screenshot with the right click menu open. 
I'm going to go try the terminal thing and will be back with success of to explain failure.

---

### Post by the wolfe on 2011-01-28
> **wojox said:**
> You need to copy the Acrobat folder into your /home/user directory. For security reasons you can't run executables from a CD.
DVD. And do I need to save the whole game disk to the /home/user directory or just the installer (the one I have been trying to use.)?

---

### Post by wojox on 2011-01-28
> **the wolfe said:**
> DVD. And do I need to save the whole game disk to the /home/user directory or just the installer (the one I have been trying to use.)?

Probably just the .exe

Don't know what exactally is in the Acrobat directory.

---

### Post by the wolfe on 2011-01-28
Its the Setup.exe folder.

---

### Post by the wolfe on 2011-01-28
It won't let me copy/move the folder. Says that I do not have write permissions for it.

---

### Post by wojox on 2011-01-28
> **the wolfe said:**
> Its the Setup.exe folder.


Do you want to play the game? I thought you were just trying to set up Adobe Acrobat.:P

---

### Post by the wolfe on 2011-01-28
Yes. I am trying to run the setup.exe under WINE so that I can play my video game.

---

### Post by wojox on 2011-01-28
Okay I just re-read your first post. Run in the terminal:

```
gksudo nautilus
```


Go to that directory and copy the whole folder over to your /home/user directory.

---

### Post by the wolfe on 2011-01-28
just the setup.exe?

---

### Post by wojox on 2011-01-28
> **the wolfe said:**
> just the setup.exe?

I would copy the whole folder holding the game('s). Vietnam?

---

### Post by the wolfe on 2011-01-28
ok. 
Its Conflict Vietnam. (COD based FPS)

---

### Post by mc4man on 2011-01-28
If the setup.exe is on a cdrom - then just browse to the .exe and
right click > open with - other application > use a custom command
For the command just enter this
wine

In the future there will be a new r. click option 'wine', use that instead of 'wine windows program loader' of any .exe and you'll never hear from the 'security bit' again

---

### Post by Vaphell on 2011-01-28
```
wine /media/VIETNAM/SoNow/Acrobat/Setup.exe
``` should work
executable bit enabled says 'hey, this is a program, run it' but when you call wine explicitly it doesn't matter because you say 'hey wine, take this and do something'

---

### Post by blueridgedog on 2011-01-29
> **wojox said:**
> You need to copy the Acrobat folder into your /home/user directory. For security reasons you can't run executables from a CD.

Is it something for security reasons or is it the fact that it is read only media and can't have the execute bit set?  I may have to burn something that is executable and test...

---

### Post by mc4man on 2011-01-29
> Is it something for security reasons...
For .exe's it's a by-product of a "security policy" of dubious value, .exe's don't need the x bit set

'Wine Windows Program Loader' uses wine.desktop that has 'cautious-launcher' in the Exec= command
'wine' just uses the binary which knows nothing of the cautious-launcher

---

### Post by the wolfe on 2011-02-01
OK, some success and Failure with the WINE exe. bit that You all were helping me with here. 
I have been trying to use games that I have that are older (~99-2003) because they don't need much in the way of hardware from the computer. Chances are that the WINE causes some processor loss in wine (most of the games read a 1.86 GHZ dual core Athlon II when it is 2.1GHZ, but still beats the 800 MHZ Athlon or P3 that they ask for). 
Anyway, I have successfully loaded 3 games under the wine loader, and been able to get into one of the games (one has an online bit from gamespy that needs to be solved when the ethernet is fixed) and one just freezes up the screen). The failure here is that the one that I can actively use is not putting out sound. I can get sound from DVD and CD, so there is not a hardware failure here. Just no sound from the game at all. 
is there anything that i need to do to WINE to get sound from the game?

---

### Post by bilallucky on 2011-02-01
Take a screenshot with the Print Screen button on the keyboard  (sometimes labeled PrntScrn).  Another way to mark it as executable is  to open a terminal (Applications -> Accessories -> Terminal) and  change to the directory the file

---

### Post by the wolfe on 2011-02-01
I have got the printscreen under control, and now know how to make the install.exe executable. 
I need to find a way to have sound output from WINE.

---

