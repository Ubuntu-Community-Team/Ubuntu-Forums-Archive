---
title: "zip and unzip"
date: 2012-10-01
forum: General Help
---

### Post by winzip on 2012-10-01
I  have a folder  *mxapp*  in    */user/home/*  directory.


I  want to zip it  to mxapp.zip   and  unzip  it    */user/home/temp/ * to retrieve  *mxapp*  folder.

What is the command I need to use.

I'm worried about unzip .  If I unzip  *mxapp.zip*  will it give me  *mxapp* folder  or *mxapp*  folder contents ? I want *mxapp* folder  after unzip

---

### Post by GeForce 9500GT on 2012-10-01
You can do it with a GUI tool too. Give [Peazip]("http://peazip.sourceforge.net/") a try.

---

### Post by lisati on 2012-10-01
> **winzip said:**
> I  have a folder  *mxapp*  in    */user/home/*  directory.


I  want to zip it  to mxapp.zip   and  unzip  it    */user/home/temp/ * to retrieve  *mxapp*  folder.

What is the command I need to use.

I'm worried about unzip .  If I unzip  *mxapp.zip*  will it give me  *mxapp* folder  or *mxapp*  folder contents ? I want *mxapp* folder  after unzip

Have a look at:
```
man zip
```

---

### Post by winzip on 2012-10-01
> **GeForce 9500GT said:**
> You can do it with a GUI tool too. Give [Peazip]("http://peazip.sourceforge.net/") a try.

I want to do it in console command.

I'm using  ubuntu server 10

---

### Post by GeForce 9500GT on 2012-10-01
> **winzip said:**
> I want to do it in console command. I'm using ubuntu server 10
 
Okay, no problem. But next time, please provide us with this kind of information in your first post. If you don't mention your OS or other relevant info, people here give you the wrong answers/solutions.

---

### Post by Lars Noodén on 2012-10-01
I'd use [tar](http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html) instead.

```

mkdir /home/user/temp/mxapp
cd /home/user/mxapp
tar zcf - . | (cd /home/user/temp/mxapp; tar zxf - )

```

---

### Post by winzip on 2012-10-01
> **Lars Noodén said:**
> I'd use [tar]("http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html") instead.

```

mkdir /home/user/temp/mxapp
cd /home/user/mxapp
tar zcf - . | (cd /home/user/temp/mxapp; tar zxf - )

```

Can you please suggest  zip  solution ?

---

### Post by Lars Noodén on 2012-10-01
tar would be better, but here is one way to do it with zip
```

cd /home/user/mxapp
zip -r /tmp/z.zip ./*

cd /home/user/mxapp/temp
unzip /tmp/z.zip

```

---

### Post by winzip on 2012-10-01
> **Lars Noodén said:**
> tar would be better, but here is one way to do it with zip
```

cd /home/user/mxapp
zip -r /tmp/z.zip ./*  //[COLOR=Blue]can we add timestamp automatically during zipping ? e.g   zip -r /tmp/z_2-oct-2012.zip[/COLOR]

cd /home/user/mxapp/temp
[COLOR=Red]unzip /tmp/z.zip[/COLOR]   // [COLOR=Blue]does it  unzip  contents  or  folder ?  I need folder.   [/COLOR]

```

my comments are in [COLOR=Blue]**blue**[/COLOR] in the above.

---

### Post by Lars Noodén on 2012-10-02
To get the folder, include it when zipping.

```

cd /home/user/
zip -r /tmp/z.zip mxapp

```

To get the date in the name automatically, use [date](http://manpages.ubuntu.com/manpages/precise/en/man1/date.1posix.html) plus $()  See the manual page for all the date format options.

```

cd /home/user/
zip -r /tmp/z-$(date +"%F").zip mxapp

```

---

### Post by winzip on 2012-10-03
> **Lars Noodén said:**
> To get the folder, include it when zipping.

```

cd /home/user/
zip -r /tmp/z.zip mxapp

```

To get the date in the name automatically, use [date](http://manpages.ubuntu.com/manpages/precise/en/man1/date.1fun.html) plus $()  See the manual page for all the date format options.

```

cd /home/user/
zip -r /tmp/z-$(date +"%F").zip mxapp

```
Thanks. This is nice. Can you please provide me a link where i could find date format options in easy to understand manner. I find it difficult as to what format i can use.

---

### Post by Lars Noodén on 2012-10-03
Sorry I had the wrong link above.  You can find all the options by typing [font=Courier New]man date[/font] in the terminal or by following the link: 

[http://manpages.ubuntu.com/manpages/precise/en/man1/date.1posix.html](http://manpages.ubuntu.com/manpages/precise/en/man1/date.1posix.html)

Scroll down and you'll see %F, %Y and others.

---

