---
title: "USC vs. synaptic vs. apt-get vs. tarball"
date: 2012-09-08
forum: General Help
---

### Post by rybnik on 2012-09-08
Sorry if this is the wrong section of the forum--if it is, please let me know, and I'll repost to the correct place.  I saw an "installation and upgrades" section, but I figured that was for installing the OS rather than softwares.

So I understand that there are several different ways to install softwares.  The ones I've heard of are:

1. Ubuntu Software Center
2. Synaptic Package Manager
3. apt-get command
4. extracting a tarball

I've used (1) and (4), but I've only had very brief exposure to (2) and (3).  

I strongly prefer (1), mainly because it's idiot-proof and extremely easy, but I noticed that a software program only appears on the Applications menu of the top bar if it is installed through (1).  (I'm using 10.04 lucid lynx with gnome.)  

SO MY QUESTION IS: why doesn't a software program appear in the "Applications" menu of the top bar if it is installed through anything other than (1)???

Also, what are the major differences between (1), (2), (3), and (4) in terms of HOW they install software?

I realize this might take a while to answer--so thank you all very much in advance.  I'd appreciate any and all replies.

---

### Post by jerrrys on 2012-09-08
I will do number 2:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Synaptic is an advance way of managing and maintaining packages (plus other features) as compared to the software center.  I think its worth learning

---

### Post by mikewhatever on 2012-09-08
A menu entry should appear if a program is installed using methods 1,2,3, that is, it the program even has a launcher. Some terminal based programs simply don't have menu entries, no matter how they are installed.

The installation methods 1,2,3 can be considered the same, because they all use [APT]("http://wiki.debian.org/Apt") as backend, and only the frontends are different.
Tarballs usually contain either source or binaries. In the first case, you'd extract and build, whereas in the second, extract and run.

---

### Post by rybnik on 2012-09-08
[quote=mikewhatever]A menu entry should appear if a program is installed using methods 1,2,3, that is, it the program even has a launcher.[/quote]
Oh, I see.  I suppose I misunderstood earlier.

Thanks for your explanation of APT and tarball.

Let me throw in another:

(1) Ubuntu Software Center
(2) Synaptic Package Manger
(3) apt-get command
(4) extracting a tarball
(5) yum command

How is yum (5) different from apt-get (3)?  Since they're both terminal commands, why is there a need for the existence of both of them?

Also, I understand that synaptic uses "packages"?  Does "package" have a different meaning than "software program"?  For instance, I think of openOfficeWriter as a software program--is there a corresponding package?

Sorry to be pesky.  I really do appreciate your help.

---

### Post by cryptotheslow on 2012-09-08
Options 1, 2 & 3 have one particular advantage over 4. That is in that you must use a repository to install them. If you keep that repository in your sources list, if the maintainer of the particular packages releases an update you will receive it automagically the next time update manager does its thing.

The application installed from a tarball relies on you keeping an eye out for any updates on whatever site you found it (although a small minority of applications do have their own in-built update checkers).

---

### Post by QIII on 2012-09-08
yum is used in rpm package based distros like Fedora.

---

### Post by rybnik on 2012-09-08
Thank you all.

---

### Post by Paddy Landau on 2012-09-08
To clarify this further:

There are two ways to install, update and uninstall programs.
[LIST=1]
[*]DIY (do it yourself)
[*]Through the package manager
[/LIST]
There are two main package managers for Linux. Ubuntu uses one called Debian, or .deb for short. (The other is RPM.) The package manager has several advantages, including automatic downloading, installing, and detection of updates.

To install a program, you tell the package manager to install a .deb file. The .deb file decides how to install, and whether or not to put an entry into the menu.

.deb files can be manually downloaded, or you can simply tell the package manager to have a look at some PPAs. A PPA is a storage space for .deb files, and by using them, the package manager can automatically find applications and detect when they need to be updated. The package manager also checks for dependencies and maintains consistency, preventing you from installing or uninstalling applications that would break their dependencies.

