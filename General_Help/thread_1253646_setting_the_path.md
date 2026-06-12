---
title: "setting the path"
date: 2009-08-30
forum: General Help
---

### Post by oren tal on 2009-08-30
currently my terminal doesn't automatically run program from the current directory.
I can of course do "./the_program"

However I would like to change it so that it will be able to run program also from the current directory and not only from the specific directory.

How can I do it without removing all the directory that are already included in the "path".

---

### Post by Liolikas on 2009-08-30
PATH=$PATH:/my/bin/ in .bash_profile file but Ubuntu uses Dash so .dash_profile sth like that. Just ls -al to find good file.

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> PATH=$PATH:/my/bin/ in .bash_profile file but Ubuntu uses Dash so .dash_profile sth like that. Just ls -al to find good file.
First thanks.
 
Isn't this will just add the /my/bin/ directory and not current directory?

What I want that whenever I go to any directory I could rum program just my writing its name and not by writing ./the_name_of_the program.

---

### Post by Liolikas on 2009-08-30
For sure edit /my/bin/ to fit your needs. 
Typically scripting users have:
/home/*user*/bin
Where they store all their scripts. Ant they can just use script name in same way as command then. Directory is not important anymore.

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> For sure edit /my/bin/ to fit your needs. 
Typically scripting users have:
/home/*user*/bin
Where they store all their scripts. Ant they can just use script name in same way as command then. Directory is not important anymore.

I think I have problem in my English.
Hope now to explain myself better.

I want that whenever I go to different directory I will be able to run programs automatically from that directory..

From example if I go to directory /home/oren/learning and I have script file with the name learning, I want that by writing "learning" in the terminal it will run.

Right now I have to write "./learning"

This is just an example, I generally want that when the terminal check from where to run program it will check the also the current directory.

Hope I now expressed it better.

Maybe I should edit it to PATH=$PATH:./  ?

---

### Post by Liolikas on 2009-08-30
It you set up as I said learning becomes just like any other command and you can forget where it is.
--
Of course you can set path same as ~ or /, but not very secure situation when everything even firefox download can be runed.

---

### Post by ibutho on 2009-08-30
Not sure why exactly you would want to do something like that but, you could edit ~.bash_profile and add
```
export PATH=$PATH:.
```

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> It you set up as I said learning becomes just like any other command and you can forget where it is.
--
Of course you can set path same as ~ or /, but not very secure situation when everything even firefox download can be runed.

O.K.
Thanks 

can you explain to me how to work?

Because I don't even have the folder /my ?

Second you said something about scripting user, what if this compiled program?

---

### Post by oren tal on 2009-08-30
> **ibutho said:**
> Not sure why exactly you would want to do something like that but, you could edit ~.bash_profile and add
```
export PATH=$PATH:.
```

simply because whenever I go to different directory I want tp run the program their just by writing their_name and not by writing ./their_name 

Why wouldn't you want this?

---

### Post by Liolikas on 2009-08-30
mkdir bin
Then edit and add:
PATH=$PATH:/home/Your_username/bin/

>Second you said something about scripting user, what if this compiled program? 
Typically you want make install them. But you can ln them to ~/bin too. If they are simple ex. learning tasks so treat them same as scripts.

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> mkdir bin
Then edit and add:
PATH=$PATH:/home/Your_username/bin/

>Second you said something about scripting user, what if this compiled program? 
Typically you want make install them. But you can ln them to ~/bin too. If they are simple ex. learning tasks so treat them same as scripts.

Liolikas I think I understand your logic and it is smart one.
It will be smart  for me  to centralize my file.

However I asked in case that I don't do it, in case that they are in different folders, so I want to be able to run them form the differnet folder without writing ./ (of course when I am in the folder that those file are).

---

### Post by ibutho on 2009-08-30
> **oren tal said:**
> simply because whenever I go to different directory I want tp run the program their just by writing their_name and not by writing ./their_name 

Why wouldn't you want this?

I wouldn't want this because there is a possibility of running the wrong script. If your script has the same name as a script elsewhere in your path, you do not know exactly which script is running and the potential damage it may cause to your system.

---

### Post by oren tal on 2009-08-30
> **ibutho said:**
> Not sure why exactly you would want to do something like that but, you could edit ~.bash_profile and add
```
export PATH=$PATH:.
```

your advice worked from me only that I did it in the .bashrc  file and it was in /home/oren (oren is my user name).

---

### Post by oren tal on 2009-08-30
> **ibutho said:**
> I wouldn't want this because there is a possibility of running the wrong script. If your script has the same name as a script elsewhere in your path, you do not know exactly which script is running and the potential damage it may cause to your system.

well from what I understand if there is a script elsewhere in the path it will run it and not the script in my current directory since it will go for it is in the end of the path check.

Correct me if I am wrong (or if my English is not good enough)?

---

### Post by Liolikas on 2009-08-30
Yes I think but I never messed up with these settings so much.

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> Yes I think but I never messed up with these settings so much.

you think what?

---

### Post by Liolikas on 2009-08-30
That you are right in 11:28 AM post.

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> That you are right in 11:28 AM post.

our local time is not the same but do you mean this post?:
> well from what I understand if there is a script elsewhere in the path it will run it and not the script in my current directory since it will go for it is in the end of the path check.

Correct me if I am wrong (or if my English is not good enough)?

---

