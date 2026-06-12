---
title: "Help me with creating a simple bash script."
date: 2011-06-08
forum: General Help
---

### Post by karthick87 on 2011-06-08
I just want to create a simple bash script, to do the following task

In my Desktop i have the folders named i.e  Datas,Albums,Images,Work,General etc etc.. i just want to keeps these three folders (Datas,Albums,Images)alone and i want to delete all the other folders( What ever they may be). Also i want to delete all the excel files, and word files from the Desktop but not the PPT.. Can anyone help me in writing these script?

---

### Post by sisco311 on 2011-06-08
> **karthick87 said:**
> I just want to create a simple bash script, to do the following task

In my Desktop i have the folders named i.e  Datas,Albums,Images,Work,General etc etc.. i just want to keeps these three folders (Datas,Albums,Images)alone and i want to delete all the other folders( What ever they may be). 


```

shopt -s extglob
**echo** rm -rf ~/Desktop/!(Albums|Datas|Images)/

``` 
The above code will only print the directories. If you really want to rm them, then delete the **echo** command. 

> **karthick87 said:**
> 
Also i want to delete all the excel files, and word files from the Desktop but not the PPT.. Can anyone help me in writing these script?

Do you want to delete them recursively from each subdirectory or only from ~/Desktop?

---

### Post by ianc1 on 2011-06-08
Although I've only recently started to learn bash I believe your deletion script is a simple one```
rm $(find ~/Desktop/ -name "*.xls") && rm $(~/Desktop/ -name "*.doc")
```Basically rm is remove and the bit after $ in brackets is finding the files and listing them for the rm command.  The && tells the second command to only run if the first is successful.

It would be worth running```
find ~/Desktop/ -name "*.xls"
```and```
find ~/Desktop/ -name "*.doc"
```first just to see what will be removed.  This assumes your Excel and Word files have extensions of .xls and .doc.

I think the above script will only work if the filenames have no spaces.  If this isn't the case start the script with```
IFS=$'\x0A'
```and end with ```
unset IFS
```This changes the field separator from space to new line.

I hope this helps.

---

### Post by DaithiF on 2011-06-08
> **sisco311 said:**
> ```

shopt -s extglob
**echo** rm -rf ~/Desktop/!(Albums|Datas|Images)

```The above code will only print the directories. If you really want to rm them, then delete the **echo** command. 

Hi, Just to note that the command above will also echo/rm files within the Desktop directory.  Since you want to be selective about which files you delete then you may want to restrict it to directories only, by adding a trailing '/', ie.
```
echo rm -rf ~/Desktop/!(Albums|Datas|Images)/

```

---

### Post by karthick87 on 2011-06-08
> **sisco311 said:**
> ```

shopt -s extglob
**echo** rm -rf ~/Desktop/!(Albums|Datas|Images)

```The above code will only print the directories. If you really want to rm them, then delete the **echo** command. 



Do you want to delete them recursively from each subdirectory or only from ~/Desktop?

Only from Desktop..

---

### Post by sisco311 on 2011-06-08
> **DaithiF said:**
> Hi, Just to note that the command above will also echo/rm files within the Desktop directory.  Since you want to be selective about which files you delete then you may want to restrict it to directories only, by adding a trailing '/', ie.
```
echo rm -rf ~/Desktop/!(Albums|Datas|Images)/

```

Good point. Thanks!

---

### Post by sisco311 on 2011-06-08
> **karthick87 said:**
> Only from Desktop..

Check out:
[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)

For example, you can match any .odt file with ~/Desktop/*.odt and delete them with the rm command.

---

### Post by karthick87 on 2011-06-08
Getting the below error on running the script,
```

operator1@tme13:~/Desktop$ bash removedata.sh 
: invalid shell option namet: extglob
removedata.sh: line 3: syntax error near unexpected token `('
```

---

### Post by sisco311 on 2011-06-08
Strange. Could you post your script?

---

### Post by karthick87 on 2011-06-08
```
#!/bin/bash -x
shopt -s extglob
rm -rf /home/operator1/Desktop/!(File_New|New_Datas|Ubuntu_shortcuts|Forum_Rules)

```Below are the folder names which i dont want to delete,

File_New
New_Datas
Ubuntu_shortcuts
Forum_Rules

---

### Post by AlphaLexman on 2011-06-08
> **ianc1 said:**
> ```
rm $(find ~/Desktop/ -name "*.xls") && rm $(~/Desktop/ -name "*.doc")
```
I believe you had a typo and missed a **find** command in there.
```
rm $(find ~/Desktop/ -name "*.xls") && rm $([COLOR="Red"]find[/COLOR] ~/Desktop/ -name "*.doc")
```

---

### Post by karthick87 on 2011-06-08
Pls see my previous script, which throws an error..

---

### Post by AlphaLexman on 2011-06-08
How are you invoking your script, with 'bash removedata.sh'
as in your post or are you using 'sh removedata.sh', sh is a link to dash, not bash.

Best to source it like this to use the shebang in the script.
```
. ./removedata.sh
```

---

