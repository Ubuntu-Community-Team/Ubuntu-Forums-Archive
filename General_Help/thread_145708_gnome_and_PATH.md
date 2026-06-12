---
title: "gnome and PATH"
date: 2006-03-16
forum: General Help
---

### Post by chadmichael on 2006-03-16
I'm trying to force eclipse to use the java stuff that I want.  I have the free java installed, which is found under the default path settings.  I put the "real" java in /opt/java1.5/    I tried to add the appropriate path to the PATH variable in /etc/profile .  This doesn't work.  Someone suggested restarting the gdm, which I did, and it still doesn't seem to take effect within the graphical session.  If I login on the console it takes effect.  It seems to me that the /etc/profile file does not get exectued during a graphical login?  Where do I set PATH changes that take effect for a graphical session?

---

### Post by ComplexNumber on 2006-03-16
did you set the path to the jre too?

i can't remember where it is exactly in ubuntu, but in fedora and most others (except suse), set the PATH in /home/<username>/.bash-profile or /home/<userrname>/.bashrc. for root, replace "home/<username>" with "root".

---

### Post by chadmichael on 2006-03-16
Yeah, well, it seems its a bit more complicated than that.  

/etc/profile and your local .profile run when a login shell is started, it seems that they don't run when I login to the gdm

/etc/bash.bashrc and your local .bashrc run when you start an interactive shell session.  

Indeed, if I put the appropriate path changes in the bashrc files, and start a shell, the path is appropriate, BUT when I try to launch my application, that depends upon the path being correct ( to get the proper java ), it doesn't seem to have the path changes that I've put into files discussed above.  When I say launch I mean that I'm launching the app ( eclipse actually ) through a gnome icon launcher.  

How do I control the PATH used by the Gnome based launchers?

---

### Post by ComplexNumber on 2006-03-16
did you export the PATH?


>  How do I control the PATH used by the Gnome based launchers? like i say, it should be controlled by your .bash-profile or .bashrc files. they don't just determine the path for the terminal, they determine the path for each specific user throughtout your session, whether it be launched from the menu, the terminal, or wherever.

your PATH should looks something like this:
export PATH=/sbin:/bin/:/usr/bin:/usr/local/bin:/usr/games/bin:/opt/java1.5/jre/bin:/opt/java1.5/bin

if the export command isn't immediately before 'PATH', it will just have 'PATH=...." and later on it will have 'export PATH'.

---

### Post by chadmichael on 2006-03-17
I exported the path after adding the changes.  And, this seems to be verified by the fact that when I open a terminal from within gnome, PATH shows my changes.  

The question is:  How is the PATH effected by /etc/bash.bashrc ( the global version of .bashrc) when I open a terminal from within gnome but not when I launch an app via gnome's icon launcher interface ?

---

### Post by ComplexNumber on 2006-03-17
> The question is: How is the PATH effected by /etc/bash.bashrc ( the global version of .bashrc) when I open a terminal from within gnome but not when I launch an app via gnome's icon launcher interface ? apparently, thats only for the command line. its also used in case the .bashrc doesn't exist for any particular user. read [this]("http://lists.debian.org/debian-user/2006/02/msg00451.html").
> 
anything defined in one file can be redefined in the
> subsquent files
>
>         - user defined changes override system defined variables
>
>    system files
>         /etc/profile            = read first for user login
>
>         /etc/bash.bashrc        = interactive shell only
>
>
>    user can do what you want in these files ..
>
>         # after /etc/profile, search in order for the first executable:
>         ~/.bash_profile
>         ~/.bash_login
>         ~/.profile              - not read if the files exists before it
> >         ~/.bashrc               interactive shell read it if it exists


[here]("http://lists.debian.org/debian-user/2006/02/msg00272.html") is somehting else:
> > Is there a good system for setting variables, aliases, etc that need to be
> set for user X, whether I log in at a login prompt or using su?  I'm
> confused by all the different .profile options (there are at least 3 for

> bash, why is that?)

I don't know if there is such a system/program but I can help you clear things up.

Each of these files are read by bash at different times:

.bash_profile is executed when you login.

Stuff you put in there might be your PATH and other important environment variables.

.bashrc is used for non login shells. I'm not sure what that means. I know that RedHat

executes it everytime you start another shell (su to this user or simply calling bash

again)
You might want to put aliases in there but again I am not sure what that means. I
simply ignore it myself.

.profile is the equivalent of .bash_profile for the root. I think the name is changed
to let other shells (csh, sh, tcsh) use it as well. (you don't need one as a user)


There is also .bash_logout wich executes at, yeah good guess...logout.
You might want to stop deamons or even make a little housekeeping .
You can also add "clear" there if you want to clear the screen when you log out.

---

