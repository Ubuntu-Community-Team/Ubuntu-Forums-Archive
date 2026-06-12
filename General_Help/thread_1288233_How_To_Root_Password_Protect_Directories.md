---
title: "How To: Root Password Protect Directories"
date: 2009-10-11
forum: General Help
---

### Post by BJ_Covert_Action on 2009-10-11
Howdy All,

I just spent my Saturday night trying to figure out a decent, simple, and easy way to password protect some directories on my Ubuntu 8.04 machine without having to go through the entire process of encryption and decryption every time I access the folder. In essence, what I wanted to achieve was:

[list]Navigate to a directory via my GUI (Nautilus)[/list]
[list]Double-click on said directory and have it fail to show contents[/list]
[list]Right-click on said directory and specify password to successfully show  contents[/list]
[list]Do not have to use multiple 3rd part programs to do such[/list]

After some digging, I found that this problem seems to be a common issue that many folks want to implement but don't know exactly how. For instance, see  [these](http://ubuntuforums.org/archive/index.php/t-449219.html) [three](http://ubuntuforums.org/showthread.php?t=410513&highlight=password+protect) [discussions](http://www.cyberciti.biz/tips/linux-or-unix-password-protecting-files.html) on the same issue. All three discuss a wide variety of solutions from permission changing to encryption methods. After fiddling through all of that material myself, I hacked together some of the methods from the easier to implement solutions and came up with my own as discussed below.

Essentially, I did this by following a 4-step process:
[list]Find right-click script directory on my machine[/list]
[list]Write a script to change directory permissions to root only[/list]
[list]Write a script to pop open Nautilus as root[/list]
[list]Mod both scripts executable[/list]

These are each detailed below:

**[size=+1] Step 0) Familiarize yourself with the right-click script directory [/size]**

