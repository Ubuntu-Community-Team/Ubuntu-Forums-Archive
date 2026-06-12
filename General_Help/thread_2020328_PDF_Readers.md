---
title: "PDF Readers"
date: 2012-07-08
forum: General Help
---

### Post by rickm1945 on 2012-07-08
What is recommended for a PDF reader? I used Foxit a free PDF reader that is excellent. Any suggestions  would be helpful.
Maybe one of the developers could take a look at Foxit, it is a really great reader, but it is only for Windoze at the present.

---

### Post by msammels on 2012-07-08
If you're using Ubuntu, the built in PDF reader (Eye of Gnome [EOG] I believe), is excellent. As for porting Foxit... challenge and a half :P Of course, there's always Adobe's original one.

---

### Post by rickm1945 on 2012-07-08
> **msammels said:**
> If you're using Ubuntu, the built in PDF reader (Eye of Gnome [EOG] I believe), is excellent. As for porting Foxit... challenge and a half :P Of course, there's always Adobe's original one.
EOG is installed but it is a Image viewer. Didn't say anything about PDF. I looked in Software Center and saw Adobe but don't think I really want Adobe.

---

### Post by msammels on 2012-07-08
Hmm... have you tried downloading a PDF and opening it? I was sure it was EoG... oh wait no it's document viewer! Ubuntu definitely has a PDF reader built in though.

---

### Post by Rexilion on 2012-07-08
Gnome's default document viewer is called 'evince' (which is 'gnome dumbed down' to 'document viewer') This piece of software is based on the modern and maintained poppler library which is capable of rendering like 99% of PDF's without issue's and it's fast!

I always use 'epdfviewer', it's also based on the poppler library but less memory hungry.

Using the original viewer is possible and works well. However, it takes almost 10 times more memory since it has nearly everything bundled with it to run. Which is considered bad in Linux world for many reasons.

You could also open pdf's in Gimp...

---

### Post by rickm1945 on 2012-07-08
> **Rexilion said:**
> Gnome's default document viewer is called 'evince' (which is 'gnome dumbed down' to 'document viewer') This piece of software is based on the modern and maintained poppler library which is capable of rendering like 99% of PDF's without issue's and it's fast!

I always use 'epdfviewer', it's also based on the poppler library but less memory hungry.

Using the original viewer is possible and works well. However, it takes almost 10 times more memory since it has nearly everything bundled with it to run. Which is considered bad in Linux world for many reasons.

You could also open pdf's in Gimp...
Ok thanks for the help, I used the Document viewer and it worked fine and it is already installed.

---

### Post by rickm1945 on 2012-07-08
> **Rexilion said:**
> Gnome's default document viewer is called 'evince' (which is 'gnome dumbed down' to 'document viewer') This piece of software is based on the modern and maintained poppler library which is capable of rendering like 99% of PDF's without issue's and it's fast!

I always use 'epdfviewer', it's also based on the poppler library but less memory hungry.

Using the original viewer is possible and works well. However, it takes almost 10 times more memory since it has nearly everything bundled with it to run. Which is considered bad in Linux world for many reasons.

You could also open pdf's in Gimp...
I think I will just use the document viewer. Thank you for your help.

---

### Post by rickm1945 on 2012-07-08
> **rickm1945 said:**
> I think I will just use the document viewer. Thank you for your help.
I sent Foxit an email and they have the basic version, which is the free  version. I downloaded it but I couldn't get it to install. here is  there Link:

```

```
[http://www.foxitsoftware.com/downloads/](http://www.foxitsoftware.com/downloads/)```

```
Would you check to see what download I should get and how to install the app. I downloaded the Linux Desktop version, tar.bz But I couldn’t get it to install.
```

```This is my return for attempted install.
richard@XPS8100:~$ cd Downloads
richard@XPS8100:~/Downloads$ sudo apt-get install FocitReader-1.1.0.tar.bz2
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package FocitReader-1.1.0.tar.bz2
E: Couldn't find any package by regex 'FocitReader-1.1.0.tar.bz2'
richard@XPS8100:~/Downloads$ 
```

```

---

### Post by Ambimom on 2012-07-08
Foxit has a linux version which I installed successfully.

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

It isn't as full-featured as the Windows version, but it does work.

Download the DEB Package for Ubuntu
 Open the terminal and  use the root account command for installation.
 sudo dpkg -i FoxitReader_1.1.0_i386.deb
 Please use the root account on terminal to execute the below command for uninstallation.
 dpkg -r FoxitReader

---

### Post by rickm1945 on 2012-07-08
> **Ambimom said:**
> Foxit has a linux version which I installed successfully.

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

It isn't as full-featured as the Windows version, but it does work.

Download the DEB Package for Ubuntu
 Open the terminal and  use the root account command for installation.
 sudo dpkg -i FoxitReader_1.1.0_i386.deb
 Please use the root account on terminal to execute the below command for uninstallation.
 dpkg -r FoxitReader
Thanks for the Help. I got it installed. It does work, but like you say not as full featured as the one for Windows. Too bad some of Ubuntu's developers couldn't cut a deal with the people at Foxit and get the full version for Ubuntu.

---

### Post by paulohora on 2013-01-21
Hello,

Does anyone know if Foxit can handle embedded mp3 into PDF files? Or if there's any PDF reader that have this feature?

I'm using Adobe for that matter, but it's insanely slow.

Ty all!

---

