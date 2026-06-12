---
title: "Help on tar command"
date: 2009-08-07
forum: General Help
---

### Post by tonysonney on 2009-08-07
Hi,
     I am trying to use the following command

*tar -strip-components 2 -dir /home/tt0r/Documents/mydroid/ -xvvzf foo.tar.gz *

But I get error message 

[I]tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.[/I]
 What am I doing wrong?
From the man tar I found
[I]-strip-components n
              Strip the given number of leading directory components[/I]
What does it mean? What is mean t by leading directory components? Does it mean first 'n' number of directories out of n+x directories. Sorry being really stupid. 

Thanks in Advance,
Tony

---

### Post by wojox on 2009-08-07
> **tonysonney said:**
> Hi,
     I am trying to use the following command

*tar -strip-components 2 -dir /home/tt0r/Documents/mydroid/ -xvvzf foo.tar.gz *

But I get error message 

[I]tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.[/I]
 What am I doing wrong?
From the man tar I found
[I]-strip-components n
              Strip the given number of leading directory components[/I]
What does it mean? What is mean t by leading directory components? Does it mean first 'n' number of directories out of n+x directories. Sorry being really stupid. 

Thanks in Advance,
Tony

`-Acdtrux' option must be the first argument meaning
```
tar -xvvzf -strip-components 2 /home/tt0r/Documents/mydroid/foo.tar.gz
```
I don't know what -dir does.

---

### Post by The Cog on 2009-08-07
> **wojox said:**
> I don't know what -dir does.

I am guessing he wanted it to change directory. But to do that, the argument is either **-C <directory>** or **--direcory <directory>**.

---

### Post by tonysonney on 2009-08-20
Thanks guys. Yes I wanted it to be extracted to /home/tt0r/Documents/mydroid/ . I will try I let you know how it goes.
Thanks,
Tony

---

### Post by tonysonney on 2009-09-10
> **wojox said:**
> `-Acdtrux' option must be the first argument meaning
```
tar -xvvzf -strip-components 2 /home/tt0r/Documents/mydroid/foo.tar.gz
```
I don't know what -dir does.

Hi ,
 I tried
```
tar -xvvzf -strip-components 2 /home/tt0r/Documents/mydroid/foo.tar.gz
```

But I get error 
```
tar: -strip-components: Cannot open: No such file or directory.
```
 Any ideas??:confused:

---

### Post by tonysonney on 2009-09-10
I found what I was doing wrong. I should have used
```
tar --strip-components 2 --dir /home/tt0r/Documents/mydroid/ -xvvzf foo.tar.gz 
istead of
tar -strip-components 2 -dir /home/tt0r/Documents/mydroid/ -xvvzf foo.tar.gz 
```

Any way thank you all for the help --dir is used to specify the path to be extracted.
Cheers,
Tony:)

---

