---
title: "Partial Upgrade question"
date: 2010-08-30
forum: General Help
---

### Post by TheOneEyedMan on 2010-08-30
In order to install a Matlab optimization package I use (Tomlab) I need to have libg2c.so.0 installed. Unfortunately, because I use 10.04 (Lucid Lynx) I cannot seem to do it with the package manager because it depends on some stuff that is deprecated in 10.04. However, when I try to force it to install after downloading it manually using:
sudo dpkg --force-depends -i libg2c0_3.4.6-8ubuntu2_amd64.deb
It installs and things all appear to be working properly in Matlab and no user land  programs have problem. I'm not sure is user land is the term I want, I mean that none of the programs that I choose to run have problems. However, Synaptic Update Manager no longer works properly. Every time it tries to upgrade me it offers me only partial upgrade and cancel where it un-installs  libg2c.so.0 and then upgrades everything. Then I can rerun the forced install and continue. 

As you can probably tell, this is not a great situation. I'd like to just make Synaptic Update Manager ignore the fact that libg2c0_3.4.6-8ubuntu2_amd64.deb is installed and run the upgrades as normal, but I cannot do that. Baring that, I'm interested in any ways to make this situation better. Other than a Ubuntu downgrade, I'm up for most anything. 

Thanks!

---

### Post by costoich on 2010-09-07
I also am having trouble with this problem.  I use Tecplot, which will not run without libg2c.so.  I have forced it to install and have not used synaptic since.

---

### Post by TheOneEyedMan on 2010-09-16
I have a solution to this, though it is pretty ugly. 
1)Go to [libg2c0_3.4.6-8ubuntu2_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.4/") and get the file you need for your architecture. 
2) Use Archive Manager to open the file. One way to do this is right click on it it in Nautilus.
2) Get the library. Double click on data.tar.gz. Double click on the period. 
3) Save the file libg2c.so.0.0.0 to a directory. I suggest your Downloads folder. I'm going to assume you've saved it there (/home/<your_username>/Downloads. You con do this with right click and extract or just drag it into the directory if both are on the screen. 
4)Open a command prompt.
5) Change to your download directory using 
cd /home/<your_username>/Downloads
6) Copy the library to lib directory using the command: 
sudo cp libg2c.so.0.0.0 /usr/lib/libg2c.so.0.0.0 
7) Change to this directory using:
cd /usr/lib
8) Link the library to the alias using:
sudo ln libg2c.so.0 libg2c.so.0.0.0

You are done and things should work. Because you haven't used a deb package the system doesn't know it is there and it doesn't bother you with the error messages. In general this is a bad idea because of dependencies. For my purposes and perhaps yours, this doesn't actually happen so this appears safe. From a usage perspective this appears to be the same as running:
sudo dpkg --force-depends -i libg2c0_3.4.6-8ubuntu2_amd64.deb

Hope this helps you.

---

### Post by saepuloh on 2012-05-08
It works great,thank you TheOneEyedMan. Only one correction for the last command should be:

sudo ln libg2c.so.0.0.0 libg2c.so.0

Thx,

---

