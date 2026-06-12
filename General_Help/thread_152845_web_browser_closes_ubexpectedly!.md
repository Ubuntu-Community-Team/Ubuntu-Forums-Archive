---
title: "web browser closes ubexpectedly!"
date: 2006-03-30
forum: General Help
---

### Post by B3Nji on 2006-03-30
Hey, 

I have a really weired problem.
In the past few hours firefox has been closing on me for no reason on the same websites! like [http://www.bbc.co.uk/radio1](http://www.bbc.co.uk/radio1) and a few others, so I installed Epiphany to use while I find a fix for it. But it is doing it on the same sites to!

Whats going on?
Cheers for your help.

---

### Post by aggiechemist on 2006-03-30
I don't have an exact answer, but I have a couple suggestions.

1) Run firefox from a terminal. That way when it shuts down, you might get an error message. That can be a huge help in diagnosing this.

2) Change your theme. I was having a problem a while back that was just like this. Buried somewhere on the forums was a suggestion to change my theme ( under you preferences folder). It fixed the crashes, though I don't know that anyone has ever figured out why.

Good luck!

---

### Post by B3Nji on 2006-03-30
[QUOTE=aggiechemist]I don't have an exact answer, but I have a couple suggestions.

1) Run firefox from a terminal. That way when it shuts down, you might get an error message. That can be a huge help in diagnosing this.

2) Change your theme. I was having a problem a while back that was just like this. Buried somewhere on the forums was a suggestion to change my theme ( under you preferences folder). It fixed the crashes, though I don't know that anyone has ever figured out why.

Good luck![/QUOTE]

okies done that, got an error thing, dont know what it means! any takers? 

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by towsonu2003 on 2006-03-30
[QUOTE=B3Nji]okies done that, got an error thing, dont know what it means! any takers? 

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/QUOTE]

try the same thing with ```
firefox --safe-mode
```
If it crashes on you again, after posting the error message here and waiting for a week or so for a nice solution (hoping and praying ;) ), you might wanna file a bug report on [https://launchpad.net/malone](https://launchpad.net/malone) along with the error. 

PS. I don't have that crash behavior.

---

