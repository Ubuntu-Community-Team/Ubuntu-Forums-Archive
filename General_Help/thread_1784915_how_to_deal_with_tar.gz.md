---
title: "how to deal with tar.gz"
date: 2011-06-17
forum: General Help
---

### Post by evilheart on 2011-06-17
hi , i have been using linux for about 2 months now , and still can't deal with tar.gz files!!!!!

i extract the achieve , open the folder , open terminal in that folder , then make and..... nothing 

i didn't find the make file in firefox 6 tar.gz for example , for other files there was missing libraries , is there a compiler that can do the job simply like synaptic???,
it is really stupid that every application should have its installation instructions!!!!  why there isn't some standardization for all linux distro in this point? 
deb packages are simple to use , why there isn't a general package system for all linux distro ? or at least a unified system for compiling where i can use the tar.gz files like .deb files?

---

### Post by squaregoldfish on 2011-06-17
> then make and..... nothing

There can't be 'nothing' - there must be some error, or output of some sort. Posting the output will help us to debug things.

Frequently you have to run ./configure when you enter the directory, before you run make. This is a clever script that checks your system to make sure the required libraries etc. are installed, and sets everything up so make knows where to find the things it will need. If it can't find something it needs, it will tell you.

The five commands:
```
tar xzf prog.tar.gz
cd prog
./configure
make
sudo make install

```

are pretty much universal for installing programs from source.

Steve.

---

### Post by gordintoronto on 2011-06-17
A tar file is just like a zip, it might contain anything! If it's a program, there is usually a readme which gives you some hints about what to do. But it could also contain 20 text files, and no program.

If you are looking to install Firefox 6, you should re-evaluate your sources of information.

---

### Post by crispy_420 on 2011-06-17
I hate to point this out but don't many extracted archives include a read me file or at least the source web site has some basic instructions on how to proceed.

---

### Post by evilheart on 2011-06-18
> **squaregoldfish said:**
> There can't be 'nothing' - there must be some error, or output of some sort. Posting the output will help us to debug things.

Frequently you have to run ./configure when you enter the directory, before you run make. This is a clever script that checks your system to make sure the required libraries etc. are installed, and sets everything up so make knows where to find the things it will need. If it can't find something it needs, it will tell you.

The five commands:
```
tar xzf prog.tar.gz
cd prog
./configure
make
sudo make install

```

are pretty much universal for installing programs from source.

Steve.

thanks for the advice , i hope it solves all the problems ,

Crisp

yes , i know it probably has readme file for every tar.gz , and that what annoys me , the instruction for installing any windows program is usually

download exe file
open exe file

while the rest of the web page is for how to install it on linux!!!!!

,  i know compiling from source is the most universal way , but if there is some  strict standard for how the source files are written , we can make a universal tool to extract and compile the program just from the tar file , instead of making the user manually compile , check for errors , search and download necessary libraries , most of computer users are not programmers you know,imagine telling your old aunt or your young sister to "compile from source" and "search for required libraries"!!!! she probably doesn't know even what compiling is!!!! and all that for just installing and application!!!!

synaptic does all that with deb files , which makes it even easier than windows installer , and i was wondering why there isn't another "synaptic" for tar.gz files , i know these are just compressed files , but if all the source codes are written in a universal form , something like that is possible , the one who need the code can just extract the file , the one who needs the program directly will just use this universal tool to compile - search for errors - download necessary libraries from repositories.

the problem something like that will need all the linux distro developers to make some association and make standards for writing source codes , which i don't feel it does exist , i feel that mostly each distro is working in its own universe putting its own standards , i think that confuses the normal programmers and even users, 
at last sorry for the long reply!!!

---

### Post by Linux_junkie on 2011-06-18
> **evilheart said:**
> thanks for the advice , i hope it solves all the problems ,

Crisp

yes , i know it probably has readme file for every tar.gz , and that what annoys me , the instruction for installing any windows program is usually

download exe file
open exe file

while the rest of the web page is for how to install it on linux!!!!!

,  i know compiling from source is the most universal way , but if there is some  strict standard for how the source files are written , we can make a universal tool to extract and compile the program just from the tar file , instead of making the user manually compile , check for errors , search and download necessary libraries , most of computer users are not programmers you know,imagine telling your old aunt or your young sister to "compile from source" and "search for required libraries"!!!! she probably doesn't know even what compiling is!!!! and all that for just installing and application!!!!

synaptic does all that with deb files , which makes it even easier than windows installer , and i was wondering why there isn't another "synaptic" for tar.gz files , i know these are just compressed files , but if all the source codes are written in a universal form , something like that is possible , the one who need the code can just extract the file , the one who needs the program directly will just use this universal tool to compile - search for errors - download necessary libraries from repositories.

