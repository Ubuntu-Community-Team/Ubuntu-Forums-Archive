---
title: "Unrared tar.gz and ran install script...nothing happen"
date: 2009-11-24
forum: General Help
---

### Post by Cytochromec on 2009-11-24
I want to install Avira AV so I downloaded the linux version and extracted the folder from the tar.gz. Inside was a file called Install and the readme says it runs the install script. Ok, I double click it and click Run and nothing happens. I also tried Run in terminal, nothing. Something tells me there is a lot more to it than I first thought...

---

### Post by howefield on 2009-11-24
Does it need to be Avira ?

Some of the other popular AV programs have .deb files available for download, much easier to install.

---

### Post by Darael on 2009-11-24
I've found that sometimes, rather than choosing "run in terminal", it's a better plan to open up a terminal, cd to the folder, and run what in this case would be "./install".  Don't know why, but sometimes it works better.  Also, if you're installing software and it complains about not being root when you run it as above, try prefixing it with "sudo ".

One more thing - unless you're scanning to protect Windows boxes, you may like to know that the Wildlist, which lists all viruses currently "in the wild", shows that of all 900-odd viruses currently "out there" and active, every single one targets Windows.  Not that you can't write a Virus for unix-like systems such as Linux, but there aren't any active at the moment - and haven't been for months.

Not that there aren't good reasons to run an AV on your Ubuntu box - there are -  just thought you might like to know.

---

### Post by 3rdalbum on 2009-11-24
1. There are no viruses in Linux. You only need anti-virus if you want to try and protect Windows machines.

2. Linux will not execute a file unless you have given that file permission to be executed. You can do this in Nautilus (right-click and go to Properties) or you can type this command (but don't run it yet):

```
chmod a+x 
```

Put a space after the x, and then drag the file into the terminal. Now run the result (press Enter).

This gives the file execute permission. Now you need to run it. Drag it to the terminal again and press Enter to run it.

If the script you are trying to run is going to install the software to a system-wide location, then you need to run it as root. Put the word "sudo" into the terminal, add a space, then drag the file in.

---

### Post by Darael on 2009-11-24
> **3rdalbum said:**
> 1. There are no viruses in Linux. You only need anti-virus if you want to try and protect Windows machines.
Technically untrue - ever heard of Bliss?  However, the essence of what you're saying - that there are no viruses **to be concerned about** on Linux is quite correct, because those that have been written are no longer effective.  So there are no Linux viruses "in the wild".

Just a small point.

---

### Post by Cytochromec on 2009-11-24
> **3rdalbum said:**
> 1. There are no viruses in Linux. You only need anti-virus if you want to try and protect Windows machines.

2. Linux will not execute a file unless you have given that file permission to be executed. You can do this in Nautilus (right-click and go to Properties) or you can type this command (but don't run it yet):

```
chmod a+x 
```Put a space after the x, and then drag the file into the terminal. Now run the result (press Enter).

This gives the file execute permission. Now you need to run it. Drag it to the terminal again and press Enter to run it.

If the script you are trying to run is going to install the software to a system-wide location, then you need to run it as root. Put the word "sudo" into the terminal, add a space, then drag the file in.


Wow, thanks for this, it worked like a charm. I get an error updating the definitions, but that is unrelated to the help I asked for. 

As far as why I am installing it, I not only dual boot, but run into windows a lot so I rather not infect anyone by mistake. 

Thanks for everyones replies and help.

---

