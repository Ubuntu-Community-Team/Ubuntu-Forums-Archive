---
title: "What do I have to do to add some lines to &quot;~/.bashrc&quot;?"
date: 2010-05-08
forum: General Help
---

### Post by hihihi100 on 2010-05-08
Hi there:

I have problems starting Ibus. After an error message, I have to:

```
Add the following at the end of ~/.bashrc   export GTK_IM_MODULE=ibus
  export XMODIFIERS=@im=ibus
  export QT_IM_MODULE=ibus
```


Is it via terminal? sudo ~/.bashrc wont work


Could you please paste the exact command?


If it is not via terminal, please write what do I have to do


cya

---

### Post by notceecee on 2010-05-08
```
nano ~/.bashrc
```

or

```
gedit ~/.bashrc
```

---

### Post by hihihi100 on 2010-05-08
lol... the fastest ever solved thread in the history of the forum

thx, now I hope I can write some chinese

---

### Post by Queue29 on 2010-05-08
Don't edit as sudo, it's your file in your home directory.

Once you save the changes, either log out and log back in, or run

```
source ~/.bashrc
```

to load the changes.

---

### Post by hihihi100 on 2010-05-08
K, I shouldnt have written the celebration post...

queue:

""Don't edit as sudo, it's your file in your home directory.""

Why is it dangerous to edit it as sudo? Because I have done precisely that and re logged in, just to see that, after clicking on the Ibus icon, I get the same mnessage, and the same 3 lines to add to that same direction

""Once you save the changes, either log out and log back in, or run

     Code:
     source ~/.bashrc 
to load the changes.""

What if I run that comand now? will it make any difference?

cheers

Do you also use Ibus to write in languages that use scripts other than the latin one? (Chinese, Japanese...) because I have noticed a change in the desktop: the same way that, if using SCIM, I can see a small and movable icon that gives me easy access to all the installed IM, now I can see a totally white and movable square, which I assume is the IBUS equivalent to that SCIM icon, but its totally white. However, if I pass the mouse over it, the line "Switch input method" appears

---

### Post by Copernicus1234 on 2010-05-08
Its not dangerous to use sudo. All it does it execute the command as root instead of you. In this case it doesnt make any difference since both you and root will have write access to the file since its in your home directory. Normally you have the right to modify anything in that directory. 

So I would say its not *needed* to use sudo in this case.

But lets say you get into the habit of using sudo for everything. Maybe you type "sudo nano myfile" to create a new file in your home directory named myfile, using sudo. Then that file will be owned by root and not you. So in the future when you want to modify that file, you will *need* to use sudo to modify it. Which is of course completely unnecessary and leads to a confusing system. :)

---

### Post by hihihi100 on 2010-05-08
So, what do I have to type, instead of "sudo", to make changes as me, and not as root?

Yes, im used to make changes via terminal as sudo, in fact, I didnt know there would be any difference, but now I do...

---

### Post by Copernicus1234 on 2010-05-08
> **hihihi100 said:**
> So, what do I have to type, instead of "sudo", to make changes as me, and not as root?

Just dont type sudo ahead of the command and it will be executed as you. :)

Like you did here:

nano ~/.bashrc

That runs the nano command as you. Your user will always run all commands you type if you just type them in. Its only when you type sudo in front of it that Ubuntu will use the root account to run the command.

---

### Post by hihihi100 on 2010-05-08
ah, ok...

Can u also help me with the Ibus related question?

---

### Post by Copernicus1234 on 2010-05-08
> **hihihi100 said:**
> ah, ok...

Can u also help me with the Ibus related question?

I would if I could, but I know nothing about that. Someone else may be able to help though.

---

### Post by hihihi100 on 2010-05-08
np, u have been of help, thx

---

