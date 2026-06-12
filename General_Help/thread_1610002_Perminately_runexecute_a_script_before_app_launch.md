---
title: "Perminately run/execute a script before app launch?"
date: 2010-10-31
forum: General Help
---

### Post by Quarkrad on 2010-10-31
**Newbie** - I have found a solution (for my set up) for getting incoming and outgoing video when using Skype.  I have a little script on my Desktop that I have to run first, then launch Skype for it all to work. What I would like to do is to move this script file somewhere other than on my Desktop and then configure the appropriate commands so that when I launch Skype from the Skype icon the script runs first and then the application.  Appreciate any help with these changes.

---

### Post by Verbeck on 2010-10-31
how about a shell script?
```

#!/bin/bash
script here
sleep 5 &&
skype

```

---

### Post by Quarkrad on 2010-10-31
Thank you for your reply.  I am sorry -I'm a newbie so need a bit more help.  I have file on my desktop called **skypescript** that I have to run before I launch Skype.  I guess I could put skypescript anywhere to get it off my Desktop. I think I know what a shell is (probably not!) so at this point I'm not sure what to do with 

#!/bin/bash
script here
sleep 5 &&
skype

do I create a file and put these commands in it?  As a newbie I cannot see where this goes and how it relates to the **skypescript** file.  Thanks again.

---

### Post by Verbeck on 2010-10-31
sorry for the lack of explanation 

just create a file called skypestart.sh in your home folder
in it, past **#!/bin/bash** on the first line
in the second line, give a link to your skypescript. eg **sh /home/username/Desktop/skypescript**
then add **sleep 5 &&** 
after that, add **skype**
then save it. in its properties window in the permissions tab, check the allow executing file as a program

so every time the skypestart.sh is run, it would run both the script and skype. if you want, you can add a launcher to the desktop too

EDIT : btw, what kind of script are you running now?

---

### Post by Quarkrad on 2010-10-31
A couple of things - it works so thanks.

[LIST]
[*]I did what you said, creating skypescript.sh in my home directory.  I copied it (copy/paste) onto my Desktop as a launcher and even gave it a Skype icon so it looks like you are launching Skype.  I'm not sure this is the best method of putting the skypestart.sh launcher on the Desktop because when I double click it I get a window giving me the option to run it by **Run in Terminal**, **Display**, **Cancel**, **Run** Is there a way of when double clicking it goes straight to the Run option and launches the Skype application?
[/LIST]

[LIST]
[*]Out of interest - what does the line **sleep 5 &&** do?
[/LIST]

Re my original script I followed a post on this video Skype problem and it worked for me. What I did was:

Create a script with the contents:
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
/usr/bin/skype


Make this script executable with  chmod u+x scriptname.

In my case I called the script skypescript.

---

### Post by rnerwein on 2010-10-31
hi
i ain't your script but the sytax for backround procs in a scrip as i know is
e.g. sleep  n &
only one "&"
ciao

---

### Post by Verbeck on 2010-10-31
sorry about the double '&' . i copied it from my first post, in which i made the mistake. (wouldn't cause any trouble anyway)
it tells the computer to wait 5 seconds before doing anything else. you can make it 1 or 2

as for the launcher issue, i dont know about lxde, but in gnome when you right click on the desktop, there's a create launcher option.

also, the command /usr/bin/skype in the first script should also start skype. are you sure that the file is marked as an executable?

---

### Post by Quarkrad on 2010-10-31
It wasn't executable!  All works now  many thanks.

---

