---
title: "Problems with C Compiler :("
date: 2011-12-31
forum: General Help
---

### Post by optima4 on 2011-12-31
I ran the commands

sudo aptitude install build-essential
sudo gedit first.c

Up until this point everything seems fine except when I save the code I get this report:

```
(gedit:2977): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.EDN36V': No such file or directory

(gedit:2977): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2977): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KE136V': No such file or directory

(gedit:2977): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```


Following the rest to run the file results:

cc -c first.c

```
first.c: In function ‘main’:
first.c:5:7: error: expected ‘;’ before ‘{’ token
```


cc -o first first.c

```
first.c: In function ‘main’:
first.c:5:7: error: expected ‘;’ before ‘{’ token

```


./first

```
bash: ./file: No such file or directory
```



[b]Output should show as follows

Hello, world[/b]

... but it is not.

----

Also I added 

sudo apt-get install gcc build-essential

To install gcc, but I have the same results. 

----
*Notes

using Ubuntu 11.10

---

### Post by MadCow108 on 2011-12-31
there should be no reason to edit your source files with root rights (= drop the sudo)

before we can tell you what is wrong in your code you must first show it. Its probably a missing semicolon at the end of a line.

---

### Post by optima4 on 2011-12-31
I think my code is good here it is>

```

#include <stdio.h>

int main()
{
printf{"Hello, world\n");
return 0;
}

```



And I forgot I started a thread ealier similar to this questions and I just ran this command

sudo apt-get update && sudo apt-get install aptitude && sudo aptitude install build-essential
and this code ran perfectly, except I tried saving the file again to run Hello World and it still says 

```

(gedit:5149): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9DVW6V': No such file or directory

(gedit:5149): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:5149): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.5IPB7V': No such file or directory

(gedit:5149): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

---

### Post by MadCow108 on 2011-12-31
you get these warnigns because you edit your source files with root rights, you should not do that.
also to execute X applications with root rights you should use gksudo not sudo

the error in the source code is this
```
printf**{**"Hello, world\n");
```

replace { with (

---

### Post by lisati on 2011-12-31
It's also good form to indicate that main is returning int.

---

### Post by d3v1150m471c on 2011-12-31
s/\{/\(/

The GTK errors are obvious, file doesn't exist.

---

### Post by optima4 on 2012-01-01
Thanks for the valuable replies. 
Here is the code which I did have a syntax error which I have now gotten in order.

```
#include <stdio.h>

int main()
{
printf("Hello, world\n");
return 0;
}

```

"after printf" I had one of these "{" instead of this "("

I do not see where I am missing a colon, and I am not running this in root I do not know why it says, "root/.local/share/recently-used.xbel"

This did give the result

**Hello, world**

Within my Terminal. Thank you for your time and if you have anything else you would like to share feel free to discuss. I could use all the advice available.

---

