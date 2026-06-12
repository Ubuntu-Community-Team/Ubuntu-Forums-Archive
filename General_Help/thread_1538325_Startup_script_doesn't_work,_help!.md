---
title: "Startup script doesn't work, help!"
date: 2010-07-24
forum: General Help
---

### Post by techick on 2010-07-24
Hello, I try to run a bash script when the machine boots up.
I followed the exactly the same procedure as stated in [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
I tried to use update-rc.d and rc.local. The both ways still dont make the bash script automatically run when it boots up in Ubuntu 9.04. The script can be successfully executed when I log in as root and run it manually.
I really don't know where the problem is. Please point out. Thank you.

---

### Post by d3v1150m471c on 2010-07-24
unless your script requires root privileges there's no need to put it in rc.local. if it doesn't try placing your script somewhere secure and have it called to execute on .profile or .bashrc in your home folder. You should probably try using your normal startup manager first btw.

---

### Post by geoffjay on 2010-07-25
If you want to add a script using update-rc.d you will also need a script to start/stop/restart in /etc/init.d, did you create one? If not there's a template at /etc/init.d/skeleton. But this method is usually only for controlling system daemons.

---

### Post by bigboy_pdb on 2010-07-25
You can run scripts using **System -> Preferences -> Startup Applications** as well. However, from what I've tried to do using this method, it appears to be the least troublesome to run a single command along with its parameters. For example, redirection should be avoided in your command "Command" for a "Startup Program".

Also, the following might be helpful with respect to understanding when you should use a given method.

When your **computer starts up**, the following is run as *root*:
[LIST]
[*]local.rc
[/LIST]

When **logging into a GNOME session**, the following are run as *the user you're logging into*:
[LIST]
[*].profile
[*]Startup Applications
[/LIST]

When **opening a terminal GUI within gnome session** (Applications -> Accessories -> Terminal), the following are run as *the user you're logged into*:
[LIST]
[*].bashrc
[/LIST]

When **logging into a shell from a text based terminal**, the following is run as the *user you're logging into*:
[LIST]
[*].profile
[*].bashrc
[/LIST]

**NOTE:** .profile loads .bashrc when it's run from within in the bash shell.

**NOTE:** The CTRL-ALT-F8 combinations switches to your GNOME session and CTRL-ALT-F1 through CTRL-ALT-F6 switch to tty1 through tty6.

---

### Post by techick on 2010-07-25
I have tried that several times, but it still doesnt work

---

### Post by bigboy_pdb on 2010-07-25
You can try creating a really simple command to begin with.

For example, you can put the following in rc.local and check if the test.log file has been created and contains the text that was appended to it:

```

echo "It worked for rc.local" >> /home/**USER**/test.log

```

**USER** should be your user name.

You can try it with the other files as well. You should keep it as simple as possible in order to determine whether or not the problem is rc.local or one of the other files being read.

If it works but the code that you're using doesn't then it's probably a problem with your code. Also, you should test your code separately in its own bash file to determine if it has any problems.

---

