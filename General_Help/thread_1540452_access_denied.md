---
title: "access denied"
date: 2010-07-27
forum: General Help
---

### Post by themordy on 2010-07-27
i did a search and nothing i found seemed to relate to my issue. i am simply trying to change a couple of icons. i tried to change the screenlets.svg to a different image and got an error message that my access was denied. so, i tried a different way and got a message telling me that i am "not the owner", which is funny because i am the ONLY user on this machine. is there any way past this error?

---

### Post by Goolie on 2010-07-27
> **themordy said:**
> i did a search and nothing i found seemed to relate to my issue. i am simply trying to change a couple of icons. i tried to change the screenlets.svg to a different image and got an error message that my access was denied. so, i tried a different way and got a message telling me that i am "not the owner", which is funny because i am the ONLY user on this machine. is there any way past this error?

find the file in the terminal

when you get in that folder 

try using the chmod command to change the permissions on the files in question.

---

### Post by themordy on 2010-07-27
i suppose i should have followed the instructions for posting and let you guys know i'm fairly new to this. i'm figuring most things out, but i don't know how to find files in the terminal or change permissions. any guides around that i didn't see on this sort of thing?

---

### Post by OnlineBuddy on 2010-07-27
> **themordy said:**
> i did a search and nothing i found seemed to relate to my issue. i am simply trying to change a couple of icons. i tried to change the screenlets.svg to a different image and got an error message that my access was denied. so, i tried a different way and got a message telling me that i am "not the owner", which is funny because i am the ONLY user on this machine. is there any way past this error?
.
i could understand your situation very well....i am also a new ubuntu user..
.
to do everyday task in ubuntu u should learn some commands like(cp,chmod,rm,mkdir,sudo,gksu,gedit,....) type->  (man <*your command*>)...to get help
because working only with desktop could be very frustating...
.
.

---

### Post by arpanaut on 2010-07-27
This:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

is probably the most important thing for a beginner to Ubuntu to learn!

You are probably trying to change/edit system files which require admin. permissions.
Messing around with chmod, chown etc. on system files in linux can get you into troubles that you really don't want to deal with.

---

### Post by themordy on 2010-07-27
thanks i will take a look though it. it's not a huge deal at the moment. i just wanted to changed that giant screenlets icon to a smaller one that fits more into my theme.

---

### Post by Goolie on 2010-07-27
Go to Applications --> Accessories --> Terminal

at the terminal you'll be able to write onto a command line. . .

First, open your file browser and work on getting an idea of where the file you want to change permissions to lays.

So, let's just say it's on your Desktop.

now back in the terminal and you'll type your first command for the day. . .

```
ls 
```Ls will let ya know what files are in your current directory, kind of like a 'list' "ls" which is default your home folder. . .

your Desktop is like a folder that contins files, so we'll need to get into that directory!

next, you'll be using the cd command to 'change directory'

we'll need to 

```
cd /Desktop
```
your files will be in this directory and just bingo bango 

```
chmod ugo+rw filename.extension 
```ls = list
cd = change directory
chmod = change mode (or permissions, rather)

look them up, cd has alot of other options, but you'll have to read up more about these commands in order to learn more about options / arguments. . . 

good luck

---

### Post by themordy on 2010-07-27
> **Goolie said:**
> Go to Applications --> Accessories --> Terminal

at the terminal you'll be able to write onto a command line. . .

First, open your file browser and work on getting an idea of where the file you want to change permissions to lays.

So, let's just say it's on your Desktop.

now back in the terminal and you'll type your first command for the day. . .

```
ls 
```Ls will let ya know what files are in your current directory, kind of like a 'list' "ls" which is default your home folder. . .

your Desktop is like a folder that contins files, so we'll need to get into that directory!

next, you'll be using the cd command to 'change directory'

we'll need to 

```
cd /Desktop
```
your files will be in this directory and just bingo bango 

```
chmod ugo+rw filename.extension 
```ls = list
cd = change directory
chmod = change mode (or permissions, rather)

look them up, cd has alot of other options, but you'll have to read up more about these commands in order to learn more about options / arguments. . . 

good luck

all went well until i got this..
> chmod: changing permissions of `screenlets.svg': Operation not permitted

so back to square one

---

### Post by bodhi.zazen on 2010-07-27
> **Goolie said:**
> find the file in the terminal

when you get in that folder 

try using the chmod command to change the permissions on the files in question.


You should NOT be changing ownership or permissions of system files. System files == anything outside of your home directory.

To edit system files, use sudo for command line editro (nano, vim) and gksu for graphical applications (gedit, nautilus, etc).

For Linux permissions see:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Linux permissions are almost always one of the first things new users run up against ...

For root / sudo / gksu see the rootsudo link 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by themordy on 2010-07-30
> **bodhi.zazen said:**
> You should NOT be changing ownership or permissions of system files. System files == anything outside of your home directory.



not even just an icon? i can't even figure out why in the world it's a root file anyway. it's just an icon. shouldn't you be able to change those to your liking? isn't that half the point of open source anyway? lol. anyway, i still haven't figure out how to replace that stupid icon. it drives me nuts up there being completely out of whack with all of the others. that and desktop drapes. drives me nuts. i like a CLEAN and completely themed look. those 2 icons are the only thing keeping me from that!

---

### Post by -kg- on 2010-07-30
This may be a bit obvious, and you may have already tried this, but have you tried the Ubuntu Help (the question mark icon on the top panel)?  I'm currently doing a major partitioning operation from the Live CD, but I pulled up Help and typed "icons" in the search box and came up with some promising looking entries, like:

> GNOME Audio Profiles Manual
    Modifying the Icon Setting for a Theme

and...

> Configuration Editor Manual
    icons and key types

I'll check them out when I get back into my regular installation, but those look promising.  It just takes too long to access all that while on the Live CD.

---

### Post by bodhi.zazen on 2010-07-30
> **themordy said:**
> not even just an icon?

No, not even for an icon.

First, I highly suggest you stop and learn about Linux permissions Linux permissions are one of the foundations of security.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Second, you need to decide where you wish to keep your theme / icons. If you wish them to be available to only your user, keep them in your home folder, either in .themes or .icons, I do not know off the top of my head. In that case you should keep ownership of the icon or theme.

If you wish to install a theme or icon available to all users, use root and install the theme or icon into system directories. In that event the file should be owned by root. To save such a file as root in a system directory, either use sudo or gksu

```
sudo cp your_icon /usr/icons/your_icon
```or

```
gksu nautilus
```See the classic link for further information:

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

So, no, changing ownership or permissions of system files is both a bad habit and completely unnecessary. It is the wrong "solution" to the problem you face which is that you, as a new user, do not understand how Linux permissions work or how to add icons or themes in the "appropriate method".

With that said you are free to do as you wish with your system, I am just cautioning you that if you keep up your bad habit the end result is likely to be either a broken system or a security breach. In addition I am suggesting the is a more appropriate approach.

---

