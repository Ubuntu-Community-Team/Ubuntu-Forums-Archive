---
title: "Problem Loading Programs..."
date: 2006-03-19
forum: General Help
---

### Post by bushnate on 2006-03-19
I Run Ubuntu v 5.1 with a Gnome desktop. For some reason, Some programs don't run such as the Package Installer, Most system applications, some programs, and terminal commands sometimes don't execute. Sometimes it starts to load, but it never displays or runs. Why isn't it working?

---

### Post by willemmerson on 2006-03-19
I have the same problem exactly - I almost gave up on Ubuntu because of it but decided it was probably something I was doing wrong.

---

### Post by bushnate on 2006-03-19
Oh, also. i am a very basic Linux user, so everytihng has to be pretty dumbed down. But any suggestions, solutions will be helpful! Its kind of annoying not to be able to use Symnatic and change some properties!

Things like firefox, gaim, and open office seem to work correctly but other programs don't load at all.

---

### Post by Ramses de Norre on 2006-03-19
did you do a server install?
Are you logging in with an extra created user?
In both cases you'll need to edit the sudoers file or add the users to the admin group.

---

### Post by bushnate on 2006-03-19
no, i have a normal install. and the user i created is in the admin group. It was actually working for a bit, even after I added all the repositories and updates. But shortly after, when i decided i wanted to add some more programs, it wouldn't load. and many other things would not load, but some programs still would. that's why it confuses me, because some tihngs load and some things don't.

---

### Post by jerrykenny on 2006-03-19
maybe you've run out of diskspace, ?

Got to Applications, accesories,terminal, and type

df

hit enter and see if all your partitions have some free space . . . . .

---

### Post by bushnate on 2006-03-19
No, I already checked this possiblity. I have plenty of space. at least 7.0 GB on my system folder and 21.0 GB left on my /home folder.

It must be something else, and It is frustrating me quite a bit :twisted: .

Any other suggestions?

---

### Post by bushnate on 2006-03-19
Is it possible that there are zombie programs running in the background preventing the programs from running? is there a cmd to see the processes running? Or does anyone else have any solutions for this? I'd like to be able to use ubuntu and having half the programs not work is making it difficult!

---

### Post by bushnate on 2006-03-19
I think i found the reason... somehow, i managed to remove my name from the admin usergroup and it changed the root password... so i think now i'm screwed, even beyond linux wizard's help. i might just re-partition and try again...

---

### Post by bushnate on 2006-03-19
localhost sudo greatnate : command not allowed ; TTY=unknown ; PWD=/home/greatnate ; USER=root ; COMMAND=validate

I have that as an error message, and i think that somehow i managed to set the root password to nothing, but sudo doesn't accept that. I'm not sure what to do as in i can't seem to re-add myself to the admin group and get everything under control again. I don't even know how it happened, i awsn't messing with the root password, i was pretty sure it was the same as the first person i logged in as. is it possible it got corrupted somehow? i'm looking through the logs, and i can find no indication of it changing the root password. I'm SO stuck!

---

