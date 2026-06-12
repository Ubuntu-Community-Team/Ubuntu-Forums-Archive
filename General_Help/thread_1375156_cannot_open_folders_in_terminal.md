---
title: "cannot open folders in terminal"
date: 2010-01-07
forum: General Help
---

### Post by mocatz187 on 2010-01-07
Hi.
Can anyone explain how I can gain access to folder in Ubuntus 9.10 terminal.
when I use a command like ./ Documents or ~/ Documents
The terminal only states that "There is a folder named Documents" but never lets me enter.
I can create a folder using the mkdir command and I can navigate that folder as long as that terminal session is active.
When I close out the terminal and try to reopen it denies acces the same way as mentioined above.
Do I need to set some type of access permissions or?
Thanks.

---

### Post by llawwehttam on 2010-01-07
lol. In the command line you need to use commands such as ```
cd
```to change directory and ```
ls 
``` to list files in the current or specified directory.
eg
```
cd ~/Music
``` to go to the music folder in your home, ( ~/ ) means 'home'.
```
cd /etc
``` to go to the /etc folder and so on.

If you are in your home directory then you can use ```
cd Documents
```or to get straight to another folder in documants called 'newcar'
```
cd Documents/newcar
```If you want to use the command line more then type 'help' into terminal and research all the commands listed. It will help you a lot in the long run.

---

### Post by llawwehttam on 2010-01-07
Just to add a link for others [http://ss64.com/bash/](http://ss64.com/bash/) is GREAT for learning simple commands. Helped me no end.

---

### Post by mocatz187 on 2010-01-07
Nice list of commands there.
I think maybe I wasn't paying close enough attention to what I was doing or maybe I need to take a nap!
Thanks.

---

