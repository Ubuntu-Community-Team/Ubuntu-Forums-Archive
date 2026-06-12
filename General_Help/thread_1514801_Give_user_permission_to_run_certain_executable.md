---
title: "Give user permission to run certain executable"
date: 2010-06-21
forum: General Help
---

### Post by hogarth on 2010-06-21
Hi all,

Not too long ago i had questions about granting a specific non-admin user access to certain commands (such as aptitude update and safe-upgrade)... Well i got it figured out (thanks to others' answers), but now i've run into another problem...

I want the user 'gobbluth' (yes, an arrested development reference) to be able to run './mk' in any directory called 'code' or any sub-directory of 'code'. Just so you know, 'mk' is an executable which runs other executables 'seaicemodel' and 'plotmodel', depending on certain options ('e','o','r','i'). However, 'gobbluth' doesn't have admin privileges (and i like it that way), so i thought adding the following line to the 'sudoers' file would let him run './mk' without being prompted for a password:

```
gobbluth comp=(ALL)NOPASSWD:/*/code/* ./mk*
```Oh yeah, and the computer is called 'comp'. I figured i needed the asterisk to be able to add options (such as running './mk e'). Anyway, this doesn't seem to work, as the terminal so coldly tells me 'gobbluth' is not allowed to run that command as root...

What am i doing wrong?

Thanks in advance...

---

### Post by gzarkadas on 2010-06-21
You need to concatenate the two paths. But before you do, read carefully. And if in ambiguity, use the [HowTO: Sudoers Configuration]("http://ubuntuforums.org/showthread.php?t=1132821") guide for reference.

IMO with this setup **you give gobbluth the ability to run any command in your system as [COLOR=Red]root[/COLOR]**, which is certainly **[COLOR=Red]bad[/COLOR]** (he/she just has to copy any binary in any directory and rename it mk<something> or make a `code' subdirectory anywhere and place anything in it !).

To achieve a reasonable safety (since the user is untrusted) you will have to supply **absolute** (ie starting from /) and **unambiguous** path names for the executables he/she is allowed to execute. In addition, you should limit, using standard unix permissions, his/her ability to modify the executable or write to the directories where he/she can execute mk (because then it would be possible to create and name mk any executable he/she would wanted).

So, in minimum:

1. _Try to enumerate all possible options and arguments passed to mk to avoid ending your command with a `*'._ Note also that **just having spaces** **is not safe** (ie add some options and then a *); I just executed a script with spaces in my path named "this is a test" issuing `this\ is\ a\ test' in the command line

2. _Supply a starting path for the directory under which all mk executables will be located. _That is limit the permissions to just a subtree of your filesystem.

```

gobbluth comp=(ALL)NOPASSWD:/<where is your code rooted>/*/code/*/mk <options1> <arguments1>,/<where is your code rooted>/*/code/*/mk <options2> <arguments2>,...

```3. _Do not just depend on sudo (because here you give broad power); use file permissions to complement it and enforce policy._ If possible, do not allow the user to write anything inside the entire subtree; if your needs are different you'll have to review the situation carefully.

4. _Test your setup_. Create another user account for you and give sudo permissions + limit unix permissions first to this one; login as that user and try to circumvent security with any means that you aware of. See the results. Maybe post your setup here to get peer-review by the community. Watch especially for symlinks going oustide the subtree, for suid programs accesible by the user, or low level utilities.

Finally, give it some thought; you may be able to desing another, less permissive arrangement to complete the task. If yes, then go that way (regarding security the simpler is usually the better).

---

### Post by hogarth on 2010-06-22
Thanks gzarkadas, i appreciate all the info.

The main reason it wasn't working is (from looking at the code you supplied) i was typing './mk *' instead of specifying 'mk' in the pathname and then providing the options/arguments as necessary. After changing it to something resembling the code you supplied it seems to work fine.

I'm definitely going to add more security, i just wanted to make sure the ending part worked first. I will be limiting the directory containing the sub-directory 'code' to his ~ (/home/gobbluth), as well as specifying all the options of mk (since there are only 5 of them and i guess that wouldn't take much effort) so that he can only use those commands. Thanks for supplying the code to make that happen...

As for file permissions, i'm fine with him doing whatever he wants in there. In fact, in order for 'mk' to run properly, he needs to be able to write and delete files in any sub-directory of his home directory. As for 'mk' itself, it has read-only permissions. And i'm also letting him have the 'code' sub-directory anywhere within his home directory, since he tends to move things around a lot (bad habits).

Anyway, here's what i ended up doing:
```
gobbluth comp=(ALL)NOPASSWD:/home/gobbluth/*/code/*/mk r,/home/gobbluth/*/code/*/mk e, etc...
```

On a separate note, i'm almost certain that there's no way for a non-admin user to view the 'sudoers' file. Is that true? I'm curious because i would think the only way a non-admin user could find out what he can and can't do is by randomly typing certain commands and seeing what is/isn't denied... Let me know if i have that wrong...

Thanks again!

---

### Post by gzarkadas on 2010-06-22
By default /etc/sudoers has `-r--r----- root root ' permissions so it is not readable; do a `ls -la /etc/sudoers' inside a terminal to verify, just in case. But you shouldn't rely on this (obscurity) for security; besides you have just published your setup in a global medium, so obscurity has already gone with the wind ;).

Since you do not have an ending * in your allowed commands, I suppose (following the guide I linked in my first post) that this setting would be ok if the user could not write to directories (ie create files) in that path. But since he/she has that right, imagine the following easy to create scenario:

1. Make a code folder anywhere inside his/her home folder and whatever subfolders he/she wants.

2. Inside there, the user can either copy an administrative binary from /bin, /sbin, etc and rename it to `mk r' or whatever else allowed or, even better, create a shell script with that name and perform whatever action he/she wants.

IMO **this setup is inherently unsafe and you should not use it**, even if it were for your normal account; it makes easy for an attacker to completely compromise your system. 

You must find a way to move the executables outside of the /home hierarchy, in a part of the filesystem where only root can write (such as /usr/local/bin). A possible solution is to do just that and replace mk inside the home folder with a script, which the user will execute under his/her account, thus no need to put it in /etc/sudoers. Say something like this:

```

#!/bin/bash
CURDIR=$(dirname $0)
# since /usr/local/bin is on path no need to specify it
pushd $CURDIR

mk r   <or whatever; since this will be in sudoers it will run without asking password>

popd

```

You **must** also move every executable that mk calls outside of the /home hierarchy, in a part of the filesystem where only root can write for the very same reasons; the user can easily replace them with something malicious. If the path is needed, use the same technique as above.

---

### Post by hogarth on 2010-06-24
Thanks again gzarkadas for all the info. As you can tell i'm new to all these sysadmin responsibilities and whatnot. I will incorporate your suggestions as i continue to do these sorts of things...

And just to let you know, it's me and a friend that are users on this system, and we're taking turns learning administrative duties and doodling around with the non-admin user. Right now it's his turn to be 'gobbluth', while i'm 'sysadmin'... I may not be too bright, but i would know to avoid putting actual usernames, hostnames, and command names out on the internet --- the only person who can screw up the computer by taking advantage of a security hole is me or 'gobbluth'. The comp isn't connected to the internet.

In any event, thanks for the advice! It's definitely appreciated, for i'm still learning the basics...

---

