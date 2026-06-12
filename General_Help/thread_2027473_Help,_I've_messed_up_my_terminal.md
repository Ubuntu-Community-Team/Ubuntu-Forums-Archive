---
title: "Help, I've messed up my terminal"
date: 2012-07-16
forum: General Help
---

### Post by alan21276 on 2012-07-16
Normally I can undo my mistakes but this time I'm stuck.
I was trying to improve my android connection using this guide 

[www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

and something went wrong....my terminal now looks like this even after a restart.

“alias: command not found
“alias android-disconnect=”fusermount -u /media/GalaxyNexus”
“alias: command not found
“alias android-disconnect=”fusermount -u /media/GalaxyNexus”
“alias: command not found
“alias android-disconnect=”fusermount -u /media/GalaxyS3”
“alias: command not found
“alias android-disconnect=”fusermount -u /media/GalaxyNexus”
“alias: command not found
“alias android-disconnect=”fusermount -u /media/GalaxyNexus”
“”mtpfs: command not found
“”fusermount -u /media/GalaxyNexus”
alan@wightman-desktop:~$



How can I get back to it just showing 

alan@wightman-desktop:~$

when I open up a terminal?
I've done a bit of searching but cant find anything on removing aliases.


Thanks in advance.

---

### Post by nothingspecial on 2012-07-16
```
mv ~/.bashrc ~/.bashrc_bak
mv .bash_aliases .bash_aliases_bak

cp /etc/skel/.bashrc ~/

. .bashrc
```

---

### Post by steeldriver on 2012-07-16
it looks like you just screwed up the echo of the aliases into your ~/.bashrc - just edit it in gedit or nano and remove the leading quote marks (i.e. change "alias to alias etc.)

---

### Post by alan21276 on 2012-07-16
> **nothingspecial said:**
> ```
mv ~/.bashrc ~/.bashrc_bak
mv .bash_aliases .bash_aliases_bak

cp /etc/skel/.bashrc ~/

. .bashrc
```





This solved my problem..........thank you very much.::)

---

### Post by nothingspecial on 2012-07-16
> **alan21276 said:**
> This solved my problem..........thank you very much.::)

No problem :)

---

### Post by alan21276 on 2012-07-16
Can the forum staff mark this as SOLVED........thanks again

---

### Post by Cheesemill on 2012-07-16
You can do it yourself. Just click on 'Thread Tools' near the top of the page.

---

### Post by alan21276 on 2012-07-16
Ah.......sorry, I don't post often, now I know,   cheers

---

