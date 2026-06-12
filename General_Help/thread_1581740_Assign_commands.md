---
title: "Assign commands"
date: 2010-09-25
forum: General Help
---

### Post by d5xtgr on 2010-09-25
I recently downloaded the firefox beta; is there a way I can set things so the command 'firefox' and the applications menu launch the beta rather than the current version?

---

### Post by luvshines on 2010-09-25
You can use 'alias' in your .bashrc file located in the home folder which will overwrite the commands with the ones you define

Eg. if you write in ~/.bashrc

alias vi='vim'

Then, typing vi will instead open up vim for you.
You can unalias it any time during an open terminal session or just for single instance by using '\' as escape character

Eg; \vi <file-name>

For changing the menu to run the modified command, you'll have to change the command fired by menu options by changing them in 
system-->preferences-->main-menu then choosing and editing firefox command to be run from there

---

### Post by d5xtgr on 2010-09-25
To do this, I need to already have a command for the beta, right?  ie What would i put after the equals sign in the bashrc file?

---

### Post by Lateralis on 2010-09-25
You would need to locate the Firefox beta binary file, which would depend on how you installed it.  It looks like you can only download the source code, which means compiling yourself.  In which case only you know where you placed the binary executable!  

Of course, if you place the binary in a location in your $PATH, then you don't need to do anything except put the name of the binary exectuable after the equals sign.  A good location for the Firefox Beta binary exectuable is /usr/local/bin, but as I say in principle it can sit in your home directory - all you have to know is its location relative to **/**.

---

### Post by luvshines on 2010-09-25
Have you installed firefox-beta or running by calling the executable from some location ?

---

### Post by luvshines on 2010-09-25
I am late that Lateralis replies by 2 minutes :D

@Lateralis, just a question ??

If the firefox [ earlier one ] is found in a location say x and firefox [ new one ] in location say y and PATH looks like x:y

then calling firefox (both are same named) will call x, right ??

---

### Post by Lateralis on 2010-09-25
Yes, I think so.  

If it were me, I would call the beta executable firefox-beta and place that executable in /usr/local/bin.  He can then use either Firefox 3 or Firefox 4 beta, by either typing firefox or firefox-beta respectively into the command line.

Alternatively, he could make a ~/bin directory and add that to his $PATH.  Any compiled software binaries can be placed in there.  That way they don't get mixed up with any other binaries installed using .deb packages.   

I would then *add* a menu entry, by using the System -> Pereferences -> Main Menu GUI as you suggested earlier in the thread, which points to firefox-beta.  That way he again keeps the Firefox 3 and gets the Firefox 4 beta launchers.

---

### Post by d5xtgr on 2010-09-25
Okay, thanks!  I got it working after a bit- the mv command works a bit differently than I remember, but all sorted out now.  While looking up how to install it, I found a page that instructed me to place the binary in /opt/firefox- this wasn't a directory you mentioned; is there a good reason to put it there or not?  Thanks a bunch!

---

### Post by luvshines on 2010-09-25
Yeah, firefox installation tutorial suggests /opt directory, don't know why ??

Neways, I think that should not be an issue

PS: Good to know that you were able to resolve it

---

### Post by Lateralis on 2010-09-25
The /opt directory isn't one which is present in Ubuntu by default.  It is defined in the [Filesystem Hierarchy Standards]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") as being a directory into which optional (ah ha!) programs are to be installed.  These are non-system and custom built programs.  

Some would say that /opt isn't needed whilst others would say it is necessary.  [This]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html") link gives a good overview.  I think I would largely fall slap bang between the two!  Either way, so long as you know where everything is and have a system in mind, i.e. all source compiled programs to be located in /opt then stick with that.  You should though be aware that /opt isn't in your $PATH.  Even if it is, binaries located in /opt/<package> won't be picked up by the command line.  You should therefore consider having an /opt/bin directory and putting that in your $PATH.

---

