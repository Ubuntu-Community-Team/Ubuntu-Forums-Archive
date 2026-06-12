---
title: "bash broken, lost functionality in Terminal (gnome-terminal)"
date: 2010-12-09
forum: General Help
---

### Post by Slinkee2k on 2010-12-09
FIXED: Please scroll to the last post for the solution. Thanks!

[FONT=Arial][SIZE=2]Hello, Linux-goers. I did some research on this, but I am still fairly new to  Linux. In Ubuntu 10.10 (Maverick), I accidentally overwrote my  "/bin/bash" file. :( Dude, using "sudo" with a small typo can work disasters. :p Bash is now broken in the  Terminal (gnome-terminal). Terminal itself still works fine, technically, but *bash *is still hosed/broken. Here is what I did to try to  fix it:
[/SIZE][/FONT] 
[LIST]
[*][FONT=Arial][SIZE=2]Booted from  Ubuntu 10.10 live CD. Mounted my Ubuntu partition and manually copied  the good/fresh "bash" file onto my hard drive. Verified copy was  successful. Didn't help, as you see.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Reinstalled "gnome-terminal" using synaptic package manager.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Tried  to reinstall bash via synaptic, it failed with error, "E:  /var/cache/apt/archives/bash_4.1-2ubuntu4_i386.deb: subprocess new  pre-removal script returned error exit status 2"[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]
In Terminal, all basic commands work as far as I can tell. ("ls", "pwd", navigation, etc.) Here are some problems:[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]My "username@computername" does not display in the prompt; only the $ sign.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Bash keyboard shortcuts such as uparrow and tab do not work. Instead, each inserts a key code. I can't even move the cursor left/right.
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Aliases (a function of bash and .bashrc) are broken, of course.
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]My sanity level decreases when I use Terminal now.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]For what it's worth, even with "sudo" I get a "permission denied" error when trying to run Google Chrome! :confused:
[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]I read  something about a ".bashrc" file being a possible problem, but I don't  know how to make it work, or the file's proper locations in Ubuntu 10.10. Is there something I can do with a "make" or "apt-get install" command  or something?? Could this simply be a permissions problem? Is the link to "/bin/bash", "/bin/sh", or a ".bashrc" file broken?  Guide me, oh  Linux gurus.

Thanks!

P.S. I always wondered what exactly bash was and how it was different from the basic terminal. LoL, this is an excellent way to demonstrate the difference, and I WANT IT BACK! :-(
[/SIZE][/FONT]

---

### Post by Habitual on 2010-12-10
just rename your .bashrc on the broken shell user.

Logout and back in as original user.

Let us know...

---

### Post by Slinkee2k on 2010-12-10
Thanks! I'm stuck at work without the computer 'til 4pm EST today, so I'll respond asap afterward. I'm ecstatic to have a response. ^_^

Response to below: got it! ^_^ thanks again. What's that feature called where the OS automatically restores missing files? ;) it's like WFP in Windoz$.

---

### Post by Habitual on 2010-12-10
you're welcome. Better refresh this post/answer b/c I changed it after testing it.

Just rename .bashrc. ;)

and verify perms of 
ls -al /bin/bash
-rwxr-xr-x 1 root root 801808 Aug 10 2010  3:58 PM /bin/bash

---

### Post by Habitual on 2010-12-10
> **Slinkee2k said:**
> Thanks! I'm stuck at work without the computer 'til 4pm EST today, so I'll respond asap afterward. I'm ecstatic to have a response. ^_^

Response to below: got it! ^_^ thanks again. What's that feature called where the OS automatically restores missing files? ;) it's like WFP in Windoz$.

There isn't one, AFAIK.

Linux assumes you know what you're doing. 
Just get "better" at doing it. :)

---

### Post by Slinkee2k on 2010-12-10
> **Habitual said:**
> There isn't one, AFAIK.

Linux assumes you know what you're doing. 
Just get "better" at doing it. :)

Well in that case, once I get this darn thing working, I'm gonna make aliases for cp and mv that verify i want to overwrite a file next time -_- hahah I would have chosen not to if I were prompted! :P

---

### Post by Habitual on 2010-12-10
Great idea.

mv -i and cp -i are default on some distros.

---

### Post by Slinkee2k on 2010-12-10
> **Habitual said:**
> Great idea.

mv -i and cp -i are default on some distros.

Thanks. If they were default on *all* distros, this would not have happened. :-/ O well! At least it gives me LinuXP points. ^_^
EDIT: make that "Linuxperience Points" short as "LinuXP". :P I'll be home around 7pm EST.

---

