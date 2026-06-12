---
title: "Need some CLI help"
date: 2011-05-14
forum: General Help
---

### Post by RedHugh82 on 2011-05-14
Hi, I have some trouble with the cp command and am looking for some experienced user's advice on this one.

I'm using rute.pdf(great free book) and one of the exercises
is to do is copy a file from one directory to another using the cp command in the terminal. I'm trying to copy rute.pdf from the Documents folder to the Desktop. 

I cd to Documents; once there I cp the file, then name the copied file then input the directory.

cp rute.pdf rute.pdf Desktop

The message I get: 
cp: target `Desktop' is not a directory

Your help would be greatly appreciated.

Thanks in advance.

---

### Post by Thewhistlingwind on 2011-05-14
> **RedHugh82 said:**
> Hi, I have some trouble with the cp command and am looking for some experienced user's advice on this one.

I'm using rute.pdf(great free book) and one of the exercises
is to do is copy a file from one directory to another using the cp command in the terminal. I'm trying to copy rute.pdf from the Documents folder to the Desktop. 

I cd to Documents; once there I cp the file, then name the copied file then input the directory.

cp rute.pdf rute.pdf Desktop

The message I get: 
cp: target `Desktop' is not a directory

Your help would be greatly appreciated.

Thanks in advance.

/home/Desktop

You have to do the full filepath, which means you can't just name the directory you want. The reason for this is that you can have two directories that are the same name except one is under a different file then the other. Thus it's better to have the system take a full filepath so that no confusions arise.

---

### Post by RedHugh82 on 2011-05-14
Thanks! Problem Solved :)

---

### Post by lisati on 2011-05-14
Posts moved to own thread. Please do not hijack other people's threads, and if this problem is solved, please mark the thread solved.

---

