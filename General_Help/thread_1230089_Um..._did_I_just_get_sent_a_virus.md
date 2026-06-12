---
title: "Um... did I just get sent a virus?"
date: 2009-08-03
forum: General Help
---

### Post by Grant A. on 2009-08-03
I was talking on FreeNode, when I noticed this.

Is this anything to worry about?

---

### Post by cariboo on 2009-08-03
I really doubt it, I would suggest you run strings on the file to see if anything interesting turns up:

```
strings phear468.moo
```

---

### Post by Grant A. on 2009-08-03
This is the output I got:

```

grant@amethyst:~$ strings phear468.m00
strings: 'phear468.m00': No such file
grant@amethyst:~$ strings phear468.moo
strings: 'phear468.moo': No such file
grant@amethyst:~$ strings  phear468.moo
strings: 'phear468.moo': No such file
grant@amethyst:~$ strings  phear468.m00
strings: 'phear468.m00': No such file
grant@amethyst:~$ 

```

Is this good?

---

### Post by schauerlich on 2009-08-03
> **Grant A. said:**
> This is the output I got:

```

grant@amethyst:~$ strings phear468.m00
strings: 'phear468.m00': No such file
grant@amethyst:~$ strings phear468.moo
strings: 'phear468.moo': No such file
grant@amethyst:~$ strings  phear468.moo
strings: 'phear468.moo': No such file
grant@amethyst:~$ strings  phear468.m00
strings: 'phear468.m00': No such file
grant@amethyst:~$ 

```

Is this good?

All that means is that it couldn't find the file you were talking about. Make sure you're in the right directory.



Sounds like you want this to be a virus.

---

### Post by chris4585 on 2009-08-03
He sent you a file through DCC, turn DCC off and you shouldn't get this again.

---

### Post by Grant A. on 2009-08-03
> **EDavidBurg said:**
> Sounds like you want this to be a virus.

Nevermind about that, just forget that I said that.

---

### Post by ToyImp on 2009-08-03
> **Grant A. said:**
> I was talking on FreeNode, when I noticed this.

Is this anything to worry about?

Oddly I just got back to my computer and I had this same thing popup. I use xChat though but the file didn't download at all since I wasn't here to confirm it. I'd imagine it was just some script kiddie trying to open a back door.

---

### Post by credobyte on 2009-08-03
And what he would do after a successful file delivery ? File can't execute itself without your permission ( ssh, physical access, etc. ) .. :-k

---

### Post by Soul-Sing on 2009-08-03
> All that means is that it couldn't find the file you were talking about. Make sure you're in the right directory.

probl.   ./xchat2/downloads

---

### Post by bobince on 2009-08-03
> DCC aborted receiving file phear468.m00 from Flloder001

That is, the transfer was unsuccessful and you never received the file in the first place. I'm not sure about how irssi does it, but it looks to me like Flloder001 offered you a file and you didn't take it, so the SEND request was aborted later when Flloder001 disappeared.

---

### Post by Zorael on 2009-08-04
To find the file (if you really don't know where it ended up);
```
$ sudo updatedb         # will index your mounted partitions and save a database of the files and directories, will take a minute or three
$ locate phear468.m00
```

---

