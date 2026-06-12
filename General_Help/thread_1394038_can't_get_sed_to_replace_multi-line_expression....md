---
title: "can't get sed to replace multi-line expression..."
date: 2010-01-30
forum: General Help
---

### Post by rebeltaz on 2010-01-30
On one of my web sites, I have the following code on ever page:
```

        <p align="center"><img src="l-007.gif" border="0"></p>
        
          <br>

        <p class="body">

```

I need to replace that with:
```

        <p align="center"><img src="l-007.gif" border="0"></p>

        <p class="body">

```

in every file. Notice that on the line above <br> there are eight spaces. 

I am trying to use sed to do this:
```

 sed -i 's/        <p align="center"><img src="l\-007\.gif" border="0"><\/p>\n        \n          <br>\n/        <p align="center"><img src="l\-007\.gif" border="0"><\/p>\n/g' *.htm

```

This is not working. The expression is not matching. What on earth am I doing wrong? Thanks...

---

### Post by john newbuntu on 2010-01-30
What you may need is a multi-line sed command that basically reads 3 (or perhaps even 4) lines at a time and then do the replacement.  The template will be something like:

sed -i '{
N
N
s/        old-para\n   \n   <br>\n/new-para/g
}' *.htm

Have fun.  And always diff (or sdiff) with the original html files to make sure your changes went in the right places.

---

### Post by rebeltaz on 2010-01-31
> **john newbuntu said:**
> What you may need is a multi-line sed command that basically reads 3 (or perhaps even 4) lines at a time and then do the replacement.  The template will be something like:

sed -i '{
N
N
s/        old-para\n   \n   <br>\n/new-para/g
}' *.htm

Have fun.  And always diff (or sdiff) with the original html files to make sure your changes went in the right places.

What are the two 'N's ? Thanks for the reply...

---

### Post by john newbuntu on 2010-01-31
It basically says read 3 lines at a time before evaluating what needs to change.  Sed ordinarily operates on one line.  Each 'N' stands for an extra line (along with the delimiter)

---

### Post by rebeltaz on 2010-01-31
> **john newbuntu said:**
> It basically says read 3 lines at a time before evaluating what needs to change.  Sed ordinarily operates on one line.  Each 'N' stands for an extra line (along with the delimiter)

OK.. great. I'll give that a try. Thanks.

---

