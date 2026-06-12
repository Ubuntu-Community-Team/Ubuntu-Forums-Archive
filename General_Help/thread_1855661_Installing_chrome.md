---
title: "Installing chrome"
date: 2011-10-06
forum: General Help
---

### Post by AV Town Crier on 2011-10-06
I downloaded the .deb file and used the following command;
sudo dpkg -1 google-chrome-stable_current_i386.deb.
I get error unknown option -1
Help!
Thanks

---

### Post by meatytaco on 2011-10-06
try dpkg -i filename.deb

not a 1

---

### Post by AV Town Crier on 2011-10-06
> **meatytaco said:**
> try dpkg -i filename.deb

not a 1
I get error message no such file or directory. Yet it's on the desktop.

---

### Post by patryk77 on 2011-10-06
> **meatytaco said:**
> try dpkg -i filename.deb

not a 1

Yep... -i stands for install.

For help with (almost) any command, read the man page... From the shell:
```
man dpkg
```
Or: [http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html)

---

### Post by patryk77 on 2011-10-06
> **AV Town Crier said:**
> I get error message no such file or directory. Yet it's on the desktop.

run: 
pwd

This will tell you where you are... Probably /home/{Your User Name}

You need to run as root to install software, so use "sudo":
sudo dpkg -i ~/Desktop/google-chrome-stable_current_i386.deb

Or change to the proper directory first:
cd ~/Desktop
sudo dpkg -i google-chrome-stable_current_i386.deb

You can use "ls" to list the files and make sure it is there.

Edit: The tilde (~) means "my home directory" ... So if your home is /home/av/ you can use a path like /home/av/google-chrome-stable_current_i386.deb or ~/google-chrome-stable_current_i386.deb... They are both equal

---

### Post by AV Town Crier on 2011-10-06
> **patryk77 said:**
> run: 
pwd

This will tell you where you are... Probably /home/{Your User Name}

You need to run as root to install software, so use "sudo":
sudo dpkg -i ~/Desktop/google-chrome-stable_current_i386.deb

Or change to the proper directory first:
cd ~/Desktop
sudo dpkg -i google-chrome-stable_current_i386.deb

You can use "ls" to list the files and make sure it is there.

Edit: The tilde (~) means "my home directory" ... So if your home is /home/av/ you can use a path like /home/av/google-chrome-stable_current_i386.deb or ~/google-chrome-stable_current_i386.deb... They are both equal
I was running in desktop that's alos where files were located.

---

### Post by patryk77 on 2011-10-06
I suggest using Bash's auto-complete feature.

Simply type part of the path and press Tab. When it is only matching one file, it will complete it for you and make sure you have no typos and the file really exists.

If you still have problems, post the output of dpkg, pwd and ls.

---

### Post by AV Town Crier on 2011-10-06
> **patryk77 said:**
> I suggest using Bash's auto-complete feature.

Simply type part of the path and press Tab. When it is only matching one file, it will complete it for you and make sure you have no typos and the file really exists.

If you still have problems, post the output of dpkg, pwd and ls.
It worked I ran chrome set it as my default browser.
Closed it down. But now I can't seem to find where it is.

---

### Post by oldos2er on 2011-10-07
Just double-click the *.deb file.

---

### Post by meatytaco on 2011-10-10
Mark as solved? ;)

---

### Post by oldos2er on 2011-10-10
It's up to AV Town Crier to mark it 'Solved'.

---

