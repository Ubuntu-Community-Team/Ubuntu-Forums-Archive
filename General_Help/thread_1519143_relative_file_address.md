---
title: "relative file address"
date: 2010-06-27
forum: General Help
---

### Post by benlyboy on 2010-06-27
Here's my problem I am writing a program in pyqt to use both on my windows and linux systems. 

The only problem I seem to be having is in the way the two systems seem to handle relative file address. if a full address in not given the windows system works from the current directory, which is what i thought should happen. On the other hand my linux systen works from the home directory. this I didn't expect.

So this is my question, is there something screwy going on with my system, or is this how ubuntu handles relative file address..?

---

### Post by Revolutionary101 on 2010-06-27
Not necessarily. Originally your terminal will have your home directory as your default directory. However, lets say you want to go to /usr/bin/test. You could type this into terminal.
```
cd /usr
```
That will change the directory to /usr.
```
cd bin/test
```
That is a relative path name. Because there is no / at the beginning of the path, that means that the path is relative. After that is entered it will take you to your desired directory of /usr/bin/test.

Hope my explanation helps.

---

### Post by benlyboy on 2010-06-27
Thanks for the reply.

So what you are saying is no matter what subdirectory a file is opened in the relative file address default starting point will still be the home directory unless I change it...?

So to be able to find the data files the program needs to work(which are in the same subdirectory as the program file) I will ether  have to change the default starting point , use the full address , or place it in the home directory and name it so it can be found?

To do this I ether have to make sure that the subdirectory is placed in the home directory and name correctly. or I need to find a way to find the full address of the program subdirectory  so I can use it to find the other files I need..


Is that about the size of it...?

Thanks again for the help

---

### Post by Revolutionary101 on 2010-06-27
Yeah that is all there is to it.

---

### Post by benlyboy on 2010-06-27
ok thanks will work on it....

Have to say and I don't say this often, but I like the way windows handles this better...did i just say that:confused:


Thanks for the help

---

