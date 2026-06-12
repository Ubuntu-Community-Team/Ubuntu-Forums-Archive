---
title: "why is my laptop always warm???"
date: 2010-09-23
forum: General Help
---

### Post by Sialis on 2010-09-23
Hey Guys ,
I have worked on ubuntu from 8 days ago and I really enjoy it until now :P
at first I want to say hi to all
and then ,I have an important problem (it might be about my knowledge) .
anyway when I'm on windows my laptop works normal(fans)and its temperature is normal until I play a Game !
but on ubuntu my laptop is always warm and fans work .
please guide me ....

ps : My laptop : Dell Studio 1555 

thx

---

### Post by bryanfblareunion on 2010-09-23
I HAVE THIS SAME PROBLEM!!! I would love to know what happens. I use Windows 7/Ubuntu Lucid dual boot. When I'm on Windows 7, everything is cool. Air coming out the side is almost room temperature and not much warmer. On Ubuntu, my whole laptop is warm. It's not "hot" to a point of concern, but I'm thinking that the raised temperature for a long period of time could be harmful. 

I hope somebody can help us!!!

---

### Post by rgiles43 on 2010-09-23
Hello,

You may want to check your logs to see if anything is using up your cpu, memory, or even HD. Laptops tend to run alot warmer then just a desktop. I would suggest checking your logs to see if maybe your resources are being used up because that will cause your laptop to get hotter. 

Another thing you may want to check is your fan speed in the bios. You could set the speed to max if not already set to try to keep things more cool. 

I hope this helps you out, as I am still a noob. HAHA


Thanks,

---

### Post by bryanfblareunion on 2010-09-23
Thanks. I'll try that.

---

### Post by 3Miro on 2010-09-23
There is a variety of things that could be going on. Check for those in any order that you want.

1. Ubuntu comes by default with a lot more visual effects enabled and GPU heats more then CPU almost always. Try disabling some of the effects, or all effects altogether.

2. Go to System -> Admin -> System Monitor and make sure you don't have some rogue process taking 100% CPU that is causing the laptop to work more than needed.

3. Install sensors applet from the Ubuntu Software Center and check out the actual temperature. All OS lower the fan when the CPU is idle, maybe Ubuntu is lowering it a bit more. As long as things don't get too hot on full system load, you should be fine.

4. A friend once installed a wallpaper that he thought looked cool, however, it was using heavy OpenGL and it was causing his Intel video card to overheat.

---

### Post by Sialis on 2010-09-23
thx I'll try too :)

---

### Post by Sialis on 2010-09-23
when I was trying to do your suggestions I encountered with another problem :D :D :D  sorrY i'm nooooob .
I can't find some programs that I install them from ubuntu software center , I look for them on application and system menu but 
I can't find  :P  (ex:sensors applet)

where are themmmmmmmm?!   :D

---

### Post by bryanfblareunion on 2010-09-23
Have you tried the synaptic package manager? Installed programs show up with a filled in box to the left of the package name. you can uninstall or whatever from there.

---

### Post by s0rc3r3r on 2010-09-23
I think you have to go to the Terminal  and issue 'Sensors' command

