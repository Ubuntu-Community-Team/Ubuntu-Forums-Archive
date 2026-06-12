---
title: "BASH Programming question"
date: 2009-11-06
forum: General Help
---

### Post by dmillerw on 2009-11-06
If this isn't the right place, please move it.

```
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Just some test text, DON'T JUDGE ME! " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber --height=300 --width=300)
echo $xx

if [ $xx==Firefox ]; then
	echo "test balloon"
elif [ $xx==Pidgin ]; then
	echo "test balloon2"
fi
```

This is what I have so far, all it does is output test balloon, whether or not I choose firefox, help?

---

### Post by r.stiltskin on 2009-11-06
Just needs some spaces.

```
#!/bin/bash

xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Just some test text, DON'T JUDGE ME! " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber --height=300 --width=300)
echo $xx

if [ $xx == Firefox ]; then
	echo "test balloon"
elif [ $xx == Pidgin ]; then
	echo "test balloon2"
fi
```

---

### Post by kingbilly on 2009-11-06
spaces correct, watch out for the double ==

```
#!/bin/bash

xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Just some test text, DON'T JUDGE ME! " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber --height=300 --width=300)
echo $xx

if [ $xx = Firefox ]; then
	echo "test balloon"
elif [ $xx = Pidgin ]; then
	echo "test balloon2"
fi
```

---

### Post by dmillerw on 2009-11-06
Thank you very much, can't believe it was something so simple

---

### Post by dmillerw on 2009-11-07
Got two more questions now

1. How would i make the script restart once it gets to the end of the "elif" commands

2. How to I keep the variable values upon said restart

---

