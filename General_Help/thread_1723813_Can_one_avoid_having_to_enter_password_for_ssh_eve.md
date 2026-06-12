---
title: "Can one avoid having to enter password for ssh every time?"
date: 2011-04-07
forum: General Help
---

### Post by TheHimself on 2011-04-07
I use rsyc for synching files that I type with a server and every time I have to enter the server's password. Right now in my .bashrc file there is an alias like this:
```
alias getfiles='rsync blah blah'
```

I'm looking for something like  
```
alias getfiles='rsync blah blah --password="#@%$*&"'
```

but can't find such  a thing in rsync or ssh man pages. Does anybody know what I should do?

---

### Post by falko on 2011-04-07
This link might help: [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

### Post by lithopsian on 2011-04-07
You can completely disable passwords for ssh and use keys instead.  It is probably described in the link.  Create the key, copy it to the server, and you should just be able to ssh to it automatically.  Once you get that working, ssh tools like rsync and sshfs should also work without password prompts.

---

### Post by TheHimself on 2011-04-10
I understand what you say however isn't there any simple trick for feeding the password into the password prompt automatically? 
What do applications like Nautilus or gftp do when they store your password for sshfs? I don't think they use keys.

---

### Post by petersohn on 2011-04-10
Graphical programs usually store your password in a wallet, where it is stored encrypted, and your program can ask for the wallet program to retrieve it. You can use tools like "expect" to feed the password on the command line, but it would require you to store the password unencrypted. I recommend you to use keys instead. Look at the man page of "ssh-keygen" for more information on how to use them.

---

### Post by earthpigg on 2011-04-10
> **TheHimself said:**
> 
What do applications like Nautilus or gftp do when they store your password for sshfs? I don't think they use keys.

gnome-keyring :) 

(i know it isn't relevant to your Q, but sometimes i feel like being a goober)

---

### Post by TheHimself on 2011-04-13
I found this helpful:

[http://www.puddingonline.com/~dave/publications/SSH-with-Keys-HOWTO/document/html/SSH-with-Keys-HOWTO-4.html](http://www.puddingonline.com/~dave/publications/SSH-with-Keys-HOWTO/document/html/SSH-with-Keys-HOWTO-4.html)

---

