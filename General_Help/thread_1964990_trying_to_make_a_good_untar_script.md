---
title: "trying to make a good untar script"
date: 2012-04-24
forum: General Help
---

### Post by mferarri on 2012-04-24
hi ubuntu forums,

I'm trying to make a bash script for my (home/user/Downloads) folder to extract downloaded tar files to a folder called "extracted".

I want each extraction process to result in a parent folder with a name that I give to it because sometimes the extraction of a file results in a mess of files.

I have made a script that works, but it's very simple and i want to improve on it.

```
#bin/sh
mkdir extracted
for i in *.tar.gz
do
	tar -xf "$i" -C ./extracted
done

```



So far i have a script that dosent work:

```
#bin/sh

mkdir extracted

for i in *.tar.gz

tar -tvf "$i" > tar_contents
ls > extracted_contents

do
	if [! $tar_contents -eq $extractedcontents ]; then
		x=$(zenity --entry --text "Parent Folder Name for "$i)
		mkdir ./extracted/$x
		tar -xf "$i" -C ./extracted/$x	

	else 
		echo "done"
	fi
done
```

can anyone give me any suggestions on how i could tackle my problem?

---

### Post by papibe on 2012-04-24
Hi mferarri.

I would use the same tar filename to generate the directory name. For instance: let's say you have a tar file named 'driver_09.v45.tar.gz':
```
$ var=driver_09.v45.tar.gz
$ echo $var
driver_09.v45.tar.gz

$ dir="${$var%%.tar.gz}"
$ echo $dir
driver_09.v45

```
Modifying your first script:
```
#!bin/bash

mkdir ./extracted

for i in *.tar.gz; do
    dir="${$var%%.tar.gz}"

    mkdir ./extracted/"$dir"
    tar -x**[COLOR="Red"]z[/COLOR]**f "$i" -C ./extracted/"$dir"
done
```
I hope that helps, and tell us how it goes.
Regards.

Note 1: I explicitly use the 'z' option to extract .gz tars.

Note2: if there are spaces on the files names, that script won't work properly, thus another approach would be necessary.

---

### Post by mferarri on 2012-04-24
WOW! thanks papibe!

I was totally making things more complicated that it should be. your solution is great! thanks!:KS

---

### Post by mferarri on 2012-04-24
> 
I hope that helps, and tell us how it goes.
Regards.


I've adjusted my script to be like this:
```
#bin/sh

mkdir extracted

for i in *.tar.gz; do

		mkdir ./extracted/$i
		tar -xzf "$i" -C ./extracted/$i	

done
```

> 
Note 1: I explicitly use the 'z' option to extract .gz tars.

what is the difference if i use it or not? (it goes through gunzip?) is it a filesize difference?

> 
Note2: if there are spaces on the files names, that script won't work properly, thus another approach would be necessary.


I'll try to work out how to delete spaces from filenames now. thanks.

---

### Post by papibe on 2012-04-24
Even simpler. I like it ):P

Just don't forget to quote your variables:
```
...
mkdir ./extracted/"$i"
tar -xzf "$i" -C ./extracted/"$i"
...
```

> **mferarri said:**
> 
what is the difference if i use it or not? (it goes through gunzip?) is it a filesize difference?
It would be the proper way to do it. tar.gz means that the files were put together on a tar file and then compress using gunzip. Using the 'z' option would be asking to uncompress the file first and then untar the files.

I haven't use too much tar lately, may be it got smart and it is not a mandatory option anymore, but that's the way I learned it.

Kind Regards.

---

### Post by mferarri on 2012-04-24
I think i've made a very elegant script. Feel free to use it everybody!

Note1: You may have to change the first line from "#bin/sh" to "#!bin/bash" for it to work on you ubuntu system.

Note2: Don't forget to make it an executable! Type: $Chmod +x *nameofscript*

```
#bin/sh

mkdir extracted

for i in *.tar.gz; do
		
		#replace spaces with underscores
		mv "$i" `echo "$i"|tr " " "_"` 
		
		#make dir and extract to it
		mkdir ./extracted/"$i"
		tar -xzf "$i" -C ./extracted/"$i"	

done
```

---

### Post by papibe on 2012-04-24
The problem with spaces affects the 'for...' construction, and can't be fixed that way.

To realize the problem with spaces try this
```
for file in *; do
    echo "$file"
done
```

You would need a different approach. For example:
```
while IFS= read -d '' -r file
do
    ...
    ...
done< <(find -iname '*.tar.gz' -print0)
```
I hope that clarify things a little bit about spaces.
Regards.

---

### Post by mferarri on 2012-04-24
> **papibe said:**
> The problem with spaces affects the 'for...' construction, and can't be fixed that way.

To realize the problem with spaces try this
```
for file in *; do
    echo "$file"
done
```

You would need a different approach. For example:
```
while IFS= read -d '' -r file
do
    ...
    ...
done< <(find -iname '*.tar.gz' -print0)
```
I hope that clarify things a little bit about spaces.
Regards.


this is what i get: (note there is a tar file with spaces) 

```

mike@speedmachine:~/prog/scripts$ for file in *; do echo "$file" ;done
extracted
py gtk tutorial-src.tar.gz
tar_list
tar_list2
trash-cli-0.1.10.28.tar.gz
untarscript
untarscript_v2
untarscript_v3
mike@speedmachine:~/prog/scripts$ 

```

My last script works for me even for tar files with spaces. i think i kinda get what you mean about the error being in the "for constructor", but according to my experiments, files with spaces are still identified as 1 file.

thanks for being so helpful!

---