### Post by yousillygoose on 2009-11-07
To make the script restart at the end of the elif, I'd probably through a while loop in there at the start of the script, and have it loop only if a value isn't set (if someone in the if loop isn't met, the while loop will loop the whole script again).

---

### Post by dmillerw on 2009-11-07
> **yousillygoose said:**
> To make the script restart at the end of the elif, I'd probably through a while loop in there at the start of the script, and have it loop only if a value isn't set (if someone in the if loop isn't met, the while loop will loop the whole script again).
Could you explain the code needed?

---

### Post by yousillygoose on 2009-11-07
I'll do my best.  I'm no expert coder so I can get the job done, but there may be a better way.  

What part of your code would you want to loop (from what start point to what end point).  Also, is there any condition or part of the if loop, that if succeeds, you no longer want it to loop?

---

### Post by dmillerw on 2009-11-07
> **yousillygoose said:**
> I'll do my best.  I'm no expert coder so I can get the job done, but there may be a better way.  

What part of your code would you want to loop (from what start point to what end point).  Also, is there any condition or part of the if loop, that if succeeds, you no longer want it to loop?
```
#!/bin/bash

xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [ $xx = Firefox ]; then
	echo "$backupdir"
elif [ $xx = Pidgin ]; then
	echo "test balloon2"
elif [ $xx = XChazenityt ]; then
	echo "test balloon3"
elif [ $xx = Skype ]; then
	echo "test balloon3"
elif [ $xx = Gwibber ]; then
	echo "test balloon3"
elif [ $xx = Other ]; then
	echo "test balloon3"
elif [ $xx = Choose-backup-directory ]; then
	backupdir=$(zenity --file-selection --directory)
fi
```

I just want to look the "Choose-backup-directory" code, so it starts the code again after, well, choosing the backup directory

---

### Post by yousillygoose on 2009-11-07
> **dmillerw said:**
> ```
#!/bin/bash

xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [ $xx = Firefox ]; then
	echo "$backupdir"
elif [ $xx = Pidgin ]; then
	echo "test balloon2"
elif [ $xx = XChazenityt ]; then
	echo "test balloon3"
elif [ $xx = Skype ]; then
	echo "test balloon3"
elif [ $xx = Gwibber ]; then
	echo "test balloon3"
elif [ $xx = Other ]; then
	echo "test balloon3"
elif [ $xx = Choose-backup-directory ]; then
	backupdir=$(zenity --file-selection --directory)
fi
```

I just want to look the "Choose-backup-directory" code, so it starts the code again after, well, choosing the backup directory


So, after someone does any action in the if statmenet, the code goes where?  To the start? Or the code terminates unless someone hits choose-backup-directory?

---

### Post by dmillerw on 2009-11-07
> **yousillygoose said:**
> So, after someone does any action in the if statmenet, the code goes where?  To the start? Or the code terminates unless someone hits choose-backup-directory?
```
elif [ $xx = Choose-backup-directory ]; then
	backupdir=$(zenity --file-selection --directory)
fi
```

I'm focusing on this part, I simply want the script to restart once someone selects a backup directory

---

### Post by yousillygoose on 2009-11-07
This is one way to do it.  Tell me if it makes sense to you (or if I did something you didn't want).

```

#!/bin/bash
repeat=1
while [ $repeat = 1 ] ; do
repeat=0
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [[ $xx = Firefox ]]; then
	echo "$backupdir"
elif [[ $xx = Pidgin ]]; then
	echo "test balloon2"
elif [[ $xx = XChazenityt ]]; then
	echo "test balloon3"
elif [[ $xx = Skype ]]; then
	echo "test balloon3"
elif [[ $xx = Gwibber ]]; then
	echo "test balloon3"
elif [[ $xx = Other ]]; then
	echo "test balloon3"
elif [[ $xx = Choose-backup-directory ]]; then
	backupdir=$(zenity --file-selection --directory)
	repeat=1
fi

done

```

---

### Post by dmillerw on 2009-11-07
> **yousillygoose said:**
> This is one way to do it.  Tell me if it makes sense to you (or if I did something you didn't want).

```

#!/bin/bash
repeat=1
while [ $repeat = 1 ] ; do
repeat=0
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [[ $xx = Firefox ]]; then
	echo "$backupdir"
elif [[ $xx = Pidgin ]]; then
	echo "test balloon2"
elif [[ $xx = XChazenityt ]]; then
	echo "test balloon3"
elif [[ $xx = Skype ]]; then
	echo "test balloon3"
elif [[ $xx = Gwibber ]]; then
	echo "test balloon3"
elif [[ $xx = Other ]]; then
	echo "test balloon3"
elif [[ $xx = Choose-backup-directory ]]; then
	backupdir=$(zenity --file-selection --directory)
	repeat=1
fi

done

```
Thanks so much, that did it!

:)

---

### Post by yousillygoose on 2009-11-07
Awesome :).  I also changed your brackets to double brackets (it was complaining when I ran it so it's needed).

If you have more questions, ask away :)

---

### Post by mo.reina on 2009-11-07
you could nest all your if arguments in a function and call that function once someone hits the choose backup option.

```
#!/bin/bash

[B]function menu_list
{[/B]
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [ $xx = Firefox ]; then
	echo "$backupdir"
elif [ $xx = Pidgin ]; then
	echo "test balloon2"
elif [ $xx = XChazenityt ]; then
	echo "test balloon3"
elif [ $xx = Skype ]; then
	echo "test balloon3"
elif [ $xx = Gwibber ]; then
	echo "test balloon3"
elif [ $xx = Other ]; then
	echo "test balloon3"
elif [ $xx = Choose-backup-directory ]; then
	backupdir=$(zenity --file-selection --directory)
        **$menu_lis**t
fi
**}**

**$menu_list**

```

i think that could work anyway.

---

### Post by mo.reina on 2009-11-07
@ yousillygoose: so the while command checks the argument (in this case [ $repeat = 1 ]) at the beginning and end of the loop?

---

### Post by yousillygoose on 2009-11-07
Yea, it starts by seeing that "repeat" is 1.  It then sets repeat to 0 to kill the loop and only repeats the loop if choose-backup-directory changes it back to 1.

Like I said, maybe not the best way to do it but it worked, hehe.

---

### Post by yousillygoose on 2009-11-07
@ mo.reina- Your way is definitely smarter coding than mine.  I fixed it so that it runs (the $ isn't needed to start the function).  Also, double brackets should be used.

```

#!/bin/bash

function menu_list
{
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [[ $xx = Firefox ]]; then
	echo "$backupdir"
elif [[ $xx = Pidgin ]]; then
	echo "test balloon2"
elif [[ $xx = XChazenityt ]]; then
	echo "test balloon3"
elif [[ $xx = Skype ]]; then
	echo "test balloon3"
elif [[ $xx = Gwibber ]]; then
	echo "test balloon3"
elif [[ $xx = Other ]]; then
	echo "test balloon3"
elif [[ $xx = Choose-backup-directory ]]; then
	backupdir=$(zenity --file-selection --directory)
        menu_list
fi
}
menu_list

```

---

### Post by dmillerw on 2009-11-07
Dang it.

Your old code worked for ahwile, then stopped when I added more, tried the new code, and get this

```
dmillerw@ubuntu://home/dmillerw/Desktop$ ./test5.sh
./test5.sh: line 27: syntax error: unexpected end of file

```
...with the closing bracket
```

dmillerw@ubuntu://home/dmillerw/Desktop$ ./test5.sh
./test5.sh: line 26: syntax error near unexpected token `}'
./test5.sh: line 26: `}'

```
...without it

```

#!/bin/bash

function menu_list
{
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [[ $xx = Firefox ]]; then
	echo "$backupdir"
elif [[ $xx = Pidgin ]]; then
	if [[ $backorrest = Backup ]]; then
	cd /$HOME/
	tar -cvvf /$backupdir/purple.tar .purple
elif [[ $xx = XChazenityt ]]; then
	echo "test balloon3"
elif [[ $xx = Skype ]]; then
	echo "test balloon3"
elif [[ $xx = Gwibber ]]; then
	echo "test balloon3"
elif [[ $xx = Other ]]; then
	echo "test balloon3"
elif [[ $xx = Choose-backup-directory ]]; then
	backupdir=$(zenity --file-selection --directory)
	menu_list

fi
}
menu_list

```

...current script

---

### Post by dmillerw on 2009-11-07
```
#!/bin/bash

function menu_list
{
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [[ $xx = Firefox ]]; then
	echo "$backupdir"
elif [[ $xx = Pidgin ]]; then
	echo "test balloon2"
elif [[ $xx = XChazenityt ]]; then
	echo "test balloon3"
elif [[ $xx = Skype ]]; then
	echo "test balloon3"
elif [[ $xx = Gwibber ]]; then
	echo "test balloon3"
elif [[ $xx = Other ]]; then
	echo "test balloon3"
elif [[ $xx = Choose-backup-directory ]]; then
	backupdir=$(zenity --file-selection --directory)
        menu_list
fi
}
menu_list
```

I tested this, and it worked, but as soon as I add anything, it breaks

---

### Post by yousillygoose on 2009-11-07
if [[ $backorrest = Backup ]]; then


I believe you need a "fi" to close this if statement.  Try:

```

#!/bin/bash

function menu_list
{
xx=$(zenity --list --title "Basic Ubuntu Preferences Backup" --text "Choose a program to backup, or choose "Other" to choose a specified folder " --radiolist --column "Choice" --column "Preferences to backup" 1 Firefox 2 Pidgin 3 XChat 4 Skype 5 Gwibber 6 Other 7 Choose-backup-directory --height=300 --width=300)

if [[ $xx = Firefox ]]; then
	echo "$backupdir"
elif [[ $xx = Pidgin ]]; then
	if [[ $backorrest = Backup ]]; then
	cd /$HOME/
	tar -cvvf /$backupdir/purple.tar .purple
	fi
elif [[ $xx = XChazenityt ]]; then
	echo "test balloon3"
elif [[ $xx = Skype ]]; then
	echo "test balloon3"
elif [[ $xx = Gwibber ]]; then
	echo "test balloon3"
elif [[ $xx = Other ]]; then
	echo "test balloon3"
elif [[ $xx = Choose-backup-directory ]]; then
	backupdir=$(zenity --file-selection --directory)
	menu_list

fi
}
menu_list

```

---

### Post by dmillerw on 2009-11-07
That did it, thanks...again.

:)

---

### Post by yousillygoose on 2009-11-07
No problem :).  Keep posting as issues come up.  I'll check back from time to time to try to help :)

---

