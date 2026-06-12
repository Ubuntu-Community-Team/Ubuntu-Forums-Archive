---
title: "Environment variable for terminator"
date: 2010-08-23
forum: General Help
---

### Post by goodrench on 2010-08-23
I am having trouble with terminator all of the sudden on one of my machines. Keeps giving the error "TERM environment variable not set." whenever I type "clear".
also gives the error "Error opening terminal: unknown." when I try to edit a file with nano.
running the command "declare -x TERM=xterm" will work until the window is closed.
Everything in gnome-terminal works fine but in terminator things are not so well.
Any ideas?

BTW When I run the command "echo $TERM" it says dumb.

---

### Post by dantrevino on 2010-08-23
> **goodrench said:**
> I am having trouble with terminator all of the sudden on one of my machines. Keeps giving the error "TERM environment variable not set." whenever I type "clear".
also gives the error "Error opening terminal: unknown." when I try to edit a file with nano.
running the command "declare -x TERM=xterm" will work until the window is closed.
Everything in gnome-terminal works fine but in terminator things are not so well.
Any ideas?

BTW When I run the command "echo $TERM" it says dumb.

Your input here would be welcome:
[https://bugs.launchpad.net/terminator/+bug/621606](https://bugs.launchpad.net/terminator/+bug/621606)

---

### Post by PaulW2U on 2010-08-23
> **dantrevino said:**
> Your input here would be welcome:
[https://bugs.launchpad.net/terminator/+bug/621606](https://bugs.launchpad.net/terminator/+bug/621606)

I've added a comment as this one was driving me mad the other day, trying to track down what I had changed. 

In the end I explicitly set TERM in my .profile file and now terminator works correctly.

---

### Post by goodrench on 2010-08-23
> **PaulW2U said:**
> I've added a comment as this one was driving me mad the other day, trying to track down what I had changed. 

In the end I explicitly set TERM in my .profile file and now terminator works correctly.

I thought I tried that earlier and it did not work.
I tried it again and all is well again.
Thanks guys.

---

### Post by PaulW2U on 2010-08-25
A new version has been released, 0.95.

Problem fixed. :D

---

