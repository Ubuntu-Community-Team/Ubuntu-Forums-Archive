---
title: "How to compile I HATE the Cashew?"
date: 2009-09-14
forum: General Help
---

### Post by Slaskie on 2009-09-14
I downloaded I HATE the Cashew from [http://www.kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009](http://www.kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009) , and I tried to compile it using the instructions found here: [http://hanswchen.wordpress.com/2008/10/23/plasma-how-to-remove-the-cashew/](http://hanswchen.wordpress.com/2008/10/23/plasma-how-to-remove-the-cashew/)  . I had to use apt-get to install cmake as it was not on my 9.04 installation, and once I did that the compiling went fine, until this step:
# Now we’re ready to compile the plasmoid:

    cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..

    make

Upon inputting cmake -DCMAKE_INSTALL_PREFIX='kde4-config --prefix' into the terminal, the terminal responded with 

CMake Error: The source directory "/home/zachankiel/iHateTheCashew/build" does not appear to contain CMakeLists.txt.                                                                        
Specify --help for usage, or press the help button on the CMake GUI.

I really have no idea what to do now as this is my first time compiling a program and I was only copying the instructions to compile the widget into my terminal. Can any kind person lend me some help in ridding my computer screen of the cashew? Thank you.

---

### Post by Ayuthia on 2009-09-14
> **Slaskie said:**
> I downloaded I HATE the Cashew from [http://www.kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009](http://www.kde-look.org/content/show.php/I+HATE+the+Cashew?content=91009) , and I tried to compile it using the instructions found here: [http://hanswchen.wordpress.com/2008/10/23/plasma-how-to-remove-the-cashew/](http://hanswchen.wordpress.com/2008/10/23/plasma-how-to-remove-the-cashew/)  . I had to use apt-get to install cmake as it was not on my 9.04 installation, and once I did that the compiling went fine, until this step:
# Now we&#8217;re ready to compile the plasmoid:

    cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..

    make

Upon inputting cmake -DCMAKE_INSTALL_PREFIX='kde4-config --prefix' into the terminal, the terminal responded with 

CMake Error: The source directory "/home/zachankiel/iHateTheCashew/build" does not appear to contain CMakeLists.txt.                                                                        
Specify --help for usage, or press the help button on the CMake GUI.

I really have no idea what to do now as this is my first time compiling a program and I was only copying the instructions to compile the widget into my terminal. Can any kind person lend me some help in ridding my computer screen of the cashew? Thank you.

I have not yet tried this, but did you type:
```
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
```
The ` is a backquote instead of the single quote.  You also need to have the two dots at the end.  The backquote executes the command in the backquotes and replaces the information with the result of that command.  The .. refers to the previous directory.

---

### Post by Slaskie on 2009-09-14
I have gotten past the step specified by installing a variety of missing things, now when I type make I get

make: *** No targets specified and no makefile found.  Stop.

Blah.... Is there something simple I'm missing here?

---

### Post by Slaskie on 2009-09-14
Thank you so much Ayuthia!!!! I looked back in my terminal and it turns out I did not include the two periods after the command. Luckily, during this process I installed needed dependencies for cmake, so I deleted my iHateTheCashew folder and started anew, using the exact code, and whala, colored text when I typed make. Thanks very very much :D :D

---

