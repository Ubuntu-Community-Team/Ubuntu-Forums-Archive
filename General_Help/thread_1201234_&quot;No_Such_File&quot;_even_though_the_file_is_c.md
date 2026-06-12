---
title: "&quot;No Such File&quot; even though the file is clearly there"
date: 2009-06-30
forum: General Help
---

### Post by sangaya on 2009-06-30
So first I show the file I want as in the current directory
```

randy@diablo:~/.juniper_networks/network_connect$ ls -l ncs*
-rwxr-xr-x 1 root root 1167208 2009-03-11 08:40 ncsvc

```

Now I verify that a program can interact with it, and tell me it's type
```

randy@diablo:~/.juniper_networks/network_connect$ file ncsvc 
ncsvc: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

```

Now I'll even take a look at the beginning of the file's contents
```

randy@diablo:~/.juniper_networks/network_connect$ xxd ncsvc | head
0000000: 7f45 4c46 0101 0100 0000 0000 0000 0000  .ELF............
0000010: 0200 0300 0100 0000 80d5 0408 3400 0000  ............4...
0000020: e0ca 1100 0000 0000 3400 2000 0800 2800  ........4. ...(.
0000030: 1d00 1c00 0600 0000 3400 0000 3480 0408  ........4...4...
0000040: 3480 0408 0001 0000 0001 0000 0500 0000  4...............
0000050: 0400 0000 0300 0000 3401 0000 3481 0408  ........4...4...
0000060: 3481 0408 1300 0000 1300 0000 0400 0000  4...............
0000070: 0100 0000 0100 0000 0000 0000 0080 0408  ................
0000080: 0080 0408 4145 1000 4145 1000 0500 0000  ....AE..AE......
0000090: 0010 0000 0100 0000 0050 1000 00d0 1408  .........P......

```

Now I try to execute the file
```

randy@diablo:~/.juniper_networks/network_connect$ ./ncsvc 
bash: ./ncsvc: No such file or directory

```

I'm now totally lost. How can I list the file in the directory, interact with it's contents, and even display it's contents, but then when I try to run it Bash can't find it?  

I'll be most grateful to anyone that can clear this up for me!

---

### Post by t4thfavor on 2009-06-30
try chmod a+x file

if that doesn't work try giving it 777 permissions as a test, this looks permission related.

---

### Post by sangaya on 2009-06-30
```

randy@diablo:~/.juniper_networks/network_connect$ sudo chmod a+x ncsvc 
[sudo] password for randy: 
randy@diablo:~/.juniper_networks/network_connect$ ./ncsvc 
bash: ./ncsvc: No such file or directory
randy@diablo:~/.juniper_networks/network_connect$ sudo chmod 777 ncsvc 
randy@diablo:~/.juniper_networks/network_connect$ ./ncsvc 
bash: ./ncsvc: No such file or directory
randy@diablo:~/.juniper_networks/network_connect$ ls -l ncsvc 
-rwxrwxrwx 1 root root 1167208 2009-03-11 08:40 ncsvc

```

No luck.

---

### Post by mbeach on 2009-06-30
any chance you are running a 64 bit install attempting to run a 32 bit application?

see the following for a similar problem:
[http://www.linux.co.uk/forums/help-and-advice-registered/879177638](http://www.linux.co.uk/forums/help-and-advice-registered/879177638)

resolution there seemed to be "Installing the ia32-libs corrected the problem"

---

### Post by t4thfavor on 2009-06-30
have you tried fully qualifying the file as in /home/somewhere/something/program?

---

### Post by ~sHyLoCk~ on 2009-06-30
> **t4thfavor said:**
> have you tried fully qualifying the file as in /home/somewhere/something/program?

He is in that directory where the file is since  "ls -l" is listing the file.

This file has no exension yet it's executable? Are you sure it's not ncsvc.sh or something?

---

### Post by t4thfavor on 2009-06-30
I know he's in the same directory, but its a wierd problem, it could take a wierd solution.

---

### Post by jerome1232 on 2009-07-01
It's probably a missing library.

I've seen it happen before, in my case the program tried to access a 32 bit library that I didn't happen to have and echo'd back to the prompt "no such file or directory" confused the heck out of me.

---

### Post by sangaya on 2009-07-01
> **mbeach said:**
> any chance you are running a 64 bit install attempting to run a 32 bit application?

see the following for a similar problem:
[http://www.linux.co.uk/forums/help-and-advice-registered/879177638](http://www.linux.co.uk/forums/help-and-advice-registered/879177638)

resolution there seemed to be "Installing the ia32-libs corrected the problem"

That fixed it! Thank you so very much!! :-D

---

### Post by mbeach on 2009-07-01
no problem, glad it worked out for you. Probably one of those errors that will get a better description at some point in the future. 'Attempting to run 32 bit application...'

mb.

---

### Post by Javhar on 2009-08-16
I have the same problem, but not with an executable file. When recursively deleting a directory tree, a few directories persist because "directory not empty". When I try manually deleting the files: "rm: cannot remove [file]: No such file or directory". Same happens when I try to mv them. Sudo doesn't help. Yet I can see the files with ls, I can stat them, I can even edit them with vi and save them again.

The files are on an external hard drive that I use for backups with rsync. They are just regular jpg pictures. They all have 777 permissions, and when I sudo chmod them the permissions don't change. But the same goes for all the other files in all the backups, and yet those were deleted normally.

Any clue? Thanks!


Jack.

---

### Post by pablolibo on 2012-11-27
I can fix it whit:

sudo apt-get install libc6:i386 zlib1g:i386

source from: [http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)

:D

---

### Post by oldos2er on 2012-11-27
Closed. Please don't bump old threads.

---