### Post by Slinkee2k on 2010-12-10
Welp, no dice. I renamed it. I had an inkling it wouldn't work because it seems bash isn't even running, much less accessing that file, and the contents look fine anyway. Any stuff to try?  What happens if I break the bash executable in /bin/? What dependencies are broken? I am thankful for all suggestions.
Thanks!

---

### Post by Habitual on 2010-12-11
Either wait for someone else to help out here, or head over to askubuntu.com and post the contents of your original post. You'll get a high-quality answer pretty quickly there.

Sorry!

---

### Post by Slinkee2k on 2010-12-12
Question re-posted here: [http://askubuntu.com/questions/17056/broken-bash-overwrote-bin-bash-whoops-replaced-bash-but-still-broken](http://askubuntu.com/questions/17056/broken-bash-overwrote-bin-bash-whoops-replaced-bash-but-still-broken)

Thanks, all. Any attempt at helping me is appreciated.

---

### Post by jwbrase on 2010-12-12
Part of the problem you're probably running into here is that the system uses bash to interpet a lot of system scripts, including ones included in package files that are run when those packages are installed or removed. It just so happens that one of your error messages indicates that the preremoval script for the bash package is failing when you try to reinstall bash through synaptic. Looking through the deb for that package, it turns out that the prerm script does have "#!/bin/bash" as its first line, which means it's telling the system to run it with bash. Well, since bash isn't working, the script chokes.

Somebody might know the "deep magic" required to fix this situation, but bash doesn't just provide you with an interface to the system, it also, as I said, runs scripts that do a lot of "under the hood" stuff, to the point that I'm surprised you haven't seen much breakage in other places than the terminal yet. I have the feeling that the simplest fix might just be to back up your /home directory and reinstall Ubuntu.

---

### Post by Slinkee2k on 2010-12-12
[SIZE=6]FIXED IT![/SIZE] [SIZE=3]
I successfully reinstalled bash in Ubuntu Linux 10.10. Here's how:[/SIZE]


[LIST]
[*] I booted to the Ubuntu 10.10 Live CD
[*]From within Live Ubuntu, I mounted my Linux  partition in /mnt/disk
[*]Perhaps most importantly, I then did a "chroot" to /mnt/disk
[*]From there, I  was able to use "sudo apt-get install bash" to successfully install it! :D
[/LIST]
Thanks. This one was kind of a nightmare. I learned a lot. Nothing would allow changes to the "bash" installation from within that running operating system. By the way, I read in multiple places that /bin/sh is supposed to be a link to bash, but in this distro, it is supposed to link to "dash" (the simple shell). Right? Anyway, happy Linux to all. Good night.

P.S. Good lessons I learned the hard way:

[LIST]
[*]Keep another instance of Terminal open in case you break the Terminal so it won't open, which I did during this escapade. Don't close it. Do the same for your web browser. lol
[*]Programs/features such as *bash* are treated as "Essential" by the operating system, and may be difficult to uninstall/reinstall from within the OS on that drive. This isa situation where the Live CD is needed.
[*]cp and mv (copy and move commands) do not verify whether you actually want to overwrite a file- they just do it without asking, unless you use "cp -i" and "mv -i" respectively. Had "cp" asked whether I wanted to overwrite /bin/bash, I would have said NO in the FIRST place! ;P
[/LIST]
```
# use the following aliases to make it so copy and move commands will ASK you before proceeding with an overwrite, instead of just doing it.
alias cp='cp -i'
alias mv='mv -i'

```


> **jwbrase said:**
> Part of the problem you're probably running into here is that the system uses bash to interpet a lot of system scripts, including ones included in package files that are run when those packages are installed or removed. It just so happens that one of your error messages indicates that the preremoval script for the bash package is failing when you try to reinstall bash through synaptic. Looking through the deb for that package, it turns out that the prerm script does have "#!/bin/bash" as its first line, which means it's telling the system to run it with bash. Well, since bash isn't working, the script chokes.

Somebody might know the "deep magic" required to fix this situation, but bash doesn't just provide you with an interface to the system, it also, as I said, runs scripts that do a lot of "under the hood" stuff, to the point that I'm surprised you haven't seen much breakage in other places than the terminal yet. I have the feeling that the simplest fix might just be to back up your /home directory and reinstall Ubuntu.
I know, seriously. I really put things to the test here. The only thing that I witnessed as being broken other than bash was Google Chrome. :P

---

### Post by Habitual on 2010-12-12
You go, Boy-eeeeeeeee!

Glad you got it fixed.

Isn't askubuntu.com the bomb? \\:D/

---

