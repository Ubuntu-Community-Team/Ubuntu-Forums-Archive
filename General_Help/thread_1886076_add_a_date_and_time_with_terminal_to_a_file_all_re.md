---
title: "add a date and time with terminal to a file all ready created"
date: 2011-11-24
forum: General Help
---

### Post by linuxnoob47 on 2011-11-24
Hi ALL 
like my user name i am a noob but i am getting hooked big time i wanted to know if there is a code to add a date and time to a file that was all ready created by using terminal? i know how to add the date and time when you first create a file but just cant figure it out for one that is all ready created.:confused:
                                        thanks for any help

---

### Post by raja.genupula on 2011-11-24
[http://manpages.ubuntu.com/manpages/lucid/man1/touch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/touch.1.html)

---

### Post by Vaphell on 2011-11-24
what do you mean by 'add a date and time to a file'? do you mean changing the timestamp of a file, adding date string to the contents of a file or changing its name to include date string?

---

### Post by fdrake on 2011-11-24
> **linuxnoob47 said:**
> Hi ALL 
like my user name i am a noob but i am getting hooked big time i wanted to know if there is a code to add a date and time to a file that was all ready created by using terminal? i know how to add the date and time when you first create a file but just cant figure it out for one that is all ready created.:confused:
                                        thanks for any help

you want to add just the current date and time or the creation-date and time of the file?or you mean change the timestamp of a file?
```

date | less >> myFile
tail myFile

```

---

### Post by linuxnoob47 on 2011-11-24
just adding the current date and time. thanks

---

### Post by linuxnoob47 on 2011-11-24
> **Vaphell said:**
> what do you mean by 'add a date and time to a file'? do you mean changing the timestamp of a file, adding date string to the contents of a file or changing its name to include date string?

yeah thats it changing its name to include the date string with the time.

---

### Post by nothingspecial on 2011-11-24
```
mv file "file $(date)"
```

see ```
man date
``` for formatting options.

---

### Post by linuxnoob47 on 2011-11-27
yeah got it thanks you all for the help :popcorn:

---

