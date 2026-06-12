---
title: "Help me install deadbeef.tar.bz2"
date: 2010-09-07
forum: General Help
---

### Post by Abe21599 on 2010-09-07
ok guys decided to try out ubuntu on my POS and its awesome! just one little problem - i wanted to install deadbeef on it but i cant figure out how to get it to install.

i found it on here
[http://ianmarmour.wordpress.com/2010/05/22/best-ubuntu-10-04-applications/](http://ianmarmour.wordpress.com/2010/05/22/best-ubuntu-10-04-applications/)
but the deb command doesnt work (command not found) so i downloaded it from another site. i have it in a .tar.bz2 format but cant figure out what i need to do next. i used the built in extractor to extract it but im used to windows/mac where i can click a certain type of file (.dmg) and it installs itself. ive read the install file but this is over my head  (for now). Heres what the beginning says

 Briefly, the shell commands `./configure; make; make install' should
configure, build, and install this package.  The following
more-detailed instructions are generic; see the `README' file for
instructions specific to this package.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, and a
file `config.log' containing compiler output (useful mainly for
debugging `configure').


any help from the linux veterans out there to help get me started down teh wonderful path of ubuntu?

I look forward to reading on here a lot so i can give up using windows! yay

also, on a sidenote, it says in the INSTALL file that the simplest way to compile the package is... with a few steps. - can someone please explain what "compile" means related to ubuntu?

Thanks so much! this answered will really help me get started :p

---

### Post by flick on 2010-09-07
This should help a lot :

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Abe21599 on 2010-09-07
really? thats all you can help me with is the last part of my question?

---

### Post by bodhi.zazen on 2010-09-07
> **Abe21599 said:**
> ok guys decided to try out ubuntu on my POS and its awesome! just one little problem - i wanted to install deadbeef on it but i cant figure out how to get it to install.

i found it on here
[http://ianmarmour.wordpress.com/2010/05/22/best-ubuntu-10-04-applications/](http://ianmarmour.wordpress.com/2010/05/22/best-ubuntu-10-04-applications/)
but the deb command doesnt work (command not found) so i downloaded it from another site. i have it in a .tar.bz2 format but cant figure out what i need to do next. i used the built in extractor to extract it but im used to windows/mac where i can click a certain type of file (.dmg) and it installs itself. ive read the install file but this is over my head  (for now). Heres what the beginning says

 Briefly, the shell commands `./configure; make; make install' should
configure, build, and install this package.  The following
more-detailed instructions are generic; see the `README' file for
instructions specific to this package.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, and a
file `config.log' containing compiler output (useful mainly for
debugging `configure').


any help from the linux veterans out there to help get me started down teh wonderful path of ubuntu?

I look forward to reading on here a lot so i can give up using windows! yay

also, on a sidenote, it says in the INSTALL file that the simplest way to compile the package is... with a few steps. - can someone please explain what "compile" means related to ubuntu?

Thanks so much! this answered will really help me get started :p

You need to extract the archive and read the README

Could be you compile it :

```
sudo apt-get install build-essential
./configure 
make
sudo make install
```

You will need to download and install any dependencies first.

The link you were given covers how to do all this, if it is over your head, I suggest you install the .deb

```
sudo dpkg -i deadbeef.deb
sudo apt-get isntall -f
sudo dpkg -i deadbeef.deb
```

---

### Post by Volt9000 on 2010-09-07
In this context, to "compile" means to build an executable binary file (an .exe on Windows machines) from the source code. Usually when you download a piece of software from the repository, it's already compiled into a ready-to-run executable file. But sometimes you need to get the original source code and compile it yourself, as in this case.

So it sounds like you've already taken the first step: extracted the contents of the tar.bz2 (which is a compress archive, like a .zip or .rar).

Now, you need to go into a terminal session. Click Applications > Accessories > Terminal to bring up the terminal window. If you're not familiar with the Linux command-line, now would be a good time to learn it.

You need to enter the directory you extracted the archive to. Once there, you need to execute the following commands:

```

./configure

```

This will configure the software with the default options, and create what's called a "makefile". A makefile is a type of instruction file that tells the system how to build (compile and link) this program.
Once that's done, type:

```

make

```

This will look at the makefile and build the application for you. This may take some time, depending on the size of the app, so be patient. It's at this point you may encounter some dependency errors: that is, you won't be able to compile the program because dependencies are missing. It will be up to you to install these dependencies.

Once this command finishes successfully, type:

```

sudo make install

```

The sudo in front is important, because it specifies this command be run as superuser, or in Windows jargon, "run as Administrator." This command will take the compiled, finished application and install it and its supporting files to the proper locations on your hard drive.

If this seems overwhemling, don't worry; you'll get used to it. If you need help, you could just try these commands and if you get any errors, post the results here and we'd be happy to help you.

---

### Post by wainbee on 2010-09-08
Abe, I'm not an experienced user but the following worked great for me. DeadBeef seems like an atrocious name but it's a great music player.

I don't recommend the TAR install until you have a little more experience.

The following commands must be entered one line at a time in the TERMINAL (Applications, Accessories, Terminal)
COPY each line separately and PASTE it into your TERMINAL and hit <ENTER>.

sudo add-apt-repository ppa:alexey-smirnov/deadbeef 
sudo apt-get update 
sudo apt-get install deadbeef

The instructions are for DeaDBeeF in ubuntu 10.04/9.10 and came from:
[http://www.ubuntugeek.com/deadbeef-ultimate-music-player-for-gnulinux.html](http://www.ubuntugeek.com/deadbeef-ultimate-music-player-for-gnulinux.html)

Good luck, let us know how it goes!

---

### Post by Abe21599 on 2010-09-08
thank you guys. ill give it a go tomorrow :)

EDIT: i tried the method posted above and i get this. 


austin@austinUb-laptop:~$ sudo apt-get install deadbeef
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any ideas?

---

### Post by 3rdalbum on 2010-09-08
> **Abe21599 said:**
> thank you guys. ill give it a go tomorrow :)

EDIT: i tried the method posted above and i get this. 


austin@austinUb-laptop:~$ sudo apt-get install deadbeef
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any ideas?

Close all other package managers first.

The person who wrote that original article (about the top 10 programs) is wrong - the 'deb' bit isn't a command, it's a repository entry that you type into the Software Sources program to add the repository for the software.

---

### Post by Abe21599 on 2010-09-08
> **3rdalbum said:**
> Close all other package managers first.

The person who wrote that original article (about the top 10 programs) is wrong - the 'deb' bit isn't a command, it's a repository entry that you type into the Software Sources program to add the repository for the software.

yep i had snaptics running alongside it and it worked. thank you

---

