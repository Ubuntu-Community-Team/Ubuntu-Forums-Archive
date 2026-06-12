---
title: "Hidden characters in a bash script?"
date: 2012-09-26
forum: General Help
---

### Post by Stonecold1995 on 2012-09-26
I just started having problems with a script I made.  I can't run the script by double-clicking on it (even after chmod 755), and if I run it in Konsole I get this (I also tried running it with zsh and sh, but they had the same problem as bash):
```
alex@kubuntu:~/.kde/Autostart$ bash -x vpncheck.sh
[B]+ '#!/bin/bash'
vpncheck.sh: line 1: #!/bin/bash: No such file or directory[/B]
+ real_ip=xxx.xxx.xxx.xxx
+ check_interval=60
+ IFS='|'
+ client=ktorrent
+ allow_multiple=0
+ lockfile=/tmp/.vpncheck.lock
+ keep_logs=0
+ max_logs=10
+ archive=archive
+ log_dir=/home/alex/.vpncheck
++ date +%a_%b_%d_%T_%Z_%Y
+ log_name=vpncheck_log_Wed_Sep_26_16:43:57_PDT_2012.txt
+ hosts='icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp'
+ '[' 0 -ne 0 ']'
+ log_file=/dev/null
+ '[' 0 -eq 1 ']'
+ cat
++ date
++ id -un
++ id -u
+ '[' 0 -eq 0 ']'
+ '[' -e /tmp/.vpncheck.lock ']'
+ log 'Another instance of this script appears to be running already, and allow_multiple is set to 0.  This script will not be run.'
+ tee -a /dev/null
++ date
+ echo -e '<Wed Sep 26 16:43:57 PDT 2012>     Another instance of this script appears to be running already, and allow_multiple is set to 0.  This script will not be run.'
<Wed Sep 26 16:43:57 PDT 2012>     Another instance of this script appears to be running already, and allow_multiple is set to 0.  This script will not be run.
+ return 0
+ check_x kdialog --error 'Only one instance of the script can be running at a time.  If you believe this is a mistake, remove /tmp/.vpncheck.lock and try again.'
++ pgrep -c Xorg
+ '[' 1 -eq 0 ']'
+ kdialog --error 'Only one instance of the script can be running at a time.  If you believe this is a mistake, remove /tmp/.vpncheck.lock and try again.'
+ rename 's/\.tmp.3058$//' /dev/null
+ exit 1
```

I think something got hidden files in my script.  That's weird because I only ever use vi and sometimes Kate, and I use to use nano.  I've never edited it with a Windows editor or anything.

```
alex@kubuntu:~/.kde/Autostart$ head -1 vpncheck.sh | od -c
0000000 **357 273 277**   #   !   /   b   i   n   /   b   a   s   h  \n
```

I tried removing the first few lines with vi and then type them back in manually, but it's still giving me the same error.  I also tried opening it in Kate, selecting all, and pasting it into a new file but I got the same problem, so apparently Klipper also copies hidden characters.  How do I remove the hidden characters, short of copying the script to a new file by hand?  And what could have even caused this anyways?

---

### Post by stepking2 on 2012-09-27
Tired using "sh" instead of "bash"?

---

### Post by HiImTye on 2012-09-27
it's odd that bash is trying to execute the bang at the start of the script. especially since the bang is a declaration of the shell that should be used, and is commented out. you have got some issues with your bash interpreter.

---

### Post by Stonecold1995 on 2012-09-27
> **HiImTye said:**
> it's odd that bash is trying to execute the bang at the start of the script. especially since the bang is a declaration of the shell that should be used, and is commented out. you have got some issues with your bash interpreter.

It's not a problem with bash, because the problem also occurs with with dash, zsh, etc (and I presume with ksh and csh, but I don't know much about them).  I'm pretty sure it's a hidden character, because a normal script is like this:
```
alex@kubuntu:~/.kde/Autostart$ head -1 chkboot_user.sh | od -c                                                                                                                                                                                                                 
0000000   #   !   /   b   i   n   /   b   a   s   h  \n                                                                                                                                                                                                                        
0000014
```

After some Google searching I confirmed that it IS a hidden character for sure, but I'm still at a loss of how to remove it, and what caused it so I can prevent that from happening a second time.

---

### Post by matt_symes on 2012-09-27
Hi

Try using cat with the -v switch to see the non printable characters
> 
       -v, --show-nonprinting
              use ^ and M- notation, except for LFD and TAB

```
cat -v vpncheck.sh
```

Also the command #!/bin/bash is the first line of the script ?

Kind regards

---

