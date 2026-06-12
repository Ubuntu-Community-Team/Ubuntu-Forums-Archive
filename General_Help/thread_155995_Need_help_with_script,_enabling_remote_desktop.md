---
title: "Need help with script, enabling remote desktop"
date: 2006-04-06
forum: General Help
---

### Post by wiggy2k on 2006-04-06
I'm trying to write a script to enable Remote Desktop (and lots of other things) without having to go through the GUI util(s)

the bit i'm having problems with is this

test.sh
-----------------------------------------------------------------------
# Enabling Remote Desktop
sed -e "s/false/true/" /home/user/.gconf/desktop/gnome/remote_access/%gconf.xml > temp.xml
mv temp.xml /home/user/.gconf/desktop/gnome/remote_access/%gconf.xml

-----------------------------------------------------------------------
now this does change all instances of the word false to true in /home/user/.gconf/desktop/gnome/remote_access/%gconf.xml
but Remote Desktop doesn't work

What other files need editing / services restarting for this to work?

Thanks

---

### Post by waster on 2006-04-06
don't you need a g on the end to do global replace?

s/old/new/g

---

### Post by wiggy2k on 2006-04-06
hmm i don't know i've always thought
sed works line by line through the whole document

the g processes all occurences of the substitution on the current line. without it, it only changes the first occurance of the word in the current line 

as the file i'm editing only has the word "false" once on each of the lines i need to change it isn't required in this case.

i may be wrong though... i'll look into that

---

### Post by xenmax on 2006-04-06
wiggy2k is right. /g for global is to do replace for all occurences of pattern on a single line, like you say, sed works line by line each line unless you tell it not to

---

