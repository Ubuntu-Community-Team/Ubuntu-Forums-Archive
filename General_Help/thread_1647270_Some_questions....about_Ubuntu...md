---
title: "Some questions....about Ubuntu.."
date: 2010-12-17
forum: General Help
---

### Post by Linyx on 2010-12-17
[SIZE="2"]I was Confused for Choosing Title Of this thread, because i have some questions....

i am completely noob, so please explain it simple.

1)If i run "sudo apt-get dist-upgrade" my lucid will convert to Maverick...?

2)I am **confused** about kernels,i have seen that one can also update his kernel,how? and moreover, Lucid kernel will be different then Maverick ,right?or it is just an **update version**Of Lucid-Kernel..??[/SIZE]

3)lucid is LTS, its means that it will supported up-to 3 years, but what the **support** term means...?security , packages,new softs ..?

4)Why Linux isn't Effected by Viruses..? Only Exe-files are infected by viruses only...?

5)What is the **BEST file-sys**,as Ext-4 is the latest , that means that this will be more useful as **compared** to Ext-3, as both are journaled,then what is the difference...?

6)We normally say that Linux is (**UNIX-like OS**), means that Linux uses kernel of UNIX..?Sorry, i don't know about these things, so please explain a little-bit about Unix and Linux difference(except that Unix is only CLI).

7)Also, why Unix is more **secure** then Linux...?

[SIZE="2"]Please don't attached links,however i can Google these, but i want **straight/simple** answers about these.....[/SIZE]
[SIZE="2"]Thats all[/SIZE]

---

### Post by Linyx on 2010-12-17
[SIZE="2"]bump[/SIZE]

---

### Post by balaknair on 2010-12-17
I'll try to answer your questions one by one
1) No, it won't. dist-upgrade will tell APT(the package(software) management tool) to use 'smart' settings, where if any conflicts exist between the packages being upgraded, the most important upgrades will be carried out even if it means some of the less important ones are sacrificed.

2) Kernels: the kernel version in Lucid is 2.6.32.[COLOR="Red"]26[/COLOR], whereas that in Maverick is 2.6.35.[COLOR="Red"]23[/COLOR]. Kernel updates within each release have been marked in red. Updating the entire kernel version(2.6.32 to 2.6.35) can cause a lot of other software installed to malfunction, and you'd have to update and reconfigure all the other stuff as well.
The latest stable version of the Linux kernel is 2.6.36. You can install newer versions of the Linux kernel by compiling it yourself, but this is not recommended, especially for new users.

3) Support basically means that software updates(patches) to fix security or performance issues will be continously provided for all the programs included in that release. The software is usually packaged by the Ubuntu devs specifically for each supported release and distributed via the Ubuntu repositories. So for eg. Lucid Lynx desktop edition will be continously updated for three years till April 2013(Server version til April 2015). After that time if you continue to use Lucid, you will not recieve any more updates(includes security and other fixes) from the repositories since the Ubuntu developers will no longer be maintaining packages for Lucid Lynx.

4) The whole Linux virus thing is a bit of a long topic, I'll just give you a short version. 
a) It is possible to write a virus for Linux, but harder to install it without the user knowing. A bit like you can kill Superman(Linux), but it's a lot harder than killing an average guy. Also most Linux users tend to be smarter at avoiding malware than the average Windows user(at least according to most Windows 'security experts')
b) Most viruses around today were written specifically for Windows, so wouldn't run on Linux anyway.

5) EXT4 vs EXT3- EXT4 offers better read/write performance and crash tolerance than EXT3, and is faster especially on solid state drives(like those on some netbooks or the Macbook Air). There are differences in the way both manage files, but I'm not sure I understand it well enough to give you a simple answer. For most users installing new versions of Ubuntu, EXT4 is definitely a better/safer option than EXT3.

6) No. Linux uses its own kernel, first developed by Linus Torvalds in 1991(Linux is pretty much just the kernel and drivers; on top of it is mostly a lot of programs part of the GNU suite, hence the term GNU-Linux is regarded to be the correct name for what we usually call Linux). UNIX is an older OS family(includes the BSDs, SysV UNIX, Mac OSX, AIX and Solaris) based on the OS developed by Bell labs engineer Ken Thompson in 1970, and Linux was inspired by UNIX, using a similar file tree and also shares many components such as X Windows and OpenSSH which were originally developed for UNIX OSes. And UNIX is not just CLI, all the examples I mention above also have a GUI.

