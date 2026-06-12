---
title: "Ruby Interpreter terminal issue. Please Help!"
date: 2010-05-01
forum: General Help
---

### Post by MartyFlynt on 2010-05-01
I've begun a simple beginner's tutorial on Ruby and followed these instructions using gedit: 

                
**Open up your favourite text       editor and type in the following:          **
         **puts 1+2**         **                 Save your program (yes, that's a program!) as calc.rb       (the [B].rb** is what we usually put at the end of       programs written in Ruby).  Now run your program by typing ruby calc.rb       into your command line.  It should have put a 3 on your screen.[/B]

I saved the file to my desktop and when I run the program I get the following instead: 

marty@marty-laptop:~$ ruby calc.rb
ruby: No such file or directory -- calc.rb (LoadError)

I have no idea what is wrong and I have tried searching online for an answer but to no avail..I really just want to start learning how to program but I'm having a very frustrating delay!

It is in fact installed: 

marty@marty-laptop:~$ ruby -v
ruby 1.8.7 (2009-06-12 patchlevel 174) [powerpc-linux]

marty@marty-laptop:~$ which ruby
/usr/bin/ruby

I could really appreciate someone's help. Please keep in mind I am an absolute newbie to Linux.

Thank you in advance for your help,
                                                        Marty

---

### Post by wheredidrealitygo on 2010-05-01
when you just open a terminal, the terminal is being opened in your home directory at /home/marty/

you need to change directories (cd) into the directory you saved this calc.rb file at (if you saved it to the desktop you would type ```
cd /home/marty/Desktop/
``` for example.

---

### Post by MartyFlynt on 2010-05-01
Ah Yes! Thank you for your help!

---

