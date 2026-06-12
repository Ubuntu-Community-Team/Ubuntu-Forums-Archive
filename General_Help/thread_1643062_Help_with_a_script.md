---
title: "Help with a script"
date: 2010-12-11
forum: General Help
---

### Post by chimi_12 on 2010-12-11
Hi!

I'm making a script for check my Internet connection. I'm new on this, then if you think that my script can be more simple, I accept suggestions.

I'm just starting the script, but this is where I have the first problem, I need to know how to fix it before continuing.

This is the script:

```
1 #!/bin/bash
2 It checks the percentage of lost packets. (ping to modem's gateway)
3 ping -c 5 123.123.123.1 | grep "packet loss" | awk '{printf ("%d",$6)}' > ./loc
4 #give the status of the last ping
5 if "./loc" -gt "0"; then
6 echo -e "`date`\nNet status = down" >> ./reg; else
7 echo -e "`date`\nNet status = up" >> ./reg; fi

```

After execute it, I get a permission denied error at the line 5

```
./net.sh: línea 5: ./loc: Permiso denegado

```

I don't know why get this error, the file "loc" in my folder has permissions assigned for read and write and The error only occurs when you run the conditions, if "./ loc "... because when I run other commands on the file I have no errors.

It is noteworthy that the "loc" and "reg" files are created with the script. The resulting file "reg" is this:

```
thu 9 dic 12:39:58 CST 2010
Net status = up
```

What can be? Thanks in advance.

---

### Post by iponeverything on 2010-12-11
use "test" on loc

do 

```
man test
```

---

### Post by lykeion on 2010-12-11
This line is wrong in so many ways. 
* You cannot access file contents with only the the file name.
* -gt operator is for numerical comparisons, so why do you write "0"?
[PHP]if "./loc" -gt "0"; then[/PHP]
This works: 
[PHP]if [ $(cat ./loc) -gt 0 ]; then[/PHP]
But like above poster said, you should read up on bash test.

Good luck with your script!

---

### Post by chimi_12 on 2010-12-11
I modify the script to this:

```
1 #!/bin/bash
2 #ping local
3 ping -c 5 201.195.67.121 | grep "packet loss" | awk '{printf ("%d",$6)}' > ./loc
4 #comprobación conexión local
5 loc=./loc
6 if [ $loc -gt 0 ]; then
7 echo -e "`date`\nRed interna estado = down" >> ./reg; else
8 echo -e "`date`\nRed interna estado = up" >> ./reg; fi

```

But I get another error:

```
./net.sh: línea 6: [: ./loc: se esperaba una expresión entera

```

it means: 

```
./net.sh: line 6: [: ./loc: integer expression expected
```

If I type $cat ./loc I get 0 (zero) this is result of percentage of packet loss of the ping to modem's gateway. Then don't know what to do.

---

### Post by chimi_12 on 2010-12-11
> **lykeion said:**
> This line is wrong in so many ways:
[PHP]if "./loc" -gt "0"; then[/PHP]
This works: 
[PHP]if [ $(cat ./loc) -gt 0 ]; then[/PHP]
But like above poster said, you should read up on bash test.

I had not seen this response, I will try and comment later.

Thanks!

---

### Post by chimi_12 on 2010-12-11
> **lykeion said:**
> This works: 
[PHP]if [ $(cat ./loc) -gt 0 ]; then[/PHP]

This really works!! Thanks for your help!!

---

### Post by lykeion on 2010-12-11
Good that it worked out for you, could you please tag this thread as [SOLVED]("http://ubuntuforums.org/showpost.php...51&postcount=6") to let others find solutions easily.

---

### Post by sisco311 on 2010-12-11
I have a few suggestions if you don't mind:
[list]
[*]use indentation


[*]instead of `command` use $(comamnd)


[*]instead of $(cat file) use $(< file)


[*]don't use relative paths; save the files in your home or /tmp


[*]I don't see any reason for saving the output of ping in a file
[/list]

```

#!/bin/bash

#ping local
loc=$(ping -c 5 201.195.67.121 | grep "packet loss" | awk '{printf ("%d",$6)}')

#comprobación conexión local
if [ $loc -gt 0 ]; then
  echo -e "$(date)\nRed interna estado = down" >> ~/reg
else
  echo -e "$(date)\nRed interna estado = up" >> ~/reg
fi

```

---

### Post by chimi_12 on 2010-12-11
sending the output of ping to a file was part of tests to resolve other errors not mentioned, it worked and so I left it, now I know I can make a variable on these commands instead of sending it to a file. In fact I'm already using it and thanks for your suggestions.  ;)

---

