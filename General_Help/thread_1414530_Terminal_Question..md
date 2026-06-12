---
title: "Terminal Question."
date: 2010-02-23
forum: General Help
---

### Post by bullet311 on 2010-02-23
I am new to the terminal and somewhat new to Ubuntu.

Getting to the point-
Is there a point to using the terminal? 

Is there anything that you can do in the terminal that you can't do using the GUI?

What general purposes do people use the terminal for? 
     i.e. You can browse folders in the terminal, but for what purpose if you can use the folder system.

And lastly, I have heard using the terminal is faster. But is it really in your opinion?

Should I even take the time to learn all the commands?

Thanks,
Comment

Bull3t

---

### Post by nothingspecial on 2010-02-23
> **bullet311 said:**
> I am new to the terminal and somewhat new to Ubuntu.

Getting to the point-
Is there a point to using the terminal? 

Is there anything that you can do in the terminal that you can't do using the GUI?

What general purposes do people use the terminal for? 
     i.e. You can browse folders in the terminal, but for what purpose if you can use the folder system.

And lastly, I have heard using the terminal is faster. But is it really in your opinion?

Should I even take the time to learn all the commands?

Thanks,
Comment

Bull3t

You have this the wrong way round.

The question should be, should I bother learning where to click.

One small example - 

You have 800 mp3 files, 200 flac files and a folder named music containing the rest of your music in your home folder. You would like them all in a folder called Tunes.

```

mv {*.mp3,*.flac,music} Tunes/
```

would do that alot quicker than dragging and dropping........no?

That`s just a simple --throw away-- example, it get`s a whole lot better than that.

---

### Post by bodhi.zazen on 2010-02-23
> **bullet311 said:**
> I am new to the terminal and somewhat new to Ubuntu.

Getting to the point-
Is there a point to using the terminal? 

Is there anything that you can do in the terminal that you can't do using the GUI?

What general purposes do people use the terminal for? 
     i.e. You can browse folders in the terminal, but for what purpose if you can use the folder system.

And lastly, I have heard using the terminal is faster. But is it really in your opinion?

Should I even take the time to learn all the commands?

Thanks,
Comment

Bull3t

The command line is a very powerful tool and there are many applications / commands with no gui equivalent.

In addition many of the gui interfaces lack some or all of the command line options.

With that said, the command line is a tool, not a religion. Only you can decide if you wish to use this tool. 

IMO the vast majority of uses benefit from learning at least the basics of the command line, but certainly it is not for everyone. There are many users who never learn the command line.

When I teach Linux, I always include, where possible, a GUI solution as well as the command line approach.

See also :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by joep-vd on 2010-02-23
In my experience, using the operating system with browsing, writing, playing media et cetera all happens with mouse clicks. And maybe even the settings for some things. But something would get broken, or you have some more specific desires or demands over how your computer should behave, then the terminal becomes more and more handy. At first, I mostly did all by mouse, but in the terminal you can be quite a bit more sure of what is happening. You know kinda exactly what you're asking the system, and you also get more direct feed back from the system.

---

### Post by bullet311 on 2010-02-23
So do you guys think its all a matter of getting used to the terminal? 

Changing from the mouse after so long.

---

### Post by joep-vd on 2010-02-23
If you want to: Yes. Yet if you don't want to: No. 

But it really doesn't hurt to acquaint yourself a bit with the possibilities. 

And that will happen sooner or later if you would develop some special wishes on your computer, or if something is broken. For me that started with copy-pasting from this forum ;)

---

### Post by lyall on 2010-02-23
it all depends on want you want/need to do.

If is it all you want to do is surf the web, write a few notes, sent e-mails, watch a few movies, play some songs, etc. in general just use it how it comes.  Then you might not need to know how the use the command lines.

If you want to make the best of you system then using the command lines will help a great deal.

It mean that you have to learn, to make your system to be the best that it can be.

there is a warehouse of knowledge available, if you know how to use it


good luck and have fun learning

---

### Post by lyni on 2010-02-23
I agree with everyone else that you should use whatever feels comfortable for you.
but if you want to find out about the terminal here are a few links you might like to look at:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

just enjoy your linux system.

---

### Post by Miljet on 2010-02-23
When you make configuration changes using the GUI, you really have no idea what file, or files, are changed. Then if the change doesn't work out, it is sometimes difficult to get back to where you started.

On the other hand, if you use the terminal to backup and change a config file, you know exactly what was changed and it is very easy to reinstate the original file.

---

### Post by texaswriter on 2010-02-23
I also have to agree with the first replyer. I used to hate Command Prompt in Windows, how they had deprecated ALL the commands from original DOS. 

The command line has so much scripting ability, it's made insane. The simple fact that the majority of programs are accessible from the command line in one way or another, if not able to be ran entirely from the command line, means you can script and automate any given task. 

This is why I am trying to get into scripting... gonna go for learning python. 

YMMV though depending on your usage.

---

### Post by bullet311 on 2010-02-23
Thanks for giving me different perspectives everyone.

Thanks Lyni for the links!

This helped me a lot and I think I'll definitely start digging around in the terminal and see what trouble I can stir up. 
*[SIZE=1]and then fix it of course[/SIZE]*

bull3t

---

