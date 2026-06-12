---
title: "gzip blunder - recursively gzipped my home dir!"
date: 2006-02-21
forum: General Help
---

### Post by wombat20 on 2006-02-21
I've somehow managed a bit of a blunder whilst using gzip to backup some files.  :???: 

What appears to have happened is that I got it to individually compress each file in my home directory recursing all subdirectories.  The directories are still there, but every file has a .gz on the end.  Great for saving disk space, but inconvenient for actually using files!

So what I'm looking for is the correct syntax for gunzip (or whatever) to undo this accident.  

1. I'd prefer if it replaced the existing files rather than having a load of .gz files as well
2. I may have had some real .gz files in there, but I guess they're all .gz.gz now?

I'd rather get an expert's advice than screw things up further by trying more things.

Thanks in advance.

---

### Post by suRoot on 2006-02-21
Just a quick hack, use at your own risk.

```
#!/bin/bash
for file in `find . -name '*.gz' -print`; do
gunzip $file
done 
```

---

### Post by wombat20 on 2006-02-21
Thanks for the suggestion.  Actually not sure about how to implement a bash script - have so far wimped out of programming related stuff in Ubuntu, despite being a C# programmer during daylight hours. (where to start with Linux programming - that should be a new thread, perhaps.)

After some research (fiddling around), it appears that the following method does the job.

```

gunzip -drv *

```

---

### Post by z_diver on 2006-02-21
[QUOTE=wombat20]Thanks for the suggestion.  Actually not sure about how to implement a bash script - have so far wimped out of programming related stuff in Ubuntu, despite being a C# programmer during daylight hours. (where to start with Linux programming - that should be a new thread, perhaps.)
[/QUOTE]
bash scripts are quick and easy.  

Just make a file which starts with #!/bin/sh and has the commands you wish to run one per line or separate commands with a semi colon.

Then make it executable.  chmod 755 myscript(if the numbers are odd they are executable. In this case 4+2+1=7, 4 +1=5, 4+1=5) 4=read 2=write 1=execute.

to run it use ./myscript

---

### Post by akiro.yamamoto on 2006-02-21
[QUOTE=suRoot]Just a quick hack, use at your own risk.

```
#!/bin/bash
for file in `find . -name '*.gz' -print`; do
gunzip $file
done 
```[/QUOTE]

Ah the above is a bash script ;)
Just copy and paste the info into a text file and save it as my_bash.sh anywhere you like. Right click on the file, go to properties and check the execute permission for the file. Now you can double-click the file to run it. Thats it.

---

