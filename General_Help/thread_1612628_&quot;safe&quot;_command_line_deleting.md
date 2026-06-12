---
title: "&quot;safe&quot; command line deleting"
date: 2010-11-03
forum: General Help
---

### Post by cong06 on 2010-11-03
I've used "rm" way too many times, deleting stuff I actually want.
I tried out "rm -i", but that just gave too much output.
What I wanted was something that would list everything and then prompt before it deletes them.

So I wrote these:
```

rm_check() {
    ls $* # was thinking of using tree, but that also gave too much output.."
    read -p "proceed?:" y
    if [ "$y" == "y" ]; then
        rm -vr $*
    fi
}
rm_move() {
    folder="/home/user/.local/share/Trash_rm/"
    move_to=`mktemp -d --tmpdir=$folder rm.XXXXX`
    mv $* $move_to
}

```

Then I added two aliases:
```

alias rm='rm_move'
alias rm_d='rm_check'

```

Both are in the .bashrc, function first and then alias.

Any ideas? things that look messy?

---