### Post by HiImTye on 2012-09-27
> **Stonecold1995 said:**
> It's not a problem with bash, because the problem also occurs with with dash, zsh, etc (and I presume with ksh and csh, but I don't know much about them).  I'm pretty sure it's a hidden character, because a normal script is like this:
```
alex@kubuntu:~/.kde/Autostart$ head -1 chkboot_user.sh | od -c                                                                                                                                                                                                                 
0000000   #   !   /   b   i   n   /   b   a   s   h  \n                                                                                                                                                                                                                        
0000014
```After some Google searching I confirmed that it IS a hidden character for sure, but I'm still at a loss of how to remove it, and what caused it so I can prevent that from happening a second time.
even if there is a hidden character in the script, everything after the # should be ignored by your shell

as for removing it, you could use a stream editor, such as sed and do something like:
```
sed -i "s|[^-a-zA-Z0-9#\!\\=|_.%\[\]+\'<>]||g" vpncheck.sh
```

---

### Post by Stonecold1995 on 2012-09-27
> **matt_symes said:**
> Hi

Try using cat with the -v switch to see the non printable characters


```
cat -v vpncheck.sh
```

Also the command #!/bin/bash is the first line of the script ?

Kind regards

```
alex@kubuntu:~/.kde/Autostart$ cat -v vpncheck.sh | head -1
M-oM-;M-?#!/bin/bash
```

And yes, "#!/bin/bash" is the first line of the script.

> **HiImTye said:**
> even if there is a hidden character in the script, everything after the # should be ignored by your shell
Yes, but the problematic characters are placed before the "#", as shown with "head -1 vpncheck.sh | od -c" and now with "cat -v vpncheck.sh | head -1".

---

### Post by matt_symes on 2012-09-27
Hi

```
M-oM-;M-?#!/bin/bash
```There you go. That's your non printable characters by the looks of it.

As i am sure you know it should be

```
#!/bin/bash
```

Can't you remove those characters.

I would second the suggestion of using sed.

Kind regards

---

### Post by Stonecold1995 on 2012-09-27
I tried using sed.  Didn't work.

```
alex@kubuntu:~/scripts/vpncheck$ head -1 vpncheck.sh | od -c
0000000 357 273 277   #   !   /   b   i   n   /   b   a   s   h  \n
0000017
alex@kubuntu:~/scripts/vpncheck$ sed -i "s|[^-a-zA-Z0-9#\!\\=|_.%\[\]+\'<>]||g" vpncheck.sh
alex@kubuntu:~/scripts/vpncheck$ head -1 vpncheck.sh | od -c
0000000 357 273 277   #   !   /   b   i   n   /   b   a   s   h  \n
0000017
```

---

### Post by josephmills on 2012-09-27
I dont get it at all so ignore if not the case but I almost always  use 
```
#!/usr/bin/env bash
```
for my shebang/hashbang 

> , the #! line tells the operating system (OS) what interpreter to use. The OS runs /usr/bin/env, which in turn runs <snip> BASH itself 
[Source](http://mywiki.wooledge.org/BashGuide/CommandsAndArguments)

In other words if it is not installed  in /bin/ then env will find it

sorry that I can not be of more help

---

### Post by spjackson on 2012-09-27
Remove the first 3 characters from the file:
```

dd bs=1 skip=3 if=vpncheck.sh of=temp
mv temp vpncheck.sh
chmod a+x vpncheck.sh

```

---

### Post by steeldriver on 2012-09-27
... or you might have more luck with tr than sed? something like

```
tr -dc '\11\12\15\40-\176'
```

(from here --> [http://www.devdaily.com/blog/post/linux-unix/how-remove-non-printable-ascii-characters-file-unix](http://www.devdaily.com/blog/post/linux-unix/how-remove-non-printable-ascii-characters-file-unix) )

---

### Post by HiImTye on 2012-09-27
> **Stonecold1995 said:**
> Yes, but the problematic characters are placed before the "#"
it doesn't matter, if you comment something out with #, even after commands, it will still be ignored, for instance:
```
tye@T:~$ echo test # this is ignored
test
tye@T:~$ 
```

---

### Post by Stonecold1995 on 2012-09-28
> **HiImTye said:**
> it doesn't matter, if you comment something out with #, even after commands, it will still be ignored, for instance:
```
tye@T:~$ echo test # this is ignored
test
tye@T:~$ 
```

I know that, but the problem was that the hidden characters are *before* the "#".  So like this:
```
[COLOR="Gray"]asdf[/COLOR] echo test # this is ignored

```

> **spjackson said:**
> Remove the first 3 characters from the file:
```

dd bs=1 skip=3 if=vpncheck.sh of=temp
mv temp vpncheck.sh
chmod a+x vpncheck.sh

```

Thank you!  It worked.

Anyone know what could have caused this?  I've only ever used vi, and sometimes Kate and nano.

---