the problem something like that will need all the linux distro developers to make some association and make standards for writing source codes , which i don't feel it does exist , i feel that mostly each distro is working in its own universe putting its own standards , i think that confuses the normal programmers and even users, 
at last sorry for the long reply!!!

If you stick to debian packaged files *.deb you won't need to extract source files and compile them to run.  The *.deb files are very similar to *.exe files in Windows.

---

### Post by evilheart on 2011-06-18
> **Linux_junkie said:**
> If you stick to debian packaged files *.deb you won't need to extract source files and compile them to run.  The *.deb files are very similar to *.exe files in Windows.

i wish to , but not all linux applications have .deb packages or can be found in the repositories , i think most of the open source programmers prefer giving the source files as it more general as square goldfish said , but it is still difficult for normal users , even may be for advanced if an error showed up , you will have to waste a lot of time finding out about it .

i think small thing like that , is what makes linux a second choice for normal users ,  not all the users emigrating from windows have the patience to spend hours reading documentations for every thing he want to tweak , or detailed instructions for every application he want to install , 
many of them will probably choose simplicity of windows over the performance and flexibility of linux , those not-computer-geeks just want something to do the job and doesn't need a lot of effort.

---

### Post by alexis44 on 2011-06-18
I really have to agree with the OP on this.  I like Ubuntu, but it's matters such as this that bring up the perception of Linux that it's sometimes too geeky and not user-friendly enough.  If it wants to go mainstream then you may need to simplify things for the non-geek. :p Like Me, of course. :)

---

### Post by oldos2er on 2011-06-18
OP mentioned Firefox, which if you download in tar.gz form contains precompiled ready-to-run binaries.

---

### Post by gordintoronto on 2011-06-18
Evilheart, what you want is impossible. If tar files annoy you, stick to Synaptic Package Manager.

Some programmers use a language called C. Some use a language called Python. Some use a language called Java. And on and on. The "compile procedure" is completely different, depending on what language the programmer uses.

I do a wide range of things with my computer, and I have only needed to compile a program once. In that case, the web site where it came from gave me perfect instructions.

---

### Post by evilheart on 2011-06-19
> **gordintoronto said:**
> Evilheart, what you want is impossible. If tar files annoy you, stick to Synaptic Package Manager.

Some programmers use a language called C. Some use a language called Python. Some use a language called Java. And on and on. The "compile procedure" is completely different, depending on what language the programmer uses.

I do a wide range of things with my computer, and I have only needed to compile a program once. In that case, the web site where it came from gave me perfect instructions.

again , repositories don't contain every thing.  

i don't think it is really impossible , i am not a professional programmer , but i think i have good back ground about  programming , 
i think the variance of programming language isn't really a big problem , what i am talking about can be a complete tool that chooses the proper compiler for the source files , 
a line can be added in the ./config file so "this tool" can detect the proper compiler , even a recommended compiler can be mentioned in this file.

what matters here is having some standardization for all linux distro to make the life of users easier.

---

### Post by amauk on 2011-06-19
> **evilheart said:**
> again , repositories don't contain every thing.No, but you can add extra ones
This is the PPA for daily builds of in-development Mozilla projects (inc. firefox 6)
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

> **evilheart said:**
> i don't think it is really impossible , i am not a professional programmer , but i think i have good back ground about  programming , 
i think the variance of programming language isn't really a big problem , what i am talking about can be a complete tool that chooses the proper compiler for the source files , 
a line can be added in the ./config file so "this tool" can detect the proper compiler , even a recommended compiler can be mentioned in this file.

what matters here is having some standardization for all linux distro to make the life of users easier.Same argument that's been used for years, unfortunately

"There are N packaging formats. This is too many!! I'm going to develop the ultimate packaging format that will draw all the best bits from the others into one, single, definitive packaging format, and will reign supreme above all other formats"

"Oh bugger, there's now N+1 packaging formats"

---

### Post by oldos2er on 2011-06-19
> **evilheart said:**
>  repositories don't contain every thing. 

Which software are you wanting to install? Unless it's something incredibly obscure, chances are someone here has already installed it and can give you pointers. There may even be a PPA available.

---

### Post by evilheart on 2011-06-21
> **oldos2er said:**
> Which software are you wanting to install? Unless it's something incredibly obscure, chances are someone here has already installed it and can give you pointers. There may even be a PPA available.

well , most the tar.gz files i met was for games , or a may be some special programs .

---

