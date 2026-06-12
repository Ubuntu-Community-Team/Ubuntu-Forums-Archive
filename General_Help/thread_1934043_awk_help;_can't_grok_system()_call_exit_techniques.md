---
title: "awk help; can't grok system() call exit techniques"
date: 2012-03-01
forum: General Help
---

### Post by lbthrice on 2012-03-01
Hi all,

I can't close a gawk getline pipe. Please read my question below.

---

### Post by lbthrice on 2012-03-01
I apologize for reposting here but I realize how unclear my original post is.

My question is: why won't the grep process that I pipe to getlilnes exit?

Here's the gawk script:

```
{
      grepproc = "grep -c "$1" target.txt"
      while ( (grepproc | getline result)  > 0 ) {
          print  result
      }
      close(grepproc)
}
```

I supply the file containing the patterns by calling the script with:

```
gawk -f LB_iterative_grep.awk pattern.txt
```

...and I get the proper grep output but it just hangs with a blinking cursor until i ctrl-c. Why won't the process close?
I don't want to manually kill it every time with ^C.

output:

```
1
0
1
^C

```

---

### Post by erind on 2012-03-01
> **lbthrice said:**
> [...]

Here's the gawk script:

```
{
      grepproc = "grep -c "$1" target.txt"
      while ( (grepproc | getline result)  > 0 ) {
          print  result
      }
      close(grepproc)
}
```I supply the file containing the patterns by calling the script with:

```
gawk -f LB_iterative_grep.awk pattern.txt
```...and I get the proper grep output but it just hangs with a blinking cursor until i ctrl-c. Why won't the process close?
I don't want to manually kill it every time with ^C.

[...]

Probably because there's an empty line at the end of the *pattern.txt* file - $1 would be null, so grep has a non-valid null value (*grep -c target.tx*t) to grep from *target.txt* file. In fact if you hit CTRL+D (not CTRL+C) you'll see output showing.
So just make sure there are no empty lines at all in *pattern.txt* file. Also I don't think you need a 'while' loop in this case, an 'if' statement will suffice. The code below assumes that *there are empty lines* in the pattern.txt file:

 ```
{
    if ( $1 !~ /^$/ ) {

        grepproc = ("grep -c " $1 " target.txt")

        if ( (grepproc | getline result) > 0 ) {

          print  result

          close(grepproc)
        }
    }
 }

```

---

### Post by lbthrice on 2012-03-01
THANK YOU! I removed the trailing whitespace from the pattern file and now the command exits as I require! Thanks for taking the time to decipher my poorly composed question!

---

