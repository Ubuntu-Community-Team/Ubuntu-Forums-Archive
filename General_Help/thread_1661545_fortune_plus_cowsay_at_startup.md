---
title: "fortune plus cowsay at startup"
date: 2011-01-06
forum: General Help
---

### Post by sitmex on 2011-01-06
Hi, good day...

I really liked a stupid thing, I have most of the afternoon typing these:
```
 fortune | cowsay -n -f 
``` 

With a variety of characters and I would really like a script run at startup with the random selected character.

How can I do it?

Any help would be appreciated

---

### Post by MaxIBoy on 2011-01-07
Linux Mint does just that, and here is the script it uses:
```
#!/bin/bash
RANGE=4
number=$RANDOM
let "number %= $RANGE"
case $number in
    0)
        cow="small"
        ;;
    1)
        cow="tux"
        ;;
    2)
        cow="koala"
        ;;
    3)
        cow="moose"
        ;;
esac

RANGE=2
number=$RANDOM
let "number %= $RANGE"
case $number in
    0)
        command="/usr/games/cowsay"
        ;;
    1)
        command="/usr/games/cowthink"
        ;;
esac
/usr/games/fortune | $command -f $cow


```

Save that in ~/bin as mint-fortune, give it execute permissions, then add the following line to the end of your .bashrc:
```
~/mint-fortune
```
And it will run every time you open a terminal.

---

### Post by zami on 2011-01-09
I love it!

However, sometimes I get only

```

cowthink: Could not find small cowfile!

```

Any ideas what I am missing?

-zami

---

### Post by MaxIBoy on 2011-02-27
Well, you could replace cow="small" with something else. All available cows are in /usr/share/cowsay/cows.

---

### Post by memand on 2013-01-04
You can also do it without the script, with this shell command added to your ~/.bashrc

```
fortune -a | cow$(shuf -n1 -e say think) -f $(ls /usr/share/cowsay/cows/ | shuf -n1)
```

---

### Post by oldos2er on 2013-01-04
Old thread closed.

---

