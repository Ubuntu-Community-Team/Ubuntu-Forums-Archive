---
title: "shell script to zip a folder"
date: 2012-06-11
forum: General Help
---

### Post by winzip on 2012-06-11
I need a shell script to zip  a folder.


I have a folder . I want to zip this folder.  Please note  folder has many files and sub folders in it.

Can you please provide a sample shell script  regarding how zip a folder ?

---

### Post by codemaniac on 2012-06-11
If your requirement is to zip up a single static directory , then i believe you dont need a shell script .
Shell script is needed in order to automate some repetitive tasks . 

All you can do is just fire up tar with zip option from commandline to zip that .


```
tar -zcvf archive-name.tar.gz directory-name
```

---

### Post by winzip on 2012-06-11
> **codemaniac said:**
> 
Sheel script is needed in order to some [COLOR=Red]repetitive tasks . [/COLOR]


Yes. I'm doing that . I have a Shell Script which runs repetitively via crontab. I want to use Zipping  folder for backing up in the Shell Script.

---

### Post by codemaniac on 2012-06-11
use something like below in your shell script.

```
tar -zcvf archive-name.tar.gz directory-name
```

---

### Post by winzip on 2012-06-11
> **codemaniac said:**
> use something like below in your shell script.

```
tar -zcvf archive-name.tar.gz directory-name
```

That does not work . That works in command line through.  I need that working in shell script.

---

### Post by codemaniac on 2012-06-11
> **winzip said:**
> That does not work . That works in command line through.  I need that working in shell script.

Put absolute or full path names for **archive-name.tar.gz** and **directory-name** .

---

### Post by winzip on 2012-06-11
> **codemaniac said:**
> Put absolute or full path names for **archive-name.tar.gz** and **directory-name** .

Yes. I already did that . But still does not work. 

Do I need to add any flag in  tar command if there is  files and sub-folders  inside a folder ?

---

### Post by steeldriver on 2012-06-11
> **winzip said:**
> Do I need to add any flag in  tar command if there is  files and sub-folders  inside a folder ?

No - that's exactly what tar does. You can add flags if you need to *exclude* files or subfolders.

Have you made the script executable? What exactly doesn't work? Can you post the whole script - it would be easier to debug things if we can see them rather than just guessing

---

### Post by codemaniac on 2012-06-11
> **winzip said:**
> Yes. I already did that . But still does not work. 

Do I need to add any flag in  tar command if there is  files and sub-folders  inside a folder ?

What errors are you getting while you fire up the script ?
"Does not work " does not convey the actual scenario .

The flags/switches required are already been provided in the commnadline . The tar will recurcievely bundle all components and sub-components together .

---

### Post by sudodus on 2012-06-11
Please post the entry in crontab, the output or the relevant part of it from the command
```
crontab -l
```
and also post the shell script code! That will make it easier to help. Otherwise we are only guessing.

---

### Post by dargaud on 2012-06-11
If you want to zip instead of tar the dir, use the following command:
```
zip -r File.zip Directory
```

---

### Post by codemaniac on 2012-06-11
> **dargaud said:**
> If you want to zip instead of tar the dir, use the following command:
```
zip -r File.zip Directory
```

I have not used **zip **much , i am not sure if it is available in default Ubuntu installation.

---

### Post by David Andersson on 2012-06-11
> **codemaniac said:**
> I have not used **zip **much , i am not sure if it is available in default Ubuntu installation.

In 10.04 LTS they are in packages **zip** and **unzip**. Install them with Ubuntu Software Center, Synaptic Package Manager, or apt-get.

---

### Post by codemaniac on 2012-06-11
Instead of using zip , i would prefer gzip , tar etc that are available on default Linux/unix installation .

Unless I need the zipped output to be used in windows environments .

---

