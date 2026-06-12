---
title: "Lost variable value out of Loop!"
date: 2011-01-27
forum: General Help
---

### Post by stamoulohta on 2011-01-27
Hello,

I really don't get this!! I must be doing something really foolish but i can't figure out what it is. Please help.

```
#!/bin/bash

pro_num=0
unpro_num=0

find . | while read new_file; do

	if [ -f $new_file ]; then 
		pro_num=$(($pro_num + 1))
		echo "$pro_num"              # THIS WORKS FINE!
		echo -e "$new_file \\tis a file" #printf
	else 
		unpro_num=$(($unpro_num + 1))
		echo "$unpro_num"	     # THIS WORKS FINE!		
		echo -e "\033[31m \\n$new_file \\tis not a file \033[0m"
	fi
	
done

# THE FOLLOWING TWO DON'T WORK!!

echo -e \\n\\n"Files that can be processed = $pro_num"

echo "Files that can't be processed = $unpro_num"
```

So, the question is: Why does $pro_num and $unpro_num loose their assigned values when the "while" loop exits?! Is there a way to "global" them or something?

Please shed some light into my dark and desperate world!! ;)

Thank you,
George.

---

### Post by justleen on 2011-01-27
How about something like this?

```
#!/bin/bash

pro_num=0
unpro_num=0

**for i in $(find .); do**

	if [ -f $new_file ]; then 
		pro_num=$(($pro_num + 1))
		echo "$pro_num"              # THIS WORKS FINE!
		echo -e "$new_file \\tis a file" #printf
	else 
		unpro_num=$(($unpro_num + 1))
		echo "$unpro_num"	     # THIS WORKS FINE!		
		echo -e "\033[31m \\n$new_file \\tis not a file \033[0m"
	fi
	
done

# THE FOLLOWING TWO DO WORK!!

echo -e \\n\\n"Files that can be processed = $pro_num"

echo "Files that can't be processed = $unpro_num"
```


The pipe into read spawns a new proccess, which can "read" the set variables, but can't return it to the main proccess.

There is no such thing as globals and locals in bash, but you do have to pay attention to spawning like this.


"let" might be more readable:  pro_num=$(($pro_num + 1))  ->  becomes ->   let pro_num++

---

### Post by stamoulohta on 2011-01-27
Thank you justleen,

but the "for" loop won't work for me. The code was part of a bigger script that i tried to minimize for my examle... and obviously I failed!! ;)

I need the "while read" loop because i need to feed the files in the mp3info program recursively so i need to keep the "find" command. With the "for" loop spaces in filenames cause problems no mater what I've tried (sed 's/ /\\ /g' ; quotes ; etc).

one solution, from what you say, is to make one function to count the files and another to feed them into mp3info but i would prefer to avoid it.

Thank you very much for the clarification about pipes operation and for the "let $some_num++" tip!

Cheers ;)

---

### Post by justleen on 2011-01-27
or stay away from the pipe?
```

find .  > outputfile.txt

while read line; do
   code 
   echo $line
   code
done < outputfile.txt


```

Not sure why you simply don't use find -type f . ? Wouldnt that be way easier to find just files?

---

### Post by stamoulohta on 2011-01-28
Hey!!

Your last proposal works perfectly for my script! (Seems a bit clumsy to create a temp file but I can live with that!!)

Thank you very very much!

PS: Looking for files was just an example because it didn't seem wright uploading a code with "mp3info" in it...

Cheers ;)

---

