---
title: "Launch Terminal Into A Specific Profile"
date: 2010-02-13
forum: General Help
---

### Post by MikeVaughanG on 2010-02-13
I need to creat launcher that launches Terminal into a specific Profile.. 

I found a website that says that this code will work

```

gnome-terminal --window-with-profile=<Profile_name>

```But, I also need to launch to specific Directory also. 
So, My code looks like this

```

gnome-terminal --window-with-profile=Scripts --working-directory /home/mike2/Desktop/Scripts

```But it doesnt work.. 
I have a feeling I'm doing something wrong, though. 
Any help is appreciated.. 

Thanks. :D

_Mike Vaughan

---

### Post by nothingspecial on 2010-02-13
You need an = before the working directory

---

### Post by MikeVaughanG on 2010-02-13
That doesnt work, either. 

and previously when I had a launcher that worked perfectly the code was like this 
```

gnome-terminal --working-directory /home/mike2/Desktop/Scripts

```

---

### Post by patchwork on 2010-02-14
Is this found inside of a shell script or being run as a stand-alone terminal command?  The syntax is correct, and runs with no troubles on my computer as written (substituting profile names and user names, of course) as a stand-alone command.  If this is in a script perhaps the error is not this line of code...

---

### Post by MikeVaughanG on 2010-02-14
I'm running it as a stand alone command.

---

### Post by nothingspecial on 2010-02-14
Works for me, with or without the =

I`d always thought you needed it :p

Does it work as a command, in the sense, if you type it in a terminal, rather than try it in a launcher?

---

### Post by MikeVaughanG on 2010-02-14
no, it doesn't work as a stand alone command or in a launcher.

---

### Post by nothingspecial on 2010-02-14
Try it in terminal with profile Default and working directory Photos or Music

Are you sure you have the paths and profile names correct.

Do you have gnome-terminal installed or a different virtual terminal?

Clutching at straws here.

---

### Post by MikeVaughanG on 2010-02-14
I am POSITIVE that the profile names and paths are correct. 

I appreciate your help with the troubleshooting. 

I've found numerous cases of people getting the same error as me, but all with different causes.

---

### Post by mmmichael on 2010-02-14
I right-clicked on my Desktop, selected create launcher, and created launcher:
Type: Application (not Application in Terminal)
Name: binterm
Command: gnome-terminal --window-with-profile=bin --working-directory /home/michael/bin

and it works.

---

### Post by MikeVaughanG on 2010-02-15
> **mmmichael said:**
> I right-clicked on my Desktop, selected create launcher, and created launcher:
Type: Application (not Application in Terminal)
Name: binterm
Command: gnome-terminal --window-with-profile=bin --working-directory /home/michael/bin

and it works.

That doesn't work for me.. :(

I get 
"There was an error creating the child process for this terminal"

---

### Post by nothingspecial on 2010-02-15
Try ```


gnome-terminal --window-with-profile=Scripts --working-directory /home/mike2/Desktop/Scripts -x bash
```

---

### Post by mmmichael on 2010-02-15
> **MikeVaughanG said:**
> That doesn't work for me.. :(

I get 
"There was an error creating the child process for this terminal"

In your terminal profile preferences, did you select "Run a custom command instead of my shell"? This could be the cause of this error.

---

### Post by MikeVaughanG on 2010-02-15
> **nothingspecial said:**
> Try ```


gnome-terminal --window-with-profile=Scripts --working-directory /home/mike2/Desktop/Scripts -x bash
```


THANK YOU!
That works perfectly. 
:D

---

