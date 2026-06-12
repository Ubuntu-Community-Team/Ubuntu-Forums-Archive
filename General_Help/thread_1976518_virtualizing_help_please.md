---
title: "virtualizing help please"
date: 2012-05-08
forum: General Help
---

### Post by MA77 on 2012-05-08
I just got a new computer, its an hp pavilion dm4 beats addition and it has 6GB of ram and has windows 7. I would like to be able to access both windows 7 and ubuntu operating servers. I would be using ubuntu for the most part but would use windows 7 for microsoft office and some other software not available on ubuntu. What would the best way to go about this. From what I understand virtualization would be better than dual booting is this right? If I virtualize is there a way to switch which is the default operating system? If not should I have ubuntu run on windows 7 or the other way around? sorry for all the questions, but i would greatly appreciate any help/feedback. thanks

---

### Post by PhantomTurtle on 2012-05-08
Virtualization is not like dualbooting. It is a OS that is completely seperate from your Ubuntu install and will run at the same time as Ubuntu, so there will be a little slowdown. I would try Wine. With wine you can run (most) windows programs natively(no virtualization). The only drawback is that not all programs will work. However I know for a fact that MS Office works since I have used it. To get wine run,
```
sudo apt-get install wine
```
in terminal or search for it in the Software Center. To check if a windows app is compatible search for it at [http://appdb.winehq.org/]("http://appdb.winehq.org/")
For virtualization you can get virtualbox. To get virutalbox open terminal and run,
```
sudo apt-get install virtualbox
```
or search it in the Software Center. Try Wine first.

---

### Post by MA77 on 2012-05-08
if i chose to virtualize would it be better to run ubuntu on windows or the other way around though? would my chances of getting a virus be the same if i ran ubuntu off of windows 7 or if i was running ubuntu as the primary operating system?

---

### Post by PhantomTurtle on 2012-05-09
> **MA77 said:**
> if i chose to virtualize would it be better to run ubuntu on windows or the other way around though? would my chances of getting a virus be the same if i ran ubuntu off of windows 7 or if i was running ubuntu as the primary operating system?

I have always run Ubuntu as my main OS and used other OS's in virtualbox. I have never (ever) run a anti-virus program on Ubuntu. I never needed one. I probably should use on but I don't. I would use Windows in a virtual machine. That way the amount of viruses are less that way. However I tell you this because I like using Ubuntu and I'd rather use it than Windows and that's why I recommend you do it in vbox. If you like you can run Ubuntu in a vmachine instead.

---

### Post by MA77 on 2012-05-09
1 final question,i have windows 7 right now so if i were to get ubuntu and run windows 7 on that would i have to buy windows 7? Thank you for all the help

---

### Post by westie457 on 2012-05-09
If you have an original Windows dvd you can use that in a virtual machine provided you wipe the hard drive first, install Ubuntu then install the virtual Windows.

If all you have is an OEM dvd then probably you will have to buy a Windows only dvd because the OEM will be looking for certain things on the computer and might not be able to find them. Before you try anything like this make backups of the recovery partition and the Windows partition.

Cannot suggest any other way that will work without breaking the Windows EULA which is illegal and discouraged on these Forums.

Having said all of the above there really is nothing to stop you setting up a virtual Ubuntu machine within Windows. That way no need to purchase a Windows dvd or break the terms of the EULA.

I personally would recommend you use OSE Virtualbox from here.
[https://www.virtualbox.org/](https://www.virtualbox.org/)

Good luck with whichever route you choose.

---

