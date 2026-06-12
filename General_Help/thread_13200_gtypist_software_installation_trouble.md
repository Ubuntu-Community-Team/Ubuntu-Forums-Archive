---
title: "gtypist software installation trouble"
date: 2005-01-29
forum: General Help
---

### Post by Datchew on 2005-01-29
I'm trying to install a typing program called gtypist. 

Description is [HERE](http://www.gnu.org/software/gtypist/#downloading) 

I downloaded version 2.7 [HERE](ftp://ftp.gnu.org/gnu/gtypist/) 
and extracted it to my hard drive in a folder. 

Instructions say:
****************************************
		GNU Typist 2.7 Installation instructions

This program can be compiled under Unix and under Windows/DOS.
Compilation under Unix 
----------------------
In order to compile this program, you must have:

  - The 'ncurses' or the 'curses' library

* Uncompress the sources distribution:

  > tar jxvf gtypist-2.7.tar.bz2
  or
  > tar zxvf gtypist-2.7.tar.gz

* Change to the sources directory

  > cd gtypist-2.7

* Configure the package. By default the program will be installed at
/usr/local/bin and the lessons and international support in
/usr/local/share/gtypist (you can change with the option --prefix). By 
default it will install Native Language Support (you can disable this
with the option --disable-nls)

  > ./configure 

* Compile

  > make

* Become root and install

  > su
  > umask 022
  > make install

* To test your installation type

  > gtypist
  or
  > /usr/local/bin/gtypist
*****************************************************
I get to the part where i put in
>./configure

and it gives me the following error:
"*** The curses or ncurses library is required!"

i know from teh install instructions that i need the curses or the ncurses library (which from what i looked up is a c-compiler.) but I can't specifically find it in the synaptic package manager.  
I can find a few similar things which I installed, but that still didn't make it work in the ">./configure" part of the terminal commands. 

please advise.  I've only been doing Linux for about a month, so i'm a little lost. 
Thanks much. 
Datchew.

---

### Post by Yukonjack on 2005-01-29
Why don't you use Synaptic package manager and install from there, version 2.7.4.

---

### Post by Datchew on 2005-01-29
install what from there, gtypist????

Is it out there in the repositories?

I couldn't find it when searching. 

Datchew

---

### Post by Yukonjack on 2005-01-29
[Please read on](http://ubuntuguide.org/#extrarepositories)

---

### Post by rkn on 2005-01-29
[QUOTE=Datchew]install what from there, gtypist????

Is it out there in the repositories?

I couldn't find it when searching. 

Datchew[/QUOTE]
a search works for me:
**$ apt-cache search gtypist**
*gtypist - A simple ncurses touch typing tutor*

There is a Debian package.

-BoB

---

### Post by Datchew on 2005-01-29
Yukonjack. 

(are you related to Yukon Cornelius? "bumbles bounce!")

does that mean that if i change those settings, it will enable my synaptic manager to find more things, even some that aren't supported by the ubuntu team?

I don't really understand what synaptic manager does i guess. 
I thought it was like the feature in windows where you can add/remove components of the operating system.   If that's the case, am i simply limited by the types of things i can download by the default setting?????

thanks much.
Datchew.

---

### Post by Yukonjack on 2005-01-29
[QUOTE=Datchew]Yukonjack. 

(are you related to Yukon Cornelius? "bumbles bounce!")

[COLOR=Blue]No don't even know who you are talking about.[/COLOR]

does that mean that if i change those settings, it will enable my synaptic manager to find more things, even some that aren't supported by the ubuntu team?
[COLOR=Blue]
You edit the sources.list to had more respitory. You have to know what you are doing or you can get in big trouble.[/COLOR]

I don't really understand what synaptic manager does i guess. 
I thought it was like the feature in windows where you can add/remove components of the operating system.   If that's the case, am i simply limited by the types of things i can download by the default setting?????
thanks much.
Datchew.[/QUOTE]

[COLOR=Blue]Well it's like apt-get but with a GUI. Always reload before installing package. It act like sudo apt-get update brings everything to date in the package list. Best thing to do for a newbee is read all info you can find. The debian documatation on the debian site is a must if you want to understand the ins and outs.[/COLOR]

---

### Post by Datchew on 2005-01-30
Would you mind pointing me to the debian website you mentioned?
I know that's another distro right?
Will that help me understand some of the terminal commands in linux? i.e. sudo, apt get, gedit???

yukon cornelius was a silly cartoon characted in the 80's on a cartoon that would run every christmas season.   just a joke.

---

### Post by Yukonjack on 2005-01-30
Ubuntu is a Debian base distro

[Debian documentation](http://www.debian.org/doc/) 

Yes it will, happy reading

---

### Post by Datchew on 2005-01-30
thanks mate. 
I appreciate it.

---

### Post by Yukonjack on 2005-01-30
My pleasure  :wink:

---

