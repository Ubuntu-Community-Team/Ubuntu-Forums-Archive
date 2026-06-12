---
title: "Alias problem"
date: 2010-05-26
forum: General Help
---

### Post by telamonides on 2010-05-26
Hello,

  I am trying to set up an alias that will use a little "script" that I wrote to backup a file and then open the original in vi so I can edit it. Here is what I am trying to use for the alias:

alias v='(cp $1 $1.`date +%T\_%F`; vi)'

  I get this error when trying to "v hosts":

-bash: syntax error near unexpected token `hosts'

  I have also used this as the alias:

alias v='cp $1 $1.`date +%T\_%F`; vi'

  I get this when trying to "v hosts":

cp: missing destination file operand after `.07:17:37_2010-05-26'
Try `cp --help' for more information.


  I know that the cp operation works because I use it in a simple shell script that I call "backup" like this:

#! /bin/sh
cp $1 $1.`date +%T\_%F`

  So when I "backup hosts" I get something like this:

test-test-1:/home/lanedev # backup hosts
test-test-1:/home/lanedev # ls hosts*
hosts  hosts.07:19:22_2010-05-26

Is there anyway I can tie the two functions (backup and vi) in an alias so that I can get people to create backups of files they edit without having to remember to type both commands? Thanks.

---

### Post by Ryan Dwyer on 2010-05-26
I don't think you can use $1 in an alias. My understanding is that Bash literally replaces v with the command before running the whole thing. So it's running: (cp $1 $1.`date +%T\_%F`; vi) hosts

You could get around it by using a Bash script instead of an alias. Put the script's directory in your $PATH so you can run it from anywhere just like the alias.

---

### Post by telamonides on 2010-05-26
I solved this by modifying my "backup" script thus:

#! /bin/sh
cp $1 $1.`date +%T\_%F`
vi $1

  I then set my alias like this:

alias v='backup'

And now it copies the file with the extension and opens the original in vi.

Thanks for the comment.

---

### Post by gmargo on 2010-05-26
Shell aliases **do not** accept arguments.  However, shell functions **do** accept arguments, and it is trivial to change an alias into a function.

Non working alias:
```

alias v='(cp $1 $1.`date +%T\_%F`; vi)'

```Working function:
```

v()
{
    cp $1 $1.`date +%T\_%F` ; vi $1
}

```Of course, now that we have a function, we can get fancier.  You might prefer something like this:
```

v2()
{
    local file="$1"
    local nfile="$file".$(date +%T_%F)
    if [ "x$file" = "x" ]; then
        echo "Usage: v2 file"
    elif [ ! -f "$file" ]; then
        echo "Cannot find $file"
    elif [ -f "$nfile" ]; then
        echo "Will not overwrite $nfile"
    else
        echo "Copy $file to $nfile"
        cp -p "$file" "$nfile"
        vi "$file"
    fi
}

```

---