7) AFAIK UNIX isn't significantly more secure than Linux and both share much of the same secure computing ideas. What usually makes either OS more or less secure is the particular implementation. For eg. OpenBSD is regarded as the most secure OS out of the box and also the least 'usable', and MacOSX is apparently the least secure but shines in terms of 'user-friendliness'. Both are UNIX based OS, but OSX sacrifices security for ease of use. This sort of question doesn't really have a clear cut answer, and continues to be the subject of numerous flame wars. Not a place I really want to go now.

Hope this was helpful.

---

### Post by Linyx on 2010-12-17
> **balaknair said:**
> 2) Kernels: the kernel version in Lucid is 2.6.32.[COLOR="Red"]26[/COLOR], whereas that in Maverick is 2.6.35.[COLOR="Red"]23[/COLOR]. Kernel updates within each release have been marked in red. Updating the entire kernel version(2.6.32 to 2.6.35) can cause a lot of other software installed to malfunction, and you'd have to update and reconfigure all the other stuff as well.
The latest stable version of the Linux kernel is 2.6.36. You can install newer versions of the Linux kernel by compiling it yourself, but this is not recommended, especially for new users.

6) No. Linux uses its own kernel, first developed by Linus Torvalds in 1991(Linux is pretty much just the kernel and drivers; on top of it is mostly a lot of programs part of the GNU suite, hence the term GNU-Linux is regarded to be the correct name for what we usually call Linux). UNIX is an older OS family(includes the BSDs, SysV UNIX, Mac OSX, AIX and Solaris) based on the OS developed by Bell labs engineer Ken Thompson in 1970, and Linux was inspired by UNIX, using a similar **file tree** and also shares many components such as X Windows and OpenSSH which were originally developed for UNIX OSes. And UNIX is not just CLI, all the examples I mention above also have a GUI.

7) AFAIK UNIX isn't significantly more secure than Linux and both share much of the same secure computing ideas. What usually makes either OS more or less secure is the particular implementation. For eg. OpenBSD is regarded as the most secure OS out of the box and also the least 'usable', and MacOSX is apparently the least secure but shines in terms of 'user-friendliness'. Both are UNIX based OS, but ***OSX sacrifices*** security for ease of use. This sort of question doesn't really have a clear cut answer, and continues to be the subject of numerous flame wars. Not a place I really want to go now.

[SIZE="2"]First of all, thanks alot for this nice explanation for each Question :p

But i have some question in order to To know these things Throughly...

Ok, 1st of all, you mentioned in point 2nd that **Updating the entire kernel version(2.6.32 to 2.6.35)**, this means that updating kernal like that will convert Lucid into Mavrick..?

2)In Answer "6" that both uses same "**File-tree**", what this file-tree means..? Arrangement of data in File-sys(root)...?

3)In point "7", you means to say that when OS moved towards **GUI(more user-friendly)**, its **security level** Becomes **down**, and i am agree about that, but i don't know **why** this happens...?

4)Is MAC-OS is less secure then Ubuntu...?
[/SIZE]

---

### Post by jim_deadlock on 2010-12-17
On the topic of kernels, what happens is that if you're running Lucid, you get system updates regularly, and occasionally a kernel upgrade is included in your updates, so you just update your packages as you normally would, including kernel. When you get to October, you receive your final Lucid updates and then your update manager asks you if you want to upgrade to Maverick, so you click yes and it installs all the new Maverick stuff, including the new kernel.

Basically, your kernel upgrades are always included in your routine system updates, it's nothing to worry about.

---

### Post by Linyx on 2010-12-17
> **jim_deadlock said:**
> On the topic of kernels, what happens is that if you're running Lucid, you get system updates regularly, and occasionally a kernel upgrade is included in your updates, so you just update your packages as you normally would, including kernel. When you get to October, you receive your final Lucid updates and then your update manager asks you if you want to upgrade to Maverick, so you click yes and it installs all the new Maverick stuff, including the new kernel.

Basically, your kernel upgrades are always included in your routine system updates, it's nothing to worry about.

[SIZE="2"]Thanks for that, but if i want to **upgrade** my Lucid to Maverick,which **command** to should be used in that case...? Moreover, the **Kernel** of Lucid is **completely change** from Maverick ? or maverick kernel is **Update-form** on lucid Kernel ?[/SIZE]

