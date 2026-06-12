---
title: "Printing mutiple files from the command line"
date: 2009-09-30
forum: General Help
---

### Post by geo909 on 2009-09-30
Dear all,

Often I have to print multiple files. Instead of opening each one
of them with a viewer and printing it, I was puting everything in 
a folder, I was navigating inside the folder from the terminal and 
I would give the command

```
lpr -P printer3 *pdf
```

That was back when we had redhat in the labs of my school. Now we 
switched to ubuntu, which is great, but I am having problems with 
printing my stuff. This is what I get:

```

marquesdepombal:~/Desktop/coding theory> lpr -P printer3 *pdf
lpr: The printer or class was not found.
marquesdepombal:~/Desktop/coding theory> lp -P printer3 *pdf
lp: Bad page-ranges values 0-0.

```

Any ideas why this is happening? 
Thanks in advance

---

### Post by diesch on 2009-09-30
You need to use -d instead of -P with lp:

```
lp -d printer3 *pdf
```

---

### Post by geo909 on 2009-10-03
Hi, 

thanks a lot for your reply! i will try it next time I go to the labs and will let you know what happened.

Thanks again

---

### Post by geo909 on 2009-10-08
Actually it didn't work :(

```

marquesdepombal:~/Desktop/coding theory> lp -d printer3 *pdf
lp: The printer or class was not found.

```

..and I'm sure the name of the printer is printer3..
Any ideas?

---

### Post by diesch on 2009-10-08
What does ```
lpstat -t 
```say?

---

### Post by geo909 on 2009-10-08
Hi,

```

caballito:~> lpstat -t
scheduler is running
system default destination: LaserJet-8150
...

```

So instead of printer3 I set LaserJet-8150 and it worked!

Thanks so much again

---

