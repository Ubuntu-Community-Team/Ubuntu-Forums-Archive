---
title: "Getting all the IDEs I need for Ubuntu and other questions"
date: 2012-03-14
forum: General Help
---

### Post by JustinAnyhowStep on 2012-03-14
Hello, my name's Justin; a soon-to-be Ubuntu user.
Anyways, I have some questions about Ubuntu IDEs and how programs will run; err, I can't articulate well on this matter, maybe reading on will help =/

I will need IDEs for the following:
```

Mark up languages:
    HTML (with CSS support)
    XML

Scripting languages:
    PHP
    Javascript
    Action Script 3

Compiled languages:
    C++
    C#
    Java

```And I'll need to get Apache, MySQL and PHP running on my local machine in Ubuntu; but I'll probably figure this out myself.

Also..
If I compile a C++ or Java program in Ubuntu, will it run on Windows?
And the question goes the other way, too; if compiled on Windows, will it run on Ubuntu?

As for C#, I am aware that it is Microsoft's programming language that's based off the .NET framework or something like that and will only work on Windows.

The thing is, all of my friends and classmates use Windows and I'm in the middle of writing a C# program for them to use (I used C# because it was easy to code the GUI).
I have no idea what I'll have to do to get my unfinished project to work on both Ubuntu and Windows; I have no desire to re-code it in another language unless absolutely necessary.

Can anyone point me in the right direction in this?
I apologize if it's too many questions (I have more) but I've never had to jump from one OS to another before and I was quite comfortable with Windows.

Edit:
Guess I'm interested in cross-platform compatibility between Windows and Linux.
Also, will I be able to work on my C# project on Ubuntu?
Like, is there a C# IDE that runs on Ubuntu? (doubtful)
If not, is there any way for me to recode my project (the nightmare) from scratch in a cross-compatible way?
(Using a nice GUI framework that provides tree-views, textboxes, rich textboxes, buttons, etc., hopefully)

---

### Post by Thewhistlingwind on 2012-03-14
> **JustinAnyhowStep said:**
> Hello, my name's Justin; a soon-to-be Ubuntu user.
Anyways, I have some questions about Ubuntu IDEs and how programs will run; err, I can't articulate well on this matter, maybe reading on will help =/ 

It did.
> **JustinAnyhowStep said:**
> 
I will need IDEs for the following:
```

Mark up languages:
    HTML (with CSS support)
    XML

Scripting languages:
    PHP
    Javascript
    Action Script 3

Compiled languages:
    C++
    C#
    Java

``` 

For Java theres eclipse.

For C# theres mono.
> **JustinAnyhowStep said:**
> 
And I'll need to get Apache, MySQL and PHP running on my local machine in Ubuntu; but I'll probably figure this out myself.


```
sudo apt-get install 'apache2' 'mysql-server' 'php5-cli'
```

Remember that you will need to read these programs respective documentations to configure properly. Installing them and then not configuring them is *bad* and may leave you open to attacks from malicious 3rd parties.
> **JustinAnyhowStep said:**
> 
If I compile a C++ or Java program in Ubuntu, will it run on Windows?
And the question goes the other way, too; if compiled on Windows, will it run on Ubuntu?


Depends. I'm pretty sure you can cross compile for windows from Linux. You have to specify it though.

> **JustinAnyhowStep said:**
> 
As for C#, I am aware that it is Microsoft's programming language that's based off the .NET framework or something like that and will only work on Windows.


Theres an open source implementation of .NET called mono. It's not as good as the Microsoft implementation. But it runs as long as you stay away from certain .NET libraries. (Thats what I hear anyway.)

> **JustinAnyhowStep said:**
> 
The thing is, all of my friends and classmates use Windows and I'm in the middle of writing a C# program for them to use (I used C# because it was easy to code the GUI).
I have no idea what I'll have to do to get my unfinished project to work on both Ubuntu and Windows; I have no desire to re-code it in another language unless absolutely necessary. 

It probably won't be. You might have to change some library calls though.

> **JustinAnyhowStep said:**
> 
Can anyone point me in the right direction in this?


Yeah. If you ever need to install a program but don't know what it's called you can issue this at the command line:

```
apt-cache search [STRING]
``` Replace [STRING] with what your searching for and your good. (Don't type the brackets. You might want to get into the habit of surrounding bash arguments in quote marks however.)

> **JustinAnyhowStep said:**
> 
Edit: guess I'm interested in cross-platform compatibility between Windows and Linux.

Indeed you are. Good luck to you.

---

### Post by JustinAnyhowStep on 2012-03-14
Thanks for the very quick response.
I just got mono-devel, apache, mysql-server and php thanks to you.

I must say that using Ubuntu is.. different.
It'll take some time to get used to.

I installed Ubuntu using the installer from this link:[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
And I just realized that Ubuntu can't access the files that were on my Windows installation (music, source code, etc.).

A bit of an oversight on my part. Will I have to boot Windows, transfer files to a hard drive then boot Ubuntu to get files across?
Seems like a waste, seeing as the files are on the same hard disk.

Edit: hold on, I accidentally bumped into the fact I can mount a hard disk and access it.
Wow, that's neat.

---

### Post by Cheesemill on 2012-03-14
> **JustinAnyhowStep said:**
> I installed Ubuntu using the installer from this link:[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
And I just realized that Ubuntu can't access the files that were on my Windows installation (music, source code, etc.).

As you are using Wubi your Windows drive is already mounted under /host

---

