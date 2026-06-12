---
title: "New to Ubuntu. Please help."
date: 2011-01-23
forum: General Help
---

### Post by SquidMeal on 2011-01-23
Alrighty. So, a friend told me about ubuntu a while back.
I have recently bought a new computer, but I couldn't afford an OS liscence along with it, so I'm running Ubuntu for a while.

Here are my main problems so far.

Windows Executables

I have downloaded WINE. I've tried to install Diablo 2 from a disc.
I popped my disc in, opened the icon that appeared and tried to open the setup.exe file inside.
WINE then promted me that it was an untrusted file.
What gives?

I've also tried to instal MineCraft.
However; when I try to accquire Java using the code

"sudo apt-get install..." 

And instert the package I need, it prompts me for my password. I type it in and hit Enter and it says "Sorry. Try again"

I've tried multiple times. I know I'm getting my password right, but ther terminal thinks otherwise.

It worked one time, but when the EULA came up, I couldn't continue. I waited for a short time, but nothing changed.  I though maybe it had been installed, so I tried a java command in the terminal. It prompted me again to download Java through one of three packages.

Those are my problems so far. Thank you on advance.

PS. I'm running Ubuntu 10.10 and I believe it's WINE 1.3

---

### Post by Bucky Ball on 2011-01-23
If you're intending Ubuntu as a Windows replacement, good. If you're expecting it will run all your Windows programs, even with Wine, wrong.

Open System>Administration>Synaptics package manager, search for and install:

ubuntu-restricted-extras

That will install java and a bunch of other things properly.

---

### Post by ChrisNZ on 2011-01-23
I concur. I too was hoping for a more favorable result running Wine and some of my Win games. Its a bit hit n miss. Some will some wont.
However I would suggest you try the sites where these games come from and try searching the net for gamers who use them on liunx.
Test the search engines with the base words that sites MUST have - like 
"Linux, (name of the game your after) forums, help" and see what you get?

As for me Linux has proved to be the most stable platform in the Ubuntu range, incl Mint and Xubuntu (mouse). 

Keep Trying...

Chris

---

### Post by andymorton on 2011-01-23
[QUOTE=SquidMeal;10390998]Alrighty. So, a friend told me about ubuntu a while back.
I have recently bought a new computer, but I couldn't afford an OS liscence along with it, so I'm running Ubuntu for a while.

Here are my main problems so far.

Windows Executables

I have downloaded WINE. I've tried to install Diablo 2 from a disc.
I popped my disc in, opened the icon that appeared and tried to open the setup.exe file inside.
WINE then promted me that it was an untrusted file.
What gives?

You could try right-clicking on the installer, click on properties and then choose the permission tabs. Check the box which says 'allow executing file as program'. 

andy

---

### Post by SquidMeal on 2011-01-23
Thanks Bucky.
You've solved my Java problem. :)

I'll give the other suggestions a try, too

---

### Post by Bucky Ball on 2011-01-23
> **ChrisNZ said:**
> 
As for me Linux has proved to be the most stable platform in the Ubuntu range, incl Mint and Xubuntu (mouse). 


'Ubuntu has proved to be the most stable distribution in the Linux range.' ;)

Ubuntu is a Linux 'distribution', commonly called 'distro', as are Mint, Debian, OpenSUSE etc, 10.04 LTS is a Ubuntu 'release'.

---

### Post by SquidMeal on 2011-01-23
When I try what Andy has suggested, I get a message telling me that this program is read only and I can't change any preferences.
Thanks anyways.

I'll try Chris' suggestion next...

---

### Post by SquidMeal on 2011-01-23
Ive managed to get wine to run the file using this code:

wine /media/install/install.exe

however, I then get a prompt to "insert install disc" which is already in my disc drive.
Suggestions?

---

### Post by ChrisNZ on 2011-01-26
Hi Squidmeal

How ya going? I forgot to mention also that you can use the "Configure Wine" options. First you need "Add" to find the list the *.exe program you want to run. Then Select the version emulator... that you think needs to run it. Save if that option is present and then try and see if that works.
Try all the earlier version of windoz as well.

Note what works and what dosnet and post feed back here so others can learn.
 
(hopefully you found the 'common work around' for disc issues and protection, Linux has on running stuff direct from the CD tray - i think its having admin pref's, locate file and changing options in properties to Read Write?)

Cheers
Chris
ubu user for 6 years

---

### Post by Vaphell on 2011-01-26
someone mentioned diablo 2:
if you have windows intact, do you have Diablo 2 installed on windows partition by any chance? If so, try to run it from there. Doubleclicking on 'Diablo II.exe' always worked for me, apparently Diablo 2 is not so picky about the configuration - all libs required are in its directory and it can run even with empty registry keys.

---

