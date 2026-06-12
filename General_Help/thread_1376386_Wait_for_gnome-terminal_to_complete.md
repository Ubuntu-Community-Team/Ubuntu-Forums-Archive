---
title: "Wait for gnome-terminal to complete"
date: 2010-01-09
forum: General Help
---

### Post by jkounis on 2010-01-09
I had a script in my ~/.gnome2/nautilus-scripts which looked something like:

```
for FNAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    xterm -e <myscript> $FNAME
done

```

This worked OK, and the xterm window showed me the output from my script just fine; however, the fonts are lousy for me in xterm, and the scrollbar settings aren't the same as for my gnome-terminal, so I changed the script to :


```
for FNAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    gnome-terminal -x <myscript> $FNAME
done

```

Now, the problem is that all the gnome-terminals start at once. If I am processing 100 files, I get 100 simultaneous windows, which is unmanageable. 

Is there a way to wait until the current gnome-terminal exits before continuing through the loop and opening the next one, like xterm does?

---

### Post by John Bean on 2010-01-09
I'm intrigued why you want to launch a new terminal each time around the loop - is there a reason you can't just run the script (MyScript) inside the loop in the current terminal? You can use the current shell or create a new one each time but I can't think of any obvious need to create a new terminal each time.

---

### Post by jkounis on 2010-01-09
> **John Bean said:**
> I'm intrigued why you want to launch a new terminal each time around the loop - is there a reason you can't just run the script (MyScript) inside the loop in the current terminal? You can use the current shell or create a new one each time but I can't think of any obvious need to create a new terminal each time.

Your suggestion is probably the solution I need, although it will take a little work to implement.

