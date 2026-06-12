---
title: "True to Code Linux/Ubuntu"
date: 2010-02-09
forum: General Help
---

### Post by Aetixintro on 2010-02-09
I have an idea for Linux/Ubuntu.
Here, I'm thinking it can be useful to make slight alterations to the Ubuntu  system so that it generates a parallel logging process for  everything/selected processes. This can be terminal sessions, system to  UI firewall, system to browser, system to OSSEC, system to whatever. In  this way, learning Linux/Ubuntu can be inspiring and transparent and has  the possibility of generating greater interest and more developers to  the system. I certainly encourage this to be done!

(From [http://www.t-lea.net/various_designs.html](http://www.t-lea.net/various_designs.html).)

---

### Post by Nonno Bassotto on 2010-02-09
Can you explain better? It is completely unclear both what your goal is and how do you think to achieve it.

---

### Post by shriramrs31 on 2010-02-09
if u are just looking for a way to monitor what a process is logging / what function it is calling, there are lots of ways to achieve it.

system log will be a good start, dmsg also traps some. More indepth look requires debugging tools.

But you have to be more clear what you exactly have in mind ?

---

### Post by Aetixintro on 2010-02-09
It's meant to be done by simultaneously generating a standard text-type document where the code is displayed that runs the process in question. The whole "True to Code Linux" can very well be only an option in the OS, a program running at start-up or integrated in the system itself with parameters set for it. The created output of the feature shouldn't produce much size on the harddisk either, being only a kind of simple text-type. It should also generate a quick way of copying and pasting code one may find useful or perhaps a kind of code-lookup file. There should be many ways of incorporating this.

As a beginner with Ubuntu, at least with code, I find the use of code somewhat "demanding"/"time-consuming" until I'm properly familiar with it, which may take quite a long time (years?). But by this, you get the document produced and recorded where you can go back and pick up what has been used in the past.

Perhaps one can also incorporate a kind of option in it that marks the code you'd like to store for future uses in a new document (most conveniently building a code book of your most used codes, to the terminal or otherwise).

(I apologise to [COLOR=Black]shriramrs31 and Nonno Bassotto as this has been supposed to be directly under their posts in the threaded mode.)[URL="http://ubuntuforums.org/member.php?u=797921"]
[/URL][/COLOR]

---

### Post by Nonno Bassotto on 2010-02-09
I think we just mean different things by "code". Do you mean something like

```

class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}

```

or something like

```

find . -name '*.doc' ! -name Accounts*

```

?

---

### Post by tgalati4 on 2010-02-09
sudo apt-get install htop
htop

---

### Post by Aetixintro on 2010-02-09
Both!? I mean the actual code that runs. I see problems (obviously) with expressing code for a new process (starting the firewall) because it necessarily isn't displayed in the "parallel text registry (PTR)" in true time, but can rather be displayed as "firewall start-up [not true time]" then <next line of code>.

So yes, possibly all the code that's relevant both to the specific program and to the system in some limited way (because I do think there may be problems of getting it all shown in parallel text. The most promising may be in expression of selected processes, only one or a few at a time, but potentially **all**.

htop isn't it for this thread, but, yes, cool program: [URL="http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/"]http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/
[/URL]

---

### Post by Nonno Bassotto on 2010-02-09
No, the two examples are really quite different, and I am trying to understand what do you want.

The first example is the code of a program, specifically a simple Java program which only writes "Hello world".

The second example is a command you can type in a terminal to find files with certain restrictions.

Now the question is: do you want to see how to call in a terminal the programs which execute some actions, or rather do you want to see the actual source code of the programs?

---

### Post by Aetixintro on 2010-02-09
Why is there a problem of displaying a code that also displays what the code leads to, "Hello world"?

I want to see **all** the code running for a specific process. If you choose to display the terminal session and you type in something that initiates another process, then this other process requires another "display of code"/PTR.

This is the suggestion that all code is potentially displayed (and registered and recorded for later uses)! Yes?

---

### Post by mcduck on 2010-02-09
> **Aetixintro said:**
> Why is there a problem of displaying a code that also displays what the code leads to, "Hello world".

I want to see **all** the code running for a specific process. If you choose to display the terminal session and you type in something that initiates another process, then this other process requires another "display of code"/PTR.

This is the suggestion that all code is potentially displayed (and registered and recorded for later uses)! Yes?

Because the program code that your computer runs isn't any more in readable text format. It has been compiled into binary data that your computer can understand. 

You can insatll source code for any application from the Ubutnu repositories, but you can't actually run that code, it has to be compiled before your computer understands it. (with the exception of few interpreted programming languages like Python)

But I suppose the main point people have been made here is which one you want to learn? Source code hasn't really got anything to do with *using* a computer. It's only for *making* programs. While the commands you'd eexecute in a terminal are about you *using* programs. Only a minor part of people on these forums, for example, understand anything about programming. And even less of them would have any idea what's going on if you tried to show them source code from all the applicatiosn and the system itself. On the other hand many of use are more or less able to work with command line.

Besides, even trying to output all the data that's going on in the system (without the actual source code for the programs) would create an overwhelming stream of data, far too much for anybody to actually follow.

---

### Post by Nonno Bassotto on 2010-02-09
It seems you do not understand what code is. Try to clear your ideas.

---

### Post by Aetixintro on 2010-02-09
> Because the program code that your computer runs isn't any more in  readable text format. It has been compiled into binary data that your  computer can understand.Is there a problem with displaying the actual code **before** it is compiled? I think there should still be a fine possibility for carrying the project through by making displayed equivalents to the compiled computer/machine code language. Isn't this so?

Post #1:
> In  this way, learning Linux/Ubuntu can be inspiring and transparent and  has  the possibility of generating greater interest and more developers  to  the system.:D

---

### Post by Nonno Bassotto on 2010-02-09
The actual code fo the whole operating system is made up by thousands of files, not independent one of another, and programs are written in many different languages: C, Python, bash, C++, Java, Ruby to mention a few. Nobody can read all this stuff.

Moreover reading the source of a program you use is not simple task (and you can do it without having the system log everything for you). It may take months to actually understand the source code of a complex program, and by that time you are probably already trying to work on it.

I really think you are trying to ask something different, but I do not understand what.

---

### Post by mcduck on 2010-02-09
> **Aetixintro said:**
> Is there a problem with displaying the actual code **before** it is compiled? I think there should still be a fine possibility for carrying the project through by making displayed equivalents to the compiled computer/machine code language. Isn't this so?

Post #1:
:D

Just download the source code,a nd read through it.

The code ins't compiled on the fly when you run it (that would be really slow), any actually working program you install is already compiled into computer language.

And just to make it more clear how impossible viewing all the source code for all the programs as they run would be (if we ignore the performance question):

The very first thing that happens when you start Linux, is that the kernel is loaded into RAM. If it was in source code, that would be about 6 million lines of text. And loading it into RAM happens in a second or two. And that's before anything actually even starts working. There's absolute zero change that anybody would be able to even read those 6 million lines of tect scrolling through your display in a second, not to mention actually understanding anything about what's going on.

The thing is that your computer's processor is able to execute thousands of millions of commands per second. It's just not possible to view that in real time.

---

### Post by Aetixintro on 2010-02-09
I've tagged this thread with "code transparency" and I really think that it should be beneficial to have those 6 million lines, not in true time, but after you've logged on as a "code report [not in true time]". I agree to some objection, but there may be benefits of having ticked off an option in "True to Code Linux"-feature, you can have the review as you like, specified down to the process you like and all the rest. It may take very hard work, but I still think there are great rewards to be reaped by doing it this way, possibly, not necessarily. Cheers!

---

### Post by mcduck on 2010-02-09
> **Aetixintro said:**
> I've tagged this thread with "code transparency" and I really think that it should be beneficial to have those 6 million lines, not in true time, but after you've logged on as a "code report [not in true time]". I agree to some objection, but there may be benefits of having ticked off an option in "True to Code Linux"-feature, you can have the review as you like, specified down to the process you like and all the rest. It may take very hard work, but I still think there are great rewards to be reaped by doing it this way, possibly, not necessarily. Cheers!

You can have those lines of code. Like I've already said, the source code is available for you to read at yout own pace, all you need to do is download it.

And like I also already mentioned, it's not the source code that's actually running on your machine. And also following all the time all the data that's going on in running computer wouldn't create just some small text files, you'd get gigabytes worth of data every second. Far too much to be any use for any human, and far too much to be stored anywhere. (not to forget that doing such thing would slow down your computer to crawling speed too slow to be usable for any actual purpose any more).

---

### Post by Aetixintro on 2010-02-09
It's alright! I just like to share the idea with people that it may be nice to have the "code-equivalent" in a text-file, going one process at the time, carefully, and having the **possibility** to review **all** the processes in this fashion, by ticking off the option. It should come with great benefits.

---

### Post by wojox on 2010-02-09
> **Aetixintro said:**
> I really think that it should be beneficial to have those 6 million lines, not in true time, but after you've logged on as a "code report [not in true time]".

I really don't see anything beneficial in scrolling through 6 million lines of code.

---

### Post by Aetixintro on 2010-02-09
I see this possible specific uninterest, but think about the other processes, everyone of them, not in a pile of code in a dump of ".zip"/".tar"-file, but neatly put there, yours, (lovely) code report of "process X"! Mmm... yes, a cup of Ubuntu coffee!

---

### Post by lisati on 2010-02-09
I've been trying to follow the OP's questions and the answers. What I'm reading reminds me a little bit of the tools that a programmer uses to debug a program - source code in one window, with the current line highlighted, maybe another window monitoring the variables and other memory locations of interest, and another window with the output. Good if you're trying to figure out how a program works or what's gone wrong in a buggy program. Maybe not so useful if you just want to get on with using your computer.

---

### Post by Aetixintro on 2010-02-09
Why dismiss an idea from the outset? Let me just recommend you to leave the feature in the depository. :)

Besides, a debugger is primarily used to debug, not to review code of a process/program.

---

### Post by Nonno Bassotto on 2010-02-09
I'm starting to think you are trolling. :-(

---

### Post by lisati on 2010-02-09
> **Aetixintro said:**
> Why dismiss an idea from the outset? Let me just recommend you to leave the feature in the depository. :)

