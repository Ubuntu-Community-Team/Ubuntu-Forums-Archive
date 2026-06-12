---
title: "cant remove keyboard shortcut....HELP!!"
date: 2010-04-11
forum: General Help
---

### Post by busyboy_1123 on 2010-04-11
i set delete as a keyboard shortcut for the gnome-terminal accidentally and later changed it to ALT+T but now both DELETE and ALT+T open up a terminal 

its really annoying not to be able to use the delete key.....every time i press DELETE a terminal window opens up  

does anyone know how to fix this :confused:

thanks for the help in advance.....

---

### Post by stinkeye on 2010-04-12
> **busyboy_1123 said:**
> i set delete as a keyboard shortcut for the gnome-terminal accidentally and later changed it to ALT+T but now both DELETE and ALT+T open up a terminal 

its really annoying not to be able to use the delete key.....every time i press DELETE a terminal window opens up  

does anyone know how to fix this :confused:

thanks for the help in advance.....
In keyboard shortcuts click on the shortcut for run in terminal and when it
shows *New shortcut...* hit the backspace key.
Where did you set the shortcut?

---

### Post by busyboy_1123 on 2010-04-12
> **stinkeye said:**
> In keyboard shortcuts click on the shortcut for run in terminal and when it
shows *New shortcut...* hit the backspace key.
Where did you set the shortcut?

already tried it .....'run a terminal' shows 'disabled' in the shorcuts menu ........but still pressing DELETE opens a terminal
(i set the shorcut from system>>preferences>>keyboard shortcuts)

---

### Post by stinkeye on 2010-04-12
> **busyboy_1123 said:**
> i set it (and later removed it ) in system>>preferences>>keyboard shortcuts

but still the DELETE key opens up a terminal though the shortcut does not show up in system>>preferences>>keyboard shortcuts
As a test I added the delete key as the shortcut for run in terminal and 
it would open the terminal.
I then disabled the shortcut and delete worked as normal.
Maybe you have to disable the shortcut first before adding
ALT+T as your shortcut,so it clears the delete key back to normal.

---

### Post by akakingess on 2010-04-12
Just to add a suggestion, is there a .conf file located somewhere that stores that info, and if so you maybe could trash it (hopefully it rebuilds on itself) and then just start from scratch, this is just in case stinkeye's option doesn't work. Worth a shot and just a suggestion.

---

### Post by busyboy_1123 on 2010-04-12
> **stinkeye said:**
> As a test I added the delete key as the shortcut for run in terminal and 
it would open the terminal.
I then disabled the shortcut and delete worked as normal.
Maybe you have to disable the shortcut first before adding
ALT+T as your shortcut,so it clears the delete key back to normal.

thanks for the quick reply......n guess i forgot to mention it earlier
i had added the shortcut as a custom shortcut called terminal ......then removed the custom shortcut 
then set 'run a terminal' to ALT + T ....later disabled this too trying to fix the problem....but it didnt workout:(

---

### Post by busyboy_1123 on 2010-04-12
> **akakingess said:**
> Just to add a suggestion, is there a .conf file located somewhere that stores that info, and if so you maybe could trash it (hopefully it rebuilds on itself) and then just start from scratch, this is just in case stinkeye's option doesn't work. Worth a shot and just a suggestion.

jus started using linux 2 days back ....so could you be more specific about this .conf file.....thanks for the suggetion though will try to look it up on the web

---

### Post by akakingess on 2010-04-12
Well, usually there is some sort of config file that holds all sorts of information including customizations, unfortunately I don't know where it is located, hopefully someone can help us out with that. Otherwise, I guess I will just keep looking, by the way, wherever it is it will be within a 'hidden' folder, so if you want to search yourself, make sure you can view hidden folders/files, CTRL + H should show the hidden stuff.

---

### Post by busyboy_1123 on 2010-04-12
hoping for the same.........meanwhile will try to learn more about this config file....

---

### Post by stinkeye on 2010-04-12
I just read in another thread where someone did a similar thing and after deleting the custom shortcut and **rebooting**, delete returned as normal.
[**_[COLOR="DarkRed"]http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8848554[/COLOR]_**]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8848554")

---

### Post by busyboy_1123 on 2010-04-12
> **stinkeye said:**
> I just read in another thread where someone did a similar thing and after deleting the custom shortcut and **rebooting**, delete returned as normal.
[**_[COLOR=DarkRed]http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8848554[/COLOR]_**]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8848554")

thanks !!! restarting did the trick.....

but still wish there was a message like "restart for the changes to take effect" or something it would have saved me the time n effort 

inspite of these small problems i really am begining to like ubuntu......:)

---

### Post by akakingess on 2010-04-12
Glad it work out for you, and keep on learning and you will begin to love it even more. Good Luck, and remember that the family here at the forums are always here for you!

---

### Post by stinkeye on 2010-04-12
No problem.I'm learning at the same time as trying to help.
You'll come across a few problems, but you'll find it's a far better experience using open source software.

---

### Post by busyboy_1123 on 2010-04-12
> **akakingess said:**
> Glad it work out for you, and keep on learning and you will begin to love it even more. Good Luck, and remember that the family here at the forums are always here for you!

thanks.......n the way people support each other here is jus great:KS

---

### Post by akakingess on 2010-04-12
One last thing, if you don't mind marking this thread as SOLVED, it is under the Thread Tools menu located at the top of the thread. Thanks and good luck!

---

### Post by stinkeye on 2010-04-12
> **akakingess said:**
> Glad it work out for you, and keep on learning and you will begin to love it even more. Good Luck, and remember that the **family** here at the forums are always here for you!
Geez, that sounded a bit Charles Mansonish creepy. :twisted:

---

### Post by akakingess on 2010-04-12
Wow, didn't mean to be creepy at all, just polite ;)

---

### Post by stinkeye on 2010-04-12
Nah, just joking.

---

### Post by busyboy_1123 on 2010-04-12
lol.......
@akakingess
i did take it in the polite sense....

---

### Post by akakingess on 2010-04-12
I do not get offended, so no need to do the ol' LOL, I love some good ribbing amongst one another. Yet another reason to enjoy these forums ;)

---

### Post by pablo180 on 2011-04-22
Had the exact same problem, set up delete as a keyboard shortcut for empathy (I was just trying to remove what was already there and accidentally set it as delete) then deleted the shortcut and then no matter what I did, delete no longer worked as delete. 

As the original poster pointed out, it would have be nice to have been told that I didn't need to waste 20mins working out how to fix it (and searching for answers) when a simple reboot would have done the trick (but why is a reboot even needed?). 

Thank god for Ubuntu forums (and backspace). Now I just need to reboot.

---

