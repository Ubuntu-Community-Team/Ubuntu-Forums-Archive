---
title: "Linking in Anjuta"
date: 2010-06-08
forum: General Help
---

### Post by svenskmand on 2010-06-08
I wanted to try out Anjuta for programming C++, but I have not been able to figure out how to link a library, say ncurses into my program. This should be so easy, but apparently not, [I have not even been able to find it in the manual]("http://library.gnome.org/devel/anjuta-manual/stable/") ](*,)

I have installed everything that is needed, and if I do:
```

g++ main.cpp -lncurses

```
from the command line where main.cpp contains
```

#include <ncurses.h>

int main()
{	
	initscr();			/* Start curses mode 		  */
	printw("Hello World !!!");	/* Print Hello World		  */
	refresh();			/* Print it on to the real screen */
	getch();			/* Wait for user input */
	endwin();			/* End curses mode		  */

	return 0;
}

```
then everything works out the way it should. But I cannot get Anjuta to do it :S It complies but does not do any linking as I do not know how to tell it which libraries to use :S

Please help

PS: I could not find a category to put this in so I put it here, if this is not the right place then please move this thread.

---

### Post by svenskmand on 2010-06-09
*bump*

Surely someone is using Anjuta, and must know how to link to a library :S

---

### Post by svenskmand on 2010-06-10
*bump*

Anybody? Please advice :)

---

### Post by svenskmand on 2010-06-13
*bump* :S

---

### Post by svenskmand on 2010-06-14
*bump*

---

### Post by svenskmand on 2010-06-17
*bump*

---

### Post by Vaphell on 2010-06-17
[http://anjuta.sourceforge.net/documents/C/anjuta-advanced-tutorial/#libraries](http://anjuta.sourceforge.net/documents/C/anjuta-advanced-tutorial/#libraries)
should work

---

### Post by svenskmand on 2010-06-17
I have already checked that page out, but unfortunately it seems that Anjuta has change its userinterface since that page has been written :( But thanks anyway :)

Anybody have any other suggestions?

---

### Post by Vaphell on 2010-06-17
change ide :D
code::blocks for example


edit:
[http://library.gnome.org/users/anjuta-build-tutorial/2.26/library-anjuta.html.en](http://library.gnome.org/users/anjuta-build-tutorial/2.26/library-anjuta.html.en)
[http://ubuntuforums.org/showthread.php?t=1444716](http://ubuntuforums.org/showthread.php?t=1444716)

---

### Post by svenskmand on 2010-06-20
Thanks I will try Code::Blocks, Anjuta apparently sucks big time as they do not have documentation about a simple and essential feature like this, and as it looks they do not support linking external libraries which does not use pkg-config :S

---

### Post by dishmanw on 2010-09-19
I feel your pain. I'm trying to link to the Allegro library, and I'm having a similar problem. From the older tutorials, it looks like it used to be easy to link libraries. Why did they decide to make it harder? At least it isn't broken like Kdevelop. I can at least compile if I'm not linking libraries. For the people who right the code for Anjuta, PLEASE!!!! make it easier to link libraries.:confused:

---

### Post by johncc330 on 2011-03-10
Just a quick reply, and probably too late to be of use.

The problem with adding libraries in Anjuta in mainly that Anjuta does not support (directly) libraries that do no generate information for pkg-config.

An example is ncurses: When compiling ncurses, it is necessary to include the
--enable-pc-files option, and even then, they are not installed automatically.

So, ncurses may be an exception, but normally you have to install the -dev
packages for each library, so that the .pc files are installed, and so that 
anjuta can use the libraries.

After that, using libraries is quite easy.

John

---

