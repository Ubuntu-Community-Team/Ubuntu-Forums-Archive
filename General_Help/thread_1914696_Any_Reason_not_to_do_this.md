---
title: "Any Reason not to do this?"
date: 2012-01-24
forum: General Help
---

### Post by alphaamanitin on 2012-01-24
Is there any reason not to do this:

Make a bash script of the following```
#!/bin/bash
sudo apt-get update; sudo apt-get upgrade; sudo apt-get clean; sudo apt-get autoclean; sudo apt-get remove
```

And save it in the PATH so that it can be ran from anywhere in the system via terminal? 

AlphaA

---

### Post by bluexrider on 2012-01-24
your ```
sudo apt-get remove
```

will fail without a designated package

Use instead ```
sudo apt-get autoremove
```

---

### Post by bodhi.zazen on 2012-01-25
The main reason NOT to do this is that, IMO, it is important to review the packages before they are updated.

Also, again IMO, in your script you should use the full path, and at least some error handling.

```
#!/bin/bash
APT='/usr/bin/apt-get'

$APT update || echo "update failed"
$APT dist-upgrade || echo "update failed"
$APT clean
$APt autoclean
```

You then call the script with sudo (rather then using sudo in the script).

---

### Post by alphaamanitin on 2012-01-25
@bluexrider, that is a type, in the actual script (which I haven't used yet cause I know enough to know I don't fully understand the complications with the scrip), it is autoremove.

@Bodhi.zazen, what if I don't want to do the dist-upgrade?  I assume that bit can just be upgrade?  Also, could you explain your code a bit more in depth?  As I am sure my little script shows, I know very little BASH.

Thanks,

AlphaA

---

### Post by bodhi.zazen on 2012-01-25
> **alphaamanitin said:**
> @Bodhi.zazen, what if I don't want to do the dist-upgrade?  I assume that bit can just be upgrade?  Also, could you explain your code a bit more in depth?  As I am sure my little script shows, I know very little BASH.

Thanks,

AlphaA

My script is just a snipit, feel free to modify it as you see fit.

What part do you want explained ? || is or, so if the command fails you get an error message.

---

### Post by alphaamanitin on 2012-01-25
The APT part.  I think the APT=...... is setting the working directory/command?  Then when when it appears later as $APT, the $APT is basically equal to typing in, apt-get at the command line, right?

After you mentioned it I remember reading || stood for "or."  Thanks for reminding me.  Am I correct in guessing | stands for "and".  Also, is the functional difference between separating commands with "|" vs ";" that the pipe takes output from first command and inputs it into the second command, while ";" merely allows you to run two commands sequentially?  Most likely I am horribly wrong.  I need to find my book on the linux command line/operanting system and start reading it again.   

Thanks,

AlphaA

---

### Post by bodhi.zazen on 2012-01-25
APT= set a variable
$APT call the variable

See : [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by SeijiSensei on 2012-01-25
> **bodhi.zazen said:**
> $APT call the variable

I'll put on my pedant's hat and say that bash replaces $APT with the variable's value, then executes the line.  For instance,

```

YOU='Harry'
echo "Do you love me, $YOU?"

```

will display "Do you love me, Harry?" at the terminal. Enclosing a string in double-quotes like that tells bash to replace the variable with its value.  If you enclose the string in single-quotes, bash does no replacements and treats the variable as a literal like this:```
echo 'Do you love me, $YOU?'
```The result will be displayed as "Do you love me, $YOU?".

---

### Post by alphaamanitin on 2012-01-26
Ug, I feel stupid. I do perl coding and can't imagine why I failed to recognize $APT as a variable.  My only defense is that I am a HORRIBLE, beginnner coder, secondarily interested as it applies to Molecular Biology.  I am a PhD student of mycology.

That is the exact book I have been reading on my nook bodhi.  On a side note, anyone recommend a good starter for learning BASH scripting?

AlphaA

---

### Post by |{urse on 2012-01-26
Don't kick yourself, humility is the path to great things. :) Hell, until recently I thought I was coding in C but it was C++ the whole time lol (multifacepalm), In the end I gained something very important from this knowledge but I had to look past pride to see the reward. Now my **C++** is even better ^_-

---

### Post by bodhi.zazen on 2012-01-27
> **alphaamanitin said:**
> Ug, I feel stupid. I do perl coding and can't imagine why I failed to recognize $APT as a variable.  My only defense is that I am a HORRIBLE, beginnner coder, secondarily interested as it applies to Molecular Biology.  I am a PhD student of mycology.

That is the exact book I have been reading on my nook bodhi.  On a side note, anyone recommend a good starter for learning BASH scripting?

AlphaA

You will do fine, the link I gave you in my last post is my favorite, it will get you started.

---

### Post by sisco311 on 2012-01-27
> **alphaamanitin said:**
> Ug, I feel stupid. I do perl coding and can't imagine why I failed to recognize $APT as a variable.  



Strictly speaking, APT is the variable and $APT is called a variable expansion. 

In BASH, by convention, we capitalize environment variables (PAGER, EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...). All other variable names should contain at least one lowercase letter. Variable names are case-sensitive; this convention avoids accidentally overriding environmental and internal variables.

> **alphaamanitin said:**
> 
After you mentioned it I remember reading || stood for "or."  Thanks for reminding me.  Am I correct in guessing | stands for "and".  Also, is the functional difference between separating commands with "|" vs ";" that the pipe takes output from first command and inputs it into the second command, while ";" merely allows you to run two commands sequentially?  Most likely I am horribly wrong.  I need to find my book on the linux command line/operanting system and start reading it again.   

Thanks,

AlphaA

The man page of BASH explains the differences quite well:
```
man bash | less +/"^ +Lists"
```


So, you could do something like:
```

#!/bin/bash

apt="apt-get"

# run apt-get upgrade only if apt-get update was successful
$apt update && $apt upgrade

```

Another way would be something like:
```

...

# if the update fails, print an error message to STDERR and 
# exit with a non-zero exit status
$apt update || { printf '%s\n' "$0: update failed"; exit 1; } >&2
$apt upgrade ...
...

```

> **alphaamanitin said:**
> 
On a side note, anyone recommend a good starter for learning BASH scripting?


Check out the links in my signature.

---

### Post by alphaamanitin on 2012-02-14
How did I miss this last post??  Thought I subscribed to my thread.  Thanks for all the responses and links.

AlphaA

---

