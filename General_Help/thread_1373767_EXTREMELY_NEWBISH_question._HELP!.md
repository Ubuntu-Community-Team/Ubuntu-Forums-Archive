---
title: "EXTREMELY NEWBISH question. HELP!"
date: 2010-01-06
forum: General Help
---

### Post by DareArkin on 2010-01-06
Hello. I only just recently made the jump to Ubuntu from windows. I downloaded a program to run some hardware... and the install file was a "Makefile." What in the holy hell is a Makefile- and is it possible to get instructions told to me like i'm someone who's missing 99% of his brain? x.x

---

### Post by ndefontenay on 2010-01-06
Hi.

What you've downloaded are the source code of the application.

What you'll have to do most likely is the following:

open your terminal (located in accessories>terminal)

type the following:

cd ~/path to where the source is located

I use ~ as your home. This is short for /home/yourusername/path

So it will look like this:

cd ~/mynewapplication_unzipped
sudo ./configure
make
make install

the sudo commands means you are requesting root (super user) privileges. You will be prompted for your password.

Ok all this said:

Most of the applications supported by ubuntu are lcoated in the software repository located at the bottom of the menu (when you click on that little foot on the upper left corner).

From there you should select whatever application you want, it will download and install it for you.

So try to find the application you're trying to install there first. If you can't find it then you've got to do it the hard way.

Do you have the URL to the homepage of the application you're trying to install?

I could give you clearer directives

---

### Post by s.fox on 2010-01-06
Hello and welcome to the forum,

Providing you have the kernel headers and such for your kernel (you can get them from within synaptic) then the usual method for compiling is:

- unpack the tar either on the command line or gui

- navigate to the folder from the terminal (with the cd command)

- most programs will have a readme or install that tells you what to do but its almost always, from the terminal whilst in the directory you unpacked the tar to:


```
./configure
make
sudo make install
```

-Silver Fox

---

### Post by SchizmWolf on 2010-01-06
Makefiles are used by the system to identify and point to the source files used by a program. Think of it this way: if you want a treasure chest full of gold, and you know there's gold all over the place, the makefile is the treasure map. It tells your computer where to go to get all the pieces it needs to run the program (fill the treasure chest.)

---

### Post by DareArkin on 2010-01-06
[http://www.ibiblio.org/pub/linux/system/status/!INDEX.html](http://www.ibiblio.org/pub/linux/system/status/!INDEX.html)

the one called portato- that's what I'm trying to install. But I think I should be able to get it from your instructions now, thank you. :) I've learned about the synaptic manager, but it doesn't have random programs like this thing. x.x

---

### Post by DareArkin on 2010-01-06
Okay, still need help. All the thing does is error out madly. I got past 'Make,' But now to 'Make Install' it says it can't create something because "permission denied" and then says "Error 1." Whatever THAT means.

---

### Post by lorsen on 2010-01-06
During make install the program files are usually copied to somewhere in the systems directories. This usually needs super user rights. So
> permission deniedmeans you don't have enough rights to create the directory in the system folders.
Try it with "sudo make install" which will ask you for the superuser (root) password.
It should also be written in a README or INSTALL or similar file.

---

### Post by DareArkin on 2010-01-06
Ah well. It looks like the file itself is somehow fried- it won't start no matter what I do, and no error messages now. 

Sucks, cos it's exactly what I wanted- a program to run an LED display off Parallel to display network usage.

---

### Post by lorsen on 2010-01-06
Does it have the proper rights? In the terminal (in the directory of the file) type "ll"
and in front of the filename (on the very left) are the permissons.
There is at first on letter for directories (either "d" or "-") followed by three letters for user, three letters for group and three letters for others. They are either "r" or "-", "w" or "-", or "x" or "-". "r" means reading is allowed, "w" means write (or changing the file) is allowed and "x" means it is executable.
At least the fourth digit should be an "x" so the user can execute it.

---

### Post by DareArkin on 2010-01-06
okay, what the hell? The command II ll 11 ||; I tried all the combinations that could LOOK like that symbol and all I get is an ugly "Command Not Found." 

Is there -any- way to make it so I can just CLICK on things instead of having to know a codebook just to run a program? It's pretty infuriating, especially since this was supposed to be EASIER than windows and so far it's just been a migraine.

---

### Post by riksweeney on 2010-01-06
What is the name of the program you downloaded?

---

### Post by DareArkin on 2010-01-06
portato-1.2

It's supposed to be a controller to let me use the parallel port to run an LED driver to show network usage, among other things. Since I plan to turn this box into a fileshare/media server, I'd like to be able to see if it's being used (And how heavily) without having to hook up a monitor. My stock of screens is incredibly low.

---

### Post by DareArkin on 2010-01-06
if it helps, here's the site that got me here- I was sent it by a friend who promptly went offline. 

[http://www.ibiblio.org](http://www.ibiblio.org)

[http://www.ibiblio.org/linsearch/lsms/portato-1.2.html](http://www.ibiblio.org/linsearch/lsms/portato-1.2.html)

---

### Post by lorsen on 2010-01-06
It is just to small "L" or ls -l (small "LS -L") for which it is the abbreviation. 
And well, installation is sometimes migraine. But that does not depend on the operating system ...

---

### Post by eltama on 2010-01-06
The program you are trying to install is from January 1996! I would be surprised if it works without modifications. It's like trying to make a Windows 95 program work on Windows 7. 

I would rather spend my time looking for an up to date program. Nowadays they easy to install if they come "packaged" (i.e. in a .deb file) or if you they are in a repository.

---

### Post by DareArkin on 2010-01-06
...oh. Darnit. x.x Is there somewhere I should look...? Google's giving me nothing...

---

### Post by lorsen on 2010-01-06
Is here [http://www.epanorama.net/circuits/parallel_output.html](http://www.epanorama.net/circuits/parallel_output.html) something useful for you? It does not exactly look like what you want, but maybe ...

---

