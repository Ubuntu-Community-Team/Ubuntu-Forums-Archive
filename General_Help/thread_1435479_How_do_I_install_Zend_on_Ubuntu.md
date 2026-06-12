---
title: "How do I install Zend on Ubuntu?"
date: 2010-03-21
forum: General Help
---

### Post by unpresedented on 2010-03-21
dear all,
I want to install a program on my ubuntu, and forgive me because I'm new to linux world ...
when I was on Windows I just double click the executable file then press some NEXT buttons and then finish installation very easily ...
can i use the same way of windows to install programs in linux (i do not want apt get method coz i hate terminal and command line things) ... ?

---

### Post by hatalar205 on 2010-03-21
> **unpresedented said:**
> dear all,
I want to install a program on my ubuntu, and forgive because I'm new to linux world ...
when I was on Windows I just double click the executable file then press some NEXT buttons and then finish installation very easily ...
can i use the same way of windows to install programs in linux (i do not want apt get methos coz i hate terminal and command line things) ... ?

It is easy. 
Applications > Add/Remove Programs 
You don't need anything else.

---

### Post by Enigmapond on 2010-03-21
> **unpresedented said:**
> dear all,
I want to install a program on my ubuntu, and forgive me because I'm new to linux world ...
when I was on Windows I just double click the executable file then press some NEXT buttons and then finish installation very easily ...
can i use the same way of windows to install programs in linux (i do not want apt get method coz i hate terminal and command line things) ... ?

What programme are you trying to install? You won't be able to us a Windows programme unless it runs thru Wine...if it indeed can be run at all. Regarding the command line, you may want to get used to it. It is a faster way to both navigate and install/uninstall programmes. Just a thought.

---

### Post by wqawasmi on 2010-03-21
Since Ubuntu is debian based, you can download .deb packages and go through a nice and user friendly graphical install.

Also in Ubuntu 9.10, clicking the Applications tab, and then "Ubuntu Software Center" gives you a good choice of software. 

Getting used to the Terminal is a lot easier then you think, and you might need to get your hands dirty every now and then in Linux.

But don't worry, it becomes easy, and a snap to do :)

---

### Post by unpresedented on 2010-03-21
thank you for prompt reply, but that option is not listed in Applications !!! (appliactions ->add/remove programs) ..
also, the program that I want to install is commercial, its name is Zend Studio and it's only available on the Zend website, so basically, I have to visit their site, then download the package for linux, then double click that package and follow on screen instructions, is that right ?

---

### Post by Enigmapond on 2010-03-21
> **unpresedented said:**
> thank you for prompt reply, but that option is not listed in Applications !!!
also, the program that I want to install is commercial, its name is Zend Studio and it's only available on the Zend website, so basically, I have to visit their site, then download the package for linux, then double click that package and follow on screen instructions, is that right ?

It would depend on whether it's a .deb file or if it's a tarball (i.e tar.bz). If the first, yes just click and it will install. If the second then it gets a bit more complicated as it will need to be compiled.

---

### Post by wqawasmi on 2010-03-21
> **Enigmapond said:**
> It would depend on whether it's a .deb file or if it's a tarball (i.e tar.bz). If the first, yes just click and it will install. If the second then it gets a bit more complicated as it will need to be compiled.

Yes as he said, if it's a .deb then its an easy install.

A .tar.bz usually means some time in the terminal. 

Read the readme or INSTALL file that comes with the package and see how it goes.

But it's mostly just:

Extract files into a directory.

From terminal, do "cd ~/nameofdirectory"
./configure -optionsgohere
make
sudo make install

and your done!

That differs between programs.

---

### Post by aysiu on 2010-03-21
Are you sure it isn't in the repositories? ```
**apt-cache search zend**
libzend-framework-php - a simple, straightforward, open-source software framework for PHP 5
zend-framework - a simple, straightforward, open-source software framework for PHP 5
zend-framework-bin - a simple, straightforward, open-source software framework for PHP 5
zendframework - powerful PHP framework
zendframework-bin - binary scripts for zendframework
``` If it doesn't show up in Add/Remove (8.04 or 9.04) or Ubuntu Software Center (9.10), then you might want to try looking in System > Administration > Synaptic Package Manager

More info here:
[http://www.psychocats.net/ubuntu/installingsoftware#synaptic](http://www.psychocats.net/ubuntu/installingsoftware#synaptic)

---

### Post by Enigmapond on 2010-03-21
> **wqawasmi said:**
> Yes as he said, 
She...as she said...But I'll get over it...:D;)

---

### Post by cariboo on 2010-03-21
Double click the file you downloaded, and file-roller will open and ask you where you want to extract the *gz file. Extract it to a directory where you can find it again, next open an Applications->Accessories->Terminal and cd into the directory you extracted Zend Studio to. You have to make the .bin file executable so, at the prompt type:

```
chmod +x *bin
```

Once the file is executeable all you need to do is run it, you have to be root to install it so at the prompt type:

```
sudo ./*bin
```

The installer should open, and all you have to do is follow the prompts.

---

### Post by unpresedented on 2010-03-21
it's a commercial program so it won't be available in the list of software in ubuntu software center or syanptic package manager !! right ?
and how come that command line (terminal) is easier than the easy GUI ???!  
terminal means to read a lot and study a lot to learn new commands, and that's a big headache ..

---

### Post by unpresedented on 2010-03-21
> **cariboo907 said:**
> Double click the file you downloaded, and file-roller will open and ask you where you want to extract the *gz file. Extract it to a directory where you can find it again, next open an Applications->Accessories->Terminal and cd into the directory you extracted Zend Studio to. You have to make the .bin file executable so, at the prompt type:

```
chmod +x *bin
```Once the file is executeable all you need to do is run it, you have to be root to install it so at the prompt type:

```
sudo ./*bin
```The installer should open, and all you have to do is follow the prompts.

thank you this is a clear answer ...
but why all of this headache, when I was on windows it's a matter of single click and the application will install very easily without touching the command prompt (terminal) ... why extract .. then CD to that directory .. then .. then ... this is a complexity !!

---

