---
title: "Create multiple definition of the system date"
date: 2009-12-13
forum: General Help
---

### Post by mpx-lin on 2009-12-13
Hi,

I have a question that i think is easy to solve but, unfortunately,  I am a newbie:(.
Is it possible to open a shell and change the date only for that shell?
I mean, today is the 13 december, I need to open a shell and change the date to yesterday, the 12 december but I do not want that the date in ubuntu changes, I want to change the date only for that shell.
Can anyone help me ?

Thanks

---

### Post by lloyd_b on 2009-12-13
> **mpx-lin said:**
> Hi,

I have a question that i think is easy to solve but, unfortunately,  I am a newbie:(.
Is it possible to open a shell and change the date only for that shell?
I mean, today is the 13 december, I need to open a shell and change the date to yesterday, the 12 december but I do not want that the date in ubuntu changes, I want to change the date only for that shell.
Can anyone help me ?

Thanks

Er, the system date is the *system* date - it's the same for every program on the system.  AFAIK, there's no way to fake it for one specific terminal session.

Could you please explain exactly *why* you need the different date?  There may be a work around for the real problem, but you haven't told us what that problem is.

Lloyd B.

---

### Post by slakkie on 2009-12-13
You can set a different timezone in a shell, but setting the system time for one session, nah.

Eg, I'm in Amsterdam
export TZ="Europe/Amsterdam"

But for my shell I'm on the happy island of Aruba.
export TZ="America/Aruba"

If you want to create a file in the past, you could use touch for that:

```

#!/bin/bash

stamp2date (){
    date --utc --date "1970-01-01 $1 sec" "+%Y-%m-%d %T"
}

date2stamp () {
        date --utc --date "$1" +%s
}

echo "Enter amount of seconds you want to remove from the timestamp of the files"
read aantal

for filename in "$@" ; do
    if [ -n "$filename" -a -e "$filename" -a -n "$aantal" ]; then
        touch -m -d@$(($(stat -c %Y "$filename") - $aantal)) "$filename"
    fi
done

```

---

### Post by mpx-lin on 2009-12-13
thanks slakkie :D

that solve my problem!  I need to modify a file in a directory without changing the  time order of the files, that is if I have:

file1 created the 09 December, 
file2 created the 10 December
file3 created the 11 December

and I modify file2, then the result would have been

file1 created the 09 December, 
file3 created the 11 December
file2 created the 13 December

while I still need to have the files in the original order.
That solves my problem, thanks a lot

---

