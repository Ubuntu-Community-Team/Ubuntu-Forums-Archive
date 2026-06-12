---
title: "I can't get Java to work"
date: 2011-03-13
forum: General Help
---

### Post by Kouki on 2011-03-13
Hi all, I'm using Ubuntu in the computer that is linked up to my television in my lounge.  I want to make it so that I can control it using remote droid from my android mobile phone - turns the phone into a wireless keyboard and mouse.

I tested it on my Windows PC in the office and had it up and running in under a minute.  I've been working on Ubuntu now for over an hour and am getting fed up with it.  The installation instructions are the same.  You just download a folder called RemoteDroidServer and then double click 'RemoteDroidServer.jar in Windows this just opens the application and you're ready to go.  In Ubuntu, rather than opening the application, it opens a folder full of files.

I'm guessing this is because Java isn't properly installed on Ubuntu.  I tried to install it from the same website I used for Java on Windows, using these instructions:

[http://www.java.com/en/download/help/linux_install.xml#rpm](http://www.java.com/en/download/help/linux_install.xml#rpm)

However, there is absolutely no way I can get them to work, pretty much every step is a massive problem, so I gave up.

I then went to synaptic package manager to see what I could install from there, however, there are hundreds of packages that come up.

It would be really helpful if someone could tell me which one I need, or basically just how I can install Java so that when I open the .jar file, it runs the application - as with Windows.

I can't believe it's taken up over an hour of my Sunday morning, I'm not happy.  I've used Ubuntu for 5 years now and this should be really straightforward.

Thanks

---

### Post by Kouki on 2011-03-13
I've just tried via the terminal and this is what happens:

stuart@stuarthp:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
stuart@stuarthp:~$ 


Any idea where sun-java6-jre has gone to?

---

### Post by Kouki on 2011-03-13
Don't worry everyone, I've solved it, somehow, it would appear I managed to install Java6.  I'm not sure what I did to do this.

I then found that to run the software I needed, I had to right click the icon and open with OpenJDK Java 6 Runtime.  This still wouldn't run it, as it said the file wasn't executable.

This may be useful for others with this problem.  I made the file executable by:

stuart@stuarthp:~$ cd ~/Desktop/RemoteDroidServer
stuart@stuarthp:~/Desktop/RemoteDroidServer$ chmod a+x RemoteDroidServer.jar
stuart@stuarthp:~/Desktop/RemoteDroidServer$ 

I hope this helps.  Now my mobile phone controls Ubuntu via wifi, it's great!

---

