---
title: "Want to be a linux professional - suggestions ?"
date: 2012-01-21
forum: General Help
---

### Post by rishi_singh on 2012-01-21
Hi guys !

I have **ubuntu desktop **and I use it only for basic tasks like surfing, documents etc. 
I want to learn the basics of a Linux distro - the structure, how it communicates with the hardware, why is it more secure than windows and stuff. 

Can you suggest some books for this purpose ?

I was thinking of learning all this so that i can become a **linux admin**.
Where can i get a comprehensive list of responibilities of a linux admin ? 
Is it better to use **redhat** as a learning tool to becom a linux admin, instead of **ubuntu desktop**?

---

### Post by WorMzy on 2012-01-21
If you want to learn more about Linux, I recommend that you install Arch Linux, from scratch, using the [beginners' guide]("https://wiki.archlinux.org/index.php/Beginners%27_Guide"). If you encounter any problems, use the wiki and your preferred search engine to seek out solutions on your own; and instead of just copying and pasting commands, take the time to read them and see if you can understand what they're doing.

---

### Post by rishi_singh on 2012-01-23
Have I posted this in the right section ???

---

### Post by mastablasta on 2012-01-23
yes and you received a good response. there are linux distributions out there that are designed as a learning tool to help you learn how linux is made and how the inside of it works. such as Linux From Scratch (LFS).
 
another way (if you want to stay on Ubuntu) is to read a few books on Ubuntu Server. Theer are plenty found online.

---

### Post by Q-collective on 2012-01-23
Linux From Scratch and Gentoo are both good solutions if you want to get a grip on Linux's internals.

---

### Post by conradin on 2012-01-23
Ubuntu can do everything you need. Just keep in mind it starts out set up for you. The role of a linux system admin, in my experience is of any other admin. As far as exclusive linux system admin jobs they seem pretty rare. I do linux sys admin work, and work on stuff from dos to windows 7 and the periodic Unix systems. The linux priorities for me are setting up ssh servers, managing users, changing permissions, installing poorly writen and archiac software, trying to answer really bizaire questions, data recovery, scripting, batch job processing, system security, and data recovery. Every thing else I use linux for is my personal preference. 
Evi Nemith writes some good books on this subject:
UNIX System Administration Handbook (3rd Edition)

My recommendation is pick up a linux+ certification book and study that. Go for the license if you want, the Comptia exams are well regarded in industry another example is the A+ certification. 
Numerous other good reads exist, like the Filesytem Hierarchy Standard:
[www.pathname.com/fhs/pub/fhs-2.3.pdf](www.pathname.com/fhs/pub/fhs-2.3.pdf)

or the GNU Command line tools summary:
[http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html](http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html)

---

### Post by rishi_singh on 2012-01-29
> **conradin said:**
> 
Evi Nemith writes some good books on this subject:
UNIX System Administration Handbook (3rd Edition)

My recommendation is pick up a linux+ certification book and study that. Go for the license if you want, the Comptia exams are well regarded in industry another example is the A+ certification. 


Aha ! Thats the kind of stuff i was looking for. I am grateful to you for giving me such useful advice.
Since you recommended a unix book, I want to know if it will help me to understand linux too ? Or maybe prepare me for learning linux.

---

### Post by Artif on 2012-01-29
> **rishi_singh said:**
> 
Is it better to use **redhat** as a learning tool to becom a linux admin, instead of **ubuntu desktop**?

You may see some popularity charts:
[http://w3techs.com/blog/entry/debian_is_now_the_most_popular_linux_distribution_on_web_servers](http://w3techs.com/blog/entry/debian_is_now_the_most_popular_linux_distribution_on_web_servers)
And site [http://distrowatch.com/](http://distrowatch.com/)

They have some differences in core security software set in a ways of by which utilities system is managed.

They have different types of packages infrastructure. Admin must be able to apply patches to sources, compile them and deploy binaries. In case of urgent security issues. It is a good practice not to have sources and compiler on server - to build binary packages on a workstation and then deploy them on server. Binary packages infrastructure type may play a role.

Overall integrity is important. If you want only administer systems it will be good idea to choose one vendor for desktop and server software. In case of heterogenous infrastructure you may have some integration issues, leading you into spending of time for deep investigations on how the software to be used is designed. On the other hand - while a study you'll become more universal, flexible specialist.

P.S.

RedHat - commercial solution and conservative versions of software, with 5 year support of a distro version.

CenOS - is relabeling of RedHat Enterprise Linux (RHEL). As RedHat creates opensource systems, but with no binaries for free, CentOS maintainers do relabeling of sources, compile them and you may use it for free. So you can have RHEL with updates (do not forget to add EPEL repositories for other software). Updates delay - see CentOS site. Security updates are fast.

Fedora - think this is incubator of software tech. for RedHat: up to date software versions, innovations, but with extremely short community support for each distro versions. It means permanent whole system upgrade or short support with security updates, for enterprise both are painful. Good for IT education, but not for enterprise deployment.

Debian also have conservative and innovative distros. Ubuntu is Debian relative and derivative, I think Ubuntu is not bad balance of innovations and conservatism. Now it have 5 year support for LTS releases, the same as RHEL.

---

### Post by conradin on 2012-01-29
> **rishi_singh said:**
> Aha ! Thats the kind of stuff i was looking for. I am grateful to you for giving me such useful advice.
Since you recommended a unix book, I want to know if it will help me to understand linux too ? Or maybe prepare me for learning linux.

Unix spawned Linux and has MUCH in common. The history may or may not be as interesting, Theres a pretty geeky film about it called revolution OS.
But if you learn about the basics of Unix, you should have a decent handle on Linux. Theres alot to learn. If you know C programing that is extraordinarily helpful. 

Many other great books on linux exist. what you should read depends on your motives, and present skill set. The ORiely books cover a variety of Linux subjects.

---

