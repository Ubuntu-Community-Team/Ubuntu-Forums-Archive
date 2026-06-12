---
title: "help installing client in wine"
date: 2009-07-06
forum: General Help
---

### Post by Stronze on 2009-07-06
client download page
[http://www.hyruleonline.net/downloads](http://www.hyruleonline.net/downloads)

im trying to get this game client to run in wine but for the life of me i cant figure it out.

im new to linux and ubuntu and im not very tech savy.
i did the how to on wine and win seems to work fine but i cant unzip the file into wine using wine but i used archive manger and unziped into wine but wine wont execute the .exe

i just quits with no message of why.

---

### Post by t0p on 2009-07-06
Try running the executable in a terminal. Like this:

```
wine /path/to/whatever.exe
```

That way, you'll be able to see the error message when it fails to run.

---

### Post by Stronze on 2009-07-06
stronze@stronze-laptop:~$ wine file system/home/stronze/.wine/dosdevices/c:/program files/Hyrule 1.6.6.5..exe

wine: could not load L"C:\\windows\\system32\\file.exe": Module not found
stronze@stronze-laptop:~$

---

### Post by t0p on 2009-07-06
I think that error means wine cannot find the executable you want it to run.  Are you sure the path is correct?  You typed:

```
wine file system/home/stronze/.wine/dosdevices/c:/program files/Hyrule 1.6.6.5..exe
```

and that doesn't look like a correct path to me.  I would have expected something like:

```
wine /home/stronze/.wine/dosdevices/c:/program\ files/Hyrule\ 1.6.6.5.exe
```

Please note, I'm not saying the path I suggested is correct.  But your path didn't begin with a "/", and it contained spaces.  In linux you need to escape spaces with a "\".

Try the path I suggested anyway - paste it into the terminal to avoid typos. If you can paste the file name here, we might be able to clarify.

---

### Post by Stronze on 2009-07-06
stronze@stronze-laptop:~$ wine /home/stronze/.wine/dosdevices/c:/program\ files/Hyrule\ 1.6.6.5.exe

err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\program files\\Hyrule 1.6.6.5.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program files\\Hyrule 1.6.6.5.exe" failed, status c0000135

stronze@stronze-laptop:~$

---

### Post by NoReflex on 2009-07-06
Hello!

Looks like it needs some runtime libraries (I think VB6 runtime libraries).
You can try and download the files from DLL Files ([http://www.dll-files.com/](http://www.dll-files.com/)) or you can use winetricks ([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)).

Good luck!

Best wishes,
NoReflex

---

### Post by t0p on 2009-07-06
> **Stronze said:**
> stronze@stronze-laptop:~$ wine /home/stronze/.wine/dosdevices/c:/program\ files/Hyrule\ 1.6.6.5.exe

err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\program files\\Hyrule 1.6.6.5.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program files\\Hyrule 1.6.6.5.exe" failed, status c0000135

stronze@stronze-laptop:~$

Okay, you're missing the .DLL file MSVBVM60.DLL.  I suggest you go to [www.dll-files.com](www.dll-files.com) and search for it.

---

### Post by Stronze on 2009-07-06
okay now im reading the client but the client pos this.

runtime error 339
component 'mswinsck.ocx' or one of its dependencies not correctly 
registered: a file missing or invalid

---

### Post by Stronze on 2009-07-06
i tried searching wine and cant figure it out

i tried downloading the ocx file and putting it in windows system32 it is no longer asking for this one but for 
richtx32.ocx

did the same with richtx32.ocx and client has loaded

hmm

i get far enough in client to enter account name and password but get another error (runtime error 432) but it has no description

---

### Post by Jebtrix on 2009-07-06
Download and put mswinsck.ocx in the system32 folder (/home/<yourusername>/.wine/dosdevices/c:/windows/system32)  and manually register it with regsvr32.exe like this:

```
~/.wine/dosdevices/c:/windows/system32/regsvr32.exe /i mswinsck.ocx
```

---

### Post by Jebtrix on 2009-07-06
Glad to hear it.

---

### Post by Stronze on 2009-07-06
stronze@stronze-laptop:~$ ~/.wine/dosdevices/c:/windows/system32/regsvr32.exe /i mswinsck.ocx

Successfully registered DLL mswinsck.ocx
DllInstall not implemented in DLL mswinsck.ocx

stronze@stronze-laptop:~$

okay i went back 
reclick - VB6run - MS Visual basic 6 runtime
clicked - vcrun6 - MS Visual C++ sp4

i no longer get the error BUT the server is down so i dont know if its fixed or cuz server is down i just cant get the error

---

### Post by Stronze on 2009-07-06
okay im trying to create a shortcut into start bar but i always gotta right click and tell it to open with wine.

it also wont give me that option to open the shortcut the same way.

is there a way i can auto set it to open with wine including a shortcut?

GRRR server back up and still same error!!

okay from what i can google,
dao360.dll is what i need and putting it in system,system 32 and windows folder get me nothing.

hell i put it in all 3 at once and still get the same error.
i just cant find any solution and i feel lost.

---

### Post by Stronze on 2009-07-06
i tried a few more things and still nothing

---

### Post by Stronze on 2009-07-06
the solution for windows would hit start and use run [I]regsvr32.

i cant figure out how to do that in wine.
[/I]

---

