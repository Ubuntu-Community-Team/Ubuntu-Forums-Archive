---
title: "Redirect output to a secondary terminal window"
date: 2009-10-04
forum: General Help
---

### Post by Nunyah on 2009-10-04
Hi,

Since everything is a file in nix, where can I find the file for my 2nd terminal window?

I want to write the output of a command in my first terminal and have the output in my 2nd.

---

### Post by Nunyah on 2009-10-04
Does anyone know how to do this?

To clarify what I want to do:
```

echo "Hello, world!" > output.txt
```

only instead of writing "Hello, world!" to the file output.txt, I want to write it out to my 2nd terminal window I have already open.

---

### Post by Lars Noodén on 2009-10-04
If these are on the same machine, then one way is to make a [named pipe](http://linux.die.net/man/7/fifo), aka first-in first-out special file

```

mkfifo --mode=600 /tmp/foo

```

Then one terminal writes to it (e.g. [FONT="Courier New"]echo "Hello, world!" > /tmp/foo[/FONT]) and the other reads from it (e.g.[FONT="Courier New"]tail -f /tmp/foo[/FONT])



If they're on different machines, then you can do it anyway over ssh.

---

### Post by Nunyah on 2009-10-04
Thanks for that, Lars Noodén.

However I'm looking for a way to solve this without creating a fifo.

If I'm not horribly mistaken, there should be a way to like the example below:
```
ls -l > fileToTerminalWindow2
```
I don't know the name of the file for the terminal window and whenever I try to google keywords for this, I get guides concerning file manipulation in terminals.

So what I want is to have 2 terminal windows open, type a command in term1 and redirect the output of that command to term2..

---

### Post by Nunyah on 2009-10-04
Just in case people search for this in the future..

By giving the command tty in a terminal window, you can get the location of the file for the given terminal.

So if you have 2 terminal windows open, they will be in /dev/pts/0 and /dev/pts/1, respectly. To send output of a command to the other window, you would do something like this:
```

ls -l > /dev/pts/1

```
to have the output of that ls into your 2nd window.

---

### Post by Lars Noodén on 2009-10-05
> **Nunyah said:**
> Just in case people search for this in the future..

By giving the command tty in a terminal window, you can get the location of the file for the given terminal.

So if you have 2 terminal windows open, they will be in /dev/pts/0 and /dev/pts/1, respectly. To send output of a command to the other window, you would do something like this:
```

ls -l > /dev/pts/1

```
to have the output of that ls into your 2nd window.

@Nunyah: That's useful.  Running **ps** with no arguments will list the TTY for the current shell.  
```

$ ps
  PID TTY          TIME CMD
 2066 **pts/5**    00:00:00 bash
 5936 **pts/5**    00:00:00 ps

```

---

### Post by mobilediesel on 2009-10-05
> **Nunyah said:**
> Just in case people search for this in the future..

By giving the command tty in a terminal window, you can get the location of the file for the given terminal.

So if you have 2 terminal windows open, they will be in /dev/pts/0 and /dev/pts/1, respectly. To send output of a command to the other window, you would do something like this:
```

ls -l > /dev/pts/1

```
to have the output of that ls into your 2nd window.

I wasn't searching for it but now that I've seen it I HAVE to find a use for it!

Thanks for sharing! My hard drive is eventually going to fill up with the stuff I find on these forums.

---

### Post by youarefunny on 2010-03-08
Handy, but I am having a problem.

When I run my script in terminal it works fine but when I just run it, the terminal window that pops up has nothing in it.  (Just the standard input line.)


---What Happens---

[LIST]
[*] I have changed to output to /dev/pts/0
[*] When run the terminal opens put nothing appears.
[*] If I run the script again it will write onto the window the first run opened.
[/LIST]
---My Thoughts---

Script is waiting for terminal to close to continue?
     - but the second run will write before I close the terminal IT opened



Any help will be appreciated.
     -Thank you

---

### Post by youarefunny on 2010-03-08
Solved

```
#open terminal in the background with
gnome-terminal &

#add sleep delay to give loading time
sleep 5 #Wayyy more than nessary but works

#then output
echo "Whatever" > /dev/pts/0
```

wonderfull!


(still don't get why it worked the second time running before though :( )

---

### Post by dcstar on 2010-03-08
And if you ever want output to multiple terminals/files:

```
man tee
```

---

### Post by youarefunny on 2010-03-09
Now that I have gotten the previous to work how would you close that terminal?

---

### Post by dcstar on 2010-03-09
> **youarefunny said:**
> Now that I have gotten the previous to work how would you close that terminal?

```
man kill
```

---

### Post by youarefunny on 2010-03-09
> **dcstar said:**
> ```
man kill
```

I get an error ```
No such process
```

I use

```
#Launch teriminal
gnome-terminal --hide-menubar
#grab process pid
terminal=$!

wait 10

#kill the terminal
kill $terminal
```but come up with the mentioned error.



I found this problem in this thread also
[http://ubuntuforums.org/showthread.php?t=214121](http://ubuntuforums.org/showthread.php?t=214121)

---

