---
title: "Help: install Mathematica 7 under Ubuntu 9.04"
date: 2009-08-13
forum: General Help
---

### Post by jingpro on 2009-08-13
I copied the installation folder to desktop, and change permission:

$ cd Desktop
$ sudo chmod a+w -R Mathematica7
$ cd Mathematica7/Unix/Installer

Now, there is a file called 'MathInstaller'

If use command: 
$ **sudo ./MathInstaller**
I got error:
*sudo: ./MathInstaller: command not found*

If do following:
sudo su
$ **./MathInstaller**
I got following error:
*bash: ./MathInstaller: Permission denied*

Any ideal about solve the problem? Thanks a lot.

Regards,
Derek

---

### Post by jingpro on 2009-08-13
bump

---

### Post by soniabegonia on 2009-08-23
Try "sudo sh MathInstaller" rather than "./Mathinstaller". I was having your same problem and this fixed it.

[Reference]("https://help.ubuntu.com/community/Mathematica")

---

### Post by mrphud on 2010-07-28
Hello,

so the reason you can't execute the shell script is because it is not an executable. you can either do what the person above me said which is

```
sudo sh filename
```

or you have to enter

```
sudo chmod +x filename
```

then you can execute the file

```
sudo ./filename
```

It took me a while to figure this out. I think you can also enter

```
sudo bash filename
```

The last command is equivalent to the first. Hope this helps.

Here is a link
[http://www.cyberciti.biz/faq/run-execute-sh-shell-script/]("http://www.cyberciti.biz/faq/run-execute-sh-shell-script/")

Cheers

---

### Post by naksindia on 2010-09-12
I get the following error when I tried to install mathematica 7 in Ubuntu 10:
Can’t open /media/iso/Unix/Installer/MathInstaller
Please help me

---

### Post by mr.interested on 2010-10-03
> **naksindia said:**
> I get the following error when I tried to install mathematica 7 in Ubuntu 10:
Can’t open /media/iso/Unix/Installer/MathInstaller
Please help me

Type:

```
$ bash '/[here_type_path]/MathInstaller' 
```

It works for me, the only problem is that I get the following error:

```

Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/Mathematica/7.0:
> 

Error: Cannot create directory /usr/local/Wolfram/Mathematica/7.0.

You may need to be logged in as root to continue with this installation.

```

Any ideas?

---

### Post by mörgæs on 2010-10-03
You probably need to be root to install. What happens if you add **sudo** in front of the command?

---

### Post by mr.interested on 2010-10-03
> **mörgæs said:**
> You probably need to be root to install. What happens if you add **sudo** in front of the command?

Thanks for the reply. I've tried the following:

```

michael@michael-laptop:~$ sudo '/home/michael/emath70l_bin/Unix/Installer/MathInstaller' 
[sudo] password for michael: 
sudo: /home/michael/emath70l_bin/Unix/Installer/MathInstaller: command not found

```

```

michael@michael-laptop:~$ sudo bash '/home/michael/emath70l_bin/Unix/Installer/MathInstaller' 
bash: /home/michael/emath70l_bin/Unix/Installer/MathInstaller: Permission denied 

```

None of them worked.

---

### Post by mörgæs on 2010-10-05
Maybe posting in this forum will help you better:
[http://ubuntuforums.org/forumdisplay.php?f=169](http://ubuntuforums.org/forumdisplay.php?f=169)

---

### Post by dimk1 on 2011-09-04
My problem is that in all versions of mathematica i tried to install (6.0.2 and 7) i enter the password ID's etc but i always get the message that "You are running mathematica in non editing mode" and i'm not allowed to do anything. I tried installing it even after sudo gnome-terminal but no luck.Any idea?

---

### Post by masterjoda on 2011-12-24
Try to copy install files from iso image to the home folder and then try to install. It works for me. :)

---

### Post by Pronker on 2012-01-31
I had a problem similar to what is being described. 

For reference: I'm installing Mathematica 8 (v. 8.0.4) on a machine running linux mint 11 (kernel 2.6.38-8 generic).

I copied the .iso file to my disk, right-clicked and selected mount. Then nothing happened. I found the mounted image in the left side of nautilus but I couldn't run anything. Navigating there in the terminal, I could see that I only had reading permissions for the MathInstaller file in Unix/Installer (ls -alh). 
Moreover, running "sudo chmod o+x" didn't work. I ran "sudo sh MathInstaller" and it said permission denied. "sh MathInstaller" was allowed but it just hung. Then I unmounted and decieded to mount it as root. 
I ran "sudo mount /path/to/iso/Mathematica_8.0.4_LINUX.iso /mnt/mathematica -o loop" and then I ran "sudo /mnt/mathematica/Unix/Installer/MathInstaller" and everything worked fine!

---

