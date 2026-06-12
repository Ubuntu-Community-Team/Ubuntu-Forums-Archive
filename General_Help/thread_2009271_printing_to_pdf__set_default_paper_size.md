---
title: "printing to pdf / set default paper size"
date: 2012-06-24
forum: General Help
---

### Post by s2n6 on 2012-06-24
Hi,

I have just set up precise pangolin. I don't want to install printers, but I want to be able to print to pdf ("print to file"). This all works, but I cannot set the *default* paper size when printing to pdf.

Where can I adjust this? The system settings printer dialog does not show any printers as I didn't install any. However, the printer dialog in the application (e.g. firefox) allows me to print to a file with some default settings.

thanks in advance!

---

### Post by Ambimom on 2012-06-24
Open terminal and type:

***sudo apt-get-install cups-pdf***

If you're familiar with pdf creator for Windows, cups-pdf works in the same way.  It appears as a printer choice and will give you options to configure.

Note:  Once you print to pdf, you have to look in your home folder for a file named 'PDF."  This is where you'll find your pdf document.  Unlike a regular printer (or Windows version of PDF creator) there's no icon or other indication showing that anything has been printed.

---

### Post by gordintoronto on 2012-06-24
When I select "print to file," there is a tab labelled "Page setup." Within it, I can set the paper size. Do you see something different?

---

### Post by raja.genupula on 2012-06-24
> **gordintoronto said:**
> When I select "print to file," there is a tab labelled "Page setup." Within it, I can set the paper size. Do you see something different?

+1 , image i am adding

---

### Post by s2n6 on 2012-06-25
Thank you for the responses so far, but these do not solve my problem:

@Ambimom

This is a solution indeed. But not the one I'm looking for. What I mean is the following. There is an option already to print to a file even without cups being installed. The question was, "where can I set the defaults for the first", and not "what other programs let me do this"? Although your solution works and I appreciate you suggest it, it involves replacing the already available print to file solution, which I find cumbersome for a system claiming to be user friendly (not trying to flame here, I'm a heavy linux user already from the beginning of the nineties). If I don't have a clue how to set this easily why should my non-tech mom have an idea (and yes she prints to files every now and then) ;)

@gordintoronto @raja.genupula

I appreciate your enthusiasm, but you should read the question before trying to answer it. Although I think my question was clear, I adjusted  it a little for the sake of clarity.

---

### Post by oliverjames on 2012-06-25
> **s2n6 said:**
> Thank you for the responses so far, but these do not solve my problem:

@Ambimom

This is a solution indeed. But not the one I'm looking for. What I mean is the following. There is an option already to print to a file even without cups being installed. The question was, "where can I set the defaults for the first", and not "what other programs let me do this"? Although your solution works and I appreciate you suggest it, it involves replacing the already available print to file solution, which I find cumbersome for a system claiming to be user friendly (not trying to flame here, I'm a heavy linux user already from the beginning of the nineties). If I don't have a clue how to set this easily why should my non-tech mom have an idea (and yes she prints to files every now and then) ;)

@gordintoronto @raja.genupula

I appreciate your enthusiasm, but you should read the question before trying to answer it. Although I think my question was clear, I adjusted  it a little for the sake of clarity.

I'm experiencing frustrations with pdf printing also but mine are different, I have installed a pdf printer via CUPs and can't get the damned thing to print. Curious that this seems to be such an issue in (X)ubuntu, simply solved in Windows, Fedora, Mint, Puppy ...

Anyone found a solution for this?

---

### Post by teamanx on 2012-11-29
Probably you already solved it, but here is the way to set the system-wide paper size.

Open a terminal and type
```
sudo gedit /etc/papersize
```
After entering your password, it will open for you a text editor with the file that sets the system-wide paper size. Just change it to the setting you prefer (a4, letter, etc.).

---

