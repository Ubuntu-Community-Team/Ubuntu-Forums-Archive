---
title: "Installing Movie Magic Screenwriter 6"
date: 2010-05-23
forum: General Help
---

### Post by JustSteph on 2010-05-23
Hi
I'm a very new Linux user (I have Ubuntu 10.4) and am trying to install Movie Magic Screenwriter 6 from the software disc but I'm getting the error message "Error autorunning software. Cannot find the autorun program". I think it's a Linux compatible program as it says "Universal" on the box. Please help?
Thanks
Steph

EDIT: I've managed to install it but it gets stuck on "waiting for response from server" when I get to the activation stage, even though my computer is connected to the internet. Anyone have any ideas why?

Or, since it's installed and activated perfectly on my Windows partition, is there any way to get it to open in from there in Ubuntu?

---

### Post by howefield on 2010-05-23
Think you might be wrong there, "Universal" most likely doesn't refer to the specifications required to run the program.

Movie Magic Screenwriter 6 (PC & Mac)
Platform:    Windows NT / 98 / 2000 / Me / XP / 95, Mac

It may run with Wine, have a look at the wine database to see if anyone has tried it.

---

### Post by JustSteph on 2010-05-23
Wine?
Sorry, I'm very new at this.

---

### Post by howefield on 2010-05-23
Wine is a program that allows you to run certain Windows applications in Linux. By no means all Windows applications run, hence the database at

[http://appdb.winehq.org/](http://appdb.winehq.org/)

I'd suggest you might look for a native linux alternative for your application, failing that have a look at Virtualbox if you have a spare Windows disk and licence, next on the list for me would be to look at Wine.

Another option would be to dual boot Windows and Ubuntu if none of the above suit.

---

### Post by Zemblan on 2010-05-23
Basically this program will only run on windows or mac. However it is possible to get some windows programs to run in Linux using 'wine' which is an emulation layer (pretends to be windows sort of.) You can install it using the software centre, search for wine. 
Alternatively you could install VirtualBox, and create a windows virtual machine to run it on.

Edit: If I could figure out how to delete this I would, repeats less well what the post above says.

---

### Post by llamabr on 2010-05-23
Yes, wine is almost never the correct solution.  I'm not familiar with this software, but it looks like it's sort of a template for writing screen plays?  Seems expensive -- unless it does something else important that you need.  If so, what?  Maybe we can point you toward another native app?

Otherwise, LaTeX has a movie script environment, though LaTeX has a pretty high learning curve.  Once you know it, however, you'll never go back to working with the likes of Word of OpenOffice to making presentation quality documents.

Also this post:
[http://ubuntuforums.org/archive/index.php/t-552883.html](http://ubuntuforums.org/archive/index.php/t-552883.html)
agrees with me, and also suggests something called celtx:
[http://celtx.com/](http://celtx.com/)
[http://en.wikipedia.org/wiki/Celtx](http://en.wikipedia.org/wiki/Celtx)

Have a look, and let us know what you think.  It doesn't look like it's in the archives, but we could probably help you install it.

---

### Post by JustSteph on 2010-05-23
I think I'll just go back to Windows XP. Ubuntu's been throwing up problems since I installed it. I've spent more time trying to fix it than I have using it.

---

### Post by howefield on 2010-05-23
> **JustSteph said:**
> I think I'll just go back to Windows XP.

Sounds like a solution.

Good Luck.

---

### Post by JustSteph on 2010-06-16
I've managed to get it to install, but when I get to the activation stage, it gets stuck on "Waiting for response from server". Anyone have any idea why?

---

### Post by JustSteph on 2010-06-17
Anyone?

---

### Post by timgood on 2010-06-17
I use CeltX - it's better than MM6, open source and free. Try it out.

---

### Post by JustSteph on 2010-06-17
Thanks, but I'd rather use MM6 since I paid £160 for it and I already have loads of stuff saved in the MM6 format.

It's already installed, it just can't seem to find the server so I can activate it.

---

### Post by JustSteph on 2010-06-20
:confused:

---

### Post by ronnielsen1 on 2010-06-20
The only ones I can find fro Movie Magic are
The demo
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11805&iTestingId=25196](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11805&iTestingId=25196)
and 2000 version
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2905](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2905)

> It's already installed, it just can't seem to find the server so I can  activate it. 	
Might need to setup networking in wine?
> Thanks, but I'd rather use MM6 since I paid £160 for it and I already  have loads of stuff saved in the MM6 format.

[http://celtx.com/](http://celtx.com/)
[http://wiki.celtx.com/index.php?title=Import_Script#Importing_from_Movie_Magic_Screen_Writer](http://wiki.celtx.com/index.php?title=Import_Script#Importing_from_Movie_Magic_Screen_Writer)
> **Importing from Movie Magic Screen Writer**

 Users of Movie Magic Screen Writer will want to save their scripts  using the 'Formatted ASCII' format found under 'File -> Save As' for  Windows. 
On a Mac:  
 
[LIST]
[*] In MMSW, cancel Page Numbers in the 'Format -> Header and  Footer, by removing the #. in the Header #1 box.
[*] If trying to convert a stageplay, replace all "ACT" titles  with scene headings ("INT." and so forth)
[*] Also ensure that all elements are separate (e.g.,  parentheticals are not in dialogue)
[*] Select 'File -> Export To', then select the 'Avid Editor  Format' from the file type drop down menu.
[*] Open BBEdit or TextWrangler (or somesuch)
[*] Load the file you just exported
[*] In TextWranger, select 'Text -> Zap Gremlins' with non  ASCII set to 'Delete'
[*] Delete all spaces before first element
[*] Re-save the file
[*] Import the resulting file into Celtx
[/LIST]


---

### Post by JustSteph on 2010-06-20
> **ronnielsen1 said:**
> Might need to setup networking in wine?

How do I do this?

Thanks.

---

### Post by ronnielsen1 on 2010-06-20
Sorry, was recently playing with VirtualBox XP

I'll download the demo and see if I can figure out something. If you have a nice computer, you might also consider running xp in virtualbox like another poster suggested or check out latex or celtx. Will post back when I figure something out.

---

### Post by JustSteph on 2010-07-14
Thanks everyone.

Just to let you know, I've solved the problem. I upgraded from wine 1.1.42 to 1.2-rc7 and it let me activate. It's all running now :D

---

