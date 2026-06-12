---
title: "someone help with a bit of bash"
date: 2010-04-25
forum: General Help
---

### Post by andru183 on 2010-04-25
some of my friends are thinking of getting into ubuntu and i said id make some bash shells to help em with some things, im only at bash 3 days tho and not good and cant get this firewall script to run

chmod +x is already done so it must be with the code

#!/bin/bash
echo 'Your chance to turn your fire wall on/off or check status
================================================== ========================

Please type on/off or status'

read x

if x=on
m= enable
fi

if x=off
m= disable
fi

if x= status
m= status
fi

command sudo ufw -$m

think it runs but it just closes after it dose, if it dose run how to i get it to stay open till they press enter or sumit?

---

### Post by geirha on 2010-04-25
I recommend you start with this guide: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

You really need to learn the basic bash syntax before you start writing a bash script.

---

### Post by quadproc on 2010-04-25
> **andru183 said:**
> some of my friends are thinking of getting into ubuntu and i said id make some bash shells to help em with some things, im only at bash 3 days tho and not good and cant get this firewall script to run

I believe that bash is giving up due to errors in your script but I would have expected some kind of error message(s) from bash.

I see a number of problems in what you posted: for example, you have spaces after equals signs.  In most programming languages you can throw in spaces more or less as you choose but bash is a string oriented language and the spaces become part of the strings.  This is not what you want.  Also, since you are selecting one action in response to the input, it makes sense to use the _case_ statement rather than _if_ statements.

Rather than writing a lot of words, I will offer this:
```
#!/bin/bash

# ask the user what to do with the firewall

m=""
cmd="ufw"


echo -n ":"    #prompt the user for some input
read x

echo "saw "$x
case $x in
    "enable")
        m="on"
        ;;
    "disable")
        m="off"
        ;;
    "status")
        m="status"
        ;;
    *)
        echo "Unrecognized input - no action performed"
        ;;
esac
sudo $cmd -${m}


```
I think that this code will do what you have in mind but I haven't tested it so please be cautious.  In any event, it will show you how some script things are done.  Please feel free to change it around to suit your needs and pleasures.  Do not be discouraged when you don't succeed right away; you will soon be creating scripts.

quadproc

---

