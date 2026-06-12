---
title: "Promissions?"
date: 2009-10-27
forum: General Help
---

### Post by realchamp on 2009-10-27
Hello.

To be honest I am sick of all these root promissions in Ubuntu Desktop 9.04.

Is there anyway to disable them? As I cannot save my files in the needed folders and I have to write my password all the damn time! By the way... I am the only user on this PC. How can I grand myself "root" access?


- realchamp.

---

### Post by mcduck on 2009-10-27
Why would you need to save any of your files outside of your home directory?

(And no, nobody is going to tell you how to enable root account. That's against the forum rules. The basic idea is that anybody who understands what that means, and is able to handle the root account without breaking things, will also be able to figure out how to do it on their own..)

If you tell what you are trying to do that results in you having to type your password all the time we'll probably be able to tell you how to do it in easier way. :)

---

### Post by CharlesA on 2009-10-27
> **mcduck said:**
> Why would you need to save any of your files outside of your home directory?

(And no, nobody is going to tell you how to enable root account. That's against the forum rules. The basic idea is that anybody who understands what that means, and is able to handle the root account without breaking things, will also be able to figure out how to do it on their own..)

This. Even if you aren't able to figure it out on your own, google will probably turn something up.

You don't need root access outside of sudo.

---

### Post by martrn on 2009-10-27
> **realchamp said:**
> To be honest I am sick of all these root promissions in Ubuntu Desktop 9.04.Is there anyway to disable them? As I cannot save my files in the needed folders and I have to write my password all the damn time! By the way... I am the only user on this PC. How can I grand myself "root" access?- realchamp.

```
gksudo gedit /etc/sudoers
```

Find :
```
Defaults
```

```
add a line after saying
passwd_timeout=44640
```

Then you will only need to type your password once a month.

---

### Post by alphaniner on 2009-10-27
I use Ubuntu at work.  99% of what I do *really* requires root.  Still, I haven't enabled the root account.  There's just no point in actually logging into the GUI as root.  I do edit my sudoers file so that I am never prompted for my password.  But I don't do that on my home PC because it's rather reckless and stupid.  

There is also a command I use to make my life easier, but I can't tell you about it here.  Seek and ye shall find.

---

### Post by mcduck on 2009-10-27
> **alphaniner said:**
> I use Ubuntu at work.  99% of what I do *really* requires root.  Still, I haven't enabled the root account.  There's just no point in actually logging into the GUI as root.  I do edit my sudoers file so that I am never prompted for my password.  But I don't do that on my home PC because it's rather reckless and stupid.  

There is also a command I use to make my life easier, but I can't tell you about it here.  Seek and ye shall find.

I'd be interested to hear what you do for your work if it really requires root (so that using fakeroot and "sudo -i" or "gksudo nautilus" isn't enough)?

---

### Post by alphaniner on 2009-10-27
Sorry, I worded that wrong.  I should have said requires 'root privileges' or 'root powers' or whatever.

To put it another way, almost every command would require me to use sudo if I didn't know how to avoid it.

---

### Post by realchamp on 2009-10-27
right..

I installed XAMPP in "/" 
(Same folder as root, sys and boot)
So.. /opt/lampp is its location. Whenever I attempt to save a file in there it denies me.

And why in the world is it agianst the forum rules to tell me how to? I've been on Google, usually it returns me nonusable stuff. 

-- I can easily run my XAMPP program. However I can still not delete any .php files in there or create any new ones. Just wondering if I should delete it and install directly to my home folder. Since this is getting nowhere, though, why would I breake something?

---

### Post by mcduck on 2009-10-27
> **alphaniner said:**
> Sorry, I worded that wrong.  I should have said requires 'root privileges' or 'root powers' or whatever.

To put it another way, almost every command would require me to use sudo if I didn't know how to avoid it.

Ah, OK, that makes more sense. :)

I was just wondering since every now and then people say that some things really require root, but I can't think of anything and haven't found anything during the years I've spent running Linux. I almost had to enable it when I had to compile a couple of kernels but then I found fakeroot.. :)

---

