---
title: "This is silly I know....."
date: 2010-09-17
forum: General Help
---

### Post by subcook on 2010-09-17
I am new to linux as of Feb. 2010.

I experimented with Linux Mint for a very slight bit.

One thing I really got a kick out of was how whenever I opened a terminal, there would be a text graphic picture of a penguin, with a real Fancy motd.

I want to Incorporated that into my ubuntu terminal, and other distros.

I can only figure that this is a certain file that need to be plugged into another file.

any advice on how to do this is very much appreciated......


....Thanks in advance....



-Mike

---

### Post by sisco311 on 2010-09-17
Hmmm, sounds like fortune+cowsay...

```

fortune | cowsay -f tux

 ______________________________________
/ You need more time; and you probably \
\ always will.                         /
 --------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

```

First install cowsay and fortune:
```
sudo apt-get install cowsay fortune
```
Then edit the /etc/bash.bashrc (or ~/.bashrc) file and append it with:
```
fortune | cowsay -f tux
```

---

### Post by subcook on 2010-09-18
What would I append in the file?

Would this work in opensuse?

I appreciate your response, this has been a hard question to get answered  

Thanks!!!


-Cheers

---

### Post by sisco311 on 2010-09-18
> **subcook said:**
> What would I append in the file?


You have to add the following line at the end of the file:
```
fortune | cowsay -f tux
```

> **subcook said:**
> 
Would this work in opensuse?


Yes, assuming that cowsay & fortune are installed.

---

### Post by kostkon on 2010-09-18
You may find [this thread]("http://ubuntuforums.org/showthread.php?t=1154065") useful (especially, if you are a fan of Futurama).

---

### Post by sisco311 on 2010-09-19
Thanks for the link.

---

### Post by Serpher on 2010-09-19
Edit your bash RC. Make the final line one of the following:

```
fortune|cowsay -f tux
echo "ANY MESSAGE HERE"|cowsay -f tux
```

---

### Post by subcook on 2010-09-20
fi

if test "$is" != "ash" ; then
    #
    # And now let's see if there is a local bash.bashrc
    # (for options defined by your sysadmin, not SuSE Linux)
    #
    test -s /etc/bash.bashrc.local && . /etc/bash.bashrc.local
fi

if test -n "$restricted" -a -z "$PROFILEREAD" ; then
    PATH=/usr/lib/restricted/bin
    export PATH
fi

#
# End of /etc/bash.bashrc
#




.......this is the last bit of my bash.bashrc file......

Seeing as how am I trying to teach myself bash scripting anyway...I'm hoping to learn, by using this as an example. 


...where do I add                  


this line        to make it work??                       Thanks
fortune | cowsay -f tux

---

