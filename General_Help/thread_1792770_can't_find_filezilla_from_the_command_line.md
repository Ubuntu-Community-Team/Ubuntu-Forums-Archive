---
title: "can't find filezilla from the command line"
date: 2011-06-28
forum: General Help
---

### Post by ldt on 2011-06-28
I've spent way too much time on this so I will ask what is probably a dumb question. I have installed filezilla on Ubuntu 11.04 with apt-get. In the file viewer it shows up in /usr/bin/filezilla. If I click on it it runs as expected. My problem is I would like to create a link on my desktop or at least be able to run it from the command line. (It's a pain to have to scroll down in the applications menu to find it each time.) But from the terminal trying to create a link or running it gives the message that it can't find the file. ls /usr/bin/fi* doesn't list filezilla. It lists the file before and after it but not filezilla. Its permissions are exactly the same as all of the other executable files. Why does it show up in the file viewer but not with on the command line?

---

### Post by seawolf167 on 2011-06-28
You can create a launcher for Filezilla. Take a look at the instructions [here]("https://help.ubuntu.com/community/HowToAddaLauncher").

Alternatively, if you want a made-for-command-line ftp program, I suggest[ *lftp*]("http://kevin.deldycke.com/2006/08/basic-lftp-usage/")

```
man lftp
```

---

### Post by keithpeter on 2011-06-28
> **ldt said:**
>  Why does it show up in the file viewer but not with on the command line?

Hello ldt

I'm on xubuntu 11.04

I just installed filezilla and I can start the application from a terminal by typing 'filezilla' - no path

I can also use F2 and 'filezilla'

dmenu works fine with Unity as well (see my sig)

PS: lftp is ace for automated upload - I publish my personal web site with a couple of bash scripts and lftp.

Cheers.

---

### Post by ldt on 2011-06-28
Adding a launcher to the desktop "the easy way" worked like a charm. Thank you.

---

### Post by seawolf167 on 2011-06-28
No problem - glad it is working

---

