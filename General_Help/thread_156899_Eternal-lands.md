---
title: "Eternal-lands"
date: 2006-04-08
forum: General Help
---

### Post by megahertza on 2006-04-08
I need some help installing a mmorpg game called eternal lands.

The direction they give are as follows.

To play on Linux:
Download the zip file, and unzip it.
cd to the directory where you installed it.
chmod to 775 and execute el.x86.linux.bin
edit el.ini and change datadir to where you unzip everything
Also, the zip file has no base directory, so you should unzip it in a new directory you create.
To play under FreeBSD, download the Linux version, download the code from the CVS, and use the freebsd make file.

I don't know how to chmod and execute a bin file.

This is there website for any other info [http://www.eternal-lands.com/](http://www.eternal-lands.com/)

thanks guys

---

### Post by K.Mandla on 2006-04-08
Hi. I think I got it going on this end. Here's how I did it.

First, it looks like it needs the libstdc++5 package, so I installed that first with

```
sudo apt-get install libstdc++5
```

That will also install gcc-3.3-base by default, unless you've already installed it.

Then I unzipped the el_120_linux_full.zip folder into my home directory and renamed the directory to eternal-lands, just because that's easier to type. :)

Then

```
cd ~/eternal-lands
```
to move into the game directory, then

```
chmod 775 el.x86.linux.bin
```
to change permissions on the bin file to "executable", then

```
./el.x86.linux.bin
```
to start the game. I noticed a few error messages as it started, but I don't know if that affected game play or not. I'll poke around with it some more, to see if anything is crippled.

By the way, thanks for the question. I've been looking for a new game for a little while. I'll have to check this one out.

EDIT: It's still a little sketchy. It seems to be looking for files in /usr/local/games, so I'm not sure if the way I've described it above will actually be usable.

ANOTHER EDIT: Okay, I see what's going on. Running the executable creates el.ini inside a hidden folder in the home directory called .elc. You have to change the data directory inside that file to the installation directory you used, such as ~/eternal lands. The el.ini file in the installation directory doesn't seem to have an effect on the game. Now it's running. Cheers!

---

