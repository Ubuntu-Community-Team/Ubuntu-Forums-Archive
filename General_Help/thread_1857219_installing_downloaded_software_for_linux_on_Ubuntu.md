---
title: "installing downloaded software for linux on Ubuntu 10.10"
date: 2011-10-09
forum: General Help
---

### Post by michael2009 on 2011-10-09
Hi. Can anyone help me install a .bin programme file that is, according to the website, built for Linux? The installation instructions on the download website say:


[LIST]
[*]After downloading   open a shell and, ** cd **to the directory where you   downloaded the installer.
[*]At the prompt type: ** sh ./prayerpbasicsetup.bin**
[/LIST]
Using the terminal, I followed these instructions but only got the message:

~$ cd /home
/home$ sh ./prayerpbasicsetup.bin
sh: Can't open ./prayerpbasicsetup.bin
/home$ 

I tried several times, but got the same result. Why isn't it working? What am I doing wrong?

---

### Post by JKyleOKC on 2011-10-09
Are you sure that you downloaded the file to the /home directory? Normally this would not be possible, since it's one of the system directories that normal users do not have write access to. Your own home directory is a subdirectory of /home, and within that is another subdirectory named Downloads. By default, anything you download will wind up in that Downloads directory.

If that's where your file did wind up, issue the command ```
cd ~/Downloads
```before you try the "sh" command and things may work. If it still does not work, it's possible that the "execute bit" is not set for the setup file, but I'll hold off on instruction on fixing that until you've tried it from the correct location. If it's the execute bit, the error message will be different...

---

### Post by 3rdalbum on 2011-10-09
> **michael2009 said:**
> Hi. Can anyone help me install a .bin programme file that is, according to the website, built for Linux? The installation instructions on the download website say:


[LIST]
[*]After downloading   open a shell and, ** cd **to the directory where you   downloaded the installer.
[*]At the prompt type: ** sh ./prayerpbasicsetup.bin**
[/LIST]
Using the terminal, I followed these instructions but only got the message:

~$ cd /home
/home$ sh ./prayerpbasicsetup.bin
sh: Can't open ./prayerpbasicsetup.bin
/home$ 

I tried several times, but got the same result. Why isn't it working? What am I doing wrong?

Your home directory is not actually at "/home". It's at "/home/*username*", where *username* is your username.

The terminal always opens within your home directory anyway.

Also, did you know you can drag a file or folder to the terminal and it will automatically put in the path for you? For these instructions you can just type 'cd ' and then drag the enclosing folder to the terminal. Then type 'sh ' and then drag the file you want to run to the terminal.

---

### Post by hawthornso23 on 2011-10-10
Before running type

```
ls

```

to list the files in your current directory. If you can't seethe file you want to run, in this case

[B]prayerpbasicsetup.bin 

[/B]then you are in the wrong directory.

---

### Post by michael2009 on 2011-10-10
Thanks for the info. I typed in the right folder, with the output as follows:

:~$ cd /home/muhsin
~$ sh ./prayerpbasicsetup.binPreparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

~$


After that, the installation window for the program popped up on the desktop, and I clicked the install button. It went to the loading bar, and finished loading. Then the program appeared on the taskbar. I clicked the program, and a window opened, but it is blank.

I have been using the Windows version of this program on my Windows OS, so I know what it should look like. The taskbar icon looks right, but there should be text in the window that is blank.

---

