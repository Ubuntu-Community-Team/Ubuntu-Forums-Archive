---
title: "$(shell uname -r) Doesn't Work"
date: 2011-08-27
forum: General Help
---

### Post by darc26 on 2011-08-27
Hi,

I'm trying to write my own driver with very little experience and am having some troubles at the start. I'm following a few tutorials and most of them include the line:
```
$(shell uname -r)
```
in the Makefile.

When trying to run this I get the message that the command shell doesn't exist and I should install byobu, I did that, but I don't think the command shell that comes with byobu is the correct one.

Could someone help me out?

---

### Post by tredegar on 2011-08-27
Try just **$(uname -r)**

---

### Post by tredegar on 2011-08-27
Wait a minute....
This is in the **makefile**?
You are not supposed to *run* the makefile (as you would a bash script)  **make** is supposed to use it, in which case I believe your original syntax is correct.

---

### Post by darc26 on 2011-08-27
Thanks for the help, after some experimentation I just figured this out, but I can't explain whats going on.

For example if I do $(shell uname -r) in bash it fails, if I do $(shell uname -r) in makefile its correct.

If I do $(PWD) in bash it fails, if I do $(PWD) in makefile its correct.

Whats going on here?

---

### Post by tredegar on 2011-08-27
A makefile is not the same as bash script.
Try a [makefile tutorial]("http://www.metalshell.com/view/tutorial/120/")

---

### Post by tredegar on 2011-08-27
... And here's a more ["in depth" link]("http://www.gnu.org/software/make/manual/") that should answer all your questions about makefiles.

---

### Post by darc26 on 2011-08-27
Thanks for the help.

Do you happen to know of a good link for USB driver development in Ubuntu?  

Thought it was worth asking and thanks again for the quick responses.

---

### Post by tredegar on 2011-08-27
Here's a [link]("http://ubuntuforums.org/showpost.php?p=2554398&postcount=2") to some (oldish) links 

But what device are you trying to write a driver for?
The chances are that it has already been done, or someone else is already working on it.

---

### Post by darc26 on 2011-08-27
Its for a webcam.

I have a strong urge to develop some software from the ground up.  I am electrical engineer but spend time doing mostly high level matlab programming and am a little embarrassed that I don't know whats really involved in talking to hardware.  I have a feeling I'm biting off a little too much starting at the webcam, but it was just laying around so it seemed like a good place to start.

---

### Post by tredegar on 2011-08-27
Your webcam probably already has a suitable module written: You could take a look at the source code, or look at the source code for something like the [gspca]("http://mxhaard.free.fr/index.html") module which handles many cameras.

If I were you though, I'd start with something *very* simple (write a c program to output some data to the serial, or USB port, or make the Caps Lock light blink).

Good luck.

---

### Post by darc26 on 2011-08-27
Thats a good idea with the caps lock.  Either way I go, it seems I'm going to be toying around with module development for awhile.

---

### Post by darc26 on 2011-08-28
I was hoping I could get some additional advice from you.  

It is becoming very clear to me that starting with a webcam is much too complex.  I was able to get the gspca driver working with my webcam and was hoping to reverse engineer this driver along with Cheese to truly understand how these two components work together.  Looking at the source code for Cheese I was taken aback by the complexity of what I thought would be a simple program.

I know how to write C, and usually can read it quite well, but only in self-contained chunks and every tutorial that I've ever read never talks about building a complete software package, deploying the code and interaction with hardware drivers, etc., are you aware of well written resource (eg. Book or blog) that handles this.

I appreciate the help.

---

### Post by tredegar on 2011-08-28
> Looking at the source code for Cheese I was taken aback by the complexity of what I thought would be a simple program.

My advice is to start simply, then work forwards.

Make Caps Lock blink would be a start.

I started with computers 40y ago. Things have changed (mostly for the better), but I am now too old to develop / advance / troubleshoot code, or to give you advice as to how to do this.

> are you aware of well written resource (eg. Book or blog) that handles this.
No.

But good luck in your searches.

---

