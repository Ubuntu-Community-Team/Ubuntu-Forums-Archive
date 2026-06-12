---
title: "Duh, you are missing libraries!"
date: 2010-09-03
forum: General Help
---

### Post by Tamber on 2010-09-03
I am new to linux still and don't know what I am doing. 

I tried to install a program, and couldn't seem to do it. (no error, nothing)

I asked some people, it went:

"I downloaded the program, extracted it, but when I try to run it it asks me what application I want to use to run it."
"Duh, you are missing libraries."
"How do I find WHAT libraries I am missing."
"I dunno."

So that is where I am at. How, on my own, do I figure out what libraries I need to run it? I would rather not simply post the program and get the answer, as I am sure I will run into this again.

Thank you.

---

### Post by CharlesA on 2010-09-03
How did you install the application?

---

### Post by FinalShot on 2010-09-03
Well for one, you should install all applications through the software center. Pretty sure it will install everything that is required for it.

---

### Post by Tamber on 2010-09-03
> **CharlesA said:**
> How did you install the application?

I have not installed it, I have only downloaded it. I am trying to run the installer. 

> **FinalShot said:**
> Well for one, you should install all applications through the software center. Pretty sure it will install everything that is required for it.

I do when possible, but not everything is available through there.

---

### Post by lordhaworth on 2010-09-03
Do you get any messages when you try and install it - if so post them here

---

### Post by lordhaworth on 2010-09-03
> 

I tried to install a program, and couldn't seem to do it. (no error, nothing)



Oops sorry, how did you try and install it then? What commands?

---

### Post by CharlesA on 2010-09-03
> **Tamber said:**
> I have not installed it, I have only downloaded it. I am trying to run the installer. 

What are you trying to install?

---

### Post by Tamber on 2010-09-03
> **lordhaworth said:**
> Do you get any messages when you try and install it - if so post them here

As mentioned before, I don't. 

When I attempt to run the installer it asks me what application I want to open it with.

---

### Post by Tamber on 2010-09-03
> **lordhaworth said:**
> Oops sorry, how did you try and install it then? What commands?

No commands, I am simply double clicking on the installer that came with the program after extracting it.

---

### Post by Vaphell on 2010-09-03
what is the name of the file?

---

### Post by Tamber on 2010-09-03
> **Vaphell said:**
> what is the name of the file?

I am avoiding saying the exact files due to not wanting a "Step 1, 2, and 3 solution". I want to be told how to solve the problem so I can deal with it in the future without help.

I am running into this issue with three programs.

1. Dwarf Fortress
2. Chocolate-Doom
3. Whatpulse - I actually found out I needed the "Qt4" libraries for this to work. But this was just a "1, 2, 3" solution I got. How do I actually figure out what libraries I need, since they never are included?

As mentioned, I don't just want a solution, I want to be able to fix it in the future.

---

### Post by Vaphell on 2010-09-03
i was more interested in the file extension - sources in tarball, .bin, .deb each have a fairly standard procedure

---

### Post by Tamber on 2010-09-03
> **Vaphell said:**
> i was more interested in the file extension - sources in tarball, .bin, .deb each have a standard procedure

Well, when I right click and select properties it says "Type: executable (application/x-executable)", if that isn't it then I don't know how to tell. There is no ".bin" or ".deb" on the end of the files.

Edit: more accurately, there is no extension visible in the file name at all.

---

### Post by CharlesA on 2010-09-03
It looks like you need to install it from source, since the file I found was .tar.bz2.

---

### Post by tad1073 on 2010-09-03
what is the file type? .tar.gz, .deb

---

### Post by Tamber on 2010-09-03
> **CharlesA said:**
> It looks like you need to install it from source, since the file I found was .tar.bz2.

How do I do that, and what files are you talking about?

Edit: Oh, the dwarf fortress. I've already extracted it, I know how to do that much. But I cannot run it. THe file you need to actually RUN the program has no extension from my view.

---

### Post by tad1073 on 2010-09-03
> **Tamber said:**
> Well, when I right click and select properties it says "Type: executable (application/x-executable)", if that isn't it then I don't know how to tell. There is no ".bin" or ".deb" on the end of the files.

Edit: more accurately, there is no extension visible in the file name at all.

you can right+click the file and select "Extract Here"

then you need to open the file in a terminal....eg. cd "/location/filename/" w/o the quotes of coarse

then issue the command "./configure" then make, and lastly "sudo make install" w/o the quotes of coarse

---

### Post by Calash on 2010-09-03
If it is a tarball it should still open in the archive manager if you double click on it, assuming something is not wrong with your install.

I am assuming you downloaded a file.  Did you open the file and decompress anything or is this the file you got from the site?

As noted above it really depends on the type of file you got. .DEB files are comparable to .msi files in Windows, self installing archives that will take care of everything for you.  .tar.bz is more likely source code, so you will have to go to the terminal and compile the application.  Some, like a .py or .bin, just need you to mark it as inscrutable or run it from the command line with a ./ before the file name.

If you cannot see the extension in the GUI try opening the terminal and do a 'ls' command.



For Dwarf Fortress, download the archive and extract it to your home folder.  Open a terminal and type the following

```

cd df_linux
./df

```

