---
title: "ksh question"
date: 2009-09-29
forum: General Help
---

### Post by PeterL777 on 2009-09-29
Hi
I've come across this piece of ksh code that I couldn't quite figure out. Can someone shed a little light on the 'if ${' bit?
Is there a mistake here, a bit missing or something I don't know about?
Thanks
Peter

-----------------------------------------------------
#!/bin/ksh

# Parse the command-line options
while getopts :a: option
do
.... case "$option" in
    .... u)    v_user="$OPTARG"
........;;
.... \?)   print "Error"
........ exit 1
........ ;;
....     esac
done

if [ "${" = "" ]; then
....          print "Error"
....           exit 1
fi

---

### Post by Brandon Williams on 2009-09-29
That line doesn't make sense. "${" is the start of a bracketed variable substitution of some sort, but the substitution isn't completed. I don't see anything in the ksh documentation suggesting that the expression has special meaning on it's own.

---

### Post by PeterL777 on 2009-09-29
Thanks. Didn't make sense to me either.
Peter

---

