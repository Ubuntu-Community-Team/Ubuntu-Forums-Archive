---
title: "MP3 player is readonly?!"
date: 2010-01-22
forum: General Help
---

### Post by c0mput3r_n3rD on 2010-01-22
Hello all,

I'm having a problem with 2 of my MP3 players being readonly, so I can't put songs on and delete song.  I'm having the same problem in windoze too.  Any suggestions?

Thanks

---

### Post by c0mput3r_n3rD on 2010-01-22
> **sakura881220 said:**
> I'm wondering whether the format was wrong, you can have a formatting to have a try, could you please tell me what the problem with your computer?


The partition is type FAT, and reformatting would wipe out the O.S. of the MP3.... Not a good idea I don't believe.


EDIT:  Here's the error output of the command to cp my files to the MP3 player:


/media/KINGSTON/music/eminem/refill :cp *.wma /media/38*/Rap/Eminem 2>> ~/error.txt
cp: cannot create regular file `/media/3823-788E/Rap/Eminem/01 Forever.wma': Read-only file system
cp: cannot create regular file `/media/3823-788E/Rap/Eminem/02 Hell Breaks Loose.wma': Read-only file system
cp: cannot create regular file `/media/3823-788E/Rap/Eminem/03 Buffalo Bill.wma': Read-only file system
cp: cannot create regular file `/media/3823-788E/Rap/Eminem/04 Elevator.wma': Read-only file system
cp: cannot create regular file `/media/3823-788E/Rap/Eminem/05 Taking My Ball.wma': Read-only file system
cp: cannot create regular file `/media/3823-788E/Rap/Eminem/06 Music Box.wma': Read-only file system
cp: cannot create regular file `/media/3823-788E/Rap/Eminem/07 Drop the Bomb On \'Em.wma': Read-only file system

---

### Post by Vaphell on 2010-01-22
who is the owner of the mounted partition?

---

### Post by n0dix on 2010-01-22
Verifies the permissions of the files and the directory where you want to copy the files.

---

### Post by mr clark25 on 2010-01-22
you might try "sudo" in front of that command.
example:

sudo /media/KINGSTON/music/eminem/refill :cp *.wma /media/38*/Rap/Eminem\2

the space might also be giving you trouble. i replaced the space with "\" i think that should fix it. if it doesnt, try removing the space from the filename.

---

### Post by n0dix on 2010-01-22
> **mr clark25 said:**
> you might try "sudo" in front of that command.
example:

sudo /media/KINGSTON/music/eminem/refill :cp *.wma /media/38*/Rap/Eminem\2

the space might also be giving you trouble. i replaced the space with "\" i think that should fix it. if it doesnt, try removing the space from the filename.

the sudo command in before cp:
```
/media/KINGSTON/music/eminem/refill: sudo cp *.wma /media/38*/Rap/Eminem\2
```

---

### Post by c0mput3r_n3rD on 2010-01-22
I know about the sudo and I know about the file permissions it's not the issue.  Something else is going on here.  I've tried sudo chown [me] [name of device], I've tried sudo chmod 777 [name of device & files].  I've also tried sudo cp, but it's not a matter of permissions it's a matter of the device being read-only.  Any way to change that?

---

