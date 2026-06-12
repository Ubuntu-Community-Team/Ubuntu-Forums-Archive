---
title: "Wine!"
date: 2006-01-29
forum: General Help
---

### Post by KhanArash on 2006-01-29
HOw do i run a program which is installed with "wine" in ubuntu?!

---

### Post by KhanArash on 2006-01-29
I have installed a program and when I try to open it, it says:

```
a@ubuntu:~$ wine /home/arash/VoipStunt/VoipStunt.exe
err:module:import_dll Library pdh.dll (which is needed by L"Z:\\home\\arash\\VoipStunt\\VoipStunt.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\arash\\VoipStunt\\VoipStunt.exe" failed, status c0000135
a@ubuntu:~$
```

---

### Post by KhanArash on 2006-01-29
Could someone please help?!

---

### Post by gatorbrit on 2006-01-29
[QUOTE=KhanArash]Could someone please help?![/QUOTE]

It depends a lot on what the program is that you are trying to run.  Many windows programs will not run in wine.   Check out [http://frankscorner.org/]("http://frankscorner.org/") for your particular app.

---

### Post by psomas on 2006-01-29
i just right click on the exe file and select open with wine...
i do that for programs already installed in windows(i 've mounted the windows partition) but it should work for you too...
maybe the program  cannot run with wine...
try another one and see if you get the same errors...

---

### Post by Kethinov on 2006-01-29
[QUOTE=KhanArash]HOw do i run a program which is installed with "wine" in ubuntu?![/QUOTE]

If you've already installed it and the installation was successful, WINE has dumped the files in a special place.

Look for your program's folder in ~/.wine/drive_c/ or ~/.wine/drive_c/Program Files/

For example, when I want to play a Windows game called Continuum in WINE i simply run wine "~/.wine/drive_c/Program Files/Continuum/Continuum.exe" and it  launches.

---

### Post by dcstar on 2006-01-29
[QUOTE=KhanArash]I have installed a program and when I try to open it, it says:

```
a@ubuntu:~$ wine /home/arash/VoipStunt/VoipStunt.exe
err:module:import_dll Library pdh.dll (which is needed by L"Z:\\home\\arash\\VoipStunt\\VoipStunt.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\arash\\VoipStunt\\VoipStunt.exe" failed, status c0000135
a@ubuntu:~$
```[/QUOTE]
You should NOT run .exe Windows programs using Linux file paths.

You should run the program using the wine "C:" drive Windows file designation, so wine knows where to find the relevant libraries.

In your case, this should be something like:

wine "C:\Program Files\VoipStunt\VoipStunt.exe" (or whereever it actually got installed).

---

### Post by CameronCalver on 2006-01-29
wat is wine?

---

### Post by saubz on 2006-01-29
Wine is a program that runs in Linux and allows you to run some Windows applications.

[https://wiki.ubuntu.com/Wine]("https://wiki.ubuntu.com/Wine")

---

### Post by rudeboyskunk on 2006-01-29
here's a simple solution:

go to [www.transgaming.org](www.transgaming.org) and read their abouts there.  download cedega, it's only $5 a month.  i use it to play world of warcraft in linux.

---

### Post by qferret on 2006-01-29
Cedega...bah...waste of $$$

Compile the CVS if you must, but paying cash for the right to "vote" on what games get support and the ability to use the GUI frontend is insane. (grapevine is a free GUI frontend for it)

---

### Post by UphillSkier on 2006-01-29
[QUOTE=KhanArash]I have installed a program and when I try to open it, it says:

```
a@ubuntu:~$ wine /home/arash/VoipStunt/VoipStunt.exe
err:module:import_dll Library pdh.dll (which is needed by L"Z:\\home\\arash\\VoipStunt\\VoipStunt.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\arash\\VoipStunt\\VoipStunt.exe" failed, status c0000135
a@ubuntu:~$
```[/QUOTE]



I have just solved a similar problem (I hope).  You probably need to map the windows C:\ drive onto your ubuntu hard drive (probably /media/hda1).  Open a terminal,
do 
```

>winecfg
```

A window will open.  Choose the "Drives" tab.  Click on C:\.   Enter the path to the root of your windows partition in the path box (eg /media/hda1).  Press "Apply".  
Now launch your application from a terminal. For example

```
wine "c:\Program Files\quickenw\qw.exe" 
```


Hope this helps


Note added on editing:  Actually, I think you need double backlslashes if you give the full path - 

```
wine "c:\\Program Files\\quickenw\\qw.exe" 
```

I actually cd'd to the directory first.

```
cd /media/hda1/Program Files/quickenw
wine qw.exe
```

---

### Post by ivancruz on 2006-01-29
It's a Windows emulator:

[http://www.winehq.com/](http://www.winehq.com/)

---

### Post by BigMurph on 2006-01-29
Well... actually it's not an emulator...

***W***ine ***I***s ***N***ot an ***E***mulator

;)

---

### Post by pelle.k on 2006-01-30
If it's a dll you haven't got (for some reason not working, or not emulated through wine) , then download it: [http://dlldump.com/download-dll-files.php/dllfiles/P/pdh.dll/download.html](http://dlldump.com/download-dll-files.php/dllfiles/P/pdh.dll/download.html)
It shold be copied to /home/YOURNAME/.wine/drive_c/windows/system.
Using winecfg, add the word "pdh" to libraries section (press "add" too).

I've dumped all dll:s from my win98 SE cd, to that directory, as native dll:s often work better than the builtin (fake) dlls.

The reason you can't see the .wine folder in your home directory, is the punctuation before the folder name = hidden directory.

---

