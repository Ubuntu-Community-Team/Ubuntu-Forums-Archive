---
title: "Had a simple question i think"
date: 2010-04-12
forum: General Help
---

### Post by keithg67 on 2010-04-12
I wanted to know if ubuntu is like windows in that it has programs running in the background? for example in windows you can go to run type msconfig and kill start up programs. if there is could someone please tell me how to disable the ones I dont want running or let me know what program I can install to help me with this. Btw still learning linux so the dos for dummys version is best for me LOL.

Thanks for any info,
Keith

---

### Post by sam45 on 2010-04-12
> **keithg67 said:**
> I wanted to know if ubuntu is like linux in that it has programs running in the background? for example in windows you can go to run type msconfig and kill start up programs. if there is could someone please tell me how to disable the ones I dont want running or let me know what program I can install to help me with this. Btw still learning linux so the dos for dummys version is best for me LOL.

Thanks for any info,
Keith

I'm not very experienced with Linux but, 
In windows, I always had a high CPU usage.
Linux is different, you should get the system monitor to see it yourself (add it to your panel)
or, if you write "top" without the quotes in the terminal you will see which processes use cpu.
Linux sets most processes in sleep mode when they aren't used ;)

but to answer your question, yes linux has a lot of programs running in the background but I doubt it is safe or even possible to kill some of these..

---

### Post by Dhee on 2010-04-12
Indeed there is.  System > Preferences >Startup Programs.    (Might have to change "Startup Programs" to "Sessions" I haven't accessed my Ubuntu box in some time due to work....)    

From there it's simply unchecking boxes/adding new things.

---

### Post by c00lwaterz on 2010-04-12
i never heard of same msconfig in linux but I heard they use to kill some programs in terminal. or maybe use terminal to disable it?

---

### Post by 3rdalbum on 2010-04-12
There are two sorts of startup programs. One sort is where they start up on login. You can see these and edit them through System > Preferences > Startup Applications.

The other sort is ones that work across the whole system; these start up when your computer does. There's no easy way to edit these, as far as I know, in Ubuntu 9.10 and above.

The ones of more immediate interest to you will be the login items. However, you won't gain any noticable improvements in speed or RAM use by turning these off, they are pretty lightweight already. If you messed around with the true startup items (which is not easy) then you'd very probably break your system.

So, in short, yes there are background programs. But unless you have a real need, don't mess with them.

---

### Post by keithg67 on 2010-04-12
Ty for the reply's everyone like I said I am still very new to linux trying to read the manual but reading is not one of my strong points unfortunately, but yalls info was very helpful so thank you for the help.

Keith

---

### Post by JoelOl75 on 2010-04-12
In a terminal you can type "top" and kill programs from inside top

Or....  type ps -A and it will list all running processes which can be killed with with either:

kill (# of process)    or
killall (name of process)

You can use a pager so the list wont scroll off the bottom

ps -A | less

Hope this answers the question.  There are graphical solutions as were mentioned as well.

---

### Post by arnaudj on 2010-04-12
You can also give your terminal a shortcut, and run xkill so you can grafically kill the software you need to kill.
Also, there is `ps -elf` and for sure the powerfull top...
I think, if you need it to be graphic, you can take a look at:
[http://linux.about.com/cs/linux101/g/gtop.htm](http://linux.about.com/cs/linux101/g/gtop.htm)

---

