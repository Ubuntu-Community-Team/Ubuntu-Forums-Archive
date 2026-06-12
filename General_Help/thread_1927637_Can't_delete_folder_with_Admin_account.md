---
title: "Can't delete folder with Admin account"
date: 2012-02-18
forum: General Help
---

### Post by erbad on 2012-02-18
I was downloading onto my desktop a folder with files from the Internet.

When the download finished, this folder looked different as it had a padlock.  After I was done with the files within the folder, I tried to delete the folder and contents, but got the error message "Unable to trash file, permission denied".

I then right clicked on the folder, went to properties, permissions and it shows the owner and group as nobody and all the options are greyed out so that they can't be changed.  Also, at the bottom of this screen, it says "You are not the owner so you cannot change the permissions".

I am logged in with the admin account and can't delete this folder.

Any thoughts on how I would go about deleting this folder and its contents?

Thank you

---

### Post by Leppie on 2012-02-18
you could open a root nautilus session.
press ALT+F2 and enter "gksudo gnome-terminal" (without the quotes) and press enter.
then browse to your Desktop folder and delete the offending folder.

---

### Post by jamesisin on 2012-02-18
If you look at the permissions for the padlocked folder you should notice that you are not the owner (for whatever reason).  You can take ownership using chown:

```
sudo chown you.you -R /home/you/Desktop/thatfolder
```

You will be prompted for your password.

(Change all three you's to whatever your username happens to be.)

Once you are the owner of the folder and its contents you can do whatever you want with them.

---

### Post by erbad on 2012-02-18
> **jamesisin said:**
> If you look at the permissions for the padlocked folder you should notice that you are not the owner (for whatever reason).  You can take ownership using chown:


That worked perfectly, thank you

---

### Post by Leppie on 2012-02-18
it would've been quicker to delete the folder as root...

---

### Post by 0011235813 on 2012-02-18
> **Leppie said:**
> it would've been quicker to delete the folder as root...

Exactly. Use:
```
gksu nautilus
```
go to your file, and delete it. I don't know why the file you downloaded belongs to root... Is it malicious by any chance?

Or you could try:
```
sudo su && cd
```
to  make the terminal root, then use:
```
rm <folder name>
```
Note: when you put the location of your file in your "home" folder, make sure to put your username after it, since it isn't /home/downloads it's /home/<username>/downloads.

---

### Post by Leppie on 2012-02-18
> **0011235813 said:**
> Exactly. Use:
```
gksu nautilus
```
yes, good one. not sure why I wrote "gksudo gnome-terminal", must be cos I like the terminal better...

---

### Post by 0011235813 on 2012-02-18
> **Leppie said:**
> yes, good one. not sure why I wrote "gksudo gnome-terminal", must be cos I like the terminal better...

Yeah, I also put a command line method :)

---

### Post by jamesisin on 2012-02-19
> **Leppie said:**
> it would've been quicker to delete the folder as root...

Unless of course the folder contained something which he actually wanted (being why he downloaded it to begin with)...

---

### Post by WorMzy on 2012-02-19
> **0011235813 said:**
> ```
sudo su && cd
```

...wtf? o_O

```
sudo -i
```

There's no need to run two executables and a shell built-in when the first executable has the ability to rest of the command by itself, and can actually set environment variables properly.

---

### Post by 0011235813 on 2012-02-19
> **WorMzy said:**
> ...wtf? o_O

```
sudo -i
```

There's no need to run two executables and a shell built-in when the first executable has the ability to rest of the command by itself, and can actually set environment variables properly.

Or
```
sudo -s
```
the command I mentioned doesn't give you
```
root@ubuntu: ~$ 
```
it gives you
```
root@ubuntu:/home/<username>#
```
not the same thing ;)

I was thinking that this command is more likely to work as the root shell only allows the modification of root owned folders, whereas this command will allow the removal of any folder.

---

### Post by WorMzy on 2012-02-19
```
sudo -s
``` is similar, but like you noticed, it doesn't properly set env variables.

```
sudo -i
``` is the recommended command.

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by 0011235813 on 2012-02-19
> **WorMzy said:**
> ```
sudo -s
``` is similar, but like you noticed, it doesn't properly set env variables.

```
sudo -i
``` is the recommended command.

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

Oops. I was referring to sudo su && cd. But yes, I know you're supposed to use sudo -i. But I know sudo su && cd will allow you to delete anything.

---

### Post by WorMzy on 2012-02-19
But so will sudo -i, so why type more? @_@

---

### Post by 0011235813 on 2012-02-19
> **WorMzy said:**
> But so will sudo -i, so why type more? @_@

Fair point. I was just being sure that the OP could delete what ever nonsense they downloaded (seriously, what reputable app randomly decides to create a root folder in the users Downloads directory?).

---

### Post by erbad on 2012-02-20
> **0011235813 said:**
>  Is it malicious by any chance?.

The folder/files are gone, but just to respond to your question, I don't think they were meant to be malicious.

It was only a comma delimited text file that could be imported into Excel or Open Office.

---

### Post by 0011235813 on 2012-02-20
> **erbad said:**
> The folder/files are gone, but just to respond to your question, I don't think they were meant to be malicious.

It was only a comma delimited text file that could be imported into Excel or Open Office.

Strange... I might have guessed if they were some sort of program, but documents? That sounds really odd.

---

