---
title: "How do I find a file that has no file extension?"
date: 2009-12-10
forum: General Help
---

### Post by Rytron on 2009-12-10
Hi.

In Ubuntu I go to Accessories -> Search For Files.

I can find any flv files by doing a search for *.flv.

How though could I find an flv file that doesn't have .flv at the end? I know that the actual file extension is only for human readability.

I have a few flv files that are not found by doing a search for *.flv. What other methods can I use?

---

### Post by Steve834 on 2009-12-10
You could open a terminal and use the find command.  You need to know something about the file you are looking for first.  Does it have a special name or characters in the name? The find command is powerful and it can search on many criteria.  You can find all files that were changes in the last 5 minutes, for example.

---

### Post by kaibob on 2009-12-10
> **Rytron said:**
> I have a few flv files that are not found by doing a search for *.flv. What other methods can I use?

I don't know of anything with a GUI that will do what you want. The bash file command will show the file type for most files with or without an extension. I don't have a FLV file to see if this would work. Also, to actually search for FLV files, you would have to use a short shell script, which is perhaps more trouble than it's worth.

To see how the file command works, open a terminal window, navigate to a directory with a few files and enter:

```
file *
```

---

### Post by Rytron on 2009-12-10
Thank you Steve834 & kaibob.

I reckon so that it is a good idea to add file extensions to all files in Ubuntu that don't have a file extension. It would make searching easier.

---

### Post by kaibob on 2009-12-10
I was curious and tried to use the file command to locate files of a certain type including those that do not have an extension and that have an incorrect extension. As a test, I used the following command line to locate PDF files in my home directory. It worked fine.

```
find /home/kaibob -type f | while read f ; do t=$(file -b "$f") ; [[ "$t" = "PDF document"* ]] && echo "$f" ; done

```

---

### Post by Rytron on 2009-12-10
> **kaibob said:**
> I was curious and tried to use the file command to locate files of a certain type including those that do not have an extension and that have an incorrect extension. As a test, I used the following command line to locate PDF files in my home directory. It worked fine.

```
find /home/kaibob -type f | while read f ; do t=$(file -b "$f") ; [[ "$t" = "PDF document"* ]] && echo "$f" ; done

```

I also tried your code, kaibob. Excellent work. How would you modify it for searching for text files, flv, mpg, etc that didn't have file extensions?

---

### Post by Vaphell on 2009-12-10
i don't know where to find the full list of filetypes, but you can get that info by running **file -b <file_of_a_given_type>**

replacing that "PDF document" with a proper identifier should do the trick

EDIT: won't be that easy, my mp3 files give different answers to file -b
MPEG ADTS, layer III, v1, 128 kbps, 44.1 kHz, JntStereo
or
Audio file with ID3 version 2.3, MP3 encoding

plain text - ASCII text
FLV from youtube - Macromedia Flash Video

---

### Post by kaibob on 2009-12-10
> **Rytron said:**
> I also tried your code, kaibob. Excellent work. How would you modify it for searching for text files, flv, mpg, etc that didn't have file extensions?
I would do as suggested by Vaphell--just run "file -b filename" with a file of the desired file type. 

I wasn't aware that one file type might return different strings with the file command. To a certain extent, you can modify the command for this by inserting additional  tests (i.e. [[ "$t" = "identifying string"* ]]) but at some point this all becomes too unwieldy or unreliable. As you previously mentioned, it's probably best just to be sure and use extensions.

---

### Post by Rytron on 2009-12-10
Thanks guys.

I will note the code on this thread for future reference.

I will also begin adding extension to my files right away. It makes for easier searching in the long run.

---

### Post by Rytron on 2009-12-16
Thanks go to [tjoff]("http://ubuntuforums.org/member.php?u=805999")

To list it for the current directory.

```
find . -maxdepth 1 -type f ! -name "*.*"
```

To do it recursively, just remove "***-maxdepth 1***"

---

