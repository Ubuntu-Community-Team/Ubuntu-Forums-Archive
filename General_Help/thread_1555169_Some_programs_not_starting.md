---
title: "Some programs not starting"
date: 2010-08-17
forum: General Help
---

### Post by blob dob 11 on 2010-08-17
Hi, not sure where to post this, so this should do.

I recently had to do a clean install of ubuntu. (Don't ask why, it's complicated) I installed a program called unetbootin, because I thought it'd be cool to have an OS on a memory stick. I tried to install DamnSmallLinux, but when I tried to boot from USB it was permanently counting down to an automatic boot. So I gave up, but when I went back in to Ubuntu, I found some applications wouldn't start up, and when I opened the terminal I got this message:

bash: /home/robert/bin/uname: cannot execute binary file
bash: [: !=: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: /home/robert/bin/sed: cannot execute binary file
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected

So, I tried to remove both files from /robert/bin. It worked, sort of. Firefox and Banshee were the two programs I was trying to open. Firefox now works, but Banshee doesn't. I've tried the basics, re-installing, turning it off and on again. Nothing has worked. Does anyone know what's going on?

I appreciate the help, I know there are a lot of people with problems of their own. :)

---

### Post by spibou on 2010-08-17
Please tell us exactly how you tried to start banshee. Did you type something on the command line ? If yes could you cut and paste what you typed and the output you got (or part of the output if it's too long)?

---

### Post by blob dob 11 on 2010-08-19
I had a shortcut on the panel, I tried it from there, it didn't work, so I tried it from the main menu, and that didn't work either, not sure how to start it from the terminal.

Another problem: I've tried to open tar.gz files, but I keep getting this message.
/home/robert/bin/gzip: 5: Syntax error: Unterminated quoted string
Not sure if it's related to this problem, just thought I'd mention it.

---

### Post by spibou on 2010-08-19
Try```
/usr/bin/banshee
```or```

/usr/bin/banshee-1
```and tell us what you get.

---

### Post by Renderd on 2010-08-19
Hello, just a new user here that likes to look in the general help forums

```
Another problem: I've tried to open tar.gz files, but I keep getting this message.
/home/robert/bin/gzip: 5: Syntax error: Unterminated quoted string
Not sure if it's related to this problem, just thought I'd mention it.     
```I open everything via command line, out of curiosity are you using command
```
tar zxvf <filename.tar.gz>
```

---

