---
title: "right permissions"
date: 2009-09-12
forum: General Help
---

### Post by deltat on 2009-09-12
Hello

I changed all my user priviliges to have administration rights, also with sudo -i command in the terminal, yet when trying to extract a folder to eg. usr/share/new folder, I get the following error message: you don't have the right permissions etc... (see screenshot).

What could be the solution?

---

### Post by khelben1979 on 2009-09-12
Why are you extracting the file archive there? Use the /home/[your username] instead.

Also, it's very bad security policy on giving a default user too much permissions. I wouldn't recommend it.

---

### Post by deltat on 2009-09-12
I was under the impression that programs should be installed elsewhere than in your user file...? But maybe that's irrelevant with linux.

As for the privileges. If I don't give them to myself, who would I give them to? I use ubuntu as a desktop OS.

Thomas

---

### Post by Vaphell on 2009-09-12
from the screenshot it looks like you tried to plant some library/plugin manually in the root owned system directories.
You could extract them in your home and then copy/move/install to a proper place using temporary elevation to administrator status.
If you have permanent rights to modify any system dir without any safeguards, you can easily destroy the whole system. For example SHIFT+DEL (nautilus)/rm -r (terminal) in the wrong place - the system is gone because it will not ask you if you are sure you really want to delete a system dir. Anybody getting 15 second access to your user account can grant himself remote access to your box.

you should do your daily stuff with a limited rights and use sudo/gksu commands to temporarily gain admin rights only when absolutely necessary.

---

### Post by mcduck on 2009-09-12
> **deltat said:**
> Hello

I changed all my user priviliges to have administration rights, also with sudo -i command in the terminal, yet when trying to extract a folder to eg. usr/share/new folder, I get the following error message: you don't have the right permissions etc... (see screenshot).

What could be the solution?

Having admin rights doesn't mean that you'd actually have root permissions all the time, it only means that you are allowed to temporarily gain them (by using "sudo").

---

### Post by suavecu on 2009-09-12
> **deltat said:**
> Hello

I changed all my user priviliges to have administration rights, also with sudo -i command in the terminal, yet when trying to extract a folder to eg. usr/share/new folder, I get the following error message: you don't have the right permissions etc... (see screenshot).

What could be the solution?

while I agree with the above statements in regards to security, to answer you question, what are the permissions of the folder you are trying to extract it to? It should be something like:

drwxr-xr-x   2 somegroup someuser    4096 2009-04-24 09:13 Public

and then let us know your username.

---

### Post by tubasoldier on 2009-09-12
This is one of those Linux isn't Windows frames of mind. If it is not available in the repositories, which would be crazy for Ubuntu, then you should compile it from source. However, trying to do something like that directly into the root system is the wrong way to approach it. Thus the majority of reasons for vulnerabilities in Windows.

You should instead extract it to your home directory and then move it in as Khelben1979 said. I would assume that going into the libxine directory you are trying to compile something? 

It would be a lot easier to give you proper instructions on how to accomplish the task at hand if we knew what you were trying to do.

---

### Post by deltat on 2009-09-12
I've now extracted the xine tar package into a folder in my home directory. I'm wondering in what directory such a program is best stored so as to move it there.

---

### Post by Vaphell on 2009-09-12
but what do you want to do with it? merely storing it does you no good.

---

### Post by deltat on 2009-09-12
Obviously watch movies with it :)

---

