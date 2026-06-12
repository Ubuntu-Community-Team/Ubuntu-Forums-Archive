---
title: "auto start app at console login"
date: 2009-07-31
forum: General Help
---

### Post by tvall on 2009-07-31
how do i get an app to start at console login? :confused:

---

### Post by razorboy5 on 2009-08-01
System -> Pref -> Start Up Applications

---

### Post by dlmarti on 2009-08-01
> **tvall said:**
> how do i get an app to start at console login? :confused:[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Did you mean text login? or the graphical login, or just when ever you run a terminal?

---

### Post by tvall on 2009-08-01
I meant to have an application start wen I log in

I don't have gnome, kde, x11, kdm, or gdm, just cli

---

### Post by W4l0ck on 2009-08-01
You have to know the command.

---

### Post by tvall on 2009-08-01
> **W4l0ck said:**
> You have to know the command.

I know the command but I want it to start automatically when I login.

---

### Post by tvall on 2009-08-01
Does anyone know how to do this?

---

### Post by dlmarti on 2009-08-01
> **tvall said:**
> I know the command but I want it to start automatically when I login.

When bash runs (after you login), several scripts are evaluated.
Putting a program in there would work.

[http://www.faqs.org/docs/bashman/bashref_63.html](http://www.faqs.org/docs/bashman/bashref_63.html)

Just remember, if the programs don't return then you will never get a login prompt.
So make sure you are careful, and always keep another terminal open to fix screw ups.

---

### Post by tvall on 2009-08-01
> **dlmarti said:**
> When bash runs (after you login), several scripts are evaluated.
Putting a program in there would work.

[http://www.faqs.org/docs/bashman/bashref_63.html](http://www.faqs.org/docs/bashman/bashref_63.html)

Just remember, if the programs don't return then you will never get a login prompt.
So make sure you are careful, and always keep another terminal open to fix screw ups.

it didn't work.

I have ubuntu set up to auto login.
does that effect anything?

I need this to get mp3 blaster to automatically run.

---

### Post by dlmarti on 2009-08-01
> **tvall said:**
> it didn't work.

I have ubuntu set up to auto login.
does that effect anything?

I need this to get mp3 blaster to automatically run.

It works, you just didn't do it right.

What did you try that didn't work?

---

### Post by tvall on 2009-08-01
> **dlmarti said:**
> It works, you just didn't do it right.

What did you try that didn't work?

I added the command to start mp3blaster in .profile.

---

### Post by dlmarti on 2009-08-01
> **tvall said:**
> I added the command to start mp3blaster in .profile.

Wrong place, read the link I sent you.

It should have gone in the bottom of the .bashrc file.

Put the following command at the bottom of your .bashrc file:
echo "Hello World"

---

### Post by tvall on 2009-08-01
Thank You!!

It works perfectly.

---

