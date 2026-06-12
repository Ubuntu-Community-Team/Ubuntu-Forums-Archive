---
title: "Ubuntu default application problem"
date: 2011-03-19
forum: General Help
---

### Post by Isaacgallegos on 2011-03-19
**[COLOR="DarkSlateGray"]Background information:[/COLOR]**
So you know how we choose from a list what applications we want associated with a file type? It's a menu full of applications. 

I've filled mine with different applications I've reinstalled. There are many repeats of application names, with the only difference being most of them don't work. This is due to changing the installation location, via WINEPREFIX. No biggie. 

I'm also using Ubuntu 10.10. *It's very nice!*

**[COLOR="DarkSlateGray"]Problem:[/COLOR]**
How in the world do I get rid of these unwanted list items? It's very hard to find the ones that are good. 

**[COLOR="DarkSlateGray"]Plan B:[/COLOR]**
The easiest solution, so far, is to reinstall ubuntu and install these applications correctly the first time. Then I won't have all of those repeats. 

Thank you, thank you, and thank you for any help!

---

### Post by cottfcfan on 2011-03-19
If I understand your question correctly, find a file for eg, an ODT file. Right click on the file, click properties, click open with and pick the application you want to open that file and all your other ODT files. From there you can also delete all the other applications you don't want associated with that file.
You can repeat this with all different file types.
Hope this helps.

---

### Post by 5149.5 on 2011-03-19
Go to software center or package manager and uninstall the problem apps?

---

### Post by Isaacgallegos on 2011-03-19
Sorry. 
I meant this menu: (see attached) 
Only one out of all those repeats actually is pointing to the correct directory. There should be a way to remove the items that don't work/exist.

---

### Post by cottfcfan on 2011-03-19
Looks like the same menu in my last post.
Its strange you don't have the option to remove them, I do.
Maybe its because there Windows applications run in Wine.
Try the same thing as "root" and see if you can.

Edit.
No I see what you mean even as root you cannot remove applications from the "add applications"
menu, my list is quite large as well.

---

### Post by Isaacgallegos on 2011-03-19
I think this is a developer-grade problem and not something a general user, like me, will be able to solve...

---

### Post by tredegar on 2011-03-19
It's when you click ""Add", to add an application to open the selected file with.
You are presented with a list of applications, and most of them have duplications, triplications and in my case, okular is listed about 20 times (and I don't even use it).

Some list or database is corrupted.

---

### Post by cottfcfan on 2011-03-19
Is it such a big issue though.
Once you've set your default applications, you never need to look at that menu again.
To be honest its the 1st time ive noticed it.

---

### Post by grahammechanical on 2011-03-19
I see in that screenshot a Remove button. It is greyed out. What happens if you click the line that is selected? Does the Remove button become active?

Regards.

---

### Post by Isaacgallegos on 2011-03-19
> **cottfcfan said:**
> Is it such a big issue though.
Once you've set your default applications, you never need to look at that menu again.
To be honest its the 1st time ive noticed it.
Actually I just reinstalled MS Office and everything works great. I've just discovered that none of those items work, even though they used to. If I could somehow edit the file that populates that list I could fix the problem and click on a file to open it in the default applications. Currently I have to open Word then open the file with in word. I thought that at least one of them worked, but none do. 

> **grahammechanical said:**
> I see in that screenshot a Remove button. It is greyed out. What happens if you click the line that is selected? Does the Remove button become active?

Regards.

I've tried that and different things. Nothing removes the items. Can you on yours?

edit:
I know it seems silly to go through this trouble instead of using Libre Office or Open office, but MS Office is more stable under wine than those other programs are.

---

### Post by cottfcfan on 2011-03-19
Isaacgallegos,

Totally off subject, but how did you install MS Office?
I tried today as my daughter needs it for school, it appeared to install correctly using Wine 1.3.15, but everytime I clicked on word or excel etc it just came up with an error message "file not found"
Any help would be appreciated.

---

### Post by Isaacgallegos on 2011-03-19
> **cottfcfan said:**
> Isaacgallegos,

Totally off subject, but how did you install MS Office?
I tried today as my daughter needs it for school, it appeared to install correctly using Wine 1.3.15, but everytime I clicked on word or excel etc it just came up with an error message "file not found"
Any help would be appreciated.

Deleted my old Office installation by deleting .wine

I installed using a new prefix (New target directory like .wine, but a different folder) .MSOffice. 

$ export WINEPREFIX=~/.MSOffice

Important -- Applied library overrides:
set riched20 to native 
set usp10 to native, builtin 

I did not use winetricks for Office 2007

I installed using the CD and key on CD. 

I did not customize the installation. 

Once finished I went to my wine menu, from the main ubuntu applications menu, and clicked on one of my Office applications, MS Word. It then asked me to register my copy and I did.

Put wine prefix back to normal:
$ unset WINEPREFIX

---

### Post by cottfcfan on 2011-03-19
Thanks.
I'll try that tomorrow.

---

### Post by Isaacgallegos on 2011-03-19
> **cottfcfan said:**
> Thanks.
I'll try that tomorrow.

I've added some more information to my last post.

---

### Post by Isaacgallegos on 2011-03-21
Found out it was a bug: [http://forum.winehq.org/viewtopic.php?t=11558](http://forum.winehq.org/viewtopic.php?t=11558)
BUG - [http://bugs.winehq.org/show_bug.cgi?id=26505](http://bugs.winehq.org/show_bug.cgi?id=26505)

Patch was made by one of the admins. 

Marking this thread as solved.

---