Besides, a debugger is primarily used to debug, not to review code of a process/program.

:lolflag: (+facepalm)

Edit: How is someone meant to debug code without reviewing it? Surely some of the same tools can be used.....

---

### Post by Aetixintro on 2010-02-09
Trolling? Absolutely not! I think it's pretty obvious that I'm wholly constructive here, by this.

Facepalm too? Oh no! They must think I'm stupid! :)

Leave my "religion" to myself if you're not interested... :)

---

### Post by Nonno Bassotto on 2010-02-09
Ok, sorry for being so harsh. The point that we are trying to make is that what you propose to realize is:

-not useful, as anyone can download the source of all open source programs if he so wishes
-not usable, because noone could possibly read a minuscule fraction of all that code. Indeed reading the source of a single program requires a lot of dediction
-not feasible, because it would slow down the computer in a major way, and would use a lot of gigabytes of hard disk space
-not easy to do, because it would involve having the sources of all programs organized in a standard way

---

### Post by Aetixintro on 2010-02-09
> -not useful, as anyone can download the source of all open source  programs if he so wishesUnderstood, but availability would increase somewhat and the threshold to investigate would be lowered.

> -not usable, because noone could possibly read a minuscule fraction of  all that code. Indeed reading the source of a single program requires a  lot of dedictionLet's say I would like to check up on the integration and possible improvements of ufw and GUI Firestarter (uh.. 1MiB + 4MiB?). Are you seriously telling me this would be to much for the system to process or myself to review?

