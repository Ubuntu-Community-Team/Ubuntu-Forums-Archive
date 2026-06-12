---
title: "Frustrated beginner seeking help"
date: 2009-12-06
forum: General Help
---

### Post by shaffer17 on 2009-12-06
Very new to Ubuntu and not that computer savvy to begin with. My Ubuntu system was set up by a friend and I only know how to use the programs I have already. I've been trying to install sql-ledger but when I try to open a directory as the instructions call for it says it can not, permission is denied. I'm ok with it but it seems my system is overriding my decision on this one. I'm having a hard time figuring out how to post this msg. Oh its at the bottom.

---

### Post by MelDJ on 2009-12-06
did you try typing sudo before the command

---

### Post by shaffer17 on 2009-12-06
I didn't,  I give that a go. Thanks

---

### Post by shaffer17 on 2009-12-06
alright so I typed "sudo mkdir /usr/local/sql-ledger" and then it asked me for my password, I typed it in and pressed enter and nothing happened it just started another line like whats there when I first open the terminal.

---

### Post by MelDJ on 2009-12-06
just type the password. in terminal, the password is invisible (meaning there wont be any **)

---

### Post by shaffer17 on 2009-12-06
Alright. Sorry,  first timer. So once I do that, and press enter, is something supposed to happen? Or am I now in that new directory or do I need to go find it and open it?

---

### Post by chillicampari on 2009-12-06
> **shaffer17 said:**
> Alright. Sorry,  first timer. So once I do that, and press enter, is something supposed to happen? 



Yep, it should have made  the directory. It won't confirm or show anything back to you.

> Or am I now in that new directory or do I need to go find it and open it?You're not in it just yet. 

Is this the guide you are following? Just want to make sure we're looking at the exact same thing.

[http://www.sql-ledger.org/cgi-bin/nav.pl?page=source/readme.txt&title=README](http://www.sql-ledger.org/cgi-bin/nav.pl?page=source/readme.txt&title=README)

Also- it's  really important to make sure everything below (except for #6) is already installed and is all set up right before doing anything else.


 REQUIREMENTS:
 -------------
 1 - Perl, 5+
 2 - http server (Apache, NCSA, httpi, thttpd, ...)
 3 - SQL Server (PostgreSQL 7.1+)
 4 - DBD (DBD-Pg)
 5 - DBI
 6 - LaTeX (optional)

---

### Post by MelDJ on 2009-12-06
if you wan to move to to he folder just type cd the path. cd /home/owner/folder for example

---

### Post by shaffer17 on 2009-12-06
Yep. Oh Man, I have no idea if I have all that. Thanks for all your help. This is a lot more complicated than i thought. I think I'm gonna have to just have my friend who talked me in to ubuntu come by and help with all this. Thank you so much though. You saved me from spending the entire night banging my head into the monitor.

---

### Post by chillicampari on 2009-12-06
(edit- just saw the post above).

Yeah- it might be best to have the very first install be something you can do in Synaptic package manager, and once you get the hang of that move on to command line.

(original post below).

I'm almost out for the night, and this is kinda big for a first install (if you could, it might be best for the friend who set it up to help out) and if you are 100% sure everything else you need to do this is installed and running properly it might be good to:

Back up all of your really important stuff first.

Like MelDJ says, "cd" (change directory) moves you around, for example- 

cd /directory/subdirectory

takes you two levels in. There might be more or less directories depending on what the install guide has you do.


"pwd" will show you where you're at (print working directory- it won't actually print to a printer, just shows it on the screen).

"cd" 

on it's own takes you back to your home directory.

To see what's in a directory you'll want to run a "list":

"ls"

I'd get comfortable with using those before going on to the next step.

---

### Post by MelDJ on 2009-12-06
you might be interested in [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

happy learning though;)

---

### Post by shaffer17 on 2009-12-06
Right on thanks a lot. I would of been up all night on my own. Now I can just put it off until i get some local help. Thanks to all who helped me realize that. Seriously!

---

### Post by chillicampari on 2009-12-06
No problem, and the guide MelDJ linked to should be a great start to get familiar with things for when you want to dive on in.

---

