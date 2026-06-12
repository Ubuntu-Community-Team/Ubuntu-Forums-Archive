---
title: "Bash newbie - blank string help"
date: 2011-03-26
forum: General Help
---

### Post by JPKowal on 2011-03-26
Using awk I pull the first field of a random line from my datafile.

   myvar1=`awk -F"\t" 'NR=='$randline' {printf "%s\n", $1}' myfile

This works fine. The problem is there will be empty lines at the end of the file. Rather than using awk
to filter out blank lines I would like to figure this out first. 

So I test $myvar1 for a blank string after setting $randline to one that I know is blank:

   test -z "$myvar1" && echo "true" || echo "false"

But, this returns "false"? So, the string is not zero length. Why? It's a tab-separated file. Is awk storing the tab with the $1 field or something.

This is where I get headache. I try to echo my variable to see what it looks like.

  echo  "$myvar1"                            >         outputs: nothing
  echo "My variable is [$myvar1]"       >         outputs: [y variable is [

Why is the closing bracket at the beginning? What character could be stored in $myvar1 that would do such a thing and how did it get there?

---

### Post by bobmct on 2011-03-26
One of the tenants of Linux is keeping things simple. That means use a small tool to filter prior to using awk.  Grep is a great tool for this so something like this should work:

grep -v "^$" filename | awk '{ printf ....}'

Use man grep and man awk for particulars.

Hope this helps somewhat.  Good luck.:)

---

### Post by JPKowal on 2011-03-26
> **bobmct said:**
>  grep -v "^$" filename | awk '{ printf ....}' 

That helps. Thanks.

First, I have to fix my data file though.  Using that grep statement or awk NF!=0 does not output the number of non-blank lines correctly.

Turns out, someone else explained that  my file was written and saved on a Windows machine. That explains the  unusual result of placing  the square bracket at the front . (It should be a standard ASCII text file though)

So I need something like dos2unix to make sure the file is clean and try your scripts again.

Are there any native bash fuctions that can do this?

---

### Post by CharlesA on 2011-03-26
You can use sed or perl. I prefer sed.

```
sed -e s/"^M"//g <infile> > <outfile>
```

See here: [http://www.perlmonks.org/?node_id=258025](http://www.perlmonks.org/?node_id=258025)

EDIT: I ran into the same problem and ended up just using a linux box to write my scripts. Saves me some time, even tho you can use a sed one-liner to fix it.

---

### Post by gmargo on 2011-03-26
> **CharlesA said:**
> 
```
sed -e s/"^M"//g <infile> > <outfile>
```
It is inadvisable to use a literal ^M in a script.  Use the \r escape sequence form:
```

sed 's/\r//'

```or my preference, which also chops trailing whitespace:
```

sed 's/[[:space:]]\+$//'

```

---

### Post by CharlesA on 2011-03-26
> **gmargo said:**
> It is inadvisable to use a literal ^M in a script.  Use the \r escape sequence form:
```

sed 's/\r//'

```or my preference, which also chops trailing whitespace:
```

sed 's/[[:space:]]\+$//'

```
That's good to know. Thanks.

---

