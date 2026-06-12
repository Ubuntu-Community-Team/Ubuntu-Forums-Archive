---
title: "how do i download a c++ compiler?"
date: 2011-03-21
forum: General Help
---

### Post by btf18 on 2011-03-21
:guitar:Hi,

I need very exact instructions on how to do this as i cant seem to do it, on windows or ubuntu, and will give up and learn something else if i cant do it soon. I dont care what c++ compiler it is. I need to get it downloaded and ready to work in. Thanks heaps

---

### Post by WorMzy on 2011-03-21
Open a terminal (Application -> Accessories -> Terminal) and run ```
sudo apt-get install g++
```

This is how you use it: [http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html)

---

### Post by btf18 on 2011-03-21
Thanks, i'd already done that command. So i guess i have it. How do i open it?

---

### Post by wojox on 2011-03-21
> **btf18 said:**
> Thanks, i'd already done that command. So i guess i have it. How do i open it?

Click the link WorMzy posted. You don't open it, you write a program and call it to compile it for you.

---

### Post by btf18 on 2011-03-21
Thanks. Do i type my program into the terminal?

---

### Post by WorMzy on 2011-03-21
You write the code in a text editor, such as gedit, vim or nano. You then use the terminal, with the g++ command, to compile the code.

---

### Post by GregBrannon on 2011-03-21
Often, someone asking your question is really wondering how to get an Integrated Development Environment (IDE) or program(mer's) editor.  There are several available and have been discussed extensively in the Programmer's Talk sub forum here on UF.  Review the stickies in that sub forum and search/review the threads there for IDE discussions.

Good luck!

---

### Post by btf18 on 2011-03-21
Thanks. Do some compilers give you the development environment? Im happy with vim, im just doing this tutorial that made it sound like to the c++ compiler they told the viewer to download was also where you typed. 

Can you just glance over the code in this first tutorial and tell me if this can me typed into vim? So i would type it into vim, then do the command you said to compile? So i can use vim to type programs in different languages including c++? Then save them, then compile them, then they will be saved as an executable? Im just trying to get the big picture of what im doing. 

Thanks heaps

EDIT [http://www.guidetoprogramming.com/joomla153/beginning-programming-tutorials/16-c-tutorial-1](http://www.guidetoprogramming.com/joomla153/beginning-programming-tutorials/16-c-tutorial-1) <<<the tutorial. sorry xP

---

### Post by btf18 on 2011-03-21
Thanks Greg, awesome, i actually have been learning vim though so this will suffice, i just thought a compiler was also an environment similar to vim. Its all very confusing at first

---

### Post by wojox on 2011-03-21
Your link is for Borland C++. Use the link WorMzy showed you.

---

### Post by btf18 on 2011-03-21
Yes, done, borland was a huge set up process that failed. Can i type different languages into vim and use it to make programs in c++, c, etc as long as i compile them with the appropriate compiler? 

EDIT: and can i effectively do the tutorial i posted just above in vim?

thanks

---

### Post by wojox on 2011-03-21
[Check this out]("http://ubuntuforums.org/showpost.php?p=10586314&postcount=6") :P

---

### Post by btf18 on 2011-03-21
Thanks i definitely will, but im loving this tutorial ive been doing, please, answer my queries :-D spoon feed me. Believe me i need it

---

### Post by WorMzy on 2011-03-21
> **btf18 said:**
> Can you just glance over the code in this first tutorial and tell me if this can me typed into vim? So i would type it into vim, then do the command you said to compile? So i can use vim to type programs in different languages including c++? Then save them, then compile them, then they will be saved as an executable? Im just trying to get the big picture of what im doing. 

Thanks heaps

EDIT [http://www.guidetoprogramming.com/joomla153/beginning-programming-tutorials/16-c-tutorial-1](http://www.guidetoprogramming.com/joomla153/beginning-programming-tutorials/16-c-tutorial-1) <<<the tutorial. sorry xP

Yeah, that compiles for me. The thing to watch out for though is that different compilers may interpret the exact same code differently -- if you're following a tutorial for the Borland compiler, you may get errors when trying to compile it with the g++ compiler. So if you start getting errors later on in the tutorial, that may be why, despite the code being "correct".

You can use vim to write code for any language, C++, C, Python, Java, etc. Just like any text editor. So long as the code you write can be parsed by the compiler (or interpreter) it doesn't matter what you write it in.

---

### Post by btf18 on 2011-03-21
Thanks. It's not like im trying to focus on c++, i just want to learn to program, and this tutorial seems to be easing me into it. I have also been doing a shell tutorial including shell scripting, which is what got me to learn to use vim, but then i thought vim was mainly just for shell scripting and i just didnt know what language i was typing and ergh confusing. what language is shell scripting in? command line? is that a language? Im finding this tutorial on general programming in c++ etc easier to grasp.

Thanks heaps

---

### Post by WorMzy on 2011-03-21
Shell scripts are run in which ever shell you put in the shebang (the #!/path/to/shell you put on the first line); usually bash or dash.

e.g.
```
#!/bin/bash
echo hello
```
will run in the bash shell, whereas
```
#!/bin/dash
echo hello
```
will run in the dash shell.

Obviously in a simple example like this there's no real difference; but like compilers, shells are different and may not be able to run scripts written for another shell.

Note that, if you call a script with a shell, e.g.
```
bash script.sh
``` the script will run in that shell, and not the shell specified in the shebang. You should make the script executable and run it with
```
./script.sh
```
to make the shebang do it's job.

---

### Post by btf18 on 2011-03-22
Thanks. Whats a shebang?

---

### Post by WorMzy on 2011-03-22
Re-read the first sentence in my last post. :P

---

### Post by btf18 on 2011-03-22
Thanks

Ive written a program and called it demo1.cpp, now i compile it from the terminal, could you tell me what to type to compile? Then what to type to make it an executable, then run it? sorry its my first time writing a program.

---

### Post by WorMzy on 2011-03-22
Firstly, cd to the directory with the source code file, then run

```
g++ demo1.cpp -o demo1
```

Assuming all goes well, you should then be able to run the program with

```
./demo1
```

---

### Post by btf18 on 2011-03-22
Thanks. Unfortunately it didnt work so i tested again by making a demo2.cpp and again didnt work. I got this message:ben@ubuntu:~$ g++ demo2.cpp -o demo2
demo2.cpp:1: error: expected constructor, destructor, or type conversion before &#8216;<&#8217; token

Could you tell me what -o and demo2 do? i made the filename demo2.cpp so should it still only say demo2 at the end of the command?

Thanks heaps

---

### Post by WorMzy on 2011-03-22
The "-o filename" just tells the compiler what to call the compiled output file. If you didn't specify one, it'd output the file as a.out.

---

### Post by btf18 on 2011-03-22
Thanks. Do you have any ideas why its not working from what i showed you?

Also, i've noticed the shell in linux and mac is very similar, but windows it's completely different. Is linux using bash, and mac using dash perhaps, windows using...? this is just out of interest.

---

### Post by WorMzy on 2011-03-22
No idea, I'm afraid. I don't use C++. You're better off asking in the [development/programming subforum]("http://ubuntuforums.org/forumdisplay.php?f=310").

I don't use macs, so I couldn't tell you which shell OSX uses by default. If you have a mac handy, you may be able to find out by running ```
echo $SHELL
``` I dunno about Windows. I only use it for playing games. :P

---

### Post by btf18 on 2011-03-22
Thats all good. I think i will go to the programming forum as thats what im learning. I just googled it and mac uses bash! no wonder i was able to use the terminal on my friends computer xP Thanks for your help. I'll mark this thread as solved and check out the programming forum. cheers

---

