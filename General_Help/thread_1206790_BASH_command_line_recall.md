---
title: "BASH command line recall"
date: 2009-07-07
forum: General Help
---

### Post by Krupski on 2009-07-07
Hi all,

I know about BASH command line recall, control-r and all that... I am hoping to do something different.

In Windows XP, using JPSoft 4NT console mode command processor, I can use the tab key and up arrow / down arrow similarly to BASH, however there is one feature I would REALLY like to setup in BASH if I could.

Example: Let's say I typed these commands:

```

cd "Program Files\ImgBurn"
dir "z:\C_DRIVE\Program Files\WinImage"
dir f:\DOWNLOAD\nero* /od
**unzip f:\DOWNLOAD\Nero_8_All.zip**
cp f:\DOWNLOAD\nero_8_serial.txt
cd "Program Files\Nero"
dir templates /a /t /s /p

```

Now, let's say I wanted to re-execute the "unzip" line (bolded above).

I could just type "un" then hit up-arrow and any lines with "un" in them would be recalled (newest to oldest).

I know ctrl-r does *something* like this, but not anywhere near as nicely.

Is there any way to setup BASH like this?

And please, I'm looking for help. Posting links to "gnu.org" or saying "type man bash" are not what I'm looking for.

Thanks!

-- Roger

---

### Post by unutbu on 2009-07-07
```
!un
```
would execute the last command that begins with 'un'.

If you wish to see all commands that contain 'un', you could type Ctrl-r un then repeatedly tap Ctrl-r...

If you wish to list all the commands that start with 'un', you could run
```

grep '^un' ~/.bash_history
``` 

If that is too much typing, you could always package it into a script or bash function so the typing can be minimized.

> 
I know ctrl-r does *something* like this, but not anywhere near as nicely.

Maybe I don't understand what you are looking for...

---

### Post by Krupski on 2009-07-07
> **unutbu said:**
> ```
!un
```
would execute the last command that begins with 'un'.

If you wish to see all commands that contain 'un', you could type Ctrl-r un then repeatedly tap Ctrl-r...

If you wish to list all the commands that start with 'un', you could run
```

grep '^un' ~/.bash_history
``` 

If that is too much typing, you could always package it into a script or bash function so the typing can be minimized.



Maybe I don't understand what you are looking for...

Well, let's see if I can explain it graphically... without graphics. Here's a console screen (in XP) after typing the "history" command which dumps all the commands I've typed so far (including dupes... which I filter later):

```

unzip SysinternalsSuite.zip
del SysinternalsSuite.zip
del *.txt pdh.dll
ren sync.exe pssync.exe
lower
copy *.* c:\WINDOWS
del *.*
dir
exi
history
history | more
**[COLOR="SeaGreen"]gwbasic && exit[/COLOR]**
**[COLOR="Blue"]gwbasic[/COLOR]**
list f:\OLD_C\SRC\BAS\ANALOG.BAS
qbasic
cd WINDOWS\system32
dir z:\C_DRIVE\WINDOWS\system32
cp z:\C_DRIVE\WINDOWS\system32\oemlogo.bmp
cp z:\C_DRIVE\WINDOWS\system32\oeminfo.ini
exit
history
cls
history

C:\>

```

Now, let's say I want to re-run "gwbasic" (which I highlighted above for your convenience):

I type "gw", then hit up arrow and get this:

```

cp z:\C_DRIVE\WINDOWS\system32\oeminfo.ini
exit
history
cls
history

C:\>[COLOR="Blue"]**gwbasic**[/COLOR]

```

up arrow again gives me this:

```

cp z:\C_DRIVE\WINDOWS\system32\oeminfo.ini
exit
history
cls
history

C:\>[COLOR="SeaGreen"]**gwbasic && exit**[/COLOR]

```

The color highlights are for clarity only... they do not appear on my screen.

Anyway, see what happens?

I know I want to run "gwbasic", so I type "gw" then hit up arrow and it gives me the latest entry with "gw" in the history list. Up arrow again gives me an earlier entry, etc... until it runs out, then it loops back to the bottom again.

I'm quite sure a small script change to BASH would accomplish this same thing. I would *RATHER* use multiple up-arrows than control-r if possible.

Does this better explain what I'm trying to do?

BTW, thanks for your reply!

-- Roger

---

### Post by unutbu on 2009-07-07
Googling came up with this:
[http://www.geocities.com/h2428/petar/bash_hist.htm](http://www.geocities.com/h2428/petar/bash_hist.htm)

To enter the Up-arrow as a key in the terminal, you may need to press Ctrl-v Up-arrow.

I haven't played with it very much, but I confess I'm having a hard time making this solution work. The bind command doesn't seem to work for me when I put it in .bashrc, and although I can get the Up-arrow to behave like Ctrl-r when I press it once in the terminal, repeatedly pressing the Up-arrow for some reason does not behave like Ctrl-r. Sigh... 

Sorry I don't know the complete solution, but I thought I'd share this in case you can figure it out.

---

### Post by Locutus_of_Borg on 2009-07-07
```

alias h="history|grep"

```
now enter: h un
you will get a numbered list of all commands with "un" in them
e.g.
1 unzip 
2 unrar
3 mv *un* /
4 etc.

if you wanted to re-run command number 4,
!4
in the shell would re-run it

---

