---
title: "Help with Nautilus Scripts"
date: 2012-05-23
forum: General Help
---

### Post by lisanels47 on 2012-05-23
I'm using simple scripts, but when you select files that have spaces in the names, there seems to be no way to script those files.

For example, I have files "file 1.txt"  "file 2.txt" 
If I select those and try to run the scripts, the passed file list shows: file 1.txt file 2.txt
Looking like 4 instead of just 2.  

How can I get Nautilus to put quotes around the individual files before sending it to the scripts?

---

### Post by Sidewinder1 on 2012-05-23
I'm terrible with scripting; as long as you don't have too many files with the dreaded spaces in their names, you could always just rename them to something like
file_1.txt. But you probably already thought of that.

---

### Post by sisco311 on 2012-05-23
```

#!/bin/bash

for file in "$@"
#or simply:
#for file
do
    command "$file"
done

```

or if the command you run accepts more file names, then:
```

#!/bin/bash

command "$@"

```

@ expands to the positional parameters, starting from  one. When the  expansion  occurs  within  double  quotes,  each  parameter expands to a separate word. That is, "$@" is equivalent to "$1" "$2" "$3" ...

---

### Post by lisanels47 on 2012-05-23
Here's my test code, and the results from selecting two screenshots from the desktop.  


#!/bin/bash
    #
	echo $* > /tmp/junk
    for I in `echo $*`
    do
       /bin/chmod a+rw "$I"
       echo /bin/chmod a+rw "$I" >> /tmp/junk
       done
    done
    exit0
[email]lisa@lisa-Inspiron-1545:~/.gnome[/email]2/nautilus-scripts$ 

[email]lisa@lisa-Inspiron-1545:~/.gnome[/email]2/nautilus-scripts$ cat /tmp/junk
/home/lisa/Desktop/Screenshot from 2012-05-23 07:02:46.png /home/lisa/Desktop/Screenshot from 2012-05-23 07:08:22.png
/bin/chmod a+rw /home/lisa/Desktop/Screenshot
/bin/chmod a+rw from
/bin/chmod a+rw 2012-05-23
/bin/chmod a+rw 07:02:46.png
/bin/chmod a+rw /home/lisa/Desktop/Screenshot
/bin/chmod a+rw from
/bin/chmod a+rw 2012-05-23
/bin/chmod a+rw 07:08:22.png

---

### Post by sisco311 on 2012-05-23
For the differences between $* and $@, please check out:
```

man bash | less +/"^ +Special Parameters"

```

You should use "$@":
```
#!/bin/bash

chmod a+rw -- "$@"

```

---

### Post by lisanels47 on 2012-05-23
I get the same results with the $@.  See below:

#!/bin/bash
    #
	echo /bin/chmod a+rw -- "$@" > /tmp/junk
     	/bin/chmod a+rw -- "$@"
	exit 0


[email]lisa@lisa-Inspiron-1545:~/.gnome[/email]2/nautilus-scripts$ cat /tmp/junk

/bin/chmod a+rw -- Screenshot from 2012-05-04 11:26:29.png Screenshot from 2012-05-07 18:44:11.png

---

### Post by lisanels47 on 2012-05-23
Getting closer.  If I can figure out how to replace the newline characters with a set of quotes, I think I can do it.

---------------------------------------------------------------
#!/bin/bash
    #
	echo \""$@"\" > /tmp/junk
	exit 0

[email]lisa@lisa-Inspiron-1545:~/.gnome[/email]2/nautilus-scripts$ cat /tmp/junk
"/home/lisa/Desktop/Screenshot from 2012-05-14 22:13:21.png /home/lisa/Desktop/Screenshot from 2012-05-23 07:02:46.png"
---------------------------------------------------------------
#!/bin/bash
    #
	echo \""$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"\" > /tmp/junk
	exit 0


[email]lisa@lisa-Inspiron-1545:~/.gnome[/email]2/nautilus-scripts$ cat /tmp/junk
"/home/lisa/Desktop/Screenshot from 2012-05-14 22:13:21.png
/home/lisa/Desktop/Screenshot from 2012-05-23 07:02:46.png
"

---

### Post by sisco311 on 2012-05-23
> **lisanels47 said:**
> I get the same results with the $@.  See below:

#!/bin/bash
    #
	echo /bin/chmod a+rw -- "$@" > /tmp/junk
     	/bin/chmod a+rw -- "$@"
	exit 0


[email]lisa@lisa-Inspiron-1545:~/.gnome[/email]2/nautilus-scripts$ cat /tmp/junk

/bin/chmod a+rw -- Screenshot from 2012-05-04 11:26:29.png Screenshot from 2012-05-07 18:44:11.png

See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)


"$@" is the equivalent to "$1" "$2" "$3" and so on. $1, $2 $3 ... are the values of the positional parameters. The positional parameters contain the arguments that were passed to the current script. In our case the file names.

The quotes are not actually passed along to the command. If you run **echo "file name 1" "file name 2" "file name 3"**, the echo command will not *see* the quotes. The quotes are telling to bash, to pass **file name 1** as the first parameter, **file name 2** as the second parameter... to the echo command.

That's why you don't see the quotes around each file name in your /tmp/junk file. But, **chmod a+rw -- "$@"** will work as expected.

---

### Post by lisanels47 on 2012-05-23
AH!  Thank you!  I understand it now.

---

### Post by sisco311 on 2012-05-23
You are welcome!

Oh, and don't use the NAUTILUS_SCRIPT_SELECTED_FILE_PATHS variable. The value of the variable is a newline-delimited paths for selected files. Sounds very convenient. You would expect that each line in it's value is a path to a file. The problem is that file names can contain newlines. In which case the file name will take up two lines.

---

