---
title: "How to append data to a file where immutable flag is set?"
date: 2010-03-10
forum: General Help
---

### Post by karthick87 on 2010-03-10
I want to append data to a file where immutable flag is set..So i have tried this command 
**chattr [COLOR=#990000]+[/COLOR][COLOR=#000099]a[/COLOR] file_name **to append data..But i am unable to append the data..

---

### Post by psusi on 2010-03-10
You can't.  That's the whole point of the immutable flag.

---

### Post by karthick87 on 2010-03-10
Pls visit this link [http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html](http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html)

It is said that we can append data...

---

### Post by psusi on 2010-03-10
No it doesn't.  The append only flag lets you append data, immutable means immutable.

---

### Post by karthick87 on 2010-03-11
I tried append only flag but still i cant append the data...I created a file name test in my desktop with append flag..When i append the data i cant able to save the file..

```
karthick@Learners-desktop:~$ cd Desktop
karthick@Learners-desktop:~/Desktop$ ls
test
karthick@Learners-desktop:~/Desktop$ sudo chattr +a test

```

---

### Post by psusi on 2010-03-11
gedit does not just try to append to the file, it tries to write out a new file and replace the original.  To append you have to do something like:

```

echo this is a new line >> file.txt

```

---

### Post by karthick87 on 2010-03-11
Yes it worked for me..Thanks a lot :)

---

### Post by karthick87 on 2010-03-27
> **psusi said:**
> gedit does not just try to append to the file, it tries to write out a new file and replace the original.  To append you have to do something like:

```

echo this is a new line >> file.txt

```


Is there any Graphical text editor to append data rather than appending it from terminal?

---

