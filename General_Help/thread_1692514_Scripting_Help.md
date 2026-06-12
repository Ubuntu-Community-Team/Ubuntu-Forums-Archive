---
title: "Scripting Help?"
date: 2011-02-21
forum: General Help
---

### Post by giantanakim on 2011-02-21
On a day to day basis, I have to sort and catalog hundreds of .wav files.  Basically, I have a text file with a list of filenames (i.e. 12223334444.wav) that need to be broken down over multiple folders.  Right now this is very manual.  I know that Linux is capable of automatic scripting, and I have written a few, but I am not sure how to do what I need to do here.  Basically, I need to take the filenames listed in the text file, and move the corresponding wav file into a specific folder.   I would also like to generate an additional text file that tells me what specific files were moved, in case any that should be there are not.  I appreciate any help on this.

Thanks

---

### Post by 3Miro on 2011-02-21
You need to establish specific criteria on which file needs to go where (like any file containing the word Aerosmith needs to go to the folder Aerosmith, just an example). You can use time modification and other such things.

Look up Bash scripting

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

you want to pay heavy attention to Conditional statements and loops.

---

### Post by giantanakim on 2011-02-21
Thanks for the info.  However, I was actually able to do this pretty simply with the following script.

for line in $(cat text.txt)

do 

mv "$line" /home/here/there/everywhere

done.

---

