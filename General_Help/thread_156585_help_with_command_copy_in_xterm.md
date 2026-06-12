---
title: "help with command copy in xterm"
date: 2006-04-07
forum: General Help
---

### Post by harys on 2006-04-07
hi, i'm trying to compil mplayer. ive untar the file : here an extract from my xterm :
harys@harys:~/Desktop$ tar -jxvf essential-20050412.tar.bz2. i want to copy it in /usr/local/lib/codecs. here an extract of what ive done :
harys@harys:/usr/local/lib/codecs$ cp /home/harys/Desktop/essential-20050412 /usr/local/lib/codecs
cp: omitting directory `/home/harys/Desktop/essential-20050412'

what should i do to copy these file . thanks. harys

---

### Post by xenmax on 2006-04-07
you need ```
cp -r <src> <dest>
``` and i am guessing you need to run this using sudo looking at the destination
EDIT: the -r option is to copy directories recursively

---

### Post by chocolatetoothpaste on 2006-04-07
[QUOTE=harys]hi, i'm trying to compil mplayer. ive untar the file : here an extract from my xterm :
harys@harys:~/Desktop$ tar -jxvf essential-20050412.tar.bz2. i want to copy it in /usr/local/lib/codecs. here an extract of what ive done :
harys@harys:/usr/local/lib/codecs$ cp /home/harys/Desktop/essential-20050412 /usr/local/lib/codecs
cp: omitting directory `/home/harys/Desktop/essential-20050412'

what should i do to copy these file . thanks. harys[/QUOTE]
cp /home/harys/Desktop/essential-20050412/* /usr/local/lib/codecs
assuming "essential-20050412" is a dir

---

### Post by harys on 2006-04-07
thanks zen max it worked!!!!!!

---

