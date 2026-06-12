---
title: "Trying to instal xl_cheeselooks engine..."
date: 2009-08-19
forum: General Help
---

### Post by forgotten_hell on 2009-08-19
I am trying to install the xl_cheeselooks engine so I can install a theme. I'm really new at Ubuntu and Linux in general, so I didn't know what to do.

I found this old thread: [http://ubuntuforums.org/showthread.php?t=1096040](http://ubuntuforums.org/showthread.php?t=1096040) by googling it and so I unpacked it like it said. That worked, but now when I try to actually install it, it doesn't. The code the download site and that thread give me seem to be dated, the name of the files have changed. I tried changing it to that and it's still not working. 

This is what I am getting:

```
andrew@ubuntu:~$ cd to xl_cheeselooks_Engine_Themes
bash: cd: to: No such file or directory
andrew@ubuntu:~$ ./autogen.sh --prefix=/usr --enable-animation
bash: ./autogen.sh: No such file or directory
andrew@ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
andrew@ubuntu:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
andrew@ubuntu:~$ 

```

Keep in mind I'm a complete noob at this, but I really want to learn it and learn to use the terminal, so if someone could help me and explain it, that'd be awesome.

---

### Post by forgotten_hell on 2009-08-19
bump

---

### Post by mthalis on 2009-08-19
Are you sure you go inside that folder?

---

### Post by forgotten_hell on 2009-08-19
> **mthalis said:**
> Are you sure you go inside that folder?


Erm, what?

---

### Post by mthalis on 2009-08-19
First download gtk-enginesxl_cheese.tar.gz and unzip
go inside that folder
> 
cd /home/gtk-enginesxl_cheese


before installed that you have install libtool, intltool and automake

> 
sudo apt-get install automake
sudo apt-get install libtool
sudo apt-get install intltool


after that 
> 
./autogen.sh --prefix=/usr --enable-animation


> make

---

### Post by mthalis on 2009-08-19
If you get error message like
> 
configure: error: GTK+-2.12 is required to compile gtk-engines
make: *** [config.status] Error 1


install

> 
sudo apt-get install libgtk2.0-dev


---

### Post by forgotten_hell on 2009-08-19
It's telling me "No such file or directory" right after the first step. Where was I supposed to extract them to?

---

### Post by prshah on 2009-08-19
> **forgotten_hell said:**
> 
```
andrew@ubuntu:~$ cd[color=red] to[/color] xl_cheeselooks_Engine_Themes
bash: cd: to: No such file or directory

```


I think you mean ```
andrew@ubuntu:~$ cd xl_cheeselooks_Engine_Themes
```

You've add an extra "to" (in red, in your code)

---

### Post by mthalis on 2009-08-19
No can't be, because I test it few minuets ago. My early replies show how I did it

---

### Post by forgotten_hell on 2009-08-19
> **prshah said:**
> I think you mean ```
andrew@ubuntu:~$ cd xl_cheeselooks_Engine_Themes
```You've add an extra "to" (in red, in your code)


Thanks, but my code was wrong anyway. The folder contained a bunch of themes, so the folder inside (the one the other poster used and the one in the other thread and on the download page) was the right one. It's still not working, though. :(

---

### Post by forgotten_hell on 2009-08-19
> **mthalis said:**
> No can't be, because I test it few minuets ago. My early replies show how I did it

```
andrew@ubuntu:~$ 
andrew@ubuntu:~$ cd /home/gtk-enginesxl_cheese 
bash: cd: /home/gtk-enginesxl_cheese: No such file or directory
andrew@ubuntu:~$ 


```

...

---

### Post by mthalis on 2009-08-19
Downloaded **gtk-enginesxl_cheese.tar.gz ** file in desktop
Right click and extract it

After that 

> cd /home/ites/Desktop/gtk-enginesxl_cheese

out put

> 
ites@ites-desktop:~$ cd /home/ites/Desktop/gtk-enginesxl_cheese
ites@ites-desktop:~/Desktop/gtk-enginesxl_cheese$ 


---

### Post by mthalis on 2009-08-19
read this you can get more details

[http://ubuntuforums.org/showthread.php?t=778611](http://ubuntuforums.org/showthread.php?t=778611)

---

### Post by prshah on 2009-08-19
> **forgotten_hell said:**
> ```
andrew@ubuntu:~$ 
andrew@ubuntu:~$ cd /home/gtk-enginesxl_cheese 
bash: cd: /home/gtk-enginesxl_cheese: No such file or directory
andrew@ubuntu:~$ 


```

...

the directory cannot be in /home, it should be in /home/andrew.. or instead, just try```
cd `find ~ -iname gtk-enginesxl_cheese`
```

Copy and paste the code, or, if you can't do that, pay special attention to the single quotes, it's not the one with double quotes, it's the key with the tilde (~)

---

### Post by forgotten_hell on 2009-08-19
> **prshah said:**
> the directory cannot be in /home, it should be in /home/andrew.. or instead, just try```
cd `find ~ -iname gtk-enginesxl_cheese`
```Copy and paste the code, or, if you can't do that, pay special attention to the single quotes, it's not the one with double quotes, it's the key with the tilde (~)

Thanks so much! Using that with what the other guy said totally worked!

My only question: why wouldn't it work every other time I tried it, not searching for it like that?

---

### Post by 3rdalbum on 2009-08-19
A quick tip for you: You don't need to blunder around with navigating on the command-line. Install the "nautilus-open-terminal" package, and log out and log in again. Now you'll be able to right-click within a Nautilus window and choose "Open In Terminal", and a new terminal window will open already at the location where your file browser is.

---

