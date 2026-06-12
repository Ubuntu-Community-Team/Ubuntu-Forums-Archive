---
title: "Bash startup script, string help"
date: 2010-10-04
forum: General Help
---

### Post by K7522 on 2010-10-04
I have a fairly extensive startup bash script when the computer begins, and currently have the commands in a string variable with an example below.

```
pro4="/path/to/program/programfile start"
```

One program requires you to CD into the directory prior to starting it, is there a way to remove everything in the variable after the last / and if so could you explain the example you post?

Basically I would like to 'cd /path/to/program/' before calling the command. Thanks for your time in advance.

By the way, I know I can define a new variable for the directory of the program(s) but that would require extensive changes to the script and effectively double the number of variables, complexity and filesize of the script.

---

### Post by K7522 on 2010-10-04
I had to do two things. First, remove any operand at the end with the first 2 lines, then call dirname to get the directory.

```
set -- $pro4
pro4p=$1
$pro4d=`dirname "$pro4p"`
echo $pro4d
```

results in:

```
/path/to/program
```

---

### Post by lloyd_b on 2010-10-05
> **K7522 said:**
> I had to do two things. First, remove any operand at the end with the first 2 lines, then call dirname to get the directory.

```
set -- $pro4
pro4p=$1
$pro4d=`dirname "$pro4p"`
echo $pro4d
```

results in:

```
/path/to/program
```

Instead of calling the external 'dirname' command, you can accomplish the same using bash's internal string handling:```
$pro4d=${pro4p%/*}
```

Lloyd B.

---