---

### Post by jim_deadlock on 2010-12-17
Just use your Update Manager as usual. When all of the Lucid updates are completed, you will automatically see a button to upgrade to Maverick.

---

### Post by Verbeck on 2010-12-17
> **Linyx said:**
> [SIZE=2]Thanks for that, but if i want to **upgrade** my Lucid to Maverick,which **command** to should be used in that case...? Moreover, the **Kernel** of Lucid is **completely change** from Maverick ? or maverick kernel is **Update-form** on lucid Kernel ?[/SIZE]
the kernel 2.6.32 to 2.6.35 is an update

to upgrade the distribution from a LTS to a non-LTS version, change 'show distribution release' to normal releases in system>administration>software sources>updates tab and then run the update manager

---

### Post by migs73 on 2010-12-17
5) try looking here [http://www.howtogeek.com/howto/33552...ld-you-choose/](http://www.howtogeek.com/howto/33552...ld-you-choose/)
thanks to MrFaler for the link. 

Also adding a GUI doesn't make the system less secure, making it more user friendly (less security hoops to jump through) does.

ie remove all the passwords from your system, very user friendly (no need to remember any passwords now), but definitely less secure.

by the way that is an extreme example for illustration only.!!!!

Yes, Linux is considered more secure than Mac OS (just!)

---

### Post by Linyx on 2010-12-17
> **Verbeck said:**
> the kernel 2.6.32 to 2.6.35 is an update

to upgrade the distribution from a LTS to a non-LTS version, change 'show distribution release' to normal releases in system>administration>software sources>updates tab and then run the update manager
[SIZE="2"]
As mentioned by **balaknair** in the first post that "**kernel version in Lucid is 2.6.32.26, whereas that in Maverick is ****2.6.35.23"** So if i update my kernel(2.6.32-26)to 2.6.35, so My lucid will convert to Maverick right...?

I am confused about the that, that lucid is Different from maverick **just in kernel**...?[/SIZE]

> [SIZE="2"]Also adding a GUI doesn't make the system less secure, making it more user friendly (less security hoops to jump through) does.

ie remove all the passwords from your system, very user friendly (no need to remember any passwords now), but definitely less secure.[/SIZE]

[SIZE="2"]No, i don't means to say that user-friendly means less **authentication**, i means that **power-full GUI**, like nice graphics and something like this make OS **less secure**, well, i don't know about this ,but i want to learn about this,...

E.g BSD is more secure OS then Ubuntu(as mentioned by balaknair) because Ubuntu is more **user-friendly** as compared to BSD's....
[/SIZE]

---

### Post by Verbeck on 2010-12-17
> **Linyx said:**
> [SIZE=2]
As mentioned by **balaknair** in the first post that "**kernel  version in Lucid is 2.6.32.26, whereas that in Maverick is ****2.6.35.23"**  So if i update my kernel(2.6.32-26)to 2.6.35, so My lucid will convert  to Maverick right...?

I am confused about the that, that lucid is Different from maverick **just  in kernel**...?[/SIZE]

[SIZE=2]No, i don't means to say that user-friendly means less **authentication**,  i means that **power-full GUI**, like nice graphics and something  like this make OS **less secure**, well, i don't know about this ,but  i want to learn about this,...

E.g BSD is more secure OS then Ubuntu(as mentioned by balaknair) because  Ubuntu is more **user-friendly** as compared to BSD's....
[/SIZE]


an operating system _is not just the [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computing%29")_. i'll have to leave the explanation of every component to someone more knowledgeable than me (and the other question too)

---

### Post by balaknair on 2010-12-17
> **Linyx said:**
> [SIZE="2"]
As mentioned by **balaknair** in the first post that "**kernel version in Lucid is 2.6.32.26, whereas that in Maverick is ****2.6.35.23"** So if i update my kernel(2.6.32-26)to 2.6.35, so My lucid will convert to Maverick right...?

I am confused about the that, that lucid is Different from maverick **just in kernel**...?[/SIZE]



[SIZE="2"]No, i don't means to say that user-friendly means less **authentication**, i means that **power-full GUI**, like nice graphics and something like this make OS **less secure**, well, i don't know about this ,but i want to learn about this,...

E.g BSD is more secure OS then Ubuntu(as mentioned by balaknair) because Ubuntu is more **user-friendly** as compared to BSD's....
[/SIZE]

About the Lucid-Maverick kernel upgrade stuff, that's not exactly how it works. I'll try my best to explain
The kernel is the basic foundation of an OS, upon which you have a layer of tools(GNU toolkit), and on top of that you have various applications like browsers, office suites, multimedia suites etc. A bit like a car has an engine(kernel), chassis and transmission(toolkit), and bodywork, interiors and gadgets(GUI and apps). So upgrading from Lucid to Maverick is more than just updating from Linux 2.6.32 to 2.6.35, just like getting a new engine doesn't mean you have a new car. It also upgrades almost everything else like the compiler GCC from 4.4.3 to 4.4.4 and your apps like from Firefox 3.5 to 3.6, GNOME from 2.30 to 2.32. 
That's still not a complete picture but I hope it helps clear your confusion.

As for the second issue you mention about more graphics stuff etc making things less secure. IMO there are four reasons for that happening
a) more code, more room for mistakes to happen, more security bugs creep in
b) open source security- more eyes looking at the code means shallower bugs, patched faster
c) the ubergeeks who regularly use CLI heavy systems tend to be more knowledgeable about computer security and don't (often) make the same mistakes that noobs do.
d) the OpenBSD devs put in a lot of effort to make sure that the OS was as secure as possible, prettiness and user friendliness were not high on their list of priorities. The Apple folks on the other hand wanted to make an OS that was as polished as possible and easy to use, and didn't let secondary concerns like high security stand in their way. It seems they even disabled some of the security features to make the OS more polished. The result is a highly regarded OS that wows all beholders but is also the first to fall during the CanSecWest hacking competitions(within minutes).  Keep in mind that both OpenBSD and OSX are based on BSD UNIX.
Obligatory TSA analogy:
OpenBSD: all passengers have to be profiled, strip searched, X-rayed, porno-scanned, DNA samples taken and cavity searched before being allowed to board the plane. And on the plane passengers will be strapped in to their unupholstered seats for the entire flight. Noob Passengers are however permitted to sigh, think suicidal thoughts, or hate us for putting them through this. We are sure they'll thank us for keeping them safe, some time in the future.
Apple OSX: anyone can walk in anywhere, even in to the cockpit, as long as They can afford to buy a ticket(we only have First Class). Passengers are not allowed to bring a gun or edged weapon of their own, but can buy them from our cool inflight iTunes store. There is no point in bringing bombs or explosives on board because our airplane already has several smoke-free high-powered bombs laced with rose oil built into the airframe(Steve Jobs thought they looked prettier that way) so if they should explode you'll go to your eternal rest in style and smelling fantastic. And for those worried about our airplane security, Steve Jobs has said that there's nothing wrong, Steve is always right, so shut up, read your EULA again and enjoy the super smooth ride to wherever Steve wants you to go. Or we'll set the fanbois against you.

