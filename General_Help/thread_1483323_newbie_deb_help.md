---
title: "newbie deb help"
date: 2010-05-14
forum: General Help
---

### Post by pythonsyntax on 2010-05-14
I got a tar file i want to make into a deb file but how do i do it from a tar file?

---

### Post by agnes on 2010-05-14
tar = just an archive 
deb = archive which contains software + install scripts, dependency configuration etc. so Ubuntu can automatically install the software for you

I think you want to install software? If you downloaded it as a .tar it usually means you downloaded the source code of the software. Which you have to compile manually. Extract the tar and see the instructions (readme.txt, install.txt) in the archive.
Making a deb file is done through[ a process of packaging]("https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html"), for which you also need to build the source code first, but it involves quite a few other steps.

---

### Post by pythonsyntax on 2010-05-14
How do i  make sure it is stable?

---

### Post by cdenley on 2010-05-14
> **pythonsyntax said:**
> How do i  make sure it is stable?

In my opinion, anything you didn't get from the repos and compiled yourself shouldn't be considered stable.

---

### Post by Nythain on 2010-05-14
well now thats just semantics... i mean, tty-clock is rather simple and stable but not in the repos :P

---

### Post by cdenley on 2010-05-14
> **Nythain said:**
> well now thats just semantics... i mean, tty-clock is rather simple and stable but not in the repos :P

A general answer for a general question. Basically, if you want to ensure stability, stick to the repos. Of course there are exceptions, but there is no catch-all method for determining what third-party software can be considered stable, which is what pythonsyntax seems to be looking for.

---

### Post by garvinrick4 on 2010-05-14
Here is link I keep in Bookmarks. 


[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software) 

Suppose you have a source file name src.tar.gz, what you do initially is that you need to extract the source files and then in the terminal&#8230;. 
navigate to the folder where the source file is extracted using the cd commands&#8230;.. and then 
 type the following&#8230; 

./configure

make

sudo make install 

clean install 

lets see what each one of them does&#8230; 

./configure&#8230;.. checks whether the required dependencies are available on your system or not&#8230;.. if not an error is reported&#8230;. 

make...... compiles the source code and make install is used to install the program in to the location 

if it asks for an installation location it is recommended to install all the source to /usr/src 

clean install...... removes any temporary files created in the installation process of the source and thats it your source file in installed in your system.

---

### Post by garvinrick4 on 2010-05-14
> **cdenley said:**
> In my opinion, anything you didn't get from the repos and compiled yourself shouldn't be considered stable.
This is about the smartest, is just to wait until they are updated in Ubuntu repo's and stay away from compiling. It is fun to screw around with so you know how to do it but that is about the end of it. Just an opinion.

---

### Post by pythonsyntax on 2010-05-15
Then how do i update my Ubuntu repo'sto 10.04 i from 9.10 with out upgrade it?

---

### Post by garvinrick4 on 2010-05-15
You do not, you use the repo's for your version. If you want to stay with 9.10 you just use what is in their repo's. If there is a new version of something it takes a couple of weeks to hit the repositories. 9.10 is a nice stable OS.
   Now if you want to upgrade from 9.10 to 10.04 here is the code:


```
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by pythonsyntax on 2010-05-18
that what i was looking for:)

---