> -not feasible, because it would slow down the computer in a major way,  and would use a lot of gigabytes of hard disk spaceAgain, check the example of ufw+Firestarter.

> -not easy to do, because it would involve having the sources of all  programs organized in a standard waySure, if the program is written in a crappy way, some may feel tempted to improve it. I can't see the descriptive problem, no matter what. Obviously, if one refuses, then it's up to someone else to "True to Code Linux"-it.

---

### Post by lisati on 2010-02-09
/me begins to get an inkling of where we're at.....

Are we looking at a scenario where we automate as much as we can of the checking that a program is functioning correctly? If so, there are one or two potential flys in the proverbial ointment, one of which is that it's difficult to write a program to verify the correctness of another program. See here: [http://ubuntuforums.org/showthread.php?p=7379756&#post7379756](http://ubuntuforums.org/showthread.php?p=7379756&#post7379756)

---

### Post by 3rdalbum on 2010-02-09
> **Aetixintro said:**
> Let's say I would like to check up on the integration and possible improvements of ufw and GUI Firestarter (uh.. 1MiB + 4MiB?). Are you seriously telling me this would be to much for the system to process or myself to review?

UFW is a Python program. It runs very briefly when you invoke it. You can use a Python debugger to step through the code.

Firestarter is, I believe, C or C++ source code. It is compiled to machine-readable form before it even reaches your computer. Firestarter depends on external libraries too, like GTK+, which are also precompiled.