Ubuntu: Hopefully manages to find the right balance(crosses fingers)

Disclaimer:
Please note that the above statements on security are my opinion only, based in small part on my personal experience and that of some friends I've helped with computer issues,  and mostly on stuff I've read(most of it on the internet), I am not an expert on computers or on cyber security or a geek. I have used Windows, OSX and Ubuntu, but never managed to set up OpenBSD after three tries, though I hear it's a terrific OS to use once you manage to configure it.

---

### Post by Linyx on 2010-12-17
[SIZE="2"]@balaknair > It is an Awesome-Explanation , thanks alot for providing this :p[/SIZE]
[SIZE="2"]Correct me if i am Wrong, but, i think you forgot to explain "**File-tree**"[/SIZE]


[SIZE="2"]All the Issue i had Posted in my thread are Completely cleared to me, but i don't want to close this Thread as Another questions like this, which i want to know, I want to post it here in this thread , not to make another thread....Hope no One mind ;)[/SIZE]

[SIZE="2"]1)Every OS has its own kernel right..?it means that Windows has his own kernel......Linus Torvalds has Provided a Kernel for this OS(Linux) and the Graphics and other stuff are provided by GNU, it means that the kernel it still same upto now..?well, i know that updates are provided with time for a kernel, but, i want to know that "The kernel provided by **Linus Torvald** is still same(but a little of change with time) or the Kernel is also being **Upgraded** with time...?"[/SIZE]

