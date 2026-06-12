---
title: "can one user have multiple login scripts depending on remote or local login?"
date: 2009-09-21
forum: General Help
---

### Post by makkan77 on 2009-09-21
Well the title pretty much says it all. 
I want one user to have one login script run when he logs on locally and another if he logs on remotely (via ssh). 

Is this possible? 

I'm using this for my digital picture frame project ([see it here]("http://genericnerd.blogspot.com/2009/05/converting-toshiba-320cds-to-digital.html")). My intention is to autologin locally and from there on run GNU screen starting a number of apps in different screens. 
When I log in remotely I don't want this to happen since I most likely will be doing maintenance instead.

---

### Post by makkan77 on 2009-09-23
Yes you can. Thanks to a helpful hint in #debian on irc.debian.org I realized it was just a matter of finding out what tty the user was on. 

So I wrote a script for just that, thought I might share it if anyone might need the same. 

```
#!/bin/sh

#
# tty-vs-pts.sh
# tty vs pts checker by Markus Ulfberg 2009-09-22
# Inteded use is running different scripts wether
# the user logs in remotely or locally.
#

# Get the name of the tty the user is on.
FULL_USER_TTY=`tty`
# strip everything but tty or pts from the string that "tty" produces.
USER_TTY=${FULL_USER_TTY:5:3}

# Check if it is tty or pts.
if [ $USER_TTY == 'tty' ]
        then
                echo "You are logged in locally using: $FULL_USER_TTY"

        else
            if [ $USER_TTY == 'pts' ]
                then
                    echo "You are logged in remotely using: $FULL_USER_TTY"
                else
                    # Return failure if it is neither.
                    echo "Failed to establish type of tty"
            fi
fi
```

---

