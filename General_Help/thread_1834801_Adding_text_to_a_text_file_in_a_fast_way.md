---
title: "Adding text to a text file in a fast way"
date: 2011-08-28
forum: General Help
---

### Post by theskag on 2011-08-28
Hi,

I want to add a line of text at the end of a specific textfile, fast.
The text file is my todo list. :)

Say that I run a script, I would want to define the text that is to be writen to the text file.

Example:
./test.sh "INPUT"

test.sh:
echo INPUT >> /pathto/text.txt

Then after running script text.txt contains:
INPUT

Is this possible? If so, how do I add the INPUT string to the script?
If not are there any other suggestions?

Any help is appreciated, thanks.

---

### Post by dino99 on 2011-08-28
create a launcher with:
sudo gedit path/to/mytext

---

### Post by sanderd17 on 2011-08-28
your script should be

```

#! /bin/bash

echo $* >> text.txt

```

Than you can just do
```

./text.sh INPUT

```

Which will add "INPUT" to your file text.txt.

---

### Post by fdrake on 2011-08-28
there is no need for a script. you may end up moving it or deleting it. Also you wiil alsways need to find it or type the path... just add an alias to your bashrc.

```
cat >> ~/.bashrc
alias append='read $input; echo $input>> /path/of/myfile.txt'
<press enter>
<Contrl+D>
```

logout-login and run:

```
append 
add this text to my file.....
<enter, text added>
```

---

### Post by theskag on 2011-08-28
The thing is I don't want to use a texteditor unless I can add it in a script.

I want to add a line of text by simply typing one command with the text in the terminal.
If possible.

~$ command/script "text"

---

### Post by fdrake on 2011-08-28
> **theskag said:**
> The thing is I don't want to use a texteditor unless I can add it in a script.

I want to add a line of text by simply typing one command with the text in the terminal.
If possible.

~$ command/script "text"

all the answers posted run on the terminal.

---

### Post by theskag on 2011-08-28
My reply was to  dino99. I was slow, sorry.

I know, that was exactly what I was looking for. Thank you! :)

---

