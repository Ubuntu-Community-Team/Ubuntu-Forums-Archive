---
title: "permissions for world of warcraft folder keep locking up?"
date: 2009-11-10
forum: General Help
---

### Post by Arminius on 2009-11-10
every time I run the wow launcher.exe under wine. the whole world of warcraft folder permissions lock up, I click on properties, then under permissions folder access for the owner is blank, I change it to create and delete files, and this temporarily solves the problem

but next time I run launcher.exe the permissions go back to being blank.

I don't know how this started? how do I solve it?

---

### Post by Dekafox on 2009-11-10
The latest patch last night/today was a patch to the tools, including Launcher.exe.  I've been told running under Crossover doesn't have the issue, but right now anyone who tries running the current Launcher under wine and as their user will lose perms on the folder.  Supposedly if you run it as root it works fine, but I'm wary of running anything, especially anything in wine, as root.

Gogo Blizz.

I just added two lines for now to my launching script so after the launcher exits it restores the perms and launches Wow.exe as a workaround.  This way I'll at least know if another patch comes out, even if it may not be able to patch initially because of this permissions issue.

---

### Post by Arminius on 2009-11-10
ok, I think I understood half of that,
so what should I do?

---

### Post by marwade on 2009-11-10
> **Dekafox said:**
> 
I just added two lines for now to my launching script so after the launcher exits it restores the perms and launches Wow.exe as a workaround.  This way I'll at least know if another patch comes out, even if it may not be able to patch initially because of this permissions issue.


LOL  I understood maybe one-**third** of that.  Maybe I should start out with half a coffee bean I'm such a noob at the innerwork of computers.  I know there's a permissions issue, and how to change permission so at least the launcher window pops up, but when it clicks to launch the wow application it pulls a Houdini.  

What two lines did you add?  And where? And you were able to play?! I'll try the two lines!  Just tell me how.  And baby step me please.

---

### Post by GJLenon on 2009-11-10
Cancel that, lemme fiddle and I'll post a line that works. :)

---

### Post by marwade on 2009-11-10
GL, you're a hoot.  Thank you for the chuckle!  I had just posted a query as to which directory to be in and whatnot to use that command line when I saw your edit.  I look forward to reading whatever resolution you come up with for this latest Blizzblooper.  

Guess it's not so much their blooper as maybe an oversight.  I mean windows doesn't use permissions?  So maybe whoever wrote that patch just didn't think about how it would affect wine users?  

Eh.

---

### Post by GJLenon on 2009-11-10
Alright, this is probably not the best method, but it is what I used.

**Step 1:** *Creating a shell script*
Open gedit (Applications/Accessories)

In gedit, type:

> #!/bin/bash
clear
wine "/home/<user>/.wine/drive_c/Program Files/World of Warcraft/wow.exe";
chmod 755 "/home/<user>/.wine/drive_c/Program Files/World of Warcraft/" -R

Obviously change the <user> to your user name and modify the directories as needed.

Then save the file as wow.

**Step 2:***Accessing the Script*
Open a Terminal (Applications/Accessories).

Type in chmod 755 ./wow

This will allow you to access the script you just created.

Close the Terminal.

**Step 3:***Modifying the Panel*
Right click on your World of Warcraft icon on the panel, and go to Properties.

Delete what it has under the Command and replace it with:

> ./wow

Now close out of the properties.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

That should work, again, not the most stream-lined, but it works for me. :)

---

### Post by Raptorial on 2009-11-10
Deleting My Previous Message: Problem Solved. Thanks all!

---

### Post by marwade on 2009-11-10
> **GJLenon said:**
> Alright, this is probably not the best method, but it is what I used . . . it works for me. :)


It worked for me too. =D>   

I did need to open wow directly and choose to bypass the launcher.  Even with the new script, the launcher window still mucks up the works and shifts permissions again.  So back to the folder, change permissions, unlocked it, launched wow.exe, unchecked the launcher, and then clicked the icon again.  SUCCESS!

---

### Post by Mr. Hibba on 2009-11-10
I want to thank you guys for this thread. Before I saw this, I thought that my installing kubuntu-desktop in Ubuntu was causing the trouble (I opened the WoW launcher right after installing the kubuntu package.... right on patch day, it looks like lol. Made me think something was up with Kubuntu). I'll have to try running the game from the WoW.exe instead of the launcher and see if that works.

Mr. Hibba.

---

