---
title: "No Sound In Eternal Lands"
date: 2010-12-19
forum: General Help
---

### Post by Andysoldier on 2010-12-19
Hi all, i'm new to Ubuntu but have installed the game Eternal Lands just a couple of days ago.
I also downloaded and unzipped the sound folder (and placed it in the EL folder as directed).

All sound is working ok on my PC but i'm getting no sound in the game.  I changed the el.ini file to "sound - 1" and saved it and also changed in-game settings to "sound - on".

The error i'm getting when i execute the bin file in a terminal is:

open /dev/[sound/]dsp: No such file or directory

Any help is much appreciated.

Using Ubuntu 10.10.

---

### Post by tredegar on 2010-12-19
> open /dev/[sound/]dsp: No such file or directory
Something is wrong with the path to your dsp
It should be just **/dev/dsp**
So, somewhere in your .ini file you have **[sound]** where it should not be.

I don't know EL, so you'll have to experiment: See it as another puzzle to be solved ;)

Good luck.

---

### Post by Andysoldier on 2010-12-19
Ok thanks for the quick response - i'll take a look in that file.

I have noticed this when i execute - the EL window opens and it lists everything it has "found" and at the end of that list i get this:

The location of the data files in use is ./
Your personal settings and logs will be saved in /home/fred/.elc/main/
alcOpenDevice () Error initializing sound: ALC_NO_ERROR

I've looked for those locations and can't find them.

Any pointers?

---

### Post by tredegar on 2010-12-19
> The location of the data files in use is ./
./ means "the directory you are currently in"

If you open nautilus (your file browser) and press CTRL-h you'll see the ""hidden" files (those that have a name beginning with a dot). They are not really hidden, but ususally they are config files, and we'd prefer not to see them unless we have to, because, like you are now, debugging.

Perhaps you have installed this program to your home directory.

In which case, open a terminal, **cd **to the Eternal Lands dir, and then run the executable (I have no idea what it is called, but use your file manager to find a likely executable name, and then type it in the terminal window), from there.

---

### Post by Andysoldier on 2010-12-19
Yes i was changing directory to the Downloads folder - that's where everything is.

So everything is running ok - apart from the sound.

---

### Post by Andysoldier on 2010-12-19
Ok tredegar, thanks for your help.  I just want to make things clear.  I'm executing the bin file which is in an Eternal-Lands folder in my Downloads folder.

Inside that EL folder is another folder entitled "sounds".  I'm positive the folder structure is correct.  Here is a line from someone else trying to help on the EL website:

First of all, make sure you have unzipped the file in the right location  - it should be in the game INSTALL dir (not the logs/settings dir), in  other words you should have a folder "sound" in the same directory as  other folders "2dobjects", "3dobjects" ... "textures". And, "sound"  should contain directly the various .ogg files, not another subdirectory.

As you said, if i go to my home folder and do Ctl-h there is a .elc folder with a few txt and cfg files etc - i'm guessing they're save files and such.

Is it ok that i have these 2 folders in different locations?  

Thanks, still learning!

---

### Post by Andysoldier on 2010-12-19
Ok there's a few threads regarding /dev/dsp missing - i think this could be the problem but to be honest the solutions are above me.

Does that seem likely?

---

### Post by tredegar on 2010-12-20
> Ok there's a few threads regarding /dev/dsp missing
I doubt it is missing, but you can check for yourself. Navigate to **/dev** in your filemanager, and see if there is a **/dev/dsp** listed there.

_But_ **/dev/dsp** us owned by **root** but can also be accessed by members of the group **audio**

Are you a member of the group **audio** ? To find out, whilst logged in as yourself, in a terminal type the command **groups**. The groups you are members of will be listed.

If you are not a member, then you will not be allowed access to **/dev/dsp**, and will need to make yourself a member of that group.

Once added to that group, you need to logout and then back in again for it to take effect.

Are you still getting the "open /dev/[sound/]dsp: No such file or directory" error?

---

### Post by Andysoldier on 2010-12-20
Thanks for getting back to me tredegar.  

Yes i'm still getting the "open /dev/[sound/]dsp: No such file or directory" in the terminal.

I've added myself to the audio group (didn't know about groups so that's good) and there is no dsp folder or file in the dev folder.

I also checked the el.ini file and looked to see if there was a syntax error as you thought earlier with the [sound] text but nothing seems to be wrong in that file.

I'm totally stumped to be honest.

---

### Post by Andysoldier on 2011-01-08
Ok, thank you everybody for the help and advice.

What i have to do is  when starting the games bin file i need to type in "aoss" before it.

I have to do this every time.

Any comments on this are still appreciated to help me understand this more.

---

### Post by tredegar on 2011-01-08
Thanks for posting the solution.
More about **aoss** [here]("http://manpages.unixforum.co.uk/man-pages/linux/suse-linux-10.1/1/aoss-man-page.html")
> I have to do this every time.
If it annoys you, you can write a "wrapper script" with the commands you'd normally use to start the game:

```
#!/bin/bash
cd   /wherever/the/game/is
aoss  ./thegame
```

Save this script somewhere
Make it executable **chmod +x /full/path/to/name_of_script**
Check it starts the game with
**/full/path/to/name_of_script**


Now R-click Applications
Edit menus
Click on Games at the left
Click New Item
In Name box put Eternal Lands
In Command box put /full/path/to/name_of_script
In Comment Box put anything you like.
Click OK

Try running the game from the menu.

---

### Post by Andysoldier on 2011-01-08
Thanks tredegar.

Ok i've typed the script using Open Office and saved it.

  	 	 	 	p { margin-bottom: 0.21cm; }  #!  /bin/bash
 cd /home/bertie/Downloads/Eternal-Lands
 aoss ./el.x86.linux.bin
 

I've made it executable.

When testing to see if it runs i get

"invalid file (bad magic number): Exec format error"

I have saved the file as and odt file, and i renamed to bin file.

Advice appreciated as always.

---

### Post by tredegar on 2011-01-08
> Ok i've typed the script using Open Office and saved it.
No Noooooo!
*Not* Openoffice - that's a wordprocessing program, that puts a whole load of other stuff (about formatting , fonts and whatnot, which you do not want) into the file.
You need a _text-editor_ like **gedit**

Applications Accessories Gedit
Use that to create the file
Then it will be saved with just the plain text. That's all linux expects, needs and wants to see.

Try again.

---

### Post by Andysoldier on 2011-01-08
haha ok silly me!

Well i've now replaced that odt file with one created using gedit and hey presto it works a treat.

Thanks very much for your help tredegar - i'm chuffed to bits that it's all working and at how much i've learnt!

Andy

---

### Post by tredegar on 2011-01-08
Pleased it worked.

When you are editing linux configuration files always use a text editor ( gedit, vi, vim, nano, kate, whatever) but NOT a word-processing application.

Anyway, it worked for you.

Good that you have learned.

Best wishes.

---

