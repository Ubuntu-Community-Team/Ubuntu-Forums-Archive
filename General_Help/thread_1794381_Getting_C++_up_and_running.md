---
title: "Getting C++ up and running"
date: 2011-06-30
forum: General Help
---

### Post by cddpys on 2011-06-30
Hi i just installed Kubuntu and i am working to get all of my usual applications running which i ran with windows.

i am familiar with using the sudo apt-get install command line and i have installed the synaptic package installer.


My problem is that i want to get c++ up and running and before i just used Microsoft visual studio.  I have search around and installed eclipse and have ran the sudo apt-get install build-essential.  My question is what do i have to do now?  I dont see any trace of c++ when i open eclipse?

o and i am using the latest version of kubuntu (11.04?)

thanks for the help!

---

### Post by Linux vs God on 2011-06-30
I think you download the Java edition of eclipse. Download geany. It's much easier (sudo apt-get install geany)

---

### Post by Gyokuro on 2011-07-01
For eclipse: you need eclipse CDT plugin

---

### Post by sam_delta on 2011-07-01
+1 on geany or if you are in kubuntu, why dont you try Kdevelop?

sam

---

### Post by cddpys on 2011-07-01
ok thanks for the quick reply!

I liked the way kdevelop looked so i installed that.

One small problem though, when i open kdevelop it has a premade hello world program. when i run it however it just gives me an error saying Job Failed in a pop up box?  any ideas why this wont work, i did not modify the code at all.

---

### Post by sam_delta on 2011-07-01
the message appears when you try to run it? or when you try to compile/build it?? does it build fine?

remember that each c++ app has to be compiled/built before running

sam

---

### Post by pjd99 on 2011-07-01
> **cddpys said:**
> I have search around and installed eclipse and have ran the sudo apt-get install build-essential.  My question is what do i have to do now?  I don't see any trace of c++ when i open eclipse?
thanks for the help!
Installing build-essential has installed at the very least: gcc, g++ and make.

If the aim is simply to be able to code in c++ and compile it (i.e. you're not writing software for large, complex projects), an IDE may be a bit much for you.

IMO, if this is just for homework/tinkering, use kate. It has syntax highlighting and lets you condense functions etc, and do the compiling from the terminal (or even better, learn to use make). Also, you'll learn more.

p.s. I used kate for all my undergrad c/c++ and it was great - even though I had to install a heap of kde libraries to get it running on my gtk based DE. Kubuntu users don't have that problem.

---

### Post by cddpys on 2011-07-01
Yea i am only programming for personal use but I want to get familiar with using an IDE

Ok i should have been more specific.

When i do a "quick compile" it compiles in the build below.

However when i hit the build selection button a pop up message appears saying "Build Failed". I guess im just used to Visual Studio where you hit the green arrow and everything works lol.

---

### Post by cddpys on 2011-07-01
Just an update i solved it by switching to using codeblocks,(was a much simpler setup)

thank for the help though!

---

### Post by sam_delta on 2011-07-01
im not sure if kdevelop depends on cmake for building c++ files, you could give it a try. check if cmake is installed and if not, install it with ```
sudo apt-get install cmake
```

let us know how it goes!!

---

### Post by sam_delta on 2011-07-01
> **cddpys said:**
> Just an update i solved it by switching to using codeblocks,(was a much simpler setup)

thank for the help though!
alright, i just saw this post

enjoy!
sam

---

### Post by cddpys on 2011-07-02
ok, i have been testing out code blocks and i am really not enjoying the way it is setup and finding the debugger not very intuitive.

ive been trying to get eclipse up and running be i seen to only be able to get the java version running. For c++ it seems i need Eclipse Helios but ive been searching and have no idea how to download this? ive tried downloading it from the site but kubuntu doesnt know which application to use on the file(and neither do i).

Is there any step be step guide to getting Eclipse Helios up and running ??

---

### Post by sam_delta on 2011-07-02
To use the latest eclipse (helios) with support for c++, do the following.

You will not need the repos version anymore, so optionally remove the repos version of eclipse with 
```
sudo apt-get purge eclipse
```

download eclipse helios with c++ support from the following link
[http://www.eclipse.org/downloads/packages/eclipse-ide-cc-developers/heliossr1](http://www.eclipse.org/downloads/packages/eclipse-ide-cc-developers/heliossr1)
Check out the download links on the right of the page, download the "Linux 32 bits" or the "Linux 64 bits" depending which version of kubuntu you installed.

you will get a .tar.gz package,extract the folder (right click-> extract here).

Eclipse comes in a stand alone executable, so just open the folder (eclipse, the one extracted from the package) and double click the "eclipse" file to execute eclipse c++.

let us know how it goes.
sam

---

### Post by cddpys on 2011-07-02
Awsome that worked! Thanks!

New issue though, I wrote hello world and when i click run i get an error "Binary Not Found". I have g++ installend and mingw, but i think i have to configure MinGW? What would be the proper way to do this? 
 
UPDATE: I was wrong i dont even have MinGW installed. When i type "sudo apt-get install mingw" however the konsole says "unable to locate package".

any ideas?

---

### Post by sam_delta on 2011-07-02
have you built the project first??

The following steps work for me:

Create a new c++ project: File > New > C++ Project
(make sure you select Linux GCC in the toolchain option).

Build the project: Project > Build All (or simply press CONTROL-B)

Execute the compiled program: Run > Run/Debug, (or press F11(debug) /CONTROL-F11 (just run))

let us know how it goes.
sam

---

### Post by cddpys on 2011-07-02
Ok so when i am creating a new project and select "Empty Project" under executable and write hello world it i get the binary error. However when i select the "Hello World C++ Project" under executable it comes with a pre made hello world as the template code. when i build and run this then it works fine. so i guess ill just always have to select "Hello World C++ Project" when making a new program.

---

### Post by sam_delta on 2011-07-02
Its probably because the file you are working on its not part of the empty project (the default c++ project already comes with a added file). 

Try the following:

Create a new empty project

Add a new file to the empty project: File > new > source file
Name it as you like, end it with .cpp

Write any program, and build/execute.

sam

---

