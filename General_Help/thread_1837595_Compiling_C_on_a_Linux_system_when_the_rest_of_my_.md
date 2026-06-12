---
title: "Compiling C on a Linux system when the rest of my class is doing it on a Windoze VM"
date: 2011-09-02
forum: General Help
---

### Post by ClientAlive on 2011-09-02
Hi,

I have a computer science class where we will be doing some basic C programming and compiling the code. Since my system is Linux (Ubuntu 10.04) and I really don't feel like the headache of switching back to Windoze just for a couple class projects - I asked the instructor and got permission to do it on my Linux system (but I have to do it all on my own, no support from them).

So I know I'll be using gcc in some capacity to compile whatever they have me do, but the question arose about the differences between Unix like systems and Windows systems and what's going to happen when I hand the project in and the instructor tries to check it. If I create it on my Linux system and she tries to run the thing on a Windows system I'm kinda getting that it won't work. (The whole thing about shared libraries on Linux and all that).

So I was wondering if anyone can help me understand the basic difference - no - also the way it works for Windows by comparrison; and how I might be able to work it so my finished product does work on a Windoze system even if I create it on this Linux system. Technically, according to the instructor, they will be working on a Windows VM and will be using Cygwin. What can I do?

Thanks in advance for any help.

---

### Post by wt8008 on 2011-09-04
The answer is: it depends.

It appears you are using cgywin in windows for C development. In this case, you should be fine, since cgywin provides a standard Unix like environment for programming, meaning if you take the code and go somewhere else it should just mostly work just fine.

You can work in Ubuntu, but I recommend before turning your assignment in, you should test your code in lab under the system your professor will grade your project. If you find some differences, it may be a learning opportunity for you of why.

---

### Post by arjunajith on 2011-09-04
You can use dosbox to run Turbo c++ compiler is ubuntu.
Works like a charm. If you need more help on this hit me back (not literally.. LOL).

And this of course has no difference from the windows version.

---

### Post by ClientAlive on 2011-09-05
> **wt8008 said:**
> The answer is: it depends.

It appears you are using cgywin in windows for C development. In this case, you should be fine, since cgywin provides a standard Unix like environment for programming, meaning if you take the code and go somewhere else it should just mostly work just fine.

You can work in Ubuntu, but I recommend before turning your assignment in, you should test your code in lab under the system your professor will grade your project. If you find some differences, it may be a learning opportunity for you of why.


> **arjunajith said:**
> You can use dosbox to run Turbo c++ compiler is ubuntu.
Works like a charm. If you need more help on this hit me back (not literally.. LOL).

And this of course has no difference from the windows version.


Sorry for going mia there for a while. I've just been swamped with stuff to do.

Actually, I'm a comp sci major and I'm in an introductory class "Computer Science I" where we will be writing in C and doing some basic stuff just to get familiar. The issue was that I run a Linux system (Ubuntu 10.04) and they're using Windows there. It's an online course and the campus is a little distance away from me and I don't have a way to just go there and use their lab. So I was trying to find a way to just compile in my, Linux system and have it work for them on their windoZ system. Now a couple things have changed since I wrote that op. I am still interested to learn the answer to a situation like that though - for future reference.

So one thing that's changed is that I installed Windows on my other machine (the beast, my desktop) so now I could use it to just follow along the way they're doing it. Another thing is that I learned more about what is expected (for this first project anyhow). What they are doing is having us install some 'client' on our computer at home that we use to access a Windows virtual machine on their server there. It is in that VM that we already have all the tools to do the project, already all set up for us. In the end we are merely to take a screen shot of the terminal with what commands we ran, and of the program running after it's been compiled, and submit that.

Our instructor is super super cool. For openers she welcomed me to do it on my Linux system but I'd have to figure it out on my own and would get no support. That sounded fine to me and the first thing I thought was "gcc." Then I thought maybe I'd end up with something they couldn't run or check on their system. It gets better though, When I looked at our checklist for this week last night, I saw that our instructor included a link to a client for Linux users, again with the disclaimer of 'no support' though. Talk about a neat instructor!

Anyway though. I'd like to learn more about cross compiling tools that are out there and what some good ones are. Stuff I can run in Linux but will spit out compiled programs for multiple platforms. Heck, if there was a compiler that did that and could run the jobs all at the same time that would just be ****! So if you guys have any suggestions about what's out there, easy to use, robust, fast, etc, etc, I'd love to hear about it. We will, however, only be working with C in this class - not C++ or C# or any of the other languages.


Thanks
Jake

---

### Post by wt8008 on 2011-09-05
As long as you get the linux VM client working, you should be fine. You can develop and test in Ubuntu, then move over to the VM running Windows ans cygwin. Since what you turn in is only a screen shot, that may not be necessary, but it may be a good practice to do it anyway for the experience. For an introductory class, I think you won't run into anything unusual.

Cross compiling: I don't know too much about this.

---

### Post by ClientAlive on 2011-09-05
> **wt8008 said:**
> As long as you get the linux VM client working, you should be fine. You can develop and test in Ubuntu, then move over to the VM running Windows ans cygwin. Since what you turn in is only a screen shot, that may not be necessary, but it may be a good practice to do it anyway for the experience. For an introductory class, I think you won't run into anything unusual.

Cross compiling: I don't know too much about this.


Right on. Jeeze, I'm so excited about this class and to get into this stuff. Coolest discipline on the planet!!

---