### Post by Mr. Hibba on 2009-11-10
Ok, so, I unticked the launcher, and then after it gets done patching (earlier I uninstalled the WoW bottle from Crossover and reinstalled and haven't yet got it all updated) the launcher comes up with an greyed out "Play" button and the folder permissions change again. So, I change 'em to let me play and the open the WoW.exe file through Crossover (so far skipping the Launcher). So far, it is letting me patch... looks like we'll see how this goes. 

On a side note, if I uninstalled and completely reinstalled the game, should I still be getting errors with the Launcher? I mean, wouldn't I have the launcher version that was before the patch that messed me up?

---

### Post by inspiteofmyself on 2009-11-11
eh i am using a different script than this ... might be of use to some of you. replace my username with your own, if you do not require padsp for better sound in pulseaudio, remove it from the script. i also do not use the Program Files directory for my wow... so add that if you need it.

```
#!/bin/bash
clear
env WINEPREFIX="/home/fluid/.wine/" padsp wine "c:\World of Warcraft\Launcher.exe"
chmod 755 "/home/fluid/.wine/drive_c/World of Warcraft/" -R
env WINEPREFIX="/home/fluid/.wine/" padsp wine "c:\World of Warcraft\Wow.exe"
```

---

### Post by Mr. Hibba on 2009-11-11
Ok, looks like it worked. So, for anyone else running into this, find the WoW folder and, if in Gnome, right click on it and choose properties and then the permissions tab, and give yourself read and write access to the folder. Close window and, as others suggested play from the WoW.exe file. Avoid using the Launcher for now as much as possible, as every time you do, you will have to re-change the permissions. However, I checked, and running WoW.exe itself won't change the permissions. However, if you need to download a patch, you will have to reset your permissions once per patch. 

Mr. Hibba.

---

### Post by inspiteofmyself on 2009-11-11
> **Mr. Hibba said:**
> Ok, looks like it worked. So, for anyone else running into this, find the WoW folder and, if in Gnome, right click on it and choose properties and then the permissions tab, and give yourself read and write access to the folder. Close window and, as others suggested play from the WoW.exe file. Avoid using the Launcher for now as much as possible, as every time you do, you will have to re-change the permissions. However, I checked, and running WoW.exe itself won't change the permissions. However, if you need to download a patch, you will have to reset your permissions once per patch. 

Mr. Hibba.

which is exactly what my script does, except that you get the ability to check for a patch everytime you run the game as every other user playing the game that runs launcher everytime they play ;)

---

### Post by Seraphim x on 2009-11-11
Here is a little less technical solution:

1. Browse to .wine/drive_c/Program Files/World of Warcraft
2. Launch Wow.exe
3. Uncheck the box in the bottom left-hand corner that says "Show Launcher"
4. Quit

Now try to launch from the WoW shortcut again.

---

### Post by ischliky on 2009-11-12
while its perfectly possible to have a script to reset permissions, or just not use the launcher, its kind of annoying in general to have to do this all the sudden.

anyone heard if blizzard is planning on fixing this bug? or if its going to be permanent since they dont officially support linux?  i was really hoping this would go away since ive been running wow on linux for around 3 years, and this is one of the most annoying bugs weve ever had.  short of the crash if you run away from a vendor/AH guy that i had for awhile.

---

### Post by Retrograde77 on 2009-11-12
Thanks for this thread, thought my home partition was dying for a min there lol, don't like seeing "contents unreadable".

Have been using a seperate wow script due to the repeatkeys prob, so usually bypass the launcher anyway.

---

### Post by GJLenon on 2009-11-13
Made a modification to the origional script I wrote, I recommend you change it.  Only true difference is that it changes the permissions from 755 to 750, a security enhancement.

> #!/bin/bash
clear
wine "/home/<USER>/.wine/drive_c/Program Files/World of Warcraft/Launcher.exe"&&chmod 750 "/home/<USER>/.wine/drive_c/Program Files/World of Warcraft/" -R
wine "/home/<USER>/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"

---

### Post by Mr. Hibba on 2009-11-15
> **inspiteofmyself said:**
> which is exactly what my script does, except that you get the ability to check for a patch everytime you run the game as every other user playing the game that runs launcher everytime they play ;)

Ah, ok. I don't know too much about scripting, so my method was just what I was more comfortable with.

I do want to thank you for writing the script, though. It helped some users here. :)

Mr. Hibba

---

### Post by inspiteofmyself on 2009-11-16
> **GJLenon said:**
> Made a modification to the origional script I wrote, I recommend you change it.  Only true difference is that it changes the permissions from 755 to 750, a security enhancement.

great idea...i just dont worry too much about security around a single folder that contains a game. thanks for posting this. a lot of people would make the change and never mention it :)

---

### Post by julianb on 2009-11-16
> Supposedly if you run it as root it works fine, but I'm wary of running anything, especially anything in wine, as root.

Running windows programs with full (root) permissions in windows is scary, but you deal with it if you want to use windows.

Running windows programs with root permissions in Linux is scary, and generally you DON'T do it!

---

### Post by inspiteofmyself on 2009-11-17
> **julianb said:**
> Running windows programs with full (root) permissions in windows is scary, but you deal with it if you want to use windows.

Running windows programs with root permissions in Linux is scary, and generally you DON'T do it!

heck running pretty much anything as root is a bad idea period.

---

### Post by Larsm1980 on 2010-01-31
Hi i wanted to post this link if someone read the thread and would like to know what the different permissions do. (A closer look at the code)

[http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html)

---

