---
title: "an existing file doesn't exist."
date: 2010-09-02
forum: General Help
---

### Post by levone on 2010-09-02
A quick question.
screen shot is failing hardcore ATM so..
```
christian@christian-desktop-ubuntu-vm:~$ ls
asm_projects              Downloads         Password Databases  Templates
codeblocks-10.05-release  examples.desktop  Pictures            Videos
Desktop                   Music             Portable Programs   xchat-2.8.8
Documents                 output            Public
christian@christian-desktop-ubuntu-vm:~$ ./output 
bash: ./output: No such file or directory
christian@christian-desktop-ubuntu-vm:~$ wtf??

```wtf??

output is an executable btw.. I'm teaching myself x86 asm using gas and linked with ld.

---

### Post by llawwehttam on 2010-09-02
try :

```
sh output
```

---

### Post by levone on 2010-09-02
```

christian@christian-desktop-ubuntu-vm:~$ sh output
output: 2: &#65533;: not found
output: 2: &#65533;: not found
output: 2: &#65533;&#65533;&#832;&#65533;&#65533;&#832;h@x@x@: not found
output: 2: 

           &#65533;: not found
output: 2: ELF: not found
output: 3: Syntax error: ")" unexpected

```

strange.. 

props for the fast reply though.

---

### Post by llawwehttam on 2010-09-02
NP

That is very strange.

Could you try :

```
gedit output
```

to see if it opens in gedit

---

### Post by lisati on 2010-09-02
I'm wondering if the eXecutable bit of output's attributes needs to be set:
```
chmod +x output
```

---

### Post by llawwehttam on 2010-09-02
> **lisati said:**
> I'm wondering if the eXecutable bit of output's attributes needs to be set:
```
chmod +x output
```

if that was the case I would have thought [FONT=monospace]

[/FONT]```
sh output
```would have worked anyway.

Just to find out could you also try:
```

ls -l
```

---

### Post by levone on 2010-09-02
file is set as excecutable and gedit couldn't open due to character encoding issues.. (well yea xD)

regardless, here is this.
```
-rwxr-xr-x 1 christian christian 2007 2010-09-02 20:25 output

```

---

