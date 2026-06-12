---
title: "Terminal shell help?"
date: 2010-08-28
forum: General Help
---

### Post by JoJo on 2010-08-28
When I use the terminal to execute commands, all files paths are interpreted as relative to the current directory.  

For example if I execute this, it looks for a directory called "usr" inside my "Documents" directory.
```
joanna@flower:~/Documents$ sudo cp file.txt /usr/share/blahblah
```

Instead what I have to do is this, ~ being my home directory.
```
sudo cp file.txt ~/../../usr/share/blahblah
```

I am using the bash shell.  Does it have anything to do with that?

---

### Post by Ayuthia on 2010-08-28
Does this only happen in the Documents directory or does it happen in any directory?  If it only happens in the Documents directory, you might check and see what files are in there.

The command that you are using should default to /usr/share instead of looking in the Documents directory.

---

### Post by AlphaLexman on 2010-08-28
You are better off entering the full path for each file ->
```
sudo cp ~/Documents/file.txt /usr/share/blahblah/
```Be sure to add the slash (/) after the last directory name!

---

### Post by AlphaLexman on 2010-08-28
One more thing, what is the output of:
```
echo $CDPATH
```

---

### Post by JoJo on 2010-08-28
> **AlphaLexman said:**
> One more thing, what is the output of:
```
echo $CDPATH
```

That command gives me a blank line.
```
joanna@flower:~$ echo $CDPATH

joanna@flower:~$ 

```

And the problem is full paths.  My terminal sees full paths as relative to the current directory, no matter what directory I'm in.

---

### Post by AlphaLexman on 2010-08-28
> **JoJo said:**
> That command gives me a blank line.
That's a good thing!

---

### Post by AlphaLexman on 2010-08-28
Just checking...
What is the output of:
```
echo $PATH
```

---

### Post by JoJo on 2010-08-28
> **AlphaLexman said:**
> Just checking...
What is the output of:
```
echo $PATH
```

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by AlphaLexman on 2010-08-28
Deadend: (that's what it should be...)

---

### Post by AlphaLexman on 2010-08-28
> **JoJo said:**
> When I use the terminal to execute commands, all files paths are interpreted as relative to the current directory. 
Does this only happen in a 'terminal'?

if
```
echo $SHELL
```= '/bin/bash'

then post:
```
cat ~/.bashrc
```

---

