---
title: "Cant find where my files are located"
date: 2012-03-11
forum: General Help
---

### Post by hares on 2012-03-11
sorry didnt mean to double post. Think i posted in wrong forum with this querstion. In any case..

I cant find where my files are stored


In windows its under C://

I use ubuntu 11.04 and cant find at ALL where my installed progs/files  are. I checked under system, home and downloads. Nothing. Please help.

---

### Post by codemaniac on 2012-03-11
When you install a software package in UNIX based systems , different files are placed in different directory structures ,i.e program binaries reside in /usr/bin , configuration files get placed in /etc , like that .Unlike widows which dumps everything under "C:/Program files" or your specified path .

If you want to search a program binary location in UNIX based systems ,issue which commnad 

```
which *program_name* 
```

the above will return the absolute path or installed location of the binary .

---

### Post by 2F4U on 2012-03-11
Not sure what exactly you mean. Your user files are stored in your home folder, which is located in /home/your_user_name. Under Linux, a normal user has not the necessary privileges to store files in other places, only root (or a normal user who uses sudo) can do that.
What I don't exactly understand is what particular files do you mean? How did they get into Ubuntu? Or are you referring to files that are stored in Windows?

---

### Post by codemaniac on 2012-03-11
> **2F4U said:**
> What I don't exactly understand is what particular files do you mean? 

2F4U , i guee the above user is talking about installed packages in his Ubuntu system .

> I use ubuntu 11.04 and cant find at ALL where my installed progs/files are.  

---

### Post by 2F4U on 2012-03-11
Yeah, but as you already said, thats a guess. In order to help solve the problem it is always better to be sure what OP exactly means or wants to achieve. The responses will be much better if the OP provides as much information as possible.

---

### Post by codemaniac on 2012-03-11
> **2F4U said:**
> Yeah, but as you already said, thats a guess. In order to help solve the problem it is always better to be sure what OP exactly means or wants to achieve. The responses will be much better if the OP provides as much information as possible.

Absolutely true .But often people forget to append vital pieces of information .

---

### Post by Paqman on 2012-03-11
By default all your personal files and config files are in your home folder. Your apps are elsewhere, but tbh you don't need to know where they are, you can launch an app with just it's name. You don't need to provide the whole path. The package cache is at /var/cache/apt/archives.

---

### Post by hares on 2012-03-11
> **codemaniac said:**
> When you install a software package in UNIX based systems , different files are placed in different directory structures ,i.e program binaries reside in /usr/bin , configuration files get placed in /etc , like that .Unlike widows which dumps everything under "C:/Program files" or your specified path .

If you want to search a program binary location in UNIX based systems ,issue which commnad 

```
which *program_name* 
```the above will return the absolute path or installed location of the binary .


where would I issue the commands in ubuntu?

---

### Post by bab1 on 2012-03-11
> **hares said:**
> where would I issue the commands in ubuntu?

I believe they are referring to the command line (terminal).  This is the equivalent of Start>>Run in Windows.  If you click on Applications>>Accessories>>Terminal you will open a terminal session.  Type your command there.

Most Ubuntu packaged (Software Center or Synaptic) applications will provide a launcher in the drop down Applications menu.  I don't use Unity so I'm not familiar with that interface, but I believe there is a place to type the name of the app and it will find the launcher.

---