If you can read and understand this:

```
less /bin/bash
```

then your idea has worth. If you can't understand it, then you should drop the idea.

---

### Post by john newbuntu on 2010-02-10
Remember that software and tools are abstractions.  I am pretty darn sure 99% of the people who use Nautilus, Amarok, Picasa etc are not interested in what happens behind the scenes.  What needs to be delivered is just the end product - play music, open files etc.  Like someone mentioned not all of us are programmers nor are they interested in running strace for each app.   Now, if you really need to understand the code, gdb or raw source code is our friend and that is freely available to us thank to linux. The author of these programs can probably alter the verbosity of these programs so that it helps us understand more about each function as the verbosity level is increased.

As an analogy, when I watch TV, I dont need to know how the tuner,  amplifier and LCD works and what its parameters are.  What ultimately matters is the video and audio delivered in perfect synchronization.  I do not need subtitles or a split screen mode telling me what is going on in the electronics on the TV except when there is a malfunction.  That's for the technician to understand.  Considering over 99% of the people who watch TV are common folks, this works.  Same with Ubuntu

---

### Post by lisati on 2010-02-10
> **john newbuntu said:**
> 
As an analogy, when I watch TV, I dont need to know how the tuner,  amplifier and LCD works and what its parameters are.  What ultimately matters is the video and audio delivered in perfect synchronization.  I do not need subtitles or a split screen mode telling me what is going on in the electronics on the TV except when there is a malfunction.  That's for the technician to understand.  Considering over 99% of the people who watch TV are common folks, this works.  Same with Ubuntu

Good analogy. Another one of my favourites (wish I'd remembered it earlier) is that I don't need to be a motor mechanic or understand all the workings of an internal combustion engine to enjoy driving a car or using public transport.

---

### Post by iponeverything on 2010-02-10
strace is a good way to get a very low level view of what process is doing. It is useful for debugging, but generates a ton of output. lsof is also very handy for getting a window into processes.

---

### Post by Aetixintro on 2010-02-10
I call this thread off for now. There's no need to address this "True to Code Linux" unless you have positive feedback/input.

iponeverything has cleared it with strace and lsof. In addition, there's probably a rich number of developer's tools to aid in reviewing and getting acquainted with the system code and code otherwise.

Thank you, everyone for your interest! :)

---

