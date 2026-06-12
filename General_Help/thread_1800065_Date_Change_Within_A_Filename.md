---
title: "Date Change Within A Filename"
date: 2011-07-08
forum: General Help
---

### Post by cc_taylor on 2011-07-08
[LEFT][/LEFT]Hello;

As an Ubuntu newbie - I'm trying to change the date of the following text file from 1970 to 2011 (I have 500 text files to rename).  Can Ubuntu do this natively or will I have to speak to the "Script Guru's"?

TG.ALISISPOASDLDSIASI-1970-2d938787212.txt

Any advice you could give would be hugely appreciated.

Kind Regards

Chris.

---

### Post by lmarmisa on 2011-07-08
Open a terminal and type the command touch:

```

touch filename

```

For more information type:

```

man touch

```

---

### Post by haqking on 2011-07-08
> **cc_taylor said:**
> Hello;

As an Ubuntu newbie - I'm trying to change the date of the following text file from 1970 to 2011 (I have 500 text files to rename).  Can Ubuntu do this natively or will I have to speak to the "Script Guru's"?

TG.ALISISPOASDLDSIASI-1970-2d938787212.txt

Any advice you could give would be hugely appreciated.

Kind Regards

Chris.

rename will do what you want

go to terminal and type man rename for options.

You could alsonwrite a short script using the for command but rename from cli would be easier in this case i think.

something like the following using * wildcards etc.

rename oldname newname *.files

---

### Post by haqking on 2011-07-08
> **lmarmisa said:**
> Open a terminal and type the command touch:

```

touch filename

```For more information type:

```

man touch

```

touch is for changing timestamps.

I think from the OP the date is in the filename and not the timestamp itself.

he wants to replace the 1970 contained in 500 filenames to 2011 instead ?

---

### Post by cc_taylor on 2011-07-08
HaqKing has got it - I need to change the date of 1970 to 2011 on 500 files......am I going to need to speak to someone who could script this or can Ubuntu do it natively? :-)

---

### Post by TeoBigusGeekus on 2011-07-08
```
#!/bin/bash
find ./ -iname "*-1970-*"|while read oldname;
do
	newname=$(echo $oldname | sed 's/1970/2011/g')
	mv "$oldname" "$newname"
done
```

Save it as 1970_to_2011 in the directory where the files to be renamed are.
Navigate to the directory from the command line, make it executable
```
chmod +x 1970_to_2011
```
and run it
```
./1970_to_2011
```
The script will also act recursively, ie. search the subfolders and rename any matching files in them as well.

---

### Post by JC Cheloven on 2011-07-08
I think the OP will be more comfortable with a simple gui program. I used pyrenamer once and worked fine for what I needed.

There are some others: purr or gprename for instance.

You can install any (of all) of them from the repos.

Hope this helps

---