---

### Post by balaknair on 2010-12-17
> **Linyx said:**
> [SIZE="2"]@balaknair > It is an Awesome-Explanation , thanks alot for providing this :p[/SIZE]
[SIZE="2"]Correct me if i am Wrong, but, i think you forgot to explain "**File-tree**"[/SIZE]


[SIZE="2"]All the Issue i had Posted in my thread are Completely cleared to me, but i don't want to close this Thread as Another questions like this, which i want to know, I want to post it here in this thread , not to make another thread....Hope no One mind ;)[/SIZE]

[SIZE="2"]1)Every OS has its own kernel right..?it means that Windows has his own kernel......Linus Torvalds has Provided a Kernel for this OS(Linux) and the Graphics and other stuff are provided by GNU, it means that the kernel it still same upto now..?well, i know that updates are provided with time for a kernel, but, i want to know that "The kernel provided by **Linus Torvald** is still same(but a little of change with time) or the Kernel is also being **Upgraded** with time...?"[/SIZE]
The file tree is the way filesystems are arranged- on Windows as A:\, C:\, D:\ and on UNIX-like systems as root(/), /usr, /home, /media, /media/sda1 and so on. Linus based his new OS on MINIX, a 'mini-UNIX OS' which was distributed free for educational purposes but not commercial use. Linux was partly intended to remedy the things Linus didn't like about MINIX, and was actually developed on a PC running MINIX. This meant that the new OS basically inherited MINIX's filesystem.

The other point about the kernel being upgraded with time- yes it's updated constantly, new 'vanilla' versions are released by the Linux kernel team approximately 3 months apart. The distro developers package the version they want and add their own patches optimizations, test it and release according to their own schedule as part of their distro. They then provide updates to that kernel version for as long as that release is supported.

The Linux kernel development is however pretty much independent of all that.
1991 September- Linux version 0.01 is released- ~10,000 lines of code. New versions 0.02, 0.03 etc are released almost monthly as the baby OS gets more features like more tools integrated from the GNU toolkit, X Windows is bolted on and so on till
1994 March- Linux version 1.0 released- ~170,000 lines of code.

The Linux kernel 2 series that we now use was released in 1996, version 2.6 in 2003 with 5,929,913 lines of code. The current stable version 2.6.36 was released in October 2010 with 13,499,457 lines of code. 2.6.37 is currently in development(2.6.37-rc6) and is slated for release around Jan 2011. And the Ubuntu-ized version of 2.6.37 will be used in Natty Narwhal(right now at 2.6.37.10.12), released in April 2011. Updates to the kernel in Natty will be issued as 2.6.37.14.1, 2.6.37.15.22 and so on for Natty, but the basic kernel version will remain 2.6.37 and will not change to 2.6.38 or 2.6.39.

I hope that clears up things for you.
Cheers

---

### Post by Linyx on 2010-12-18
Thats nice..:P

However i am not completely Understand by the term "**File-tree**", Although, i Got that it is the Way of arrangment of File-system like just in Windows >C:/ but what this **Arrangement** means...?what is the **difference** of the files arrange by Windows and Linux,

Except that , In linux the /Root is Protected and in windows C:/ is not **Authenticated** and any 1 can easily harm C:...

---

### Post by balaknair on 2010-12-19
> **Linyx said:**
> Thats nice..:P

However i am not completely Understand by the term "**File-tree**", Although, i Got that it is the Way of arrangment of File-system like just in Windows >C:/ but what this **Arrangement** means...?what is the **difference** of the files arrange by Windows and Linux,

File trees in UNIX- so called because of the tree like structure- '/' root is the tree trunk, and subfolders '/home' '/usr' '/etc' '/boot' are all branches, which again have sub-branches '/home/USERNAME' '/usr/bin' '/usr/share' and so on, and the files are the leaves. Physical drives or partitions were 'mounted' inside this within '/dev/' or '/media/'. So all the files on many different physical drives would still appear within the same file tree. This way the users' /home folders could be on a separate drive from the OS itself and preserved even when the OS had to be reinstalled. And it kept the users from messing the rest of the system.