The reason I originally chose to invoke gnome-terminal multiple times is because I have had problems passing paths with spaces in them to a script through gnome-terminal. (And because I already had a script that I didn't want to modify that processed one directory at a time.)

For example, if $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS contains two directory names: "January Data" and "February Data", then I can execute the for loop with no problem as long as I change IFS. So the full code below:
```
IFS=$'\n'
for FNAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    gnome-terminal -x <myscript> "$FNAME"
done
```
would execute twice: once for "January Data" and once for "February Data".

However the following code:
```

gnome-terminal -x <myscript> $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

```
will receive 4 arguments: "January", "Data", "February" and "Data".

The only solution I can think of isn't very pretty:
```
TEMPFILE=`mktemp`
echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > $TEMPFILE
gnome-terminal -x <myscript> $TEMPFILE

```
To use the code above, of course, my script would need to be modified to read the filenames from a file too.

This added complication was the reason I hadn't originally gone this route. I can't think of a simpler way to do it.

---

### Post by John Bean on 2010-01-09
I think we're at cross purposes, I'll try to make my question a bit clearer. Inside the loop you execute ```
gnome-terminal -x <myscript> "$FNAME"
``` and I'm asking why you don't just run your script directly: ```
myscript "$FNAME"
```I really don't understand why you're invoking a new terminal (which then invokes your favoured shell) to run your script when you're in a perfectly good shell already...

What am I missing?

---

### Post by itcotbtoemik on 2010-01-09
I do recall seeing the embedded-blanks issue as one of
gnome-terminal's bugs.

However, xterm's fonts can be changed (man xterm).
You might want to use a TrueType font (see the -fa option).

---

### Post by falconindy on 2010-01-09
> **John Bean said:**
> I think we're at cross purposes, I'll try to make my question a bit clearer. Inside the loop you execute ```
gnome-terminal -x <myscript> "$FNAME"
``` and I'm asking why you don't just run your script directly: ```
myscript "$FNAME"
```I really don't understand why you're invoking a new terminal (which then invokes your favoured shell) to run your script when you're in a perfectly good shell already...

What am I missing?

Second this. You want to execute the script with the -X flag of gnome-terminal, not launch gnome-terminal repeatedly inside the script.

If you're having issues dealing with white space, your issue isn't choice of terminal -- it's your syntax in the script itself. Fix the problem, don't bandaid it!

---

### Post by jkounis on 2010-01-09
> **John Bean said:**
> I think we're at cross purposes, I'll try to make my question a bit clearer. Inside the loop you execute ```
gnome-terminal -x <myscript> "$FNAME"
``` and I'm asking why you don't just run your script directly: ```
myscript "$FNAME"
```I really don't understand why you're invoking a new terminal (which then invokes your favoured shell) to run your script when you're in a perfectly good shell already...

What am I missing?

Unfortunately, I am invoking the script from nautilus, not from my favoured shell.

The script is intended to be run from a shell (i.e. it interacts with the user through "echo MESSAGE" and "read VARIABLE"). It collects statistics about how many log files were created in a directory, how many errors there were, etc., then it asks the user if the source files should be archived or deleted or saved after it gives the user some information about them.

But I am too lazy to invoke the script manually for a bunch of directories, so I wrote a parent script and put it in ~/.gnome2/nautilus-scripts. That way, I could select a bunch of directories, right-click on them and then select "Process Statistics". 

Since the script is invoked from nautilus, rather than from a shell, there is no way for it to interact with the user. I either have to invoke it in an xterm or in a gnome-terminal, or rewrite it to interact with the user by using zenity rather than read/echo, or I have to invoke it in a terminal window.

---

### Post by jkounis on 2010-01-09
> **falconindy said:**
> Second this. You want to execute the script with the -X flag of gnome-terminal, not launch gnome-terminal repeatedly inside the script.

If you're having issues dealing with white space, your issue isn't choice of terminal -- it's your syntax in the script itself. Fix the problem, don't bandaid it!

I would love to fix the problem, but the only solution I could come up with seems like it could be more of a bandaid to me than the original solution. The original solution I had was to take an old, tested, known-working script and execute it several times through the nautilus right-click "Scripts" menu. 

Is there an accepted the best practice for passing the NAUTILUS_SCRIPT_SELECTED_FILE_PATHS variable to a child script without splitting all the paths at the white space?

The only solution I could come up with is to use a temp file, which isn't very elegant:
```
TEMPFILE=`mktemp`
echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > $TEMPFILE
gnome-terminal -x <myscript> $TEMPFILE
```

Then, I would have to change the first line of myscript from:

```
cd "$1"
```

to:

```
cd "`cat "$1"`"
rm "$1"
```

Is this the best way to solve the problem?

---

### Post by kaibob on 2010-01-09
I'm not sure I completely understand the issue but wanted to look into the use of gnome-terminal with a Nautilus script. I wrote the following Nautilus script on a conceptual basis. It works and does not have any issues with directories and files with spaces. I think this could be adapted without difficulty to the OP's needs--at least as I understand them. 

```
#!/bin/bash

print () 
{ 
read -p "Select (c)opy, (m)ove, or (e)xit: " response
[ "$response" = c ] && action=cp
[ "$response" = m ] && action=mv
[ "$response" = e ] && exit 1

IFS=$'\n'

for dir in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ; do
   for file in ${dir}/* ; do
      ${action} ${file} /home/kaibob/temp
   done
done
}

export -f print

gnome-terminal --execute bash -c "print ; bash"
```

The bash at the end of the gnome-terminal line keeps the terminal window from closing. If you want the terminal window to close upon completion of the script, then remove this bash.

---

### Post by jkounis on 2010-01-09
> **kaibob said:**
> I'm not sure I completely understand the issue but wanted to look into the use of gnome-terminal with a Nautilus script. I wrote the following Nautilus script on a conceptual basis. It works and does not have any issues with directories and files with spaces. I think this could be adapted without difficulty to the OP's needs--at least as I understand them. 
<snip>


Thank you. Your example script is exactly what I needed. The key items in it that I learned are:
[INDENT]     (1) You can export a function from the parent script to the gnome terminal with "export -f".
     (2) It's a good idea to use "gnome-terminal --execute bash" rather "gnome-terminal --execute scriptname" to invoke the shell I need
[/INDENT]
Incidentally, once the script is done, I don't need the bash window anymore, so I changed gnome-terminal --execute bash -c "print ; bash"  to "gnome-terminal --execute bash -c print", and it works just fine. As soon as the script asks what to do with the files, it does it and the window closes.

Thanks again.

---

### Post by kaibob on 2010-01-09
> **jkounis said:**
> Thank you. Your example script is exactly what I needed. The key items in it that I learned are:
[INDENT]     (1) You can export a function from the parent script to the gnome terminal with "export -f".
[/INDENT]<snip>
I'm glad you got things working. 

On the export function issue, I encountered this some time back and was only able to resolve it with help from jpkotta in the Programming Talk forum. 

[http://ubuntuforums.org/showthread.php?t=1236152](http://ubuntuforums.org/showthread.php?t=1236152)

---

### Post by cben on 2010-10-26
```
gnome-terminal **--disable-factory** -e some_command 
```

should wait for command to complete.
Opened [https://bugs.launchpad.net/ubuntu/+bug/666418](https://bugs.launchpad.net/ubuntu/+bug/666418) about this.

---