### Post by doas777 on 2009-10-27
check out the first sentence of this (a description of /opt):
[http://www.pathname.com/fhs/2.2/fhs-3.12.html](http://www.pathname.com/fhs/2.2/fhs-3.12.html)

**EGIN RATIONALE**

   
  The use of /opt for add-on software is a well-established practice in the UNIX community.  The System V Application Binary Interface [AT&T 1990], based on the System V Interface Definition (Third Edition), provides for an /opt structure very similar to the one defined here.  The Intel Binary Compatibility Standard v. 2 (iBCS2) also provides a similar structure for /opt. 
 Generally, all data required to support a package on a system must be present within /opt/<package>, including files intended to be copied into /etc/opt/<package> and /var/opt/<package> as well as reserved directories in /opt. 
 The minor restrictions on distributions using /opt are necessary because conflicts are possible between distribution-installed and locally-installed software, especially in the case of fixed pathnames found in some binary software.   
 
**END RATIONALE**

---

### Post by martrn on 2009-10-27
What does ```
sudo su -- 
``` mean ?

I know never to type it, as its best just to edit your sudoers file if you are typeing your password all the time, but what does this do (other than being an idiot) ?

---

### Post by t0p on 2009-10-27
Well, as mcduck wrote earlier, it's easy to allow yourself to lon in as root.  But if you can't figure out oan your own how to do it, it's probably best that you don't do it.  An enabled root login in ignorant hands can be pretty "dangerous" to your system.

Of course there are ways to give yourself admin privs that don't entail typing in your password every 5 minutes.  If you're doing stuff in the terminal, the command

```
sudo -s
```

will put you in a root terminal that lasts as long as you like.  If you're using Nautilus (the GUI file manager) you can hit Alt+F2 and type into the box

```
gksudo nautilus
```

Alternatively you can install the package **nautilus-gksu**, then you can right-click on a file or folder and there will be the option "Open as administrator".

---

### Post by sisco311 on 2009-10-27
> **realchamp said:**
> right..

I installed XAMPP in "/" 
(Same folder as root, sys and boot)
So.. /opt/lampp is its location. Whenever I attempt to save a file in there it denies me.

And why in the world is it agianst the forum rules to tell me how to? I've been on Google, usually it returns me nonusable stuff. 

-- I can easily run my XAMPP program. However I can still not delete any .php files in there or create any new ones. Just wondering if I should delete it and install directly to my home folder. Since this is getting nowhere, though, why would I breake something?

According to this howto: [http://ubuntuforums.org/showthread.php?t=223410]("http://ubuntuforums.org/showthread.php?t=223410")
 
You can make a public_html  directory in home directory:
```
mkdir ~/public_html
```

and link it  to /opt/lampp/htdocs:
```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```

---

### Post by P4man on 2009-10-27
what a terrible idea to install it in /. I guess that means you didnt install it from the repo's either?

but anyhow, the folders where you put your website in, just can just change ownership and give read/write permissions so that your user account can write in them. Or you can configure apache and php to use folders in your homefolder.

 this is no reason to log in as root, quite on the contrary,...

---

### Post by mcduck on 2009-10-27
> **realchamp said:**
> right..

I installed XAMPP in "/" 
(Same folder as root, sys and boot)
So.. /opt/lampp is its location. Whenever I attempt to save a file in there it denies me.

And why in the world is it agianst the forum rules to tell me how to? I've been on Google, usually it returns me nonusable stuff. 

-- I can easily run my XAMPP program. However I can still not delete any .php files in there or create any new ones. Just wondering if I should delete it and install directly to my home folder. Since this is getting nowhere, though, why would I breake something?

First, I'd actually recommend using Ubuntu's own LAMP stack instead of XAMPP. It will integrate better to rest of the system and save you from some extra work.

But if you still want to use XAMPP, then yes, you might want to install it into your home directory. Or alternatively just hit Alt-F2 and run "gksudo nautilus" to start file manager as root, allowing you to easily manage files in that directory. You can even make a launcher on your desktop/panel/menu if you want.

(The forums rules prohibit instructions for enabling root since these forums support Ubuntu's security model, which includes using "sudo" instead of direct root access. And also because, like I said, those who really might need to enable root account will already now how to do it since it's actually quite obvious. It's just not necessary, and in most cases beginners would enable it without understanding what they do, and that they don't really need to do it. And that would make giving support on these forums a lot harder for no actual benefits...)

---

### Post by t0p on 2009-10-27
> **martrn said:**
> What does ```
sudo su -- 
``` mean ?

I know never to type it, as its best just to edit your sudoers file if you are typeing your password all the time, but what does this do (other than being an idiot) ?

Okay, so what's wrong with using "sudo su"?  I frwquently use "sudo -s", which is pretty much the same thing, and I don't think it's idiotic.  Please explain why you think I'm an idiot.

---

### Post by alphaniner on 2009-10-27
I use **sudo su**, until recently (~10 mins ago) I thought it was one of those commands we were forbidden to mention here.  I don't know if the '--' changes anything, but I'm not about to find out.

The only difference I notice is that **sudo su** doesn't take me to /root.

---

### Post by sisco311 on 2009-10-27
> **t0p said:**
> Okay, so what's wrong with using "sudo su"?  I frwquently use "sudo -s", which is pretty much the same thing, and I don't think it's idiotic.  Please explain why you think I'm an idiot.

if you use "sudo -s" some environment variables are preserved.
this may cause problems. i.e.
```
sudo -s
echo $HOME
/home/username
exit
sudo -i
echo $HOME
/root

```

---

### Post by t0p on 2009-10-27
> **alphaniner said:**
> I use **sudo su**, until recently (~10 mins ago) I thought it was one of those commands we were forbidden to mention here..

The Ubuntu security model involves using "sudo".  "sudo su" is a documented use of the "sudo" command.  This means it's part of the Ubuntu security model and therefore this forum doesn't mind its being suggested.

---

### Post by realchamp on 2009-10-27
> **t0p said:**
> Well, as mcduck wrote earlier, it's easy to allow yourself to lon in as root.  But if you can't figure out oan your own how to do it, it's probably best that you don't do it.  An enabled root login in ignorant hands can be pretty "dangerous" to your system.

Of course there are ways to give yourself admin privs that don't entail typing in your password every 5 minutes.  If you're doing stuff in the terminal, the command

```
sudo -s
```will put you in a root terminal that lasts as long as you like.  If you're using Nautilus (the GUI file manager) you can hit Alt+F2 and type into the box

```
gksudo nautilus
```Alternatively you can install the package **nautilus-gksu**, then you can right-click on a file or folder and there will be the option "Open as administrator".
I don't care, why would I damage my own system?
I'd probably give that nautilus a try. :)

> **sisco311 said:**
> According to this howto: [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)
 
You can make a public_html  directory in home directory:
```
mkdir ~/public_html
```and link it  to /opt/lampp/htdocs:
```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```

> **P4man said:**
> what a terrible idea to install it in /. I guess that means you didnt install it from the repo's either?

but anyhow, the folders where you put your website in, just can just change ownership and give read/write permissions so that your user account can write in them. Or you can configure apache and php to use folders in your homefolder.

 this is no reason to log in as root, quite on the contrary,...
What's the "repo's"? Hmm sounds interessting, I want to give that one a go too.

> **mcduck said:**
> First, I'd actually recommend using Ubuntu's own LAMP stack instead of XAMPP. It will integrate better to rest of the system and save you from some extra work.

But if you still want to use XAMPP, then yes, you might want to install it into your home directory. Or alternatively just hit Alt-F2 and run "gksudo nautilus" to start file manager as root, allowing you to easily manage files in that directory. You can even make a launcher on your desktop/panel/menu if you want.

(The forums rules prohibit instructions for enabling root since these forums support Ubuntu's security model, which includes using "sudo" instead of direct root access. And also because, like I said, those who really might need to enable root account will already now how to do it since it's actually quite obvious. It's just not necessary, and in most cases beginners would enable it without understanding what they do, and that they don't really need to do it. And that would make giving support on these forums a lot harder for no actual benefits...)
I don't want to spend time on learning that, it probably doesn't have MySQL, PHP, Perl and so on as standard.

---

### Post by realchamp on 2009-10-27
> **t0p said:**
> Well, as mcduck wrote earlier, it's easy to allow yourself to lon in as root. But if you can't figure out oan your own how to do it, it's probably best that you don't do it. An enabled root login in ignorant hands can be pretty "dangerous" to your system.

Of course there are ways to give yourself admin privs that don't entail typing in your password every 5 minutes. If you're doing stuff in the terminal, the command

```
sudo -s
```will put you in a root terminal that lasts as long as you like. If you're using Nautilus (the GUI file manager) you can hit Alt+F2 and type into the box

```
gksudo nautilus
```Alternatively you can install the package **nautilus-gksu**, then you can right-click on a file or folder and there will be the option "Open as administrator".
I don't care, why would I damage my own system?
I'd probably give that nautilus a try. :)

> **sisco311 said:**
> According to this howto: [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)
 
You can make a public_html  directory in home directory:
```
mkdir ~/public_html
```and link it  to /opt/lampp/htdocs:
```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```

> **P4man said:**
> what a terrible idea to install it in /. I guess that means you didnt install it from the repo's either?

but anyhow, the folders where you put your website in, just can just change ownership and give read/write permissions so that your user account can write in them. Or you can configure apache and php to use folders in your homefolder.

 this is no reason to log in as root, quite on the contrary,...
What's the "repo's"? Hmm sounds interessting, I want to give that one a go too.

> **mcduck said:**
> First, I'd actually recommend using Ubuntu's own LAMP stack instead of XAMPP. It will integrate better to rest of the system and save you from some extra work.

But if you still want to use XAMPP, then yes, you might want to install it into your home directory. Or alternatively just hit Alt-F2 and run "gksudo nautilus" to start file manager as root, allowing you to easily manage files in that directory. You can even make a launcher on your desktop/panel/menu if you want.

(The forums rules prohibit instructions for enabling root since these forums support Ubuntu's security model, which includes using "sudo" instead of direct root access. And also because, like I said, those who really might need to enable root account will already now how to do it since it's actually quite obvious. It's just not necessary, and in most cases beginners would enable it without understanding what they do, and that they don't really need to do it. And that would make giving support on these forums a lot harder for no actual benefits...)
I don't want to spend time on learning that, it probably doesn't have MySQL, PHP, Perl and so on as standard.

---

### Post by mcduck on 2009-10-27
> **sisco311 said:**
> if you use "sudo -s" some environment variables are preserved.
this may cause problems. i.e.
```
sudo -s
echo $HOME
/home/username
exit
sudo -i
echo $HOME
/root

```

+1 for this. :)

The recommended command is "sudo -i", not "sudo su" or "sudo -s".

Just like graphical apps should be launched using "gksudo" or "kdesu" instead of "sudo".

In many cases the differences are meaningless, but in others using the wrong command will have some nasty side effects, like your user's files becoming owned by root.

---

### Post by sisco311 on 2009-10-27
> **t0p said:**
> The Ubuntu security model involves using "sudo".  "sudo su" is a documented use of the "sudo" command.  This means it's part of the Ubuntu security model and therefore this forum doesn't mind its being suggested.

sudo and su are two different commands. both are setuid root.

I would try to avoid to use them together. Instead you can use:
```

sudo -s   #  su
sudo -i   #  su -

```

---

### Post by martrn on 2009-10-27
I would say its daft, because doing this (either way) you are ignoring all file permissions.  They are there for a reason, you can always sudo something if you need to, ruuning as root, you can read/write anything.  Don't you pay any attention to file permissions at all ?

---

### Post by mcduck on 2009-10-27
> **realchamp said:**
> 
I don't want to spend time on learning that, it probably doesn't have MySQL, PHP, Perl and so on as standard.

yes it does. That's what makes it LAMP instead of just Apache. :)
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
(Adding Perl to the stack is just a question of, well, installing Perl... :))

