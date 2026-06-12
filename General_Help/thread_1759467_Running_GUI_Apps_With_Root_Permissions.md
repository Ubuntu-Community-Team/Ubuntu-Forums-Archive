---
title: "Running GUI Apps With Root Permissions"
date: 2011-05-15
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-15
Hello,

I occasionally run into the situation where a GUI app needs to write some value to a configuration file, but then fails to do so because of lack of proper permissions; but also fails to ask for those permissions.  TORK was like that...  I resolved it by 'chown'-ing the relevant file to ***'my-username'*** to allow the configuration script to modify this file, without my having to do it manually.  [COLOR=Blue]***This is an extremely bad practice; and I hated doing it.***[/COLOR]

What I'd like to know is if there's a way to run an app, that's buggy in this way, with those permissions, without having to enter my root password manually, or at least having the app ***itself*** ask for those permissions.

For example, GRUB Customizer is a program that has to run with root permissions, and does ask for them; but if it didn't, how could I get it to run with those permissions???

The command that actually launches GRUB Customizer is:

```
[COLOR=Blue]**su-to-root -X -c grub-customizer**[/COLOR]
```For instance, in the TORK example, could I have configured the launcher in the main-menu to run the following command???:

```
[COLOR=Blue]**su-to-root -X -c tork**[/COLOR]
```Or would I have to write a shell-script with root permissions to call the app in question; and then run the shell-script from the launcher in the main menu???

[COLOR=Blue]***Also, what does the -X -c do???***[/COLOR]

[IMG]http://www.fanhow.com/images/a/a5/Permanent_run_specific_application_as_Administrator_in_Windows_7_003.png[/IMG]




[COLOR=Blue]***Thanks Hannibal***[/COLOR]

---

### Post by chellrose on 2011-05-15
In the terminal, type

