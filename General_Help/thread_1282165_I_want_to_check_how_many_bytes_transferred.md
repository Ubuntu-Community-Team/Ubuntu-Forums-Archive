---
title: "I want to check how many bytes transferred"
date: 2009-10-04
forum: General Help
---

### Post by thedreamer09 on 2009-10-04
I want to use ubuntu for my network access. But i am not finding the right software the gives me the details like this ... I have this in my local area connection in XP . is there anything similar in ubuntu
if so where can i find that ... 
I need to know how many bytes have transferred and how many bytes have recieved. It will be useful to check my usuage limit. I have a limited usage in my broadband. So if i get this info it would be easy for me to monitor the usage 
please reply me thank you ..

[IMG]http://tinypic.com/r/11wdieu/4[/IMG]

[IMG]http://i33.tinypic.com/11wdieu.gif[/IMG]

---

### Post by DeMus on 2009-10-04
> **thedreamer09 said:**
> I want to use ubuntu for my network access. But i am not finding the right software the gives me the details like this ... I have this in my local area connection in XP . is there anything similar in ubuntu
if so where can i find that ... 
I need to know how many bytes have transferred and how many bytes have recieved. It will be useful to check my usuage limit. I have a limited usage in my broadband. So if i get this info it would be easy for me to monitor the usage 
please reply me thank you ..

[IMG]http://tinypic.com/r/11wdieu/4[/IMG]

[IMG]http://i33.tinypic.com/11wdieu.gif[/IMG]

You could use Conky. With the right settings it gives you your down- and upload speed and also the amount of bytes transferred.

---

### Post by thedreamer09 on 2009-10-04
can you tell me how to install the software in ubuntu and where can i get this conky software. More details please. because i pretty new to ubuntu and don't know much about it

---

### Post by DeMus on 2009-10-04
> **thedreamer09 said:**
> can you tell me how to install the software in ubuntu and where can i get this conky software. More details please. because i pretty new to ubuntu and don't know much about it

Okay, let's get started:
Start Synaptic package manager: Menu System -> Administration -> Synaptic
Type your password
In Synaptic, in the search field, type conky. It will show all programs with the name conky, in my case just one.
Click the little square box at the beginning of the line and choose "mark for installation"
Click apply at the top menu bar.
Close synaptic when done.
Attached to this post you find a file called .conkyrc.txt
Save it in your home folder as .conkyrc (mind the dot at the beginning of the name, it is important. Don't use the .txt part, I had to use it to send the file)
On your desktop make a new launcher: rightclick your desktop
choose new launcher
type conky in the name field and in the command field
click OK
click the launcher and conky starts.
You can change colors, items, etc in the .conkyrc file in your home folder. Make a copy before you do.
It is a hidden file (starts with .) so to be able to see it in nautilus you have to type ctrl h
Success.

---

### Post by thedreamer09 on 2009-10-04
ok thanks for the reply , i will try and ask for further doubts. hope you will help me further. thank you

---

### Post by thedreamer09 on 2009-10-04
hello there i have tried what you have said , but i didnt find this thing.. 

conky

it says no files matches your search.. 
now what to do ...

---

