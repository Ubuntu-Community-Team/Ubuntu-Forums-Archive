---
title: "Re: Terminal Changing directories"
date: 2010-01-25
forum: General Help
---

### Post by geekguy on 2010-01-25
i want to access a folder at /home/Daniel/Downloads/pyinstaller-1.3/source/linux
i am using the default 'gnome-terminal' on 9.10.
i used cd but it didn't work.

---

### Post by gabo.cr on 2010-01-25
It looks weird.
Is "linux" the file you need to find?

You can search the file using this command:

```
find /home -name linux
```

---

### Post by Rocket2DMn on 2010-01-25
Are you sure you are using the correct letter cases?  You can tab complete to help you autofill the directory names.  For instance:
```
cd /hom[TAB]/Dan[TAB]/Dow[TAB]/py[TAB]/so[TAB]/li[TAB]
```
It helps you get around a lot faster.

---

### Post by Sef on 2010-01-25
> i want to access a folder at /home/Daniel/Downloads/pyinstaller-1.3/source/linux

I would eliminate the last part (/linux) and see if that works.   If not eleminate the one before that. (source.)  Keep going back until you can get to a spot on the terminal that works, then check for that package and how it is spelled.

---

### Post by audiomick on 2010-01-25
If I am looking for something in the terminal, I often do the "cd" one step at a time, and a "ls" in between to check the contents of the directory I am in. That way I am sure of getting the name right for the next "cd" step.

---

### Post by Ordes on 2010-01-25
@audiomik, u can use [TAB] to autofill, try it out, u will be much faster than cd , ls , cd ..... if there are multiple choices tab will give u a list of choices ...

start with cd /h[tab] 

@geekguy

> /linux is a folder? it looks like a file of the py-installer... so your path would be cd /home/..../source ; and in there u use the file "linux"
> check if the pathing is written correct using [tab] like rocket said
> u have a [space] after cd? 
  cd/home  >>wrong
  cd /home >>right
> do u get on error output from the terminal.. or just nothing?

---

### Post by geekguy on 2010-02-04
> **Ordes said:**
> @audiomik, u can use [TAB] to autofill, try it out, u will be much faster than cd , ls , cd ..... if there are multiple choices tab will give u a list of choices ...

start with cd /h[tab] 

@geekguy

> /linux is a folder? it looks like a file of the py-installer... so your path would be cd /home/..../source ; and in there u use the file "linux"
> check if the pathing is written correct using [tab] like rocket said
> u have a [space] after cd? 
  cd/home  >>wrong
  cd /home >>right
> do u get on error output from the terminal.. or just nothing?

/linux IS a folder, which might be my problem.
but when i tryed cd on other things which are supposed to work they didn't work either.

---

### Post by oldos2er on 2010-02-04
> **geekguy said:**
> /linux IS a folder, which might be my problem.
but when i tryed cd on other things which are supposed to work they didn't work either.

Can you post the terminal output? Saying it doesn't work isn't specific enough for us to give you good advice.

---

### Post by Monotoko on 2010-02-04
You cant have a capital letter for the username? Ubuntu forbids it

It must be daniel, cant be Daniel, there two seperate things for linux

Try: 
```
cd /home/daniel/Downloads/pyinstaller-1.3/source/linux
```

---

### Post by mr clark25 on 2010-02-04
You might try cd'ing to your home directory just to make sure it works.
```

cd /home/yourname/

```
if that still doesn't work,you might try these two things:
1. Sudo to that directory
```

sudo cd /home/yourname/

```
2. Try a different method. Like nautilus (graphicly)
```

sudo nautilus

```

be very carefull using this. There is no way to empty the trash and you can delete important system files.

---

### Post by audiomick on 2010-02-04
Ah ah[-X

Nautilis is a graphical application. It should be started with root privileges using
```
gksu nautlilus
```

---