The file has no extension but looking at it and the readme files shows that it is a shell script.

---

### Post by alaukikyo on 2010-09-03
From what i gather you are trying to run an installer which is not executable
so click properties then permissions and tick allow exceting the program and then double clcik it and click run in terminal(so any error messages are recorded) and follow on-screen instructions

---

### Post by Tamber on 2010-09-03
> **tad1073 said:**
> you can right+click the file and select "Extract Here"

then you need to open the file in a terminal....eg. cd "/location/filename/" w/o the quotes of coarse

then issue the command "./configure" then make, and lastly "sudo make install" w/o the quotes of coarse

This both doesn't work and is exactly the kind of explanation I was trying to avoid. 

> **Calash said:**
> If it is a tarball it should still open in the archive manager if you double click on it, assuming something is not wrong with your install.

I am assuming you downloaded a file.  Did you open the file and decompress anything or is this the file you got from the site?

As noted above it really depends on the type of file you got. .DEB files are comparable to .msi files in Windows, self installing archives that will take care of everything for you.  .tar.bz is more likely source code, so you will have to go to the terminal and compile the application.  Some, like a .py or .bin, just need you to mark it as inscrutable or run it from the command line with a ./ before the file name.

If you cannot see the extension in the GUI try opening the terminal and do a 'ls' command.

Yes, it came in a compressed format, and I have extracted it. That is simple enough. 

Now, the program itself, is what does not show an extension. It still doesn't show an extension in the terminal.

---

### Post by Tamber on 2010-09-03
> **alaukikyo said:**
> From what i gather you are trying to run an installer which is not executable
so click properties then permissions and tick allow exceting the program and then double clcik it and click run in terminal(so any error messages are recorded) and follow on-screen instructions

It appears to be ticked by default.

---

### Post by Vaphell on 2010-09-03
dwarf fortress available is a standalone, ready to use app which is somewhat surprising

you simply run it with **./df** or **sh df** (at least it was enough on my copy)

but usually tar.gz files have sources inside and then you usually do ./config, make, sudo make install combo

---

### Post by Calash on 2010-09-03
> **Vaphell said:**
> dwarf fortress available is a standalone, ready to use app which is somewhat surprising

you simply run it with **./df** or **sh df** (at least it was enough on my copy)

but usually tar.gz files have sources inside and then you usually do ./config, make, sudo make install combo

Chocolate Doom is like this.  The archive is source code and you will need to compile it.  Usually the instructions above, typed while in the root directory, are all you need to get going but each application can be different.  Check out the readme files if you hit any snags.

---

### Post by Tamber on 2010-09-03
> **Vaphell said:**
> dwarf fortress available is a standalone, ready to use app which is somewhat surprising

you simply run it with **./df** or **sh df** (at least it was enough on my copy)

but usually tar.gz files have sources inside and then you usually do ./config, make, sudo make install combo

Finally, an error I can post.  >.<   (pretty bad when I get excited over an error, eh?)

I attempt to run it in a terminal, since I cannot click on it. I get...

"./lib/Dwarf_Fortress: error while loading shared libraries: **libSDL_image-1.2.so.0**: cannot open shared object file: No such file or directory"

Leading me back to the question I have been trying to ask this while time, how to I figure out what library files I need? How can I find out ON MY OWN? That way I wont have to ask next time.

edit: lol, this is why I shouldn't stay up for multiple days. Should the terminal always tell me what ones I am missing?

---

### Post by Calash on 2010-09-03
> **Tamber said:**
> Finally, an error I can post.  >.<   (pretty bad when I get excited over an error, eh?)

I attempt to run it in a terminal, since I cannot click on it. I get...

"./lib/Dwarf_Fortress: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory"

Leading me back to the question I have been trying to ask this while time, how to I figure out what library files I need? How can I find out ON MY OWN? That way I wont have to ask next time.


You do just what you did now.  Type it in the terminal and then do some searching for that library to see what you have to install.  Try dropping that library name into synaptic and see if anything comes up.  Failing that Google the entire error line with the word "Ubuntu" at the end and see what you can find.

You also check the providers documentation and see what they need.

And if all else fails you come here and ask, that is why so many of us hang out here, so we can help people out :)

---

### Post by Tamber on 2010-09-03
> **Calash said:**
> You do just what you did now.  Type it in the terminal and then do some searching for that library to see what you have to install.  Try dropping that library name into synaptic and see if anything comes up.  Failing that Google the entire error line with the word "Ubuntu" at the end and see what you can find.

You also check the providers documentation and see what they need.

And if all else fails you come here and ask, that is why so many of us hang out here, so we can help people out :)

I can't believe I sat there and typed out the library name I was missing, then needed to ask what library I was missing. -_-

Anyway, thank you for the help. Assuming I actually retain any of this, this knowledge should really help me in the future. 

By the way, is a library file more or less a .dll file?

---

### Post by Vaphell on 2010-09-03
yes
DLL = dynamic-link **library** :-)

---

### Post by oldos2er on 2010-09-03
> **Tamber said:**
>  How can I find out ON MY OWN?

Read README.Linux.

> **Tamber said:**
> By the way, is a library file more or less a .dll file? 

In Linux they are lib* files.

---

