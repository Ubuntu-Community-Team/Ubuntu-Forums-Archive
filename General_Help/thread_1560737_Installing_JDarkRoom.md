---
title: "Installing JDarkRoom"
date: 2010-08-25
forum: General Help
---

### Post by strnad on 2010-08-25
Hello,

I am trying to install JDarkRoom. I downloaded the package and typed java -jar JDarkRoom.jar as instructions told me.

When I did it, I've got this response:

strnad@lenovo-s12:~$ java -jar JDarkRoom.jar
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
Try: sudo apt-get install <selected package>
strnad@lenovo-s12:~$ 

What can I do with it? I do not understand the response too well, I am just newbie.

Thanks for help

Peter

P.S. I found a thread here consulting this but that did not help.

---

### Post by oldos2er on 2010-08-25
Assuming you're using 10.04, open menus System, Administration, Software Sources, Other software tab, and enable the partner repository. Then run ```
sudo apt-get install sun-java6-jre
``` Or you can install that package from Ubuntu Software Center or Synaptic, if you prefer.

---

### Post by strnad on 2010-08-26
Hello ann,

thanks for help, it worked well.

I would have one additional question.

In order to run the program I always have to type a sequence into Terminal.

Is there any way of how I can "install" the program so I will have an icon to run it?

Thanks a lot

Peter

---

### Post by strnad on 2010-08-26
Hello,

so I figured it out.

I installed java as told in the thread.

Then I just created Terminal Launcher where I copied the command line in order to run the JDarkRoom.

I am just exploring Ubuntu, but I am growing to like it more and more.

Thanks to all for great job.

Peter

---

