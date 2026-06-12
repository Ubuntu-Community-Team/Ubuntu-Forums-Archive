---
title: "Output of htop in a file"
date: 2011-04-15
forum: General Help
---

### Post by humla on 2011-04-15
Okay, need some help outputting the result of a command in the terminal. Tried using 

command > resultfile

but this works with commands like ls which provide a result line by line. But for commands like top, htop and some other the text file adds some string of characters.

Example of running htop > test.txt is shown in the attached image. Anybody know how I can remove those characters and get something useful.

[http://i51.tinypic.com/2igepgm.jpg](http://i51.tinypic.com/2igepgm.jpg)

The problems are those strings of character liek (B and [39m and so on. 

Also if i open the file on cat if displays fine(well it closes as soon as it opens but i can just see its ok) but on vim and gedit i get the result shown in the image.

---

### Post by Vaphell on 2011-04-15
these are the formatting codes and you can try to get rid of them with regular expressions
i played a bit with htop output and it's pretty much out of the question, colors and formats introduce too much garbage to filter it out in a sensible way.
top looks much better, it's largely human readable

what happens when you redirect cat to another command/file?

---