```
gksudo tork
```Prefacing any GUI command with "gksudo" will open it with root permissions (though you'll have to enter your password).  I'm sure there's a way to do it directly from within the GUI, but I don't know of a general method.  Hope that helps.

NB: If you're running KDE, you'll want to use kdesudo instead:
```
kdesudo tork
```gksudo works for GNOME, and I suspect Unity, though I have no experience with the latter.

And yes, I think you can configure a launcher to use the gksudo command.

---

### Post by Larkspur on 2011-05-15
> **coljohnhannibalsmith said:**
> For instance, in the TORK example, could I have configured the launcher in the main-menu to run the following command???:

```
[COLOR=Blue]**su-to-root -X -c tork**[/COLOR]
```Or would I have to write a shell-script with root permissions to call the app in question; and then run the shell-script from the launcher in the main menu???

From my exhaustive research (glancing at the man page for su-to-root) that would work, and would do exactly what you're looking for.

> **coljohnhannibalsmith said:**
> [COLOR=Blue]***Also, what does the -X -c do???***[/COLOR]

Apparently the -c has to be there.  It means that the command ("tork") is run as a string, which I don't think it makes any difference for what you're after.  "-X" tells the command that the application is running in X as a graphical program, and so doesn't need to be run through a terminal.  Also, gksu or gksudo seem to acheive the same thing - those commands do work in Natty, BTW - but I know that gufw used su-to-root, so there may be some difference I'm not aware of.

---

### Post by coljohnhannibalsmith on 2011-05-15
> **Sissy13 said:**
> In the terminal, type

```
gksudo tork
```Prefacing any GUI command with "gksudo" will open it with root permissions (though you'll have to enter your password).  I'm sure there's a way to do it directly from within the GUI, but I don't know of a general method.  Hope that helps.

And yes, I think you can configure a launcher to use the gksudo command.

Thanks for the reply,

I haven't tried:

```
[COLOR=Blue]**gksudo tork**[/COLOR]
``` yet; but I did try:

```
[COLOR=Blue]**su-to-root -X -c calculator**[/COLOR]
```And the launcher 'did' ask for root permissions; however, I don't know if it'll actually use them.

[COLOR=Blue][B][I]I wonder if there's a way to test this???


[/I][/B][COLOR=Black]Also, what's the difference between [B][I]gksudo, sudo, and su???





Thanks Hannibal
[/I][/B][/COLOR][/COLOR]

---

### Post by coljohnhannibalsmith on 2011-05-15
> **Larkspur said:**
> Apparently the -c has to be there.  It means that the command ("tork") is run as a string, which I don't think it makes any difference for what you're after.  "-X" tells the command that the application is running in X as a graphical program, and so doesn't need to be run through a terminal.  Also, gksu or gksudo seem to acheive the same thing - those commands do work in Natty, BTW - but I know that gufw used su-to-root, so there may be some difference I'm not aware of.

Thanks for the reply,

I tried it without the -c; and it didn't work.  So, you're right; it has to be there...

I had a feeling that the -X had something to do with the X windowing system.





[COLOR=Blue]***Thanks Hannibal***[/COLOR]

---

### Post by Larkspur on 2011-05-15
> **coljohnhannibalsmith said:**
> [COLOR=Blue]****[COLOR=Black]Also, what's the difference between ***gksudo, sudo, and su???***[/COLOR][/COLOR]


Basically, sudo and su are for commands that don't involve a GUI, and gksu and gksudo are for ones that do.  So, if you're just using the Terminal to move a file from /usr or something, you'd preface it with su(do) but if you wanted to launch Nautilus as Root, you'd use gksu(do).  You can launch Nautilus with sudo, but that can mess up permissions somewhere down the line, or so I've read.  Also, with gksu(do), you get a graphical prompt.

You're probably wondering what difference it makes adding "do" at the end.  None, as far as I can tell, though it does make it sound more like "pseudo."

---

### Post by doas777 on 2011-05-15
ok, heres the breakdown.

first there was ['su']("http://en.wikipedia.org/wiki/Su_%28Unix%29") for "set User". you can use su to switch to any user you want, but the default if you do not pass in a username, is 'root'. most people used 'su' to get root from a non-root shell, so people started calling it 'superuser' but that is kind of misleading. 

[sudo ]("http://linux.about.com/od/commands/l/blcmdl8_sudo.htm")is a CLI-Only method for setting a user, and running a single task with it. you can use it in interactive mode with -s however. once again, it is almost exclusively used to get root. 
[URL="http://manpages.ubuntu.com/manpages/intrepid/man1/su-to-root.1.html"]
su-to-root[/URL] is a wrapper around su (so an alternative to sudo). it uses -X to run gui applications via X instead of the terminal. 

[gksu ]("http://linux.about.com/cs/linux101/g/gksu.htm")is a GUI frontend to sudo, and is used to set user for a gui application, much like su-to-root with -X.


my advice is to try to get gksu working with your command, just because I have never seen su-to-root around. doesn;t mean it;s bad, just not the standard approach.

---

### Post by coljohnhannibalsmith on 2011-05-15
[doas777]("http://ubuntuforums.org/member.php?u=451394"),

Thanks for the great explanations and all the links...




Hannibal

---

### Post by coljohnhannibalsmith on 2011-05-17
> **doas777 said:**
> My advice is to try to get ***gksu*** working with your command, just because I have never seen su-to-root around. doesn;t mean it;s bad, just not the standard approach.

[COLOR=Blue]***I've tried this and it does appear to be a superior approach; as the extra [COLOR=Black]-X -c[/COLOR] switches are unnecessary!!!***[/COLOR]

**This problem now appears to be solved...**

[IMG]http://tshirtgroove.com/wp-content/uploads/2008/10/problem-solved-tshirt.jpg[/IMG]

---

### Post by Munzx on 2011-05-31
[LEFT][SIZE=2][COLOR=black]hi! :)[/COLOR][/SIZE]

[SIZE=2][COLOR=black]i've just dumped my Windows OS a week ago in order to join the free world of ubuntu :) , i was very glad with it and everything ran smoothly but some troubles trying to save,delete or edit some files in gui as i don't have the privilage to!!! , so i googled till i found this:[/COLOR][/SIZE]
[SIZE=2][COLOR=black]https://help.ubuntu.com/community/RootSudo[/COLOR][/SIZE]
[SIZE=2][COLOR=black]then i created a launcher on my desktop with following command :[/COLOR][/SIZE]
[SIZE=2][COLOR=black]gksudo "gnome-open %u"

(i called the launcher "super user")
which enabled me to drag-and-drop any folder and open it as "root" user ,
then from the properties > permessions i changed the priviliges
so i can have full access and control without going through
(drag-drop-process) again , and now am happy with it.
:) 
[/COLOR][/SIZE]
[/LEFT]

---

