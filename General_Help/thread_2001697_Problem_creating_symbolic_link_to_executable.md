---
title: "Problem creating symbolic link to executable"
date: 2012-06-11
forum: General Help
---

### Post by emustrangler on 2012-06-11
I have an executable in an obscure directory.  I want to put a link to it in /usr/local/bin.  So I make a link with "sudo ln -s".  But then trying to run the program from the command line fails, despite /usr/lcoal/bin being in my $PATH list.  The command "which" fails to find it as well.  

Going to /usr/local/bin and running ls -l, the links are there but are red colored outlined in grey.  Googling, this apparently means they are links that are to "unstatable" files.  I don't know what that means, though.  

Running the program works if I put in the pathname to the original, obscure directory that the actual executable sits in, so I'm pretty sure its not a problem with the actual program.

What's going on?

---

### Post by sudodus on 2012-06-11
> **emustrangler said:**
> I have an executable in an obscure directory.  I want to put a link to it in /usr/local/bin.  So I make a link with "sudo ln -s".  But then trying to run the program from the command line fails, despite /usr/lcoal/bin being in my $PATH list.  The command "which" fails to find it as well.  

Going to /usr/local/bin and running ls -l, the links are there but are red colored outlined in grey.  Googling, this apparently means they are links that are to "unstatable" files.  I don't know what that means, though.  

Running the program works if I put in the pathname to the original, obscure directory that the actual executable sits in, so I'm pretty sure its not a problem with the actual program.

What's going on?
Please post the output of
```
ls -l
```
to show the file permissions of the executable itself as well as the link in [FONT="Courier New"]/usr/local/bin[/FONT]

---

### Post by LewisTM on 2012-06-11
Did you make the link specifying full pathnames?
```
sudo ln -s /<full>/<path>/<to>/<file> /usr/local/bin
```
If not the link will be relative (e.g ./<file>) and won't point to anything useful when placed in /usr/local/bin

Cheers!

---

### Post by emustrangler on 2012-06-11
> **LewisTM said:**
> Did you make the link specifying full pathnames?
```
sudo ln -s /<full>/<path>/<to>/<file> /usr/local/bin
```
If not the link will be relative (e.g ./<file>) and won't point to anything useful when placed in /usr/local/bin

Cheers!

This was the problem.  I didn't realize ln didn't understand relative pathnames for the targets.  Thanks.

---

