---
title: "java compiler in ubuntu 10.10"
date: 2011-01-20
forum: General Help
---

### Post by tubbzor on 2011-01-20
I cant find a way to install java or eclipse on my new ubuntu 10.10 install..can anyone give me the correct sudo commands to install java and/or eclipse?! 
Thanks.

---

### Post by veggen on 2011-01-20
They are both in the repos. Simply go to Software Center and type the name of the app.

---

### Post by Shibbir on 2011-01-20
[B]sudo apt-get install ubuntu-restricted-extras
[/B]
this will install some codec and other essential tools and of course your desired **java virtual machine(JVM)**. After install create a java file and save it to your home directory.

Now you can open terminal (Ctrl + Alt + T) and type:

**javac filename.java**[B]
java filename[/B]

1st command compile the file and 2nd command runs that file.

HAPPY CODING...:popcorn:

---

### Post by Mahesh Jagtap on 2011-08-03
> **Shibbir said:**
> [B]sudo apt-get install ubuntu-restricted-extras
[/B]
this will install some codec and other essential tools and of course your desired **java virtual machine(JVM)**. After install create a java file and save it to your home directory.

Now you can open terminal (Ctrl + Alt + T) and type:

**javac filename.java**[B]
java filename[/B]

1st command compile the file and 2nd command runs that file.

HAPPY CODING...:popcorn:
Hi,
  I installed ubuntu-restricted-extras as told by you. However I get the same message after giving the javac command as before. Do I need to install anything more? Thanks.

---

### Post by ofnuts on 2011-08-03
> **Mahesh Jagtap said:**
> Hi,
  I installed ubuntu-restricted-extras as told by you. However I get the same message after giving the javac command as before. Do I need to install anything more? Thanks.What message?

---

### Post by Gyokuro on 2011-08-03
You need sun-java6-jdk to compile java files (you have to enable the partner repo at first):

sudo apt-get install sun-java6-jdk

and eclipse-jdt (java development tools) get you with:

sudo apt-get install eclipse-jdt 

or download eclipse from eclipse.org (Indigo rocks :-) )

command line compiling was already shown by Shibbir.

---