[indent]
On your platform, there should be a hidden directory (directory name preceded with a '.' character) that you can place scripts in that can be run from your right click menu. This is discussed in brief at [The Gnome Library](http://library.gnome.org/users/user-guide/stable/gosnautilus-444.html.en). Essentially, if you have not installed any scripts on your computer yet (or written any yourself) then there will not be a scripts option in your right-click dialogue yet. Thus, you will need to navigate to it manually either through your favorite file browser or your terminal. It should be located at:
```
/home/<user_name>/.gnome2/nautilus-scripts
```
Once you navigate there, you are going to be creating two text files which you will make shell scripts once you have written them. Alternatively, you are welcome to use any other programming language that you have installed on your computer such as Perl to do the same function that I will talk about in the later steps. This, of course, is a more advanced method and can be discussed later, or something. 

The other thing that is good to know about the scripts directory is that any scripts placed in the directory are automagically configured to have 4 very specific variable inputs from the GUI environment. This allows our scripts easy access to particularly useful information about the whatever files we want our scripts to work on. From the [gnome website](http://library.gnome.org/users/user-guide/stable/gosnautilus-444.html.en), these four variables are as follows:

```

NAUTILUS_SCRIPT_SELECTED_FILE_PATHS   	 newline-delimited paths for selected files (only if local)
NAUTILUS_SCRIPT_SELECTED_URIS 	newline-delimited URIs for selected files
NAUTILUS_SCRIPT_CURRENT_URI 	URI for current location
NAUTILUS_SCRIPT_WINDOW_GEOMETRY 	position and size of current window

```

Once you have familiarized yourself with this script directory a little bit and the information that goes with it on the gnome website linked to above, you are ready to start the next step.
[/indent]

**[size=+1]Step 1: Create a Script to Change Directory Permissions to Root Only[/size]**

[indent]
Once you have navigated to the script directory discussed above, right click and select 'Create Document' > 'Empty File.' This will open a file with the name 'new file' that can be opened with your favorite text editor (Gedit will be used by default). Alternatively, if you are in the directory using the terminal, run the command:

```

gedit *<Script1>*

```

...where *<Script1>* is whatever you choose to name your script (I chose *Script1* for the purposes of this tutorial but using a more descriptive name like, "*Protect_Directory*" is a better idea. (**Note:** Using the '_' character in place of the space character, ' ', is a better idea for script names as spaces in names can cause things to be fussy when used in the terminal). The gedit command will pop open Gedit for editing the script so if you prefer vim, emacs, pico, or some other editor, substitute the appropriate command respectively. 

Once you have opened *Script1* in a text editor, copy and paste the following contents into the document and save it:

```

#!/bin/sh
for d in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
	if [ -d $d ]; then
		sudo chmod 000 $d 	
		exit
	fi
done 

```

This script will allow you to right click on a directory, select 'Scripts' > '*Script1*', and lock the directory to being accessible only to users with root permissions, and only by putting in their root (admin) password. It is important to note that this currently only works on directories. In order to get it to work on individual files (like, say, a special picture your girlfriend sent you) you need to add a '-f' check into the script either as a new if check or as an 'or' option within the original if check. This is touched on later in the description of how it works.

[indent]**How it Works:**
A line by line breakdown of the script follows. If you don't care, then skip to the next section.

```
#!/bin/sh
```

This line of code tells your system that the contents of the text file you just made are to be run using the **sh** language. **sh** is short (I think) for shell and it is the default scripting language for BASH systems (Ubuntu uses a BASH shell by default). The **#!** predecessor in the path is known as the shebang operator (sharp sign #, bang !) and tells your system to use the following bin file '/bin/sh' to run the contents of the script. You can use this operator as a predecessor in most scripts such as perl scripts or python scripts if you like those languages. This command, thus, tells your computer to interpret the text contents with the system shell.

```
for d in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
```

This particular line of code cycles (using a for loop) through each item selected by your cursor (remember those special scripting variables we discussed above?) and assigns them, one by one, to the variable 'd' (you can get more creative with your variable names if you like). It then enters a do command and thus, says, for each item selected, perform the next few commands:

```
if [ -d $d ]; then
```

This line tests the item to see if it's a directory. If it is, the next line is performed. If it is not a directory, then the script goes on to check the next item (Remember how we said it doesn't lock single files? This is why. -f can be used instead or in conjunction with the -d check to work on files).

```
sudo chmod 000 $d 
```

If the item is a directory, use the chmod command to set permissions to 000 (root only) on the current item ($d).

```
exit
```

Exit the if check (I think, someone might want to correct me on this).

```
fi
```

End the if statement.

```
done
```

End the for loop. Exit the script.
[/indent]

And that's it. Those simple few lines will set a directory's permissions to root only so that no one can even access them without first putting in the root password.

It should also be noted that I put a sudo command in front of the chmod command so you will have to put the root password into a prompt when using this script in order to protect your directory with the root password. Security recursivity FTW! :)

Now, step 2 is similar since it is a script, so the line by line breakdown will be a little less verbose.  
[/indent]

**[size=+1]Step 2: Write a script to pop open Nautilus as root[/size]**
[color=red][size=+1]WARNING:[/size][/color]** Opening a directory as root is not normally recommended. Any simple commands to be executed on directories as root are best done so from the command line. If you decide to browse a folder as root with this script, there is a chance that unintended commands could damage your system. All care should be taken not to change contents of a directory as root unless you know what you are doing. The root browser window should be closed immediately upon completion of browsing.**

[indent]
Now that the warning is out of the way, we want to give ourselves the ability to right click and view a directory as root. This means that we can change just about anything once we are in a directory, even crucial system and security settings. If you use this script to access folders that you didn't lock using the script above, and damage your system, I cannot be held responsible. I will, however, feel sorry for you.

We are going to use the gksudo command as well as the nautilus launcher to implement this script. It is pretty much the same as above, but instead of using the chmod command, we will use the nautilus command. So go ahead and open a new text file in your script directory with a new name. (I will call it *Script2* for this tutorial, but again, Root_Browser or something descriptive would be best).

Copy and past the following into your *Script2*:

```

#!/bin/sh
for d in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
	if [ -d $d ]; then
		gksudo nautilus $d
		exit
	fi
done 

```

Save and exit and be on your way to step 3, unless you want a discussion of the one different command, then read how it works below. 

[indent]**How it Works:**
Seeing as how a line by line breakdown would include 5 of the 6 descriptions given in the last step, I am going to discuss in detail only the following:

```
gksudo nautilus $d
```

This essentially uses the gksudo function to give the user temporary root permissions. It then accesses the Nautilus browser (your GUI)  with those permissions and pops open a new file browser containing the contents of directory $d. Again notice that this script is written for directories only and not files. If you want to access a file as root I **highly recommend** using the command line. A -f check would be used in place of or alongside the -d check in the if check to access files.

Since you are using gksudo to access nautilus, you won't be able to do so until you login as root using your root password. Thus, a protected directory using the script we wrote above, will not be able to be accessed without your root password.

Finally, you can hide all of the contents of those, errrr, 'social networking' sites from your girlfriend (or boyfriend) and store them on your computer. :) 
[/indent]
I should note here that these scripts do not, in any way, help make your system more secure. If your system gets pwnd at the root level, none of your contents will be safe because of these scripts, as they use the root password. If you are handling extremely sensitive information or pictures or whatever, I would recommend reading up on encryption (in fact, I recommend it any way as privacy in general is being threatened more than ever these days). That being said, these little guys are useful, but not professional. If you are using them for anything super important, you are truly insane.
[/indent]