MS-DOS(which evolved into Windows) was originally written to power IBM-compatible PCs. At the time IBM used drive letters to denote logical drives such as A:\, B:\ on its CP/M operating system , and so that's what MS-DOS also used for the IBM PCs. Each drive would have its own root folder but since it was to be used by only one user, they didn't need to worry about file permissions.
This probably had to do with the environment the OS was intended for. The UNIX filesystem was intended for large mainframe computers with numerous physical drives containing hundreds of thousands of files, whereas the typical IBM PC would have maybe a few hundred files residing on one or two drives(usually 8" floppies). The early versions also had no subfolders, all files were just listed under the drive letter(A:\SOMEFILE.TXT); the ability to add subfolders came with later versions.

As MS-DOS evolved into Windows, the drive letter structure was retained for backwards compatibility(since they wanted DOS programs to run on Windows), but was hacked and patched to overcome some of the initial shortcomings such as support for logical drives and file/folder permissions.

> Except that , In linux the /Root is Protected and in windows C:/ is not **Authenticated** and any 1 can easily harm C:...

The problem here is **default settings**. Access to C:\ is in fact restricted with NTFS but the first user(default user on most single user systems) is granted full access. On Windows 95/98/ME all users basically have full access to all files, thanks to the FAT filesystem.

The C:\ drive access *can be* restricted in WinNT based systems using the NTFS filesystem(Windows NT series, Windows 2000, Windows XP and later), which allows setting access permissions for each directory and file. Only users with admin rights can modify system files. The basic problem with it was *by default* the first user account added to a system was automatically given admin rights. So almost everyone ended up running with admin rights. Running with non-admin accounts was also problematic because some apps wouldn't work properly without full access to 'C:\Program Files\' and to perform any installation or updates you had to log out, log in as admin, log out and log in as regular user again. Much of this was addressed by the fast user switching and 'run as' dialogs in XP service packs 2 and 3 and UAC in Vista and Windows 7, but it was still shoddily implemented and far from perfect and many people just disabled it and ran as admin anyway. And some legacy apps still worked only with full read/write access to 'C:\Program Files\'.

I hope that clears your doubts. :rolleyes:
It took me nearly an hour and half to put that together. :D
Cheers

---

### Post by jim_deadlock on 2010-12-19
Thanks balaknair, very enjoyable reading and #12 had me in hysterics :lolflag:

---

### Post by Linyx on 2010-12-20
[SIZE="2"]@balaknair , Thanks Alot & its really very nice Explanation and i GOt all the words which you had Posted,

Once you Got free sometime, Please post why Linux **isn't effected** by viruses....will be greatful...

I can Google it also, but i wouldn't get clear Explanation like your Posts ;)[/SIZE]

---

### Post by migs73 on 2010-12-20
Linyx

I think balaknair needs a break now, lots of great info there, so here is a link to an excellent thread by an Ubuntu Security Guru.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

He explains why viruses are not a great threat but also what precautions you should take to keep your system safe.

Enjoy

Mike :)

---

### Post by Linyx on 2011-01-07
Thanks migs-73, thats helpful....

Now i am somewhat familiar with the term Kernel, like a Core for the Operating system...

Linux Kernel is made by Linux-Torvald, after his great effort for making the Base for the Linux-OS, then GUI kit was Covered by GNU....? means that GNU provided all the GUI  to Linux....?

And what about the Softs(packages) available for this OS, who Provide those Packages via Repositories....?

---

### Post by mark bower on 2011-01-07
@ balaknair

i also would like to thank you for the time you (and others) spent in detail explaining.  will only be able to digest a fraction, but you did clarify some issues on upgrading to newer versions for which i had questions.

mark bower

---

### Post by migs73 on 2011-01-07
> **Linyx said:**
> 
And what about the Softs(packages) available for this OS, who Provide those Packages via Repositories....?

Anybody who cares to do so!

Adobe, Mozilla, Google, you!!! If you can do it?

Like all OS's, anybody can (if they have the skills obviously) make software for it.

---

### Post by Linyx on 2011-01-09
Thats nice, thanks

Debian packages are all written in Python, as i have noticed that many of the applications written for Ubuntu are in Python language.....So if someone try to learn Python and he/she haven't done Fundamental of programming, whether he/she can learn Python in this case...? OR Fundamental C/C++ is the **Basics for all languages**..... ?

Right now i am trying to Learn Fundamentals of Programming and i will start From C/C++ but if someone inform me whether it is important for all other languages , because these are called Fundamentals....

---

