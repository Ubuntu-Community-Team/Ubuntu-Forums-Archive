---
title: "Basic help compiling C"
date: 2010-07-16
forum: General Help
---

### Post by warmnscsi on 2010-07-16
Hello, I just installed 10.4 and I have to say it's the best ubuntu yet. I need some help because it's been a while since I've used linux, I have a folder on my desktop named "book". I have some C text files in that folder which I'm trying to use gcc to compile and run. When I go into terminal I'm at "user@user-desktop:~$" since "book" is on my desktop I type "cd book" and it says it does not exist. I've tried variations of trying to access this folder such as "cd "book"" or "cd /book" and no dice. Help?

---

### Post by ThesaurusRex on 2010-07-16
```
cd Desktop/book
```

---

### Post by RiceMonster on 2010-07-16
when you see user@user-desktop:~$ this means you're in your home directory. This is a step below your Desktop. How do I know you're in your home directory? This is what the ~ means. Your home directory is /home/YOUR_USER_NAME. If you type /book, this means you're refering to a directory called "book" in your root directory.

Your desktop is at /home/YOUR_USER_NAME/Desktop, or more simply, ~/Desktop

so to get to the "book" folder, you do
```
cd ~/Desktop/folder
```

If you want to see what's in any directory, simple type "ls", or "ls -a" to show hidden files as well.

---

### Post by ThesaurusRex on 2010-07-16
Look into some simple help for running commands from the terminal. Some you'll need:```
ls
```lists all the files/directories in the current directory.```
pwd
```shows you your present working directory

---

### Post by warmnscsi on 2010-07-16
> **ThesaurusRex said:**
> ```
cd Desktop/book
```


Where's the face palm emoticon? Heh, I forgot Desktop needs a capital D. Thanks!

> **RiceMonster said:**
> when you see user@user-desktop:~$ this means  you're in your home directory. This is a step below your Desktop. How do  I know you're in your home directory? This is what the ~ means. Your  home directory is /home/YOUR_USER_NAME. If you type /book, this means  you're refering to a directory called "book" in your root directory.

Your desktop is at /home/YOUR_USER_NAME/Desktop, or more simply,  ~/Desktop

so to get to the "book" folder, you do
```
cd ~/Desktop/folder
```If you want to see what's in any  directory, simple type "ls", or "ls -a" to show hidden files as  well.

Thanks I forgot about that as well.

---

