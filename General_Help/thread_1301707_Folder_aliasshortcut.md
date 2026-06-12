---
title: "Folder alias/shortcut?"
date: 2009-10-26
forum: General Help
---

### Post by wesg on 2009-10-26
I have SSH/SFTP running on my server, with available access outside the network through DynDNS. When I log in, I get my user folder, but most of my most accessed files are outside of this. 

Is it possible to have an alias that would allow me to access my outside folders from within my user directory? Otherwise I have to SSH in and copy them to the user folder.

---

### Post by Giblet5 on 2009-10-26
> **wesg said:**
> I have SSH/SFTP running on my server, with available access outside the network through DynDNS. When I log in, I get my user folder, but most of my most accessed files are outside of this. 

Is it possible to have an alias that would allow me to access my outside folders from within my user directory? Otherwise I have to SSH in and copy them to the user folder.


Example:

My home directory ($HOME) is /home/gumby and I frequently want to access source code in /var/obfuscate/gumby/special/goshilikedirectories/source

```
ln -s /var/obfuscate/gumby/special/goshilikedirectories/source /home/gumby/source
```

Will create a symbolic link to that ridiculous directory name under $HOME/source.

Is that what you're after? Then mark it SOLVED, please. :)

---

### Post by wesg on 2009-10-26
Never mind, I solved my own problem with Google. Sorry about that, next I'll Google first :D

For those interested, the command is 
```
sudo ln -s /path/to/original /path/to/alias
```
and it is a symbolic link

Edit: Problem solved! (thanks Giblet)

---

### Post by wesg on 2009-10-26
> **Giblet5 said:**
> 
Is that what you're after? Then mark it SOLVED, please. :)

How might I do that? :D N00b question

---