---

### Post by akakingess on 2009-10-27
> **mcduck said:**
> yes it does. That's what makes it LAMP instead of just Apache. :)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
(Adding Perl to the stack is just a question of, well, installing Perl... :))

+1, that's what LAMP stands for, Linux, Apache, MySql, and PHP, now it's just a matter of installing Perl, which is easily done from the repo's. Have you gone into Administration-->Synaptic Package Manager? That is where all of the software is listed and ready to check off and install.

---

### Post by t0p on 2009-10-27
> **realchamp said:**
> I don't care, why would I damage my own system?


Obviously you wouldn't do that deliberately.  But you might accidently do something that adversely affects your system.

> **martrn said:**
> I would say its daft, because doing this (either way) you are ignoring all file permissions.  They are there for a reason, you can always sudo something if you need to, ruuning as root, you can read/write anything.  Don't you pay any attention to file permissions at all ?

Is this directed at me?

If so, you don't understand.  When you use **sudo -s** (or **sudo -i**), you open a root shell.  You do whatever it is you want to do, then give the command **exit**.  That ends the root shell.

You said that you edit the sudoers file so you have to type in your password once a month.  This means when you want to do an administrative task, you use "sudo" but don't need your password.  This means you can give "sudo" commands without the pause for thought that needing the password requires.

