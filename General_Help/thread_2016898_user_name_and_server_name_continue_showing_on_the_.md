---
title: "user name and server name continue showing on the screen"
date: 2012-07-04
forum: General Help
---

### Post by mike_kzc on 2012-07-04
Hey All,
 

 I had a really weird problem, it happened quite often.
 

 I am using MATLAB under command window in our server, which I remotely logged in. 



Sometimes after I exit from matlab, I cannot see what command I typed in, though the command works. If I keep hit "Enter" key, my user name and server name will continue showing on the screen, one by one.


  It sounds confusing. Let me give a example,
 

 After I "exit" from matlab under command line, if I keep hit "Enter", it shows this:
  ********************
 [mike@apple codes]$ [mike@apple codes]$ [mike@apple codes]$ [mike@apple codes]$ [mike@apple codes]$
 ********************
 "mike" is my username, "apple" server name, "codes" the directory name.
 

 If I type in "vi read_data.m", I cannot see what I typed in, but if I hit "Enter", the file content will shows on the screen.
 ********************
 Did anyone have this problem before? really annoying and I have to logout the server and log back again.
 

 Thanks. Any suggestion is welcomed.


Btw, this only happed when I use MATLAB.

 

 Mike

---

### Post by cipherboy_loc on 2012-07-04
When you encounter that, run the command **reset**. This will reset your terminal, allowing you to see what you are typing again.

Cipherboy

---

### Post by mike_kzc on 2012-07-04
> **cipherboy_loc said:**
> When you encounter that, run the command **reset**. This will reset your terminal, allowing you to see what you are typing again.

Cipherboy

thank you very much for the quick reply. 

I will try next time when I have the problem.

I cannot reproduce it now.

---

### Post by svalbard on 2012-07-09
It's been fixed in recent versions of MATLAB. Here's a MathWorks solution on the matter: 

[http://www.mathworks.com/support/solutions/en/data/1-CFTJX8/index.html?product=ML]("http://www.mathworks.com/support/solutions/en/data/1-CFTJX8/index.html?product=ML")

You could also change to a different shell; it appears that this only happens with bash.

I ran into this issue a couple of years ago and was able to fix things with ```
stty echo
``` which essentially forces the terminal to resume echoing the input text. In case you don't want to [FONT="System"]reset[/FONT] the terminal or switch to a different shell, you could give that a try.

---

### Post by mike_kzc on 2012-07-23
great to know. thanks.

> **svalbard said:**
> It's been fixed in recent versions of MATLAB. Here's a MathWorks solution on the matter: 

[http://www.mathworks.com/support/solutions/en/data/1-CFTJX8/index.html?product=ML](http://www.mathworks.com/support/solutions/en/data/1-CFTJX8/index.html?product=ML)

You could also change to a different shell; it appears that this only happens with bash.

I ran into this issue a couple of years ago and was able to fix things with ```
stty echo
``` which essentially forces the terminal to resume echoing the input text. In case you don't want to [FONT=System]reset[/FONT] the terminal or switch to a different shell, you could give that a try.

---