**[size=+1]Step 3: Mod Both Scripts to be Executable[/size]**
[indent]
Next we need to make the two scripts we just wrote executable. To do so,  run each of the following commands sequentially in your terminal. Of course, substitute <user_name> with the profile name you logged in with, and <Script1> and <Script2> with your uber-descriptive names that you chose for your scripts.

```

sudo chmod +x /home/<user_name>/.gnome2/nautilus-scripts/<Script1>
sudo chmod +x /home/<user_name>/.gnome2/nautilus-scripts/<Script2>

```

These commands use the chmod utility to make both scripts executable (hence the +x modifier). If you do not perform this step the scripts will not be accessible from the right-click menu which was one of my requirements, and kind of the whole point of all this. Thus, it is imperative that you chmod these two scripts appropriately using the commands above.
[/indent]

That about does it. Once you have chmoded both scripts as shown in Step 3, you should be able to right click on any directory and see a 'Scripts' option in the pop-up menu. Holding your cursor over this should pop out another side menu that has the two scripts you just made in it (listed by whatever name you gave them). Clicking on either once you've right clicked on a directory should do what I said they would do, that is, they should lock and unlock a directory for root access and browsing respectively.

This was my first How To that I have written up so if I made any major taboos or anything, give me a cyber-smack and let me know. I hope this helps some folks and feel free to post any questions as a response. I don't check this forum as often as I could, but I am sure someone with more knowledge will probably read this thread at some point anyways. 

Good luck hiding your sensitive information everyone. I hope you enjoy using these scripts as much as I do :)

---

### Post by 3rdalbum on 2009-10-11
Useful for people to know... but you didn't need to write your own Nautilus script. There's already an "Open as Administrator" Nautilus script, aptly titled "nautilus-gksu". It's in the repositories.

---

### Post by mcduck on 2009-10-11
..of course there's also the easy way of simply installing Cryptkeeper and using that to automatically create and manage encrypted directories.. ;)

---

### Post by iKonaK on 2009-10-11
> **mcduck said:**
> ..of course there's also the easy way of simply installing Cryptkeeper and using that to automatically create and manage encrypted directories.. ;)
+1 
Also, with encfs/cryptkeepr(GUI) your files are actually protected, root/sudo means nothing to a user with a live cd, I also use LUKS because it's also hiding the file's (size, number, etc).

---

### Post by BJ_Covert_Action on 2009-10-11
> **mcduck said:**
> ..of course there's also the easy way of simply installing Cryptkeeper and using that to automatically create and manage encrypted directories.. ;)

Yeah, I know there are packages and other things to do it, but I figured this could give a nice intro. to scripting to newbies as well. On top of it, they don't have to worry about learning all the lingo that goes along with keys, signing, RCS4, or anything else that might raise red flags while they are fiddling with encryption.