I use "sudo -s", then I exit the root shell when I've finished with it.  You use "sudo" for a month without needing the password.  Exactly how is your approach less "idiotic" than mine?

---

### Post by doas777 on 2009-10-27
op. no point in arguing if you don't wanna. took me less than 30 secs to find the sought info via google. if you do wanna argue though, I'm sure you've noticed that we are all game for a debate.

---

### Post by sisco311 on 2009-10-27
> **doas777 said:**
> op. no point in arguing if you don't wanna. took me less than 30 secs to find the sought info via google. if you do wanna argue though, I'm sure you've noticed that we are all game for a debate.

it's easy to find the answer when you know the question.

;)

EDIT:

*How do I login as root?* means *I'm doing something wrong. Every time I try to do [I]xy* i'm asked for my password.[/I] :)

---

### Post by absolutezero1287 on 2009-10-27
> **realchamp said:**
> right..

I installed XAMPP in "/" 
(Same folder as root, sys and boot)
So.. /opt/lampp is its location. Whenever I attempt to save a file in there it denies me.

And why in the world is it agianst the forum rules to tell me how to? I've been on Google, usually it returns me nonusable stuff. 

-- I can easily run my XAMPP program. However I can still not delete any .php files in there or create any new ones. Just wondering if I should delete it and install directly to my home folder. Since this is getting nowhere, though, why would I breake something?

