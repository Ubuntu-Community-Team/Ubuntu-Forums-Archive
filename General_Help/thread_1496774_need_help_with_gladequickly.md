---
title: "need help with glade/quickly"
date: 2010-05-29
forum: General Help
---

### Post by qwerty2009 on 2010-05-29
hi im trying to create a simple application, ive created my ui using glade/quickly i just need help assigning my buttons to run a file

lets say i have button1 when that button is clicked i want it to run a already made .sh file in terminal 

how do i go about doing this ?

any help appreciated

---

### Post by qwerty2009 on 2010-05-29
also if i cant program the button to run a script whats the best way of setting it to run commands through terminal?

---

### Post by oldfred on 2010-05-29
I am learning python so I looked it up. I thought it was an execute command.

Found this - subprocess:

[http://www.doughellmann.com/PyMOTW/subprocess/index.html#module-subprocess](http://www.doughellmann.com/PyMOTW/subprocess/index.html#module-subprocess)

---

### Post by J V on 2010-05-29
Yes, you will need to use subprocess to run a bash script from a button: Note that if you kill the python application process the subprocess doesn't exit with it, I spent an entire day with 2 such subprocesses running at 100% on both CPUs before I noticed it :D

If you want the bash script to run in the terminal, make a bin folder in your home, move the file there, take off the extension and relog...

Now just type the name of that file in a terminal and it will run the bash script.

---

