---
title: "How to rename a lot of files"
date: 2009-06-26
forum: General Help
---

### Post by mikesol on 2009-06-26
Hi guys, 

I'm doing an university's project and a need to rename a lot of files (yes I know, it really sucks :? ), I have something like that

ap0525cd03od06_e01_SA_**Param008**_001.clas
....
ap0525cd03od06_e01_SA_**Param008**_100.clas

ap0525cd03od06_e01_SA_**Param009**_001.clas
....
ap0525cd03od06_e01_SA_**Param009**_100.clas
.....
.....
ap0525cd03od06_e01_SA_**Param014**_001.clas
....
ap0525cd03od06_e01_SA_**Param014**_100.clas


and I wish have


ap0525cd03od06_e01_SA_**Param001**_001.clas
....
ap0525cd03od06_e01_SA_**Param001**_100.clas

ap0525cd03od06_e01_SA_**Param002**_001.clas
....
ap0525cd03od06_e01_SA_**Param002**_100.clas
.....
.....
ap0525cd03od06_e01_SA_**Param007**_001.clas
....
ap0525cd03od06_e01_SA_**Param007**_100.clas


it means, I need to change the Param008, Param009,..., Param014 by Param001, Param002,..., Param007. There are 700 files by folder, and I need to do these changes in 10 folders. So, There is an application who do that automatically? 

Any help will be appreciated. 

Thanks in advance

---

### Post by ghostdog74 on 2009-06-26
```

find /path/to/process -type f -name "*.clas" -printf "%p\n" | awk 'BEGIN{ OFS=FS="_"; q="\047"}
{
   o=$0
   gsub("Param","",$4)
   newnum = sprintf( "%03d", $4-7)
   $4="Param"newnum
   cmd = "mv "q o q" "q $0 q
   print cmd
   # system(cmd) #uncomment to use
}'

```

---

### Post by kaibob on 2009-06-26
I've been using this post as a way to explore the parsing of file names. So far, I've come up with the following, both of which work, although not recursively. For me, this is just learning, and I'm sure ghostdog74's response is the way to go. 


```
for FILE in *.clas ; do
   NUM=$(echo "$FILE" | sed 's/^.*Param//' | sed 's/_.*$//')
   BEGIN=$(echo "$FILE" | sed 's/'"${NUM}"'.*$//')
   END=$(echo "$FILE" | sed 's/^.*'"${NUM}"'//')
   NEWNUM=$(printf "%03d" $(echo "${NUM}-7" | bc -q))
   cp "$FILE" "${BEGIN}${NEWNUM}${END}"
done
```

The following also worked:

```
for FILE in *.clas ; do
   BEGIN=${FILE:0:27}
   NUM=${FILE:27:3}
   NEWNUM=$(printf "%03d" $(echo "${NUM}-7" | bc -q))
   END=${FILE:30:9}
   cp "$FILE" "${BEGIN}${NEWNUM}${END}"
done
```

I tried to use the rename command (as geirha did in a previous rename thread) but couldn't get it to work.

---

### Post by ghostdog74 on 2009-06-26
> **kaibob said:**
> 
```
for FILE in *.clas ; do
   NUM=$(echo "$FILE" | sed 's/^.*Param//' | sed 's/_.*$//')
   BEGIN=$(echo "$FILE" | sed 's/'"${NUM}"'.*$//')
   END=$(echo "$FILE" | sed 's/^.*'"${NUM}"'//')
   NEWNUM=$(printf "%03d" $(echo "${NUM}-7" | bc -q))
	cp "$FILE" "${BEGIN}${NEWNUM}${END}"
done
```

The following also worked:

```
for FILE in *.clas ; do
   BEGIN=$(echo "$FILE" | cut -c1-27)
   NUM=$(echo "$FILE" | cut -c28-30)
   NEWNUM=$(printf "%03d" $(echo "${NUM}-7" | bc -q))
   END=$(echo "$FILE" | cut -c31-40)
   cp "$FILE" "${BEGIN}${NEWNUM}${END}"
done
```


with bash , there is no need for external tools.eg
```

BEGIN=${FILE%???_???*}
num=${FILE#*Param}
NUM=${FILE%_*}
shopt -s extglob
NEWNUM=${NUM##+(0)}
newnum=$(printf "%03d" $(( NEWNUM - 7 )))
END=${num#*_}
shopt -u extglob  

```

reference: see my sig bash link

> 
I tried to use the rename command (as geirha did in a previous rename thread) but couldn't get it to work. It also occurred to me that shell expansion might be applicable, but I haven't gotten into that yet.
rename doesn't do maths for you. its just simple regex substitution.

---

### Post by ubuntu27 on 2009-06-26
I wish I were like you guys who know programming.

For a regular folk like me, I use a program written by others :popcorn:

There is an application called [pyRenamer]("http://www.infinicode.org/code/pyrenamer/") which will do the job just fine

```
sudo apt-get install pyrenamer
```

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

---

### Post by ghostdog74 on 2009-06-26
> **ubuntu27 said:**
> I wish I were like you guys who know programming.

For a regular folk like me, I use a program written by others :popcorn:

There is an application called [pyRenamer]("http://www.infinicode.org/code/pyrenamer/") which will do the job just fine

```
sudo apt-get install pyrenamer
```

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)
can it do maths, like in this case.

---

### Post by kaibob on 2009-06-27
> **ghostdog74 said:**
> rename doesn't do maths for you. its just simple regex substitution.

ghostdog74,

Thanks for the information. I like to make scripts as efficient as possible, so I'll study what you posted.

About the rename command, I had thought that it might be possible to extract and calculate the NEWNUM variable with SED or Bash and then plug that variable into the rename command. In very rough form, the rename command line would be something like:

```
rename 's/(.*Param)(_???.clas)/$1"$NEWNUM"$2/' "$FILE"
```

So, the rename command line would not involve any math calculation. But, as mentioned, I never could get it to work.

---