Canonical (Ubuntu's sponsor) provides several PPAs by default, but you can add more if you trust them. For example, if you want the latest GIMP, you can add GIMP's PPA &#8212; but of course Canonical cannot promise that it would work with your version of Ubuntu. You take the risk when you add a PPA (although if it breaks something, you can remove the PPA and undo what you did, using the package manager of course).

The package manager can be accessed in different ways. They include &#8212; but are not limited to &#8212; dpkg, aptitude, apt-get, Synaptic Package Manager, and the Ubuntu Software Centre. Use whichever you prefer.

Generally, you do not want to go the DIY route, as you lose *all* the advantages of the package manager.

A few applications do not provide PPAs, but do provide .deb files. In those cases, you still have the advantage of using the package manager, but you have to manually download the .deb file and check for updates, as the package manager needs a PPA to perform those two functions.

I hope that's sufficiently clear.

---

### Post by rybnik on 2012-09-08
Paddy Landau, 

Thank you for your detailed reply.  That was very helpful!

---

### Post by Paddy Landau on 2012-09-09
> **rybnik said:**
> Thank you for your detailed reply.  That was very helpful!
Glad to be of help.

Do you feel that your question has been answered? If so, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by afulldeck on 2012-09-09
> **Paddy Landau said:**
> To clarify this further:

There are two ways to install, update and uninstall programs.
[LIST=1]
[*]DIY (do it yourself)
[*]Through the package manager
[/LIST]
There are two main package managers for Linux. Ubuntu uses one called Debian, or .deb for short. (The other is RPM.) The package manager has several advantages, including automatic downloading, installing, and detection of updates.

To install a program, you tell the package manager to install a .deb file. The .deb file decides how to install, and whether or not to put an entry into the menu.

.deb files can be manually downloaded, or you can simply tell the package manager to have a look at some PPAs. A PPA is a storage space for .deb files, and by using them, the package manager can automatically find applications and detect when they need to be updated. The package manager also checks for dependencies and maintains consistency, preventing you from installing or uninstalling applications that would break their dependencies.

Canonical (Ubuntu's sponsor) provides several PPAs by default, but you can add more if you trust them. For example, if you want the latest GIMP, you can add GIMP's PPA — but of course Canonical cannot promise that it would work with your version of Ubuntu. You take the risk when you add a PPA (although if it breaks something, you can remove the PPA and undo what you did, using the package manager of course).

The package manager can be accessed in different ways. They include — but are not limited to — dpkg, aptitude, apt-get, Synaptic Package Manager, and the Ubuntu Software Centre. Use whichever you prefer.

Generally, you do not want to go the DIY route, as you lose *all* the advantages of the package manager.

A few applications do not provide PPAs, but do provide .deb files. In those cases, you still have the advantage of using the package manager, but you have to manually download the .deb file and check for updates, as the package manager needs a PPA to perform those two functions.

I hope that's sufficiently clear.

That was excellent. So if I was using the Ubuntu Software Center how do I add the PPA through the USC? When I pull up the USC there doesn't seem to be any direct connection.

---

### Post by Paddy Landau on 2012-09-09
> **afulldeck said:**
> That was excellent. So if I was using the Ubuntu Software Center how do I add the PPA through the USC? When I pull up the USC there doesn't seem to be any direct connection.
First, an explanation of how to specify a PPA. There are two ways. I shall use [yad]("http://www.webupd8.org/2010/12/yad-zenity-on-steroids-display.html") as an example.
[LIST=1]
[*]Specify the full line, which takes the following format.
```
deb *[PPA_URL]* *[YourUbuntuVersion]* main
```(The last item "main" may change, but you will be told when that is the case.) Using yad, and assuming that you are using Precise, you'd have:
```
deb [noparse]http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu[/noparse] precise main
```
[*]If — and only if — the PPA is on Launchpad, you can use the following abbreviated line:
```
ppa:*[PPA_abbreviation]*
```Again using yad:
```
ppa:webupd8team/y-ppa-manager
```
[/LIST]
So, how does this work with the Ubuntu Software Centre?

[LIST=1]
[*]Start USC.
[*]Menu > Edit > Software Sources > Other Software > Add
[*]Type in either the abbreviated line (if it's on Launchpad) or the full line.
[*]> Add Source
[/LIST]
[CENTER][B]Screen-shot of the two new lines
[/B][IMG]http://ubuntuforums.org/attachment.php?attachmentid=223931&stc=1&d=1347196487[/IMG]
[/CENTER]

Once you have added the PPA, you probably want to make two changes.

[LIST=1]
[*]You probably don't want the source code (unless you are a programmer wanting to change yad), so click on the line ending "(Source Code)" and press *Remove*.
[*]You probably want to remember why you added this PPA, so click on the new item > Edit > type a meaningful comment in the "Comment" box > OK
[/LIST]
[CENTER][B]Screen-shot after making changes
[/B][IMG]http://ubuntuforums.org/attachment.php?attachmentid=223932&stc=1&d=1347196487[/IMG]
[/CENTER]

Finally, press Close to close the Software Sources window.

At this point, you want the package manager to update its listings (until it does so, your changes will be ignored). Unfortunately, the USC does not have a button to do this (this should be reported as an error). But you can do so from either Synaptic Package Manager or via the CLI (command-line interface).

[LIST=1]
[*]From Synaptic Package Manager: Press the Reload button. You must close Synaptic Package Manager before using USC again, because Synaptic locks the package manager.
[*]From the CLI: Open a Terminal and enter the following command.
```
sudo apt-get update
```
[/LIST]

---

### Post by afulldeck on 2012-09-09
Again thank you for your complete answer. I've made a record of this for next time I want to add a PPA using USC. (Last time I did everything manual outside the USC.)  That said, has anyone thought of adding a button to USC (add PPA?) so one could simply add a ppa with one touch?

---

### Post by Paddy Landau on 2012-09-09
> **afulldeck said:**
>  That said, has anyone thought of adding a button to USC (add PPA?) so one could simply add a ppa with one touch?
You can raise this idea as a [Brainstorm]("http://brainstorm.ubuntu.com/"). But, I rather suspect that it would be rejected, because adding PPAs is an advanced subject — you'd need to research (exactly as you have done!) to discover about the possibility of untrusted PPAs that can put malware on your system. The USC is intended for the "average" user, who would avoid doing this sort of thing.

But try, anyway; you may find that the idea meets with general approval.

---

### Post by rybnik on 2012-09-09
My initial question has been answered to my satisfaction (thank you!), but I'll hold off on marking the thread [solved] for now, as there seems to have been another discussion emerged.

---

### Post by Paddy Landau on 2012-09-10
> **rybnik said:**
> I'll hold off on marking the thread [solved] for now, as there seems to have been another discussion emerged.
The "solved" marker is for the original question, not for subsequent discussions that may arise. (Strictly speaking, new discussions should go in new threads, but these forums are not strict in that sense.)

Marking your thread as solved serves two purposes: (1) It lets others with a similar problem find the answer; and (2) It saves time for those volunteers who try to solve unanswered questions and problems.

---

### Post by rybnik on 2012-09-10
^Okay.  I understand.

---

