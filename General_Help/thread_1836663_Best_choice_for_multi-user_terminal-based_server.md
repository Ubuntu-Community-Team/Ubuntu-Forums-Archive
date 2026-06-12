---
title: "Best choice for multi-user terminal-based server???"
date: 2011-08-31
forum: General Help
---

### Post by LumbeeNDN on 2011-08-31
Hey folks. I am IT Staff at a tech college and one of our instructors teaches a mysql course. They would like a linux server with accounts for each student, and their own mysql DB. So I have a couple of questions. First, is Ubuntu a good choice here? I'm thinking it will certainly server the purpose, but just wondering if there is a better choice out there for such a system. I would like this to be a bear bones sytem, so do I even need the gui desktop? The way I'd like to configure the server is I will have root access, but I would like to create a 'super user' which would be the instructor. They would be able to create the student accounts who would be locked down...i.e. only have access to their home directories, and thier DB in mysql. Also any tips on configuration in mysql would be helpful too. 

I know its alot of questions. I will be doing lots of googling over the next couple weeks. Just wanted to see if anyone out there has set up a linux server under similar conditions. Thanx!

---

### Post by corrytonapple on 2011-08-31
I cannot help you with all of this, but I can with some.  :)
K, so will your students be typing up code?  If so, then a GUI is preferable.  You can remove everything else from the system though, such as logout widgets and applications like so.  But, it may also be possible to code from the command line (although I am not sure).  Root access being the teacher from a CLI (Command Line Interface) is easily done with some account tweaking.  IDK much about MySQL, although I am a web dev.  So if anyone else posts, I may learn a bit. :D
Altogether, Ubuntu will work.  But Arch Linux is known widely for being bare bones, and it comes (Default) with no GUI, and a open root account with no modding for your instructor(s).  You can install a GUI, and then install one notepad app and that could be the whole extent of your GUI.  
I suggest you look into Arch. They also have excellent support and the best Linux wiki on the web.  Not just my opinion, but by many.
Good Luck and I will be watching/replying to this thread. :D

---

### Post by LumbeeNDN on 2011-08-31
The only coding the students will be doing is in mysql (queries), and its all done at the command line. I'll look int  Arch Linux...always looking for a new flavor to play with. ;)

---

### Post by decoherence on 2011-08-31
Doesn't really matter. Ubuntu Server or Arch will do what you want pretty easily. You will, of course, want to install the openssh server which is how your kids will log in. Then add the users (or integrate with ldap -- that's what i did but unless you have a LOT of students in this course, it's probably not worth the effort), make your teacher's account a member of the 'admin' group which, on Ubuntu at least, should allow them to use sudo.

install mysql.... i don't recall if users need to be part of a special group to use it but you can find out quickly with your test account.

basically, that's it. should be a blessedly simple set up (i hope i didn't just jinx you there!) i know that's what i was thinking when i was doing the ldap integration... "this would be such a blessedly simple set up if it weren't for this ldap stuff!" anyway, good luck

---

### Post by nothingspecial on 2011-08-31
For this king of project I would say debian. Ubuntu would be fine though.

---

### Post by snowpine on 2011-08-31
Ubuntu Server is a fine choice for your project. "sudo" is capable of giving admin rights to your user and the instructor's user. 

The Server Guide is a great introduction to installing and configuring Ubuntu Server: [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

I do not recommend Arch Linux for this task because, as a "rolling release" distribution, it is in a constant state of flux. Ubuntu 10.04 on the other hand offers "long-term support" (no major changes; only minor updates necessary for stability and security) through April 2015.

---

### Post by LumbeeNDN on 2011-08-31
@decoherence Nope, no LDAP...only 15-20 students so I don't think it will be that big a deal for the instructor to manually create the users.

@snowpine > I do not recommend Arch Linux for this task because, as a "rolling release" distribution, it is in a constant state of flux.

Good point. 

Oh, and this is a dumb question is there a difference in Ubuntu Desktop and Ubuntu server?

Also, is there an easy way to not install the gui? Like a switch during install?

---

### Post by snowpine on 2011-08-31
> **LumbeeNDN said:**
> @snowpine 

Good point. 

Oh, and this is a dumb question is there a difference in Ubuntu Desktop and Ubuntu server?

Also, is there an easy way to not install the gui? Like a switch during install?

Ubuntu Desktop has a GUI (Gnome/Unity) and desktop applications such as Firefox, LibreOffice, etc.

Ubuntu Server has no GUI and includes server applications such as Apache etc.

I believe there are also slight differences in the kernel.

Many of your questions are answered here: [https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

---

### Post by nothingspecial on 2011-08-31
> **LumbeeNDN said:**
> 

Also, is there an easy way to not install the gui? 

Yep, install the server edition.

---

### Post by pAsM on 2011-08-31
Hello,
[INDENT]Let me offer some advice as I know the best solution for you. My background is Web Hosting, so we have the ability to give out shell accounts to every domain we host (currently over 6,000). We use a product named cPanel as it is the industry standard fro hosting, but it is EXPENSIVE. 

You could use something like Kloxo which will give every student access to their own MySQL databases and access to a (jailed) shell to do their work. Kloxo is Open Source as well.

The advantage to this method is you can set quotas on users. You can also setup the professor as a "reseller" which gives them access to their students work.

The Web Hosting Model actually suits your needs quite well for both security and functions.
[/INDENT]

---

