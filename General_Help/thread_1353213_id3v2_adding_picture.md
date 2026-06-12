---
title: "id3v2 adding picture"
date: 2009-12-12
forum: General Help
---

### Post by g.a. on 2009-12-12
Hi,

I'm trying to embed picture in my mp3 files. One way to do it might be EasyTag, it is working and part of the repository.

I would like to try the command line

```
id3v2
```

From the ```
id3v2 -h
``` I can read that

```

...
You can set the value for any id3v2 frame by using '--' and then frame id
For example: 
        id3v2 --TIT3 "Monkey!" file.mp3
would set the "Subtitle/Description" frame to "Monkey!". 
```

and, by verifying the picture frame with
```

id3v2 -f
```

I came out with the command

```
id3v2 --APIC "mypicture.jpg" mysong.mp3
```

but the output is

```
()[, 0]: , 0 bytes
```

and no picture is embed to the mp3. I googled and read the man/help but I do not understand what is my error.

Any hint?

thanks
g.

---

### Post by Chronon on 2009-12-12
You need to embed the data.  Writing the name of the image to the image tag won't do you any good.  You need the actual data to be stored in the tag.  Maybe you could use cat to stream the data to id3v2.

---

### Post by g.a. on 2009-12-12
could you help me with the syntax?

I know how to use the output of a command as input for another, such as,

```
ps -e | grep firefox
```

but now I need the output of cat within the id3v2 command. I'm trying the syntax but without success.

Best
g.

---

### Post by mr0738 on 2009-12-31
If i read the source of id3v2 correctly, the --APIC commandline switch is read-only: [http://id3v2.cvs.sourceforge.net/viewvc/id3v2/id3v2/id3v2.cpp?revision=1.17&view=markup#l_610](http://id3v2.cvs.sourceforge.net/viewvc/id3v2/id3v2/id3v2.cpp?revision=1.17&view=markup#l_610)

So no use trying to pipe the image data into id3v2.

---

### Post by g.a. on 2010-01-03
ok, thanks a lot.

g.

---

