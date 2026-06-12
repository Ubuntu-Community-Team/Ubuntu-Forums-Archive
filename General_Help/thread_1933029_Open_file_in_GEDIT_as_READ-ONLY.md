---
title: "Open file in GEDIT as READ-ONLY"
date: 2012-02-28
forum: General Help
---

### Post by feesgo on 2012-02-28
How can I open a file in GEDIT as READ-ONLY

I want to open it, see it but I DONT WANT TO MAKE ANY INVOLUNTARY CHANGES in it.

Thank you in advance

---

### Post by evilsoup on 2012-02-28
I don't know how to do exactly what you describe (or why you'd want that - surely just don't make any changes, and don't save it if you do accidentally make changes?), but if this is just a specific file, have you tried just changing the file permissions? GUI-wise, right-click on the file and open 'Properties', then go to the 'permissions' tab and set all the options to 'read-only'.

Via terminal, the command to change permissions like that would be:
chmod 444 filename
or if you want to be able to execute it:
chmod 555 filename

I hope that helps...

---

### Post by LightRust on 2012-02-28
A bash shell script to open the file read-only and then reset the permissions after opening the file:
 
#!/bin/bash
#bash shell script
#Written by LightRust
perm=`stat -c%a $1`
chmod ugo-w-x $1
gedit $1 &
sleep 5
chmod $perm $1
 
Cludgy at best but it does work...
 
\\:D/

---

### Post by sudodus on 2012-02-28
LightRust's script will do it.

But there are also other alternatives. For example, you can use the lightweight 'terminal windows viewer' ***less***. See ```
man less
```

---

### Post by LightRust on 2012-02-28
True but try printing with context highlighting from 'less'...
 
In this case... less is... just less :wink:

---

### Post by sudodus on 2012-02-28
> **LightRust said:**
> True but try printing with context highlighting from 'less'...
 
In this case... less is... just less :wink:
I agree that highlighting is very valuable.

But it is always nice to have alternatives. Less is also good because you can pipe to it, for example to view your hardware
```
gksudo lshw | less
``` navigate with the normal keys and quit with q.

---

### Post by adit on 2012-05-18
In post#3, in bash script
What does this line do?
```
sleep 5
```

---

### Post by Vaphell on 2012-05-19
wait/sleep 5 seconds
gedit is run in the background with the file changed to readonly and sleep 5 gives it some time to access the file before restoring its original permissions.

quote $1 if you don't want problems with spaces ("$1")

---

### Post by codemaniac on 2012-05-19
When i have to open a file in read only mode , i often use **view ** .
View starts vim in read-only mode.  You will be protected from writing the files.

---

### Post by llauro on 2012-07-13
Well, I am not using Ubuntu, but what I am doing is:

1) I open 2 gedit instances.
2) In one of them, I open the desired file. It gets open as Write-enabled.
3) Then I switch to the other gedit instance, and open the same desired file. Then a pop-up appears asking if you want to open it as writtable or as read-only.
4) Select the read-only option.
5) Go to the first gedit instance, and close the write-enabled one.

You got in the second instance of gedit the file open as read-only.

Usually, when I need to open one file read-only is to edit another similar one in the other gedit instance, so I can read both instances, and edit only in the selected one.

It is a pain to do my suggested way, but at least it works on Fedora, so I guess it will work in any other Linux distribution, as this seems not distribution-dependent.

I was researching (googling) for a new (better for me) way to do that. Will continue looking for :)

It would be nice if gedit incorporates in the Edit menu an open option to toggle edit/read-only the current working file.

---