This is how Linux works. The group/users permissions system is designed so that the user controls his/her home directory while the administrative account or "root" is reserved for...what else...administrative duties.

I really don't see what you're complaining about. Just open a terminal and use sudo -i and you'll be able to run commands as the root user. To switch back just type exit.

---

### Post by sisco311 on 2009-10-27
> **absolutezero1287 said:**
> This is how Linux works. The group/users permissions system is designed so that the user controls his/her home directory while the administrative account or "root" is reserved for...what else...administrative duties.

I really don't see what you're complaining about. Just open a terminal and use sudo -i and you'll be able to run commands as the root user. To switch back just type exit.

The OP is not complaining. He doesn't understands the [linux filesystem hierarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") and [permissions]("https://help.ubuntu.com/community/FilePermissions").

Instead of arguing with him we should pointing him in the right direction.

---

### Post by absolutezero1287 on 2009-10-27
> **sisco311 said:**
> The OP is not complaining. He doesn't understands the [linux filesystem hierarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") and [permissions]("https://help.ubuntu.com/community/FilePermissions").

Instead of arguing with him we should pointing him in the right direction.

Well, if I came off as argumentative then I apologize to the OP.

@OP: Follow sisco311's advice and learn about the how UNIX filesystems are structured. It should all become clear as to why you need root access to make changes to / and its sudirectories except for $HOME.

I used to be a newbie, too. However, I found that a lot of my questions could be answered by research.

---

### Post by realchamp on 2009-10-30
Okay. I have solved this! Thanks alot! :)

I used the "mirror" to direct it to my public_html folder and it worked perfectly! Thanks,
- realchamp.

---

### Post by katzsper on 2009-11-03
> **alphaniner said:**
> I use Ubuntu at work.  99% of what I do *really* requires root.  Still, I haven't enabled the root account.  There's just no point in actually logging into the GUI as root.  I do edit my sudoers file so that I am never prompted for my password.  But I don't do that on my home PC because it's rather reckless and stupid.  

There is also a command I use to make my life easier, but I can't tell you about it here.  Seek and ye shall find.


What is the point of mentioning something you can't talk about?

---

