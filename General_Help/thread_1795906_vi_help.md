---
title: "vi help"
date: 2011-07-03
forum: General Help
---

### Post by daxbau on 2011-07-03
hi everbody

i managed to make me a script to reconfigure automacitally my routing tables (wireless internet; wired a connected hotspot for my ftpd)
now i need at last to remove line "2" from /etc/resolv.conf

when i try to ```
root@HP-Compaq-8510w:~# vi +2 --cmd "dd" /etc/resolv.conf
```i get > 
Error detected while processing pre-vimrc command line:
E492: Not an editor command: dd
Press ENTER or type command to continue
.

thanks for your help.

---

### Post by Bachstelze on 2011-07-03
vi is a visual editor, it is not really suited for non-interactive use. Use ed for that.

```
firas@aoba ~ % cat test.txt 
foo
bar
baz
firas@aoba ~ % echo "2d\nw" | ed test.txt 
12
8
firas@aoba ~ % cat test.txt 
foo
baz

```

---

### Post by mikejonesey on 2011-07-03
why use vi to dynamicaly edit a file, not what it's for it's an editor, pipe stdout with cat to say grep or sed or awk or similar and write to file eg;

cat file.txt | grep -v "smelly line" > newfile.txt

---

### Post by Bachstelze on 2011-07-03
> **mikejonesey said:**
> why use vi to dynamicaly edit a file, not what it's for it's an editor

An editor is to edit a file, dynamically or otherwise. vi is a VIsual editor, and that's why it'd not suitable here. The correct tool to use here is ed, which is also an EDitor. sed is a Stream EDitor, so it is used to edit streams, not files, and is also not the right tool to use here (and yes I know of the -i extension of GNU sed, but it is non standard and should be avoided, and even with it, ed is better here).

---

### Post by mikejonesey on 2011-07-03
both ways work... 

cat file.txt | grep -v "smelly line" > newfile.txt

or

awk 'NR%2 != 0' /etc/resolv.conf

entireley apropriate for edditing files... :(

lol didn mean to tread on ur toes [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") lol i had started replying before you 1st post went up...

lol

---

### Post by Bachstelze on 2011-07-03
> **mikejonesey said:**
> both ways work... 

cat file.txt | grep -v "smelly line" > newfile.txt

or

awk 'NR%2 != 0' /etc/resolv.conf

entireley apropriate for edditing files... :(

Not really, because those commands output to stdout, so you have to 1) dump stdout to a new file, and 2) replace the old file with the new one. For non-interactive in-place editing of files, the correct tool is ed (or sed -i if you really want to but it's like non-alcoholic beer: it tastes the same but you know it ain't right!).

---

### Post by daxbau on 2011-07-03
Dear Bachstelze.

can you give me please a example to delete line 2 of resolv.conf with "ed" command? or to insert a charakter to line to (i.e. "#")

thank you.

---

### Post by Bachstelze on 2011-07-03
The example I posted above does exactly that (deleting line 2 of a file). of course replace test.txt with /etc/resolv.conf (and run it with sudo).  If you want to comment out the line instead of deleting it:

```
firas@aoba ~ % cat test.txt 
foo
bar
baz
firas@aoba ~ % echo "2s/^/#/\nw" | ed test.txt 
12
13
firas@aoba ~ % cat test.txt 
foo
#bar
baz

```

---

### Post by daxbau on 2011-07-05
hi.

sorry but i don't understand this code. can you explain it to me please?

btw. it doesn't work ;-)

---

### Post by hawthornso23 on 2011-07-05
Who says vi can't do this.  vi can do ANYTHING! 

```
vi "+2,2d" "+wq" /etc/resolv.conf
```

Note that you'll have to put sudo in front for this particular file or run as su.

---

