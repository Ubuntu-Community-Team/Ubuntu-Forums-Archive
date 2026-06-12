---
title: "cant open .exe with wine"
date: 2010-06-19
forum: General Help
---

### Post by JordanX on 2010-06-19
everytime when i click open with wine it says: 
> The file '/home/jordan/Downloads/*******.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

im sick of it!! >.<

---

### Post by jerome1232 on 2010-06-19
Right click the file, click properties, check "Allow executing file as a program"


if it's on a cd you have to open a terminal, type "wine " without the quotes, be sure to leave a space after wine, then drag the file ontop of your terminal, then press enter.

---

### Post by Smart Viking on 2010-06-19
You must make it executable, and then execute it.

First, open a terminal, and change to the current directory, per example your download directory.

```
cd /home/<username>/Downloads
```Then you must use the "chmod" command to change the files properties. (making it executable)

```
chmod +x <name of file>
```So,  if the file is "example.exe", i would have to enter this:

```
chmod +x example.exe
```What the "+x" in the code does, is, not surprisingly, making the file executable.

I hope this helped. :)

After you have done that, you could just double click it.

---

### Post by lisati on 2010-06-19
Use the following to fix it:
```
chmod +x <filename>
```

---

### Post by JordanX on 2010-06-19
> **jerome1232 said:**
> Right click the file, click properties, check "Allow executing file as a program"


if it's on a cd you have to open a terminal, type "wine " without the quotes, be sure to leave a space after wine, then drag the file ontop of your terminal, then press enter.


thanks it worked :)

---

### Post by JordanX on 2010-06-19
now my next problem

i have another.exe file in a .rar map
when i do extract as, not all files will be extracted
i need all the files in one map or it wont work
how can i extract it correctly??

---

### Post by elliotn on 2010-06-19
Get a rar extractor

---

### Post by JordanX on 2010-06-19
> **elliotn said:**
> Get a rar extractor


i can extract it it just doesnt extract EVERY file
just a  few
why would i get a rar extracter if i already can extract
i use unrar btw

---

### Post by jocko on 2010-06-19
> **JordanX said:**
> i can extract it it just doesnt extract EVERY file
just a  few
why would i get a rar extracter if i already can extract
i use unrar btw
Unrar should extract every file in the archive. So will file-roller. Just right-click the .rar file and select "Extract here".

---

### Post by Smart Viking on 2010-06-19
I think i'll just put this right in here:

[QUOTE=stchman]The Archive Manager that comes with Ubuntu called File Roller works well  for .zip, .tar, .gz, .tar.gz, .bz., etc.  It however needs the unrar  package to be able to unpack .rar files.

sudo apt-get install unrar

You will then be able to unpack .rar archives.[/QUOTE]

---

### Post by JordanX on 2010-06-19
> **jocko said:**
> Unrar should extract every file in the archive. So will file-roller. Just right-click the .rar file and select "Extract here".

thats excactly what i did
it doesnt work

---

### Post by JordanX on 2010-06-19
i can call a few file types wich are in the .rar folder

.ico
.dll
.idx
.rot
.FVS
.dds
.file
.db
.exe
.gz
.ini
.nc
.RPT

those are all the file types

---

### Post by JordanX on 2010-06-19
bump

---

### Post by Smart Viking on 2010-06-19
What are you trying to accomplish?

If you provide use download link for whatever you are doing, and tell us what you want with it, we would do it for you and help you a little more. :)

---

### Post by Ebere on 2010-06-19
I have the same problem as the OP.

None of the answers here, worked for me. (Nor did any of the answers at the Mint forums. (Some of those at the mint forums were very good, too.)

I have tried many times over, and I have carefully followed all instructions available. All to no avail.

I can get the installation process, started. But it hangs when I have to put in the next cd.

After a couple days of frustration, (and countless hours of trying.), I finally figured out that the reason it is failing when I put in the second cd, is because the very thing that was not allowing me to start the install process from the first cd... is now stopping the process, because it is not allowing any files from the second cd to be executed.

This whole, not allowing me to run executables on my own cds, is an attempt to 'save me from myself'.

How much more draconian can you get ? For that matter, how much more like windows, can you get ?

It's like that old adage, "I'm from the government, and I'm here to help". Only replace "the government," with "Canonical."

Is there ANY way whatever, that I can disable, and completely get rid of this "feature" that is killing the useability of my system ?

Please excuse my obvious frustration.

---

### Post by jerome1232 on 2010-06-19
Type "wine " leave a space after, drag and drop your executable onto it.

And isn't this a wine change? Not an Ubuntu change.

---

### Post by Ebere on 2010-06-19
> **jerome1232 said:**
> Type "wine " leave a space after, drag and drop your executable onto it.

And isn't this a wine change? Not an Ubuntu change.


Thank you for the response Jeremy.

But as I already stated... I already tried that.

And yes, I even tried copying all the discs over to my hard drive, and making sure that all the files were marked as executable, using gksudo nautilus... Still no joy.

That gets the installation started. IOW it gets the .exe file on the first disk 'executed'. But as soon as the installation process asks for the second disk, the installation process freezes up, because the system now will not let anything on the -second- disk be 'executed'.

I don't know if the problem is in wine, or in ubuntu.

The problem is the "feature" (Isn't it windows that initiated the practice of calling things that took even more control from it's users... Features ?) that does not let any file be run as executable, unless it comes from an ubuntu repository. (Hence the reason I thought it was an Ubuntu problem.)

I'd like a way to completely turn that feature off. Or at least a way to mark a LIST of cd's as ok'd by me, so that an installation that requires several disks does not hang up on each and every disk.
 
And thanks again for at least trying.

:)

