---
title: "Scripting Help"
date: 2011-04-15
forum: General Help
---

### Post by syborfical on 2011-04-15
Not sure what part of the forum to put this in sorry.

Pretty much what im trying to do is write a basic script that:

*Searches for all .rar files in a directy. ( done sort of also need to include .part01.rar ) 
*Outputs all that info to a txt file. ( done )
*Use unrar to go through the text file then unrar the files to another directry.  ( need some help)
* Then also write to another text file that its been done. ( need some help)

My script so far does this.

find ./media/foldername -name '*.rar' | tee /home/user/rars.txt

So I have a list of all the part01.rars in the directy /media/foldername

Is there a way to tell unrar to look at a text file then go through it line by line and extract all the rars to say /media/extracted?

Thank you for reading and thank you for any help in advance

---

### Post by Vaphell on 2011-04-15
```
while read file
do
  echo "$file"
done < rars.txt
```

replace echo line with proper unrar using "$file" as the archive to extract
i am not too familiar with unrar so i won't help with the combination of switches.

---

### Post by papibe on 2011-04-15
find has an option to execute a command every time it gets a match. For example:
```
$ find ./media/foldernam -iname '*.rar' -exec unrar e {} /media/extracted \;
```

I hope it helps.

---

### Post by syborfical on 2011-04-15
> **papibe said:**
> find has an option to execute a command every time it gets a match. For example:
```
$ find ./media/foldernam -iname '*.rar' -exec unrar e {} /media/extracted \;
```

I hope it helps.

Thank You works Great !!!:-)
Now just to learn a bit more :-)

---

