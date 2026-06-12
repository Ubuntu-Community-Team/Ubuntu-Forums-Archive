---
title: "E: Type 'http://repository.spotify.com' is not known on line 1 in source list. Help!"
date: 2011-10-11
forum: General Help
---

### Post by Phalaneous on 2011-10-11
Hello!
I stupidly jumped head first into the world of linux, without knowing a single thing about it... 
I'm using Ubuntu and I was trying to install Spotify on my System. I previously installed Wine and Spotify and both were working perfectly.
Spotify started to crash frequently and then stopped working all together. I read on some forums that uninstalling the programmes and reinstalling them may help.
I tried to to do this buy following some online guides but have now permanently altered my system. 
I Have an red now entry/error sign on the tool bar, which says...

[I]"An unresolvable problem occurred while initializing the package information.
  
Please report this bug against the 'update-manager' package and include the following error message:
  
'E:Type 'http://repository.spotify.com' is not known on line 1 in source  list /etc/apt/sources.list, E:The list of sources could not be read[/I].'"

I can no longer access any of the upgrades or download any new software.
[I]
"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

"E: Type 'http://repository.spotify.com' is not known on line 1 in source list /etc/apt/sources.list
E: Unable to lock the list directory"

[/I]Any help would be greatly appreciated. I've tried hunting down a few online tutorials but they seem to be specific to misbehaving programs. I've tried entering a few commands in the Terminal but I feel I don't really understand enough to do any thing with the error messages generated. 

Regards,
-- Phalaneous

---

### Post by CatKiller on 2011-10-11
That thing you put in your sources.list? Take it out.

Welcome to the forum :)

---

### Post by Jesus_Valdez on 2011-10-11
Open a Terminal

type: sudo gedit /etc/apt/sources.list

Then write your password and will open a text file, look for the line that begins with Type 'http://repository.spotify.com' and delete it or put a # symbol at the very begining.

Save the file and close

Back at the terminal type: sudo apt-get update

Everything should be fine.

---

### Post by CatKiller on 2011-10-11
You should use gksudo rather than sudo with graphical applications.

---

### Post by Phalaneous on 2011-10-15
Thank you so much for your help and clear instructions!
The warning symbols have gone and I can open the software centre again. 
Hopefully I'll figure out how to use linux without destroying my computer and I'll be able to pass on the help to another struggling beginner.
Thanks again,

-- Phalaneous

---

