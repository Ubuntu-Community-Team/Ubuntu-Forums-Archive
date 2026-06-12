---
title: "what did I do?"
date: 2012-07-27
forum: General Help
---

### Post by takitsan on 2012-07-27
Hi! Sorry if I am posting in the wrong section.

I was trying to pass a string to makepasswd, with characters to use in password generation, but I made a mistake with the syntax and typed:

[B]user@comp:/$ makepasswd --string ^&*
[/B]
i.e. no quotation marks around the string ^&* (](*,))
The computer took a moment and then came back with:
[B]
[1] 2842
^^^^^^^^^^
No command 'bin' found, did you mean:
 Command 'win' from package 'wily' (universe)
 Command 'tin' from package 'tin' (universe)
 Command 'bip' from package 'bip' (universe)
 Command 'bing' from package 'bing' (universe)
 Command 'bins' from package 'bins' (universe)
bin: command not found
[1]+  Done                    makepasswd --string ^[/B]


can anyone figure out what was actually Done ?

---

### Post by papibe on 2012-07-27
Hi takitsan.

The characters '&' and '*' have special meaning for Bash (the terminal shell). If you want to use them as parameter you would have to 'escape' them.

Try this:
```
makepasswd --string ^\&\*
```
Hope that helps. Tell us how it goes.
Regards.

---

### Post by spjackson on 2012-07-27
Firstly it has done ```
makepasswd --string ^
```in the background. Then secondly, it has tried to execute another command starting with "bin", which isn't found to be an executable on the path, so it has done nothing.

To see what it tried and failed to do, try this
```

cd /
echo *

```

---

### Post by sisco311 on 2012-07-27
EDIT: D'oh, I'm super slow today! spjackson beat me to it.

If a command is terminated by &, then the shell executes it in a subshell in the background. So you started `makepasswd --string ^' in the background (which is harmless). 

* is a glob; by default, it matches any non-hidden file in the current working directory.

You ran the command in / so the glob was expanded to the file names from /, something like `bin boot dev etc etc...', then the shell tried to execute the command `bin' with the rest of the file names as its arguments.

Since there was no bin command installed on your system the command_not_found_handle bash function printed the warning message.

---

### Post by takitsan on 2012-07-27
That was prompt !

Thanks papibe!  I was actually looking for what spjackson and sisco311, in style, answered.
But it's always good to learn something new!
BTW, I tried the 'escaped' version and it works fine....!

Thank you all!

ps

---

### Post by sisco311 on 2012-07-27
You are welcome!

Please don't forget to mark this thread as solved.

---

### Post by takitsan on 2012-07-28
oops!  forgot to!!!

just did...

---

