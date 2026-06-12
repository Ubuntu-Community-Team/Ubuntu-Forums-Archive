---
title: "How do I install Programs?"
date: 2010-01-05
forum: General Help
---

### Post by plentymoon on 2010-01-05
How do I install programs like games that I download they are executable programs and stuff. But I'm trying to get Gekkeiju to work I read on another thread that he got the game to work but not the point right now.

ANyways how do I install stuff? That is my question

---

### Post by Strongman332 on 2010-01-05
their are 5 ways that I know of

1. using software center

applications >> software center

2. synaptic

system >> administration >> synaptic

3. adding a source

there are several guides on how to do this easily

4. using a .deb file

works just like a .exe file did in windows

5. compiling for source

very hard for a new user and not recommended


also some .exe files will work with a program called wine

---

### Post by fibercode on 2010-01-05
Edit: By the time I typed my post, Strongman332 had already replied to you....


There are a number of ways you can install programs (packages) in Ubuntu:

1. You can go to the "Ubuntu Software Center" in your main menu. Then look for the program that you want to install or uninstall. The list of programs here will be comparatively very short.

2. You can use the Synaptic Package Manager: System -> Administration -> Synaptic Package Manager. You can search and install / uninstall packages here. To find more packages you need to enable/add the repositories (software sources). There are a lot of tutorials on this. Here is a link to get you started on this: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

3. You can also install programs (packages) from command line (terminal).
The command would be:

```
sudo apt-get install *packagename*
```

Where the *packagename* is the name of the package you want to install. This is the same as if you were to do it from the Synaptic Package Manager.

4. If you have downloaded a file (compiled program) from the internet. Let say in your case this is a game. If it was compiled for Debian or Ubuntu Linux it will have a .deb extension. In that case you can just double click on it and it will be installed for you.

5. If you have downloaded a file (compiled program) from the internet but it was compiled for a different distribution than Debian/Ubuntu, then most likely its extension will be .rpm . In that case you will need to convert the package from .rpm to .deb like this:

```
sudo alien filename.rpm
```

And then you can either double click on the newly created .deb package to install it or do it with a command:

```
sudo dpkg -i filename.deb
```

6. You downloaded a source file. In this case this is the actual code of the program. You need to compile and install it. First you will need to uncompress and probably untar it.

To ugzip (most popular compression format in Linux)

```
sudo gunzip filename.gzip
```

To untar:

```
sudo tar -xvf filename.tar
```

After you are done with this you should be left with a directory.
Go into that directory and then execute these commands one after another:

```
sudo configure
sudo make
sudo make install
```


I am giving you quick explanations how to do this. You can just google any of the above methods to get more details.

---

### Post by Strongman332 on 2010-01-05
I was not aware you could convert from rpm to deb.

Go with fibercode's post he is much more knowledgeable than me.

---