Think I'll head over to wine headquarters and see what I can find. Thank you for that change in thought directions.

---

### Post by Ebere on 2010-06-19
> **jerome1232 said:**
> Type "wine " leave a space after, drag and drop your executable onto it.

And isn't this a wine change? Not an Ubuntu change.


Didn't take long at Wine, to find out that this IS an Ubuntu policy, therefore an Ubuntu problem.

[I]Right clicking and choosing Open With Wine  Windows Program Loader fails because of Ubuntu policy prohibiting  execution of files not **marked**  with the **executable** bit [https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required](https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required) 
[/I]

I'd like some way to override that "policy", for a set of cds. Not just one at a time.

.

---

### Post by jerome1232 on 2010-06-20
Hate to break it to you but Linux has always disallowed executing files that weren't marked as executable, they just implemented a change that stops gnome from circumventing those security measures for certain types of files.

From what I've read the new cautious launcher not working with cd's is actually a bug, gnome is supposed to set them as executable, but who knows... it does need to be fixed, and perhaps an option in the dialogue that pops up to set the file as executable and proceed.

This has a workaround in the last comment.

[http://ubuntuforums.org/archive/index.php/t-1457457.html](http://ubuntuforums.org/archive/index.php/t-1457457.html)

---

### Post by Ebere on 2010-06-20
> **jerome1232 said:**
> Hate to break it to you but Linux has always disallowed executing files that weren't marked as executable, they just implemented a change that stops gnome from circumventing those security measures for certain types of files.

From what I've read the new cautious launcher not working with cd's is actually a bug, gnome is supposed to set them as executable, but who knows... it does need to be fixed, and perhaps an option in the dialogue that pops up to set the file as executable and proceed.

This has a workaround in the last comment.

[http://ubuntuforums.org/archive/index.php/t-1457457.html](http://ubuntuforums.org/archive/index.php/t-1457457.html)

Some good stuff in this thread as well.

[http://ubuntuforums.org/showthread.php?t=1441315&highlight=marked+executable](http://ubuntuforums.org/showthread.php?t=1441315&highlight=marked+executable)

And thanks again.

---

### Post by mc4man on 2010-06-20
to revert the ill advised policy 
```
gksu gedit /usr/share/applications/wine.desktop
```
Change the Exec= line to this and save

```
Exec=wine start /unix %f
```

As far as multidisk installs there is another issue - lucid (fresh installs, not upgrades) doesn't use fstab entries for cd/dvd drives anymore.
This can also impact when doing a multi-disk.

If so you can create an fstab entry for your drive or try this instead
run to find softlink for drive

```
ls -l ~/.wine/dosdevices
```
then browse your cd to get the exact name of the install exe and go (adjust blue to match softlink, use the exact <whatever>.exe

Ex. of softlink d, exe named setup.exe

```
wine [COLOR="Blue"]D[/COLOR]:/setup.exe
```

---

### Post by JordanX on 2010-06-20
at this moment my problem is
i downloaded this game from a site
it was a .rar file
i tried to extract it and not everything got extracted
so now i cant play

---

### Post by clhsharky on 2010-06-20
JordanX


> i downloaded this game from a site
Site please so we can test.

> i tried to extract it and not everything got extracted
File may be corrupt re download.

Scan file for virus, Linux wont run windows viruses. Apps will (Wine, browsers)

Sharky

---

### Post by Ebere on 2010-06-23
This is a small solution, and a long workaround, really. But if you have Blizzard games that install from more than one disc...

If you go to battlenet and register your game... (You'll have to give personal info, and the cd key, etc.)

Then once it is confirmed... You can download the latest 'version' of that game.

IOW: I have diablo 2. I can download the full game... With ALL of the latest patches already applied. (In this case, a little over one and a half gigs.)

That puts the full installation right there on your hard drive. In one folder. And only one executable needed.

It works.

---

### Post by LeadFingers on 2010-07-28
I know this is an old thread but I just got bit by this problem earlier today, maybe this will help. 

The Wine dev's made two ways of opening an executable, so make sure you have the latest Wine. "Wine Windows Program Loader" is for executables you own (user level), "WineBrowser" bypasses the whole permissions issue (root level). 

Right click the CD, select "Browse Folder", right click the .exe, select "Open With"/ "Winebrowser". Quicker than using a terminal. 

While the winebrowser runs exe's at the root level it installs the apps at the user level, so there's no permissions nightmare when you're done..

---

