---
title: "setting permission"
date: 2010-07-14
forum: General Help
---

### Post by jayanramesh on 2010-07-14
Hey,
> After meddling with ".private folder's permission" in home folder I am not able to get into my desktop and exibiting the message 
"Natilus could not create the following required folders: /home/jayan/Desktop, /home/jayan/.config/nautilus
Before running nautilus please create thease folders,or set permission such that Nautilus can create them"

Could anyone on Earth with kind heart assist me through to resolve this prob.
Thank you

PS:My OS is Lucid Lynx 64 Bit

---

### Post by robsoles on 2010-07-14
Can you get a terminal prompt by entering your own login details when booting off the hard drive containing the OS you have done this to?

If so there is a quick and easy way to fix this provided the folders and files are still intact, just with bad permissions or ownership - tell me if you can open terminal using your own username and I will probably be beaten to telling you the commands required to regain control of your desktop.

If not then it is only so much more painful a process to get it back but plenty here can help you through that too.

---

### Post by jayanramesh on 2010-07-14
NO, I can't get in to my terminal

---

### Post by robsoles on 2010-07-14
Boot up from a LiveCD.

Mount the partition that contains your /home directory. Use the LiveCD's GUI/Desktop to open /media and determine what the name of the partition is when it is mounted - usually the label but can be weird and long number.

Assuming that you use the same username you have used on ubuntuforums.org and that the partition's name is 'simply_this' open terminal and type command like following but replace my assumed names with the right ones!

(If this partition is mounted as '/home' then the bit '/home' below should be dropped from the line)
```
sudo chmod -R 700 /media/simply_this/home/jayanramesh/*
```**[COLOR=Red]IT IS IMPORTANT THAT YOU ONLY HIT YOUR PERSONAL FILES IN YOUR HOME FOLDER WITH THESE PERMISSIONS BECAUSE APPLYING ELSEWHERE WILL MAKE YOUR SYSTEM UNBOOTABLE ALTOGETHER![/COLOR]**[COLOR=Red]

[COLOR=Black]It is at least the slightest bit risky even if you do only hit your private files properly but it should give you the ability to Login to your GUI/Desktop after booting from your own HDD and we can look for negative effects this may have had from there.[/COLOR]
[/COLOR]

---

### Post by jayanramesh on 2010-07-15
Dear robsoles,

Thank you so much for your prompt response .Finally, I reinstalled the OS yesterday before I have seen your reply.But now I have the different problem as I had earlier.When I typed "SUDO NAUTILUS" in terminal to open file system as a root it gives me the error as > " Nautilus could not create the required folder "/root/.config/nautilus".--Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it
Could you guide me to solve this one?.

Thank you

PS Please can you explain why this happens so?.

---

### Post by bodhi.zazen on 2010-07-15
I do not know why you are getting that error, but you should be useing gksu to run graphical applications.

```
gksu nautilus
```

Running graphical applications with sudo or su may result in changing of permission of files in your $HOME directory to root and permissions problems as you describe.

---

### Post by AlphaLexman on 2010-07-15
You are running nautilus as 'root', not as yourself. DO NOT change permissions for '/root'.

YOUR settings and configurations should be in '/home/username/.nautilus'

check:```
whoami
```

---

### Post by robsoles on 2010-07-15
<snip> - ninja posted and realised I was purporting gnome, kde or whatever other desktop in use as the file-manager - still can't see point though, may as well use a terminal if you need to be that powerful.

---

### Post by jayanramesh on 2010-07-15
Dear AlphaLexman,
Output is jayan

---

### Post by AlphaLexman on 2010-07-15
Post the result of:```
nautlius --no-desktop
```
NOT:
```
sudo nautilus
```
AND NOT:
```
gksu nautilus
```

---

### Post by jayanramesh on 2010-07-15
Dear robsoles,
For installing audacious player skin -I have to .

---

