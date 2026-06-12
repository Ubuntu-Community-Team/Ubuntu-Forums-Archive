---
title: "problem with installin &quot;xampp server&quot;"
date: 2006-03-19
forum: General Help
---

### Post by feest on 2006-03-19
hi, i'm quite new to ubuntu and i need to install xampp for my server but to install that i need to copy it to the opt directory. when i try to copy it, my pc returns a message that i don't have the rights to do that. how do i give my self rights or how do i install xampp now?

---

### Post by dermotti on 2006-03-19
Well the ubuntu way is to use **sudo**

so if you need admin rights, you preceed the command with **sudo**. So [B]sudo cp /home/me/stuff.exe /opt/stuff.exe
[/B]
Or you can ditch sudo

**sudo passwd**



then type **su**, and now you are an admin and you can do anything you want

---

### Post by feest on 2006-03-19
might work but i need the command to copy the directory lampp on my desktop to opt
or to extract the file lampp to opt

how do i do that?

---

### Post by dermotti on 2006-03-19
"admin" is not a command.


if  you precede commands with **sudo**, it executes them as if you were an admin.

If you dont want to use sudo, you can type

**sudo passwd**

and from then out, any time you want to become an admin, you type **su**

---

### Post by dermotti on 2006-03-19
[QUOTE=feest]might work but i need the command to copy the directory lampp on my desktop to opt
or to extract the file lampp to opt

how do i do that?[/QUOTE]
[B]
sudo cp /home/yourname/Desktop/lampp /opt/lampp[/B]

that will place the lammp directory in the opt directory. There is a <space> between /lammp and /opt in the above command fyi.

---

### Post by alamba on 2006-03-19
Here are the exact steps:
1. cd /home/<username>/desktop
2. sudo cp /xampp-linux-1.5.1.tar.gz /opt
3. cd /opt
4. sudo gunzip xampp-linux-1.5.1.tar.gz
5. sudo tar xvf xampp-linux-1.5.1.tar.gz -C /opt

That's it. To start xampp:
sudo /opt/lampp/lampp start

Then point your browser to localhost and you should see it in action.

A

---

### Post by feest on 2006-03-19
thx it works untill step 4, then it says:

gunzip: xampp-linux-1.5.1.tar.gz: No such file or directory

remebember that i havn't extrected xampp to opt because i can't...

---

### Post by feest on 2006-03-19
well, i will xplain what i have till now...

on my desktop the xampp file (.tar.gz)
on my desktop a directory with the xampp contents named lampp

plz help installing...

---

### Post by alamba on 2006-03-20
Did you copy the .tar.gz file into /opt with this?
1. cd /home/<username>/desktop
2. sudo cp /xampp-linux-1.5.1.tar.gz /opt

Then did you move to the /opt directory with this?
cd /opt

--> Type ls at this point and you should see the file in the current directory. If not type pwd and that should tell you if u're indeed in /opt directory. If not go there. If you are, go back to step 1 and copy the .tar.gz to this directory.

Then execute steps 4 and 5.

A

---

