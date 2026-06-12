---
title: "Need help with sh script"
date: 2011-02-12
forum: General Help
---

### Post by polardude1983 on 2011-02-12
what i am trying to do is print remotely through dropbox. so I am having a sh script check a folder called PrintQueue in my Dropbox and whatever file is in there it prints

Here is the script

```
#!/bin/bash
export PrintQueue="/root/Dropbox/PrintQueue";
IFS=$'\n'
for PrintFile in $(/bin/ls -1 ${PrintQueue}) do
lpr -r ${PrintQueue}/${PrintFile};
done
```

here is what the terminal says

```
christoph@christoph-desktop:~$ sh dropprint.sh
dropprint.sh: 5: Syntax error: word unexpected (expecting "do")

```

any help is appreciated

---

### Post by tjwoosta on 2011-02-12
try 
```

#!/bin/bash
export PrintQueue="/root/Dropbox/PrintQueue";
IFS=$'\n'
for PrintFile in $(/bin/ls -1 ${PrintQueue}); do
    lpr -r ${PrintQueue}/${PrintFile}
done

```

EDIT: I dont think you need the ; after the export line either.

---

### Post by polardude1983 on 2011-02-13
well it seems to of worked, it at least printed a txt file. i just wonder why it cuts the filenames short and says it cant find it. I also had to rename the folder PrintQueue because it would cut it at /Dropbox/Pri so i just did /Dropbox/PQ/

i had a txt file called routersettings.txt and this came up


```
christoph@christoph-desktop:~$ sh dropprint.sh
lpr: Error - unable to access "/home/christoph/Dropbox/PQ/routersetti" - No such file or directory
lpr: Error - unable to access "/home/christoph/Dropbox/PQ/gs.txt" - No such file or directory
christoph@christoph-desktop:~$ sh dropprint.sh
christoph@christoph-desktop:~$ 

```

So i renamed the file to router.txt and it didnt cut it off and printed it. wonder if it prints files with spaces or docs. hmm

---

### Post by polardude1983 on 2011-02-16
Well i got it to work and it prints txt files without a hitch. but it wont print pdf files. anybody know an answer?

---

