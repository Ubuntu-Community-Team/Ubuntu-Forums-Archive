---
title: "How do I open a .desktop file?"
date: 2011-05-01
forum: General Help
---

### Post by JRV on 2011-05-01
How do I start a program through a .desktop file located in /usr/share/applications from the command line?

---

### Post by WorMzy on 2011-05-01
Generally, you don't. But if you open up the file in a text editor and look at the "Exec" line, the command that you would use to launch the application from the terminal is after the equals sign.

---

### Post by JRV on 2011-05-01
Thanks, but I know how to do that.
Is it possible to open an an application through a .desktop file from the command line?

---

### Post by JKyleOKC on 2011-05-01
Not so far as I can tell. First, the file names bear no visible resemblance to what you see in Places. Instead, they are based on the name of the executable file that they launch. When you get past this hurdle and try to execute one from the CLI as a normal user, you get "Permission denied" and when you use "sudo" it changes you out of the directory into /root for the attempt.

Going into temporary root mode with "sudo -i" then lets you "cd" back to the applications directory, but now you get "File or directory does not exist" even though "ls" shows that it clearly does.

I'm curious, though; why would anyone want to jump through all of these hoops instead of just getting the exec name out of the file and launching it directly?

---

### Post by WorMzy on 2011-05-01
> Is it possible to open an an application through a .desktop file from the command line? 

```
`grep Exec [COLOR="Red"]/path/to/file.desktop[/COLOR] | sed 's/Exec=//'`
```

Such a convoluted and pointless way of opening an application tbh, but there you go.

---

### Post by JRV on 2011-05-01
> **JKyleOKC said:**
> 
I'm curious, though; why would anyone want to jump through all of these hoops instead of just getting the exec name out of the file and launching it directly?



I don't need to, I am just trying to learn all I can about .desktop files and the operation of the launcher.

---

