---
title: "Can't open applications from terminal with &quot;./&quot;."
date: 2011-09-28
forum: General Help
---

### Post by leon.vitanos on 2011-09-28
I have a weird problem. I am trying to open Machinarium ( game for linux ) which open with adobe flash player if you double click it from the browzer. The same will happen if i cd to the path of the executable and then ./the_executable_name. But what if i don't want to cd to the path of the executable?

Like: ./"Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/Machinarium"

I weird thing happens. It opens me Adobe flash player but the window is just black. What should i do?
I think the problem is with the spaces that the path have.

P.s Reason: Developing program.;)
P.s2 And yeah the path is correct. 3 times Machinarium...

---

### Post by linux2001 on 2011-09-28
Try
```
$ chmod +x yourprogram
$./yourprogram

```

---

### Post by christophevr on 2011-09-28
> **Bong.Da.City said:**
> I have a weird problem. I am trying to open Machinarium ( game for linux ) which open with adobe flash player if you double click it from the browzer. The same will happen if i cd to the path of the executable and then ./the_executable_name. But what if i don't want to cd to the path of the executable?

Like: ./"Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/Machinarium"

I weird thing happens. It opens me Adobe flash player but the window is just black. What should i do?
I think the problem is with the spaces that the path have.

P.s Reason: Developing program.;)
P.s2 And yeah the path is correct. 3 times Machinarium...

Your path is not correct for that.

You do ,not need to put ./ If you give the path to the specific application.

here How it must be 

   $HOME/Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/Machinarium

or 
  ~/Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/Machinarium

---

### Post by christophevr on 2011-09-28
An extra remark. If You are in Your standard home directory.

that You should be if you open a fresh terminal you can dos as well :

./Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/Machinarium

Note: no string quotes ""

But it is possible that the specific program does require You to be into 
directory 

~/Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/

In that case there is no other option then first cd to the directory or make a script file located into your home directory or home desktop directory which first cd's to the specified directory and then start the program with ./Machinarium

---

### Post by leon.vitanos on 2011-09-29
> **christophevr said:**
> Your path is not correct for that.

You do ,not need to put ./ If you give the path to the specific application.

here How it must be 

   $HOME/Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/Machinarium

or 
  ~/Desktop/The Humble Indie Bundle/Linux/The Humble Indie Bundle 2/Machinarium/Machinarium/Machinarium

As i thought it will have outpout like this: bash: /home/citybong/Desktop/The: No such file or directory

---

### Post by CatKiller on 2011-09-29
You can escape spaces in the shell with a \ so that they are treated like a character rather than something to separate arguments. If you use Tab-completion (which you should) you'll get these filled in for free.

Edit: The . when you're specifying a path means "the directory I'm currently in." You don't need to stick them in willy-nilly.

---

