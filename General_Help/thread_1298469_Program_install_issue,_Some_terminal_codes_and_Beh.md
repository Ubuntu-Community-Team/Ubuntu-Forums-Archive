---
title: "Program install issue, Some terminal codes and Behaviour of Bash"
date: 2009-10-22
forum: General Help
---

### Post by milensinan on 2009-10-22
hi,
when i install flock tar/bzip2 (or any other program). i unzip it using terminal. 
(bzip2 -cd <program>.tar.bz2)
but then i need to configure the program using ./configure. problem is that i am somewhere where the program doesnt exist. where they are extracting these programs after setup? how can i reach there (normally using cd home etc. but maybe i need to do something with permission?)

and another thing. (for flock install). after the install stops in terminal i am having such an end.
[IMG]http://www.futuremerch.com/GG/temporary/Screenshot.png[/IMG]



and after i try to write something in the terminal (like 'exit' to close it). i am having this screen:
[IMG]http://www.futuremerch.com/GG/temporary/Screenshot-1.png[/IMG]

thanks..

---

### Post by Johnny B on 2009-10-22
after you unzip it you have to cd into that directory

also make sure you have build-essential installed
> sudo apt-get install build-essential

---

### Post by milensinan on 2009-10-23
yup. but i don't know which folder holds these programs. 

and i installed 'build-essential' now.

---

### Post by Johnny B on 2009-10-24
it will create a folder for itself when you unzip it, and will usually have the name of the program followed by the version number.

---

