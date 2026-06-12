---
title: "xampp installation error..!"
date: 2011-08-07
forum: General Help
---

### Post by suryaD on 2011-08-07
hey guys hello...i've just switched from xp to ubuntu linux and i must say that ubuntu is an awesome operating system  since i pretty much do stuff on the web so this os is perfect for me..so coming to my problem..i use xampp for my php training and i used to not have any problem when working wih xampp on xp but in linux i'm not able to install xampp correcly it is giving me this error..help appreciated..
btw i'm using ubuntu 11.04 and xampp ver-1.7.4
[IMG]http://i56.tinypic.com/2lkzcip.jpg[/IMG]

---

### Post by ~!geek!~ on 2011-08-07
You should use tar command by prefixing it with sudo 
i.e.
sudo tar  . .. . . . . .. . . . 
Enter password when you are prompted for it.

---

### Post by suryaD on 2011-08-07
not working bro same error...!

---

### Post by restorator on 2011-08-07
Check you path and/or spelling. Make sure the file is in the directory you are working in. The error says no such file or directory, so its not finding it from your command.

---

### Post by ~!geek!~ on 2011-08-07
Oops, I didn't read the error previously. 
Your prompt in image shows you are in Desktop Directory. 
The tar command was not able to find the tar.gz file (compressed xampp file). So before running the command you should cd to the directory containing the compressed xampp .tar.gz file. 
If the compressed xampp is in Downloads directory in your home folder, 
you should  use cd command to go to Downloads folder, i.e. cd ~/Downloads .
Now use the tar command you were trying to use.
Although you must use sudo before tar, in this case also.


A Suggestion: Although I would suggest you to get yourself away trying to install xampp because ubuntu has a bundled package for web development known as LAMPP. Install this instead of the xampp as its kinda' standard and easy to use.
To get this package, you may follow this post of mine on thread:
[http://ubuntuforums.org/showthread.php?p=11127357#post11127357](http://ubuntuforums.org/showthread.php?p=11127357#post11127357)
Its not a comprehensive guide, but you may see if this helps. Also use google to install Lampp for web development. You will find good guides.

---

### Post by suryaD on 2011-08-07
same error again...tried it a million times...wth..aww man tired of dng this..HELP

---

### Post by Wim Sturkenboom on 2011-08-07
I think that the problem is that the filename MUST follow after the 'f' (as far as I know).

So the command should be *_tar -xvzf ..._*, not *_tar -xvfz ..._*

Also be aware that Linux is case sensitive. *_xampp_* and *_Xampp_* are different things.

I agree with ~!geek!~ that it is probably a better option to use the stuff from the repository. It's easier to get support here and it's automatically updated by the update manager.

---

### Post by suryaD on 2011-08-07
i'm getting the same error as mentioned in the pic..should i redownload the package guyz..?

---

### Post by Wim Sturkenboom on 2011-08-07
Run *_ls -l_* in the terminal. Is the file there?
Copy the result and paste here between [noparse]```
 and 
```[/noparse] if necessary.

Run *_find /root/Desktop -iname xampp* -print_* and see what it returns. It should give you the full path to the xampp tarball.

//Edit:
I just realize:
if you downloaded that file as a normal user and you did not move/copy it to root's desktop, it will NOT be there; it will be in the user's home directory somewhere.

---

### Post by suryaD on 2011-08-12
a new problem popped up guys...i'm attaching the pic guys plz do help me cuz i'm missing many php and jqury tutorials becoz of this..and what is /opt.It is saying no such file or directory.
this morning i installed xampp properly and it was a suceess and i thought of unstalling and installing xampp again and ever since then this is the error which is popping up...!
plz help..desperate now..as u can c the downloaded file is on the desktop..steps which  i folow in terminal
1.cd Desktop
2.sudo -s
3.password
4.tar xvfz xampp-linux-1.7.4.tar.gz -C /opt 
 and after these commands below is the error
[IMG][IMG]http://i56.tinypic.com/29ehgrn.png[/IMG][/IMG]

---

### Post by gordintoronto on 2011-08-12
Why don't you double-click on the file! Then you can specify where to extract it to.

---

### Post by suryaD on 2011-08-13
successfully istalled xampp guys..did it myself...thnks anyway.. :p

---

### Post by Wim Sturkenboom on 2011-08-13
> **suryaD said:**
> successfully istalled xampp guys..did it myself...thnks anyway.. :pPlease share with us how you solved it and what the cause of the problem was.

Also please mark your thread as solved using the thread tools just above the first post on this page.

And congratulations

---

### Post by suryaD on 2011-08-13
i did nothing man...was trying hard to install xampp yesterday and that didn't work out and agian tried it in the morning and out of the blue it worked..i used the following steps:-

1.opened terminal
2.cd Desktop(since the file was downloaded to desktop)
3.sudo -s
4.typed in "tar xvfz xampp-linux-1.7.4.tar.gz -C /opt"
5.started installing

to start xampp i've given the following cmd
/opt/lampp/lampp start 

to stop xampp use
/opt/lampp/lampp stop

---