hope this helps
[https://wiki.ubuntu.com/SensorInstallHowto](https://wiki.ubuntu.com/SensorInstallHowto)

---

### Post by 3Miro on 2010-09-23
> **Sialis said:**
> when I was trying to do your suggestions I encountered with another problem :D :D :D  sorrY i'm nooooob .
I can't find some programs that I install them from ubuntu software center , I look for them on application and system menu but 
I can't find  :P  (ex:sensors applet)

where are themmmmmmmm?!   :D

The applets are not separate commands. Right-click on a panel and select "Add to Panel". Then you will get a list of applets that you can choose from.

---

### Post by Sialis on 2010-09-23
it worked :D  ty guys 
but i still have the first problem :(

what have I done?
1.run system monitor to check the process 
result : I didnt have any process with taking 100% cpu or something close to it.

2.remove wallpaper :(

3.also I unistall a program that it used openGL(cairo-dock)

4.set appearance preferences--> visual effects on none.

5.install hardware sensor monitor and check result 
result:
[IMG]http://yfrog.com/jp57308270p[/IMG]

what do u think now?   

ty

---

### Post by 3Miro on 2010-09-23
The screenshot did not post. On my laptop my CPU idles in the range 42C - 48C. Under full load, it goes to 65C. This is an Intel Pentium Dual Core (nothing fancy). 48C is somewhat high for idle, but low 60s is OK under full load. So I don't think it is a problem (in my case).

You can check both the bios as well as Ubuntu for ways to manage the fan. You can try to see if Ubuntu and/or Windows is having the fan blow more air and perhaps you can set Ubuntu to do that (I am actually not entirely sure how this can be done).

BTW, remving the wallpaper was an overkill, please put it back on ;). You can also hit Alt + F2 then type "gconf-editor" and select Apps -> Metacity -> General and enable the simple "compositor", which will let you run Docky without setting "Normal" effects. No effects use "Metacity", normal and higher effects use "Compiz". If this has no effect on temperature, you can just turn them back on.

---

### Post by TBABill on 2010-09-23
Easy fix sometimes is to:
1. Enable to Gnome applet on the upper panel. Right click the panel, click add to panel and select CPU frequency scaling monitor. Once enabled, left click the new applet and select ondemand. This throttles your CPU back to about half speed unless demand need more, then it jumps as needed.

2. Biggest problem is usually the open source graphics driver. If you have ATi or nVidia, make sure you are using the proprietary driver for your machine. You'll see huge improvements.

3. Make sure you are using Sun Java, not Open Java. It runs better on some sites where open java struggles and seems to use fewer resources.

4. Make sure you are using Adobe Flash, not an open source flash. 

I do all those things on every install. Works like a champ. I get into the mid 60s when I'm running video or other things, which is much lower than the mid 80s I got to before all those changes. And 80C+ is dangerously hot for the machine and way too uncomfortable to have in your lap for long.

---

### Post by Sialis on 2010-09-23
3miro
my cpu is dual core 2.2 
I have 2 cpu icon on sensor monitor
the first shows 85c and the second 64c now.  high temperature 
/cry


TBABill
I try to do your suggestions ,
i'm noob on ubuntu , I did the first recommendation,
but about another options I need more guidance,how can I check them?


thx guys

---

### Post by TBABill on 2010-09-23
For 3 and 4 in my list, go to Synaptic. That's the "package manager" which is where you can find every piece of software available (from the repositories you have enabled) to install, or already installed, in Ubuntu. You find it by clicking System>Administration>Synaptic.

Once in it click search and enter your search term. First search for Java and see what is installed. Near the end of the list will be Sun Java. That's what you need to mark for installation (right click the box and select "mark for installation"). BUT, first find the ones already installed. If they are called "open java" or something similar, first mark them for removal. 

After the Java you can do the same for flash. Just search for flash and see if the adobe flash item in Synaptic is installed. If it is (most likely is) then you are set.

Item 2 depends on the type of video card you have. Type lspci -v | grep VGA in a terminal and hit enter, then post your results.

---

### Post by 3Miro on 2010-09-23
> **Sialis said:**
> 3miro
my cpu is dual core 2.2 
I have 2 cpu icon on sensor monitor
the first shows 85c and the second 64c now.  high temperature 
/cry


This is bad.

Go to the System Monitor and let it build a bit of a graph on the CPU usage. With nothing working (close all browsers and such) you should get a few hits by the System Monitor, but overall both cores should stay below 20%. Also, install the CPU Frequency applet to make sure you are running "ondemand".

Are you sure the temperature in Windows is lower? What are you using to monitor it? I use CPUID.

---

### Post by Sialis on 2010-09-24
[TBABill]("http://ubuntuforums.org/member.php?u=974469")

I did all your recommendation, I removed open java and set sun java,
also I have installed adobe flash on my system
about item 2 its the result :  01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
I use ondemand for cpu.
ps : as I removed open java and installed sun ,system removed google chrome completely ,
I think google chrome installed open java and it needs open java to work.


[3Miro]("http://ubuntuforums.org/member.php?u=777773")

I used system monitor and I did what u said , it's always below 20% even 15%
cpu is ondemand .
also I'm sure about temperature in widows 7 (except in game !)  


ty guys

---

### Post by teward on 2010-09-24
Okay, this seems to be something interesting.

Lets note that CPUs have temperature increases and decreases as CPU usage fluctuates.
FOR EXAMPLE:  I have a dual core system running 2 CPU cores (i.e. 2 CPUs on system monitor), running at 2.6GHz.  When one or both cores are running at 2.66GHz (max speed), it jumps up to 70C - 89C then jumps back down to 45C - 52C.  Exceptions to this are when my laptop is sitting on my bed for a while, then the fan gets blocked.


Now, are you saying that your system is ALWAYS running at those higher temperatures?  If so, do me a favor and add the CPU Scaling Applet to your desktop (should have come preinstalled), and tell me what speed out of your max processor speed your system is running at.

---

### Post by 3Miro on 2010-09-24
If this is the temperature at 20% load, the only thing that I can think of is that Ubuntu doesn't work well with the Laptop fan. I am not sure which Ubuntu program would let you check it out. Look also in the BIOS settings, if there is a way to speeds it up or something like that.

---

### Post by Sialis on 2010-09-24
fixxxxxxxxxxxxxxxxxxx , what did I do ?

I run hardware drivers from administration.
update graphic drive , active that and the restart 
now cpu temperature is around 50-58 c    :)

thx a lot guys

---

