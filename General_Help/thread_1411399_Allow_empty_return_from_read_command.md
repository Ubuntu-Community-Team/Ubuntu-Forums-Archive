---
title: "Allow empty return from read command"
date: 2010-02-19
forum: General Help
---

### Post by llawwehttam on 2010-02-19
I am writing a short script to do some backups.
Here is a small section of it:

```
echo -n "Please enter your choice ..."
    read CHOICE
    echo
    if [ $CHOICE = "4" ] ; then
        echo "Are you sure you want to exit? < Y [N] >"
        read EXIT
        if [ $EXIT = "Y" ] ; then
            echo "Exiting....."
            sleep 4
            exit
        else
            MENU
    
        fi
    fi
```So if the person types nothing it goes back to the start of the program.
When I run it its fine if I type Y or anything else but if I just hit enter I get:

[: 55: =: unexpected operator

and then it goes back to the menu as it should. How can I get it to stop showing [: 55: =: unexpected operator ?

---

### Post by llawwehttam on 2010-02-19
Forget it. I changed it to

```
    if [ $CHOICE = "4" ] ; then
        while true
        do
          echo -n "Are you sure you want to exit? < Y [N] > :"
          read CONFIRM
          case $CONFIRM in
            y|Y|YES|yes|Yes) break ;;
            n|N|no|NO|No)
              clear
              MENU
              ;;
            *) clear ; exit
          esac
        done

    else
```

---

### Post by falconindy on 2010-02-19
In case you were curious as to an answer in regards to your original question, it's because you're using single square braces for the expression. Consider the following if var 'A' is unset:

bad
```
[ $A = "someval" ]
```

good
```
[ "someval" = $A ]
```

good
```
[ x$A = "xsomeval"]
```

or just use Bash. This works:
```
[[ $A = "someval" ]]
```

---

### Post by rnerwein on 2010-02-20
hi

or just use [ "$A" = "bla" ] --> whit qoutes isn't it empty

ciao

---

