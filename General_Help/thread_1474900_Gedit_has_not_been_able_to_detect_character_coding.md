---
title: "Gedit has not been able to detect character coding"
date: 2010-05-06
forum: General Help
---

### Post by Mystiques on 2010-05-06
I recently downloaded Metasploit framework for ubuntu but i got an error which says could not open <file location>

Saying gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file.Select a character coding from the menu and try again:mad:

Please help

---

### Post by Vaphell on 2010-05-06
when you have gedit open and pick Open from file menu, at the bottom of the window you get dropdown with coding, have you tried all of them?

---

### Post by cdenley on 2010-05-06
What file are you trying to open? gedit can only handle text files. Are you trying to read the README file packaged with Metasploit or something?

---

### Post by Mystiques on 2010-05-06
It couldn't open even by using two different character coding which were 

Current Locale (UTF-8)
Western (ISO-8859-15)

The type of the file is Shell script(application/X-shellscript)

with .run extension

---

### Post by cdenley on 2010-05-06
> **Mystiques said:**
> It couldn't open even by using two different character coding which were 

Current Locale (UTF-8)
Western (ISO-8859-15)

The type of the file is Shell script(application/X-shellscript)

with .run extension

That is a binary executable. Why are you trying to open it in a text editor? You need to execute it (if you trust it).
```

chmod +x myfile.run
./myfile.run

```

---

### Post by Mystiques on 2010-05-06
I don't try to open it with gedit sorry im a linux noob.And would like to know the command that, im suppose to use to run the application through the terminal.

Coz what i have been doing is double clicking on the file and it gives me the error that i just posted

Would appreciate if i might get assistance.

---

### Post by cdenley on 2010-05-06
> **Mystiques said:**
> And would like to know the command that, im suppose to use to run the application through the terminal.


Read my previous post. I can't tell you the exact commands, because you haven't given us the exact filename.

By the way, you can't double-click execute files you downloaded without making it executable for a reason. If you download and execute the wrong file, your system can be compromised. Don't make it executable unless you can trust it.

---

### Post by Mystiques on 2010-05-06
The filename is framework-3.3.3-linux-i686.run, what you say is very true that i have to make sure that the file is legitimate before making it executable.

---

### Post by cdenley on 2010-05-06
> **Mystiques said:**
> The filename is framework-3.3.3-linux-i686.run, what you say is very true that i have to make sure that the file is legitimate before making it executable.

Assuming your current working directory is the one which that file resides in, to verify that file hasn't been altered:
```

echo "a38b5e2484eb292fa87fc5fe14213ceb6ed8beae  framework-3.3.3-linux-i686.run"|sha1sum -c

```
that should give you this output:
```

framework-3.3.3-linux-i686.run: **OK**

```
If that said "OK", and you trust Metasploit enough to grant it full access to your system:
```

chmod +x framework-3.3.3-linux-i686.run
sudo ./framework-3.3.3-linux-i686.run

```

---

### Post by dcstar on 2010-05-07
> **cdenley said:**
> Read my previous post. I can't tell you the exact commands, because you haven't given us the exact filename.
.......

Probably buried in one of those always hard to find "PLEASE READ BEFORE INSTALLING" links on the web site of the product.......

---