I know that locking these guys doesn't really mean anything in terms of protecting files from a truly determined crack artist, or as the other guy mentioned, someone with a live CD, nonetheless, it will keep other users from scrolling through your personal phone numbers, pictures, or saved e-mails if you have a lot of friends that fiddle about on your computer.

Of course there are always other user accounts that you can set up to keep this from happening, but if you have your laptop at the school library and another student wants to dump a picture from his phone to your computer, he's not going to want to log out and back in first. It just provides a basic level of privacy :)

---

### Post by BJ_Covert_Action on 2009-10-11
> **3rdalbum said:**
> Useful for people to know... but you didn't need to write your own Nautilus script. There's already an "Open as Administrator" Nautilus script, aptly titled "nautilus-gksu". It's in the repositories.

This I did not know, and I would have had no idea to look for it in synaptic or using apt-get because in all my google searches I didn't see mention of it anywhere. Maybe that's because everyone just said screw it and jumped straight to cryptography, but gpg gets cumbersome to deal with in my opinion and mcrypt works best from the terminal, which so far as I can tell tends to scare some people away...

---

### Post by mcduck on 2009-10-11
> **BJ_Covert_Action said:**
> On top of it, they don't have to worry about learning all the lingo that goes along with keys, signing, RCS4, or anything else that might raise red flags while they are fiddling with encryption.

That's why I suggested Cryptkeeper. It handles everything automatically, all you have to do is choose a name & password for your encrypted directory (and of course *remember* the password. :D).

---

### Post by KyleRaynor on 2009-10-15
You don't have to exit the if check.
You only exit once the script if finished.
A more properly coded script would look like this:

```

#!/bin/bash 
#protect.sh [note: .sh is not needed, but is more clear, and precise]
#Nautilus script to look through a selected list of directories/files and remove
#permissions from them to 'protect' them from prying eyes without having to use encryption

for d in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
     if [ -d $d ]; then #Checks for a directory in the selected list
          sudo chmod -R 000 $d #Recursively removes permissions from files in directory.
                               #Paranoid, yes, but effective just the same
     elif [ -f $d ]; then #Checks for files in the selected list
          sudo chmod 000 $d #Removes permissions from the current file
     fi
done

exit 0 #The -ONLY- proper way to successfully exit a shell script.

```NOTE::
I'm not trying to sound like a horse's @$$, this is just a more efficient way of doing this.
Of course you could easily modify this using one of the crypt* progs instead of chmod. But I'm sure they add their own context menu items(I have no need for encryption unless it's done for a login screen. So I have no idea how to use such things as of yet)

---

### Post by amoun on 2010-09-03
> **BJ_Covert_Action said:**
>  ....

I know that locking these guys doesn't really mean anything in terms of protecting files from a truly determined crack artist, or as the other guy mentioned, someone with a live CD, nonetheless, it will keep other users from scrolling through your personal phone numbers, pictures, or saved e-mails if you have a lot of friends that fiddle about on your computer.

Of course there are always other user accounts that you can set up to keep this from happening, but if you have your laptop at the school library and another student wants to dump a picture from his phone to your computer, he's not going to want to log out and back in first. It just provides a basic level of privacy :)

Hi. Well I have a couple of problems

First it doesn't work each time. For instance I can't do single folders on the desktop, but if I highlight a few some get done ???

Secondly, whereas it is a quick was of changing permissions, can't any protected folder or file be viewed just by using the same context menu and selecting properties and changing the permissions whatever?

However thanks as it does help understand the scripting options as mentioned, which is great.

---

### Post by KyleRaynor on 2010-09-03
Can you reproduce it amoun, and did you use his script or mine?
And have you tried in a nautilus window, or just on the desktop?

---

### Post by amoun on 2010-09-04
Hi KyleRaynor

Yes it always the same, inconsistent. I started with the original script and it didn't work at all, although I quickly swapped to yours. So although it doesn't work as expected either on the desktop or in a separate window I'm not fussed as I am using the cryptkeeper application.

When i get around to making my own scripts, for fun, I may find out why this one isn't working right on my EEEPC with hardy.

The root script works fine and 

Thanks for your concern.

---