### Post by jayanramesh on 2010-07-15
AlphaLexman,
Output is
> jayan@jayan-r:~$ nautilus --no-desktop
/usr/share/themes/Win2-7Darth-Vader/gtk-2.0/Styles/notebook:158: Unable to locate image file in pixmap_path: "Tabs/notebook.png"
/usr/share/themes/Win2-7Darth-Vader/gtk-2.0/Styles/notebook:161: Background image options specified without filename
/usr/share/themes/Win2-7Darth-Vader/gtk-2.0/Styles/panel:19: Unable to locate image file in pixmap_path: "Panel/PanelBasicx.png"

---

### Post by AlphaLexman on 2010-07-15
You have some 'theme' issues, but nothing that would create 'root' problems. Try running:
```
nautilus --check
```and```
nautilus
```all by itself.
Then check your /home/.nautilus/ directory [or] /home/.config/nautilus/ directory.
(I am on ubuntu 9.10 not 10.04 as your profile states, so locales may have moved!)

---

### Post by robsoles on 2010-07-15
I thought jayanmaresh wanted to run nautilus as root.

While I was composing a tirade basically saying what a mistake that was a forum admin posted (for use in terminal) [**DON'T RUSH INTO THIS**] 
```
gksu nautilus
```
which is how to get a file-browser running on your desktop as root. I tested it and when you quit the file-browser it keeps the prompt busy in terminal so (without actually checking) I think it leaves a process zombied or otherwise not so contactable but I bet it is killed when you press [CTRL]-[C] back in the terminal you used to call it.

Is that stuff you are trying to install this way Open Source?

---

### Post by robsoles on 2010-07-15
My apologies to AlphaLexman.

A little further research on my part and I now have the impression that:
```
gksu nautilus --no-desktop
```
is better because that will stop the file-browser from nuking your own permissions etc (although I didn't seem to nuke anything earlier on a desktop at home - now posting from work and will be running fine-tooth comb over things at home when I get there!)

---

### Post by jayanramesh on 2010-07-16
Dear robsoles,
Here is the output of"gksu nautilus --no-desktop"gksu: unrecognized option '--no-desktop'
GKsu version 2.0.2

Usage: gksu [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
jayan@jayan-r:~$

---

### Post by bodhi.zazen on 2010-07-16
You do not need the --no-desktop option

If you wish to include it anyways, enclose the command in quotes

```
gksu 'nautilus --no-desktop'
```You have been given what might seem like overwhelming amount of information on this thread and I am not sure of the cause of your problem, but my guess is that when you ran some application as root it changed the permissions of files in your home directory. 

This is why it is advised to run graphical applications with gksu

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

See also this post:

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

It shows you the environmental variables, in this case $HOME, when invoking su (sudo su), sudo -i, sudo -s, gksu, etc

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

If that is overwhelming to you, do this

Open a terminal, run ```
sudo xterm
```In that terminal run these commands

```
whoami
echo $HOME
exit
```Now run

```
gksu xterm
```And in that terminal run

```
whoami
echo $HOME
exit
```Do you see the difference ? If you run graphical applications with sudo, the application writes configuration information to your users home, and this causes permissions problems.

The "solution" is to use gksu (or sudo -i) and that will properly set $HOME to /root

HTH

I am not sure , but the man page may help clarify what options there are to nautilus and what those options do exactly

[http://manpages.ubuntu.com/manpages/lucid/en/man1/nautilus.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/nautilus.1.html)

[http://manpages.ubuntu.com/manpages/lucid/en/man1/gksu.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/gksu.1.html)


> 
 **--no-desktop**
              Do  not  manage  the  desktop — ignore the preference set in the
              preferences dialog.

---

### Post by robsoles on 2010-07-16
That's a pain in the neck! I never tested it but I see that what happens is that gksu steals the option we are trying to pass to nautilus

I got the info I got from this output right here:
```

rob@rob-samsung:~$ nautilus --help
Usage:
  nautilus [OPTION...] [URI...] 

Browse the file system with the file manager

Help Options:
  -h, --help                      Show help options
  --help-all                      Show all help options
  --help-gtk                      Show GTK+ Options
  --help-sm-client                Show session management options

Application Options:
  -c, --check                     Perform a quick set of self-check tests.
  --version                       Show the version of the program.
  -g, --geometry=GEOMETRY         Create the initial window with the given geometry.
  -n, --no-default-window         Only create windows for explicitly specified URIs.
  --no-desktop                    Do not manage the desktop (ignore the preference set in the preferences dialogue).
  --browser                       open a browser window.
  -q, --quit                      Quit Nautilus.
  --display=DISPLAY               X display to use

rob@rob-samsung:~$ 

```Reconsidering again, why would bodhi.zazen tell us something that is bad for us??? Just do what he said and use ```
gksu nautilus
``` into a terminal while logged into your desktop and I ***think*** it will be fine - if files in your home directory become 'root's then even I can help you recover from that so it should be all good in either case!!

Is that software you are trying to install this way nice Open Source software? If their instructions are that it must be done as root, don't their instructions include how to do it as root?

I still wonder it is a good idea to run their stuff like this at all but if you will insist!

EDIT: I see the forum admin I mentioned has ninja-posted me again - cool but, I wondered if quoting would work on gksu like that but I didn't want to 'gksu' anything to find out!!!

---

### Post by jayanramesh on 2010-07-16
Dear bodhi.zazen & robsoles,
Thank you so much for your precious & precise painstaking effort to give panacea to my problem.And unfortunately I am not able to make avail of your skill and adeptness-what is more now I have learnt the difference between the "sudo and gksu" a bit.Again I honour you both et al.

Thank you

PS: I will try reinstalling my OS

---

### Post by bodhi.zazen on 2010-07-16
> **jayanramesh said:**
> Dear bodhi.zazen & robsoles,
Thank you so much for your precious & precise painstaking effort to give panacea to my problem.And unfortunately I am not able to make avail of your skill and adeptness-what is more now I have learnt the difference between the "sudo and gksu" a bit.Again I honour you both et al.

Thank you

PS: I will try reinstalling my OS

If it is not too late ...

Try restoring your permissions :

```
sudo chown -R your_login_name:your_login_name /home/your_login_name
```

obviously, change "your_login_name" to your actual user name ;)

---

### Post by jayanramesh on 2010-07-16
Dear bodhi.zazen,
I reinstalled my system but the same thing happend after installing win2 7 transformation pack.Now I will try it with your instructions.
Thank you

---

### Post by jayanramesh on 2010-07-16
Dear bodhi.zazen,
The output is > "jayan@jayan-r:~$ sudo chown -R jayan:jayan /home/jayan
[sudo] password for jayan: 
chown: cannot access `/home/jayan/.gvfs': Permission denied"

---

### Post by robsoles on 2010-07-16
That's ok - just a placeholder for shares from a network.

all the files in your home directory belong to you again.

---

### Post by jayanramesh on 2010-07-16
Dear robsoles,
Arrogant? or excentric? ! If you really wanna help please be so explicit in your instruction.DON'T LET YOUR HELP ANNOY OTHERS.

Thank you sofar.

---

### Post by bodhi.zazen on 2010-07-16
> **jayanramesh said:**
> Dear bodhi.zazen,
The output is

Alirght, the question is your system working now ?

---

### Post by robsoles on 2010-07-16
> **jayanramesh said:**
> Dear robsoles,
Arrogant? or excentric? ! If you really wanna help please be so explicit in your instruction.DON'T LET YOUR HELP ANNOY OTHERS.

Thank you sofar.

Terribly sorry it wasn't clear: That error output post above mine is regarding ~/.gvfs and it is literally a placeholder for GUI networking and applying permissions to it generally fails so your output doesn't indicate that anything bad happened.

---

### Post by jayanramesh on 2010-07-17
Dear bodhi.zazen,
Yes,but  if I use "gksu nautilus" I get error message-

> "Nautilus could not create the required folder "/root/.config/nautilus".

Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.


---

### Post by bodhi.zazen on 2010-07-17
> **jayanramesh said:**
> Dear bodhi.zazen,
Yes,but  if I use "gksu nautilus" I get error message-

There is a similar thread here :

[http://ubuntuforums.org/showthread.php?t=1532813](http://ubuntuforums.org/showthread.php?t=1532813)

I am guessing it is a but and probably should be reported on launchpad.

---

### Post by jayanramesh on 2010-07-17
Dear bodhi.zazen,
 Thank you so much, I reported it on launchpad.

---

### Post by jayanramesh on 2010-07-17
Dear bodhi.zazen,

please go through my screen shot to get an better idea of what went wrong.

Thank you

MY terminal output- > "jayan@jayan-r:~$ gksu nautilus
/usr/share/themes/Win2-7Darth-Vader/gtk-2.0/Styles/notebook:158: Unable to locate image file in pixmap_path: "Tabs/notebook.png"
/usr/share/themes/Win2-7Darth-Vader/gtk-2.0/Styles/notebook:161: Background image options specified without filename
/usr/share/themes/Win2-7Darth-Vader/gtk-2.0/Styles/panel:19: Unable to locate image file in pixmap_path: "Panel/PanelBasicx.png"
/usr/share/themes/Win2-7Darth-Vader/gtk-2.0/Styles/panel:19: Unable to locate image file in pixmap_path: "Panel/PanelBasicx.png"

---

### Post by bodhi.zazen on 2010-07-17
The error messages in your terminal are complaining about your theme, missing icons.

Those messages are, IMO, trivial.

Something is wrong here, but honestly I do not know what or how to fix it.

---

### Post by robsoles on 2010-07-17
Did you try this variation of the command?

```
gksu 'nautilus --no-desktop'
```

Except for leaving the terminal it is called from tied up after exiting the file-manager that appears after I pop in my password I can't seem to get a problem with it and due that it doesn't rely on your theme I really think it has the best chance of doing what you want.

---

### Post by jayanramesh on 2010-07-17
Dear robsoles,
Yes,I tried but it is of no avail.Is there any other go?

Thank you

PS: I am not a computer professional and being a medico I can't fix it without the help of Ubuntu forum.

---

### Post by bodhi.zazen on 2010-07-17
> **robsoles said:**
> Did you try this variation of the command?

```
gksu 'nautilus --no-desktop'
```Except for leaving the terminal it is called from tied up after exiting the file-manager that appears after I pop in my password I can't seem to get a problem with it and due that it doesn't rely on your theme I really think it has the best chance of doing what you want.

use nohup

```
nohup gksu "nautilus --no-desktop"
```

You will then be able to close the terminal.

---

### Post by jayanramesh on 2010-07-17
Dear bodhi.zazen,

Here is the output > "jayan@jayan-r:~$ nohup gksu "nautilus --no-desktop"
nohup: ignoring input and appending output to `nohup.out'
jayan@jayan-r:~$ 

Thank you

---

### Post by jayanramesh on 2010-07-17
Dear bodhi.zazen,

Finally and gladly I found the remedy 

> "sudo su (input your password)
 mkdir -p /root/.config/nautilus" and restart.

Thank you so much

---

### Post by bodhi.zazen on 2010-07-17
> **jayanramesh said:**
> Dear bodhi.zazen,

Finally and gladly I found the remedy 

 and restart.

Thank you so much

Fantastic.

Thank you for posting the solution.

---

### Post by robsoles on 2010-07-17
The '-p' switch tells mkdir to make parent directories if they don't exist and the fact that this made it work for you makes me wonder if something you do in your installation process deletes '/root' - a very important folder in the Linux filesystem.

I find it a pity not to be sure because I couldn't make 'gksu nautilus' fail on 6 different PCs running 10.04 LTS but they all had their /root folder intact.

Anyway, glad to hear you got this out of your way - if it's really solved maybe you could mark your thread here using the 'thread tools' above.

---

### Post by jayanramesh on 2010-07-18
Dear  robsoles,

> Re: setting permission 
The '-p' switch tells mkdir to make parent directories if they don't exist and the fact that this made it work for you makes me wonder if something you do in your installation process deletes '/root' - a very important folder in the Linux filesystem.

I find it a pity not to be sure because I couldn't make 'gksu nautilus' fail on 6 different PCs running 10.04 LTS but they all had their /root folder intact.

Anyway, glad to hear you got this out of your way - [QUOTE]if it's really solved maybe you could mark your thread here using the 'thread tools' above[/QUOTE]

NO TRUST POLICY-buddy? Bit skeptical? ok I ought to to prove.please see my attachment

---

