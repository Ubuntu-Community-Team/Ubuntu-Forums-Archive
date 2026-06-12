---
title: "Can't install the Firstclass client"
date: 2012-03-21
forum: General Help
---

### Post by Skopuningurin on 2012-03-21
Hi
I'm trying to install the Firstclass Client ( Linux version ) on Ubuntu 12.04 Beta2. I've had the Firstclass client on Wine for a while, but it runs like crap, and have done so with 11.10, 11.04 and 10.10. And now when I upgraded the distro, it's not working at all. Never mind that. 
When I want to install the deb file of the Firstclass client ( [http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4](http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4) ) and install it through the Software Centre, I get the message that the debfile isn't trustworthy, thus it won't install. Is there any way to get this issue solved? I really need the Firstclass client to work.
Thanks.

---

### Post by PhantomTurtle on 2012-03-21
I downloaded it from the website you linked to and opened it with the Ubuntu Software Center (I'm using the 12.04 beta btw). I didn't get a message like that but you could just install it using the terminal. To do that open terminal, navigate to the folder the deb file is in using,
```
cd
```
then type
```
sudo dpkg -i fcc-10.014-Linux.i686.deb
```

---

### Post by Skopuningurin on 2012-03-22
I tried that, and this is the message I get : 
" sudo dpkg -i fcc-10.014-Linux.i686.deb
dpkg: error processing fcc-10.014-Linux.i686.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
Errors were encountered while processing:
 fcc-10.014-Linux.i686.deb"

---

### Post by Skopuningurin on 2012-03-22
Okay! I managed to fix the problem. 
What I did was to google a bit. I found [https://bugs.launchpad.net/aptdaemon/+bug/637489](https://bugs.launchpad.net/aptdaemon/+bug/637489) , apparantly I'm not the only one who have had this issue. By downloading [http://anders.jenbo.dk/fcc-10.009-Linux.i686.deb](http://anders.jenbo.dk/fcc-10.009-Linux.i686.deb) , you get a fixed version. I tried to install it via Software Centre, but that didn't work. Got some strange message about I had no internet connection. Then I just used the terminal, as descriped above. 
And if anyone stumbles upon this thread with the same problem, the second link provided by me should work. If it doesn't work via Software centre, do as described above by Phantom Turtle.
Thanks for the help, Phantom Turtle!

---

### Post by Aydos on 2012-04-02
I PMed the OP to see if he could help me, but I thought I would post in here as well incase anyone else is having the problem.

I will paste the PM below.

Hello I too am having a problem with First Class in Ubuntu 12.04 beta 2.

I downloaded the fixed version from the link you provided and installed it. Everything went fine with that.

When I try to open the first class though nothing happens. It is like I did not click on it.

Any ideas?

---

### Post by Skopuningurin on 2012-04-30
Hi
I just installed 12.04 ( 64 bit ) from a fresh install.
It runs smooth and everything works fine, except the First Class Client, which is a essential tool at my college.
When I download the .deb file from their download page and try to install it via the software center I get this message. ( look at the attached file ). If i chose to ignore and install it just refuses to install it.
I've tried installing it with Wine. It's installs and I get the log-in screen. I type in username and password and press the green button. It gets connected to the server, but then it just says " not connected " and doesn't connect.
I need to get this problem fixed. I made a previous thread about this, it got solved, but when I upgraded with a fresh install it just wount work. If I can't get this solved, I've to go back to crappy Windows because the First Class client is so essential.

Webpage for downloading the .deb : [http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4](http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4)

---

### Post by watgrad on 2012-04-30
Hi - I also have to use FirstClass Client for work.
I have never been able to get the linux version to work properly.  I've always had to use the windows version through wine.  That said, I've had the best luck in Wine with version 10.014 of FirstClass - I couldn't get ver 11 to work very well.
I've got it running in WINE 1.4 - FirstClass version 10.014 with no troubles.

What version of WINE are you using?

---

### Post by lisati on 2012-04-30
Threads merged

---

### Post by Skopuningurin on 2012-05-01
Hi
I'm using Wine 1.4
I managed to get it to work in 11.10 ( took a lot of time and effort ) through Wine, but now it wont work.fuuu

---

