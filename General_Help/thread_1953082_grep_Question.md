---
title: "grep Question"
date: 2012-04-05
forum: General Help
---

### Post by ukchris on 2012-04-05
[s]I am struggling to get grep to do what I want it to do.[/s]

In my /home folder is a file called **md5** containing a number of md5 checksums.  Part of one of these checksums is 0b82b43.

In the terminal I entered:

```
ca@lt-nux-ub11-10:~$ grep 0b82b43 md5
```

And got the following, correct, output:

```
0b82b43abeeec299ba9f56d6e3dc03a0  ANUPDATE002-001.ISO
```

If I then use zenity to open a file selection dialogue and select the file md5 and keep this in a variable called x and echo that x back I get:

```
ca@lt-nux-ub11-10:~$ x=$(zenity --file-selection)
ca@lt-nux-ub11-10:~$ echo $x
/home/ca/md5
```

Which is correct.

I then used this $x in the following command:

```
ca@lt-nux-ub11-10:~$ grep 0b82b43 $x
```

And again I get the correct output:

```
0b82b43abeeec299ba9f56d6e3dc03a0  ANUPDATE002-001.ISO
```

If I then select the .ISO file (again using zenity) and store it as y and echo y back I get:

```
ca@lt-nux-ub11-10:~$ y=$(zenity --file-selection)
ca@lt-nux-ub11-10:~$ echo $y
/home/ca/Downloads/ANUPDATE002-001.ISO
```

[s]I get no output at all and just get:

```
ca@lt-nux-ub11-10:~$
```

Obviously I am not doing this properly (my first script!) but what is it I am doing wrong?

Thanks in advance for any help.[/s]


I then enter:

```
ca@lt-nux-ub11-10:~$ z=$(md5sum $y | cut -d" " -f1)
ca@lt-nux-ub11-10:~$ echo $z
0b82b43abeeec299ba9f56d6e3dc03a0
```

Which is correct.  And then....

```
ca@lt-nux-ub11-10:~$ grep $z $x
```

Works and returns:

```
0b82b43abeeec299ba9f56d6e3dc03a0  ANUPDATE002-001.ISO
```

Sorry folks, never try and do something new and complex after a long day when you are tired. :)

---

### Post by Lars Noodén on 2012-04-05
[s]Try enclosing it in quotes:

```

grep "$y" $x

```[/s]

Edit: Never mind.  The problem is different than I thought.


For 'grep "$x" $y' to work, the value of $y will have to be something that you will find **in** the file.  The output from  'y=$(zenity --file-selection)' does not return anything appropriate for that.

How are you getting the md5 checksum manually?  Can that be automated?

---

### Post by ukchris on 2012-04-05
Ignore me, I missed out a step!  Changing OP now... :)

Fixed now, sorry Lars.  :oops:

---

