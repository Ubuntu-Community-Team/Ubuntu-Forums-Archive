---
title: "Bash Script Little problem"
date: 2011-08-07
forum: General Help
---

### Post by jolian ramos on 2011-08-07
This is Bash script that i use , it opens many separated gnome terminal ; all what i want is to gather all those separate terminal in one multi-tabbed terminal ; so i want a command to add to this script to open tabs ..ANY help ? 


#!/bin/bash  
    
 gnome-terminal -x  bash -c " firefox & 
gedit '/home/Desktop/passwords for emails etc....' '/home/Desktop/messages to send  ' &
 sudo  cpulimit -e firefox-bin -l 25" 

gnome-terminal -x  bash -c "sudo  cpulimit -e plugin-container -l 60" 

gnome-terminal -x  bash -c  "kopete & 
skype &
sudo  cpulimit -e kopete -l 5 " 

gnome-terminal -x  bash -c " sudo  cpulimit -e chrome -l 60 "

---

### Post by jolian ramos on 2011-08-07
i found something and work nice 

gnome-terminal --tab -e 'bla bla blaa ' --tab -e '....... '

But the problem is when this bla bla is for example gedit ' address' , so the mark of gedit ' ' mix with -e marks ' ' for start and end  , so does anyone have idea about how to make bash distinguishes them ??

---

### Post by jolian ramos on 2011-08-07
> **Major_Bloodnok said:**
> The need to have the terminal opened to run a GUI application, serves you what purpose.
In other words, in bash script  just call the application, without opening a terminal.

As u see ,sir in that script above i need to open terminal , because i need to use a command under SUDO , and ;as i guess;  SUDO runs only under terminal not just by running the script i already solve that problem and found solution please read my second post to see my new problem , hope u can help me .. thanks in advance

---

### Post by Spyderkid on 2011-08-07
this will open a new window with a designated number of tabs....
```

gnome-terminal --tab --tab

```
the number of "--tab" will specify how many will open so in the case above 2 tabs wil open in the new window.
to open 6 tabs for example just write....
```

gnome-terminal --tab --tab --tab --tab --tab --tab

```

---

### Post by jolian ramos on 2011-08-07
> **Spyderkid said:**
> this will open a new window with a designated number of tabs....
```

gnome-terminal --tab --tab

```
the number of "--tab" will specify how many will open so in the case above 2 tabs wil open in the new window.
to open 6 tabs for example just write....
```

gnome-terminal --tab --tab --tab --tab --tab --tab

```

gnome-terminal --tab -e 'bla bla blaa ' --tab -e '....... '

But the problem is when this bla bla is for example gedit ' address' , so the mark of gedit ' ' mix with -e marks ' ' for start and end , so does anyone have idea about how to make bash distinguishes them ??

---

### Post by hakermania on 2011-08-07
try --tab -e **'**gedit "file"**'**

---

### Post by AlphaLexman on 2011-08-07
I think the original direction and objective of the OP is a little misguided here.

The script should not execute a program and limit cpu usage all at once.

'cpulimit' works on **existing** processes only. See the manpage  [here]("http://www.howtoforge.com/how-to-limit-cpu-usage-of-a-process-with-cpulimit-debian-ubuntu").

The OP's original script should have some test constructs to check if a program is running (i.e. firefox-bin, google-chrome, skype, etc.)

As Major_Bloodnok pointed out, you do not need to invoke another instance of 'gnome-terminal'

Leave the 'sudo' command out of the script and run the script with sudo.

---

### Post by jolian ramos on 2011-08-08
> **hakermania said:**
> try --tab -e **'**gedit "file"**'**

It works well , but inside the --tap -e ' bash-c "  "   ' , so that " of gedit will conflict with bash quotations marks

---

