---
title: "Lucid Freeze"
date: 2011-10-01
forum: General Help
---

### Post by Mr Watch on 2011-10-01
Today, I found that after I was overclocking my CPU, my computer would randomly freeze. I set it back to default settings, but still received the freeze. It would usually freeze when I was running a java application, and music in the back ground. The music would at first have static when I loaded the java application, then repeat a 1-2 second segment and I couldn't do anything, plus my application froze also. Searching the internet for a solution to my problem, I found [http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html]("http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html"), which seemed to work at first. I went without error for about an hour before the problem occurred again. 

Some System Information:
AMD Phenom II X6 1090T Black Edition Thuban 3.2GHz OC @ 3.7GHz
12gb 1333MHz RAM
Sapphire Radeon HD 5770

---

### Post by 2F4U on 2011-10-02
Overclocking may have caused damage to your system. I would start by running memtest to verify that the RAM is working properly. Is there a pattern behind the freezes, e.g. are they happening always with the same set of applications? There are several settings to overclock a AMD CPU. Did you reset every setting to its previous state?

---

### Post by Mr Watch on 2011-10-02
I ran Memtest, and there was no errors. I haven't been able to reproduce the freeze again except when I run a torture test from Prime95. The set off applications I had open usually when the freeze happened were Pithos, and a graphical java application(For example, a program written in java to create random colors in an applet(Was during my learning of java), Minecraft(once), or browser/java based IRC). There hasn't been a problem so far today. When I reset everything to its previous state, I just loaded up the defaults. Went back to my overclock setting for the CPU, and still no problems. I don't know what caused the random freezes yesterday.

So I guess it is solved if there isn't anymore problems?

---

### Post by Claus7 on 2011-10-02
Hello,

if you check out the forums, you will find a link with >100000 views about the freezing issue of lucid. Which means that it would be nice not to see it again, yet time will tell. This might not be related with your over-clocking... How long your system is up and running? I do not know if they have found the reason of it...

Regards!

---

### Post by Mr Watch on 2011-10-02
Claus7,

Thank you for directing me to this thread. I will be looking through it for some way to solve my problem, should it occur again. So far today, my uptime has been 6 hours and 42 minutes. I thought it was an issue due to my overclocking because it happened as soon as I had my overclock setting. Thanks again for the thread.

If there is a way for me to view the error in some sort of system file, what would it be? That would probably be helpful on locating the cause if it wasn't because of my overclocking.

---

### Post by Claus7 on 2011-10-02
Hello,

I had faced some freezing issues with lucid a long time ago. Taking a look on that thread:
[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

I saw that people were mentioning that it was not possible to find a specific log file so as to track the problem. Yet I do not know, whether they found a solution to that. I do not use lucid any more.

In case you need to find log files in your system, you have to check them under:
System->Administration->Log file viewer

Regards!

---

