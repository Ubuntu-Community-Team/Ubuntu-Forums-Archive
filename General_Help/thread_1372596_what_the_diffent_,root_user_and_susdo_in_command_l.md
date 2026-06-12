---
title: "what the diffent ,root user and susdo in command line"
date: 2010-01-04
forum: General Help
---

### Post by rany on 2010-01-04
why we have to log in as root user some times while we can use sudo in command line ,is it diffrent , does sudo dont have all access and all permessions?
i am really lost , i know little of alot of things in ubuntu ,but still missong alot of circles to make the complate picture some body help

---

### Post by jonest1 on 2010-01-04
Just a couple quick thoughts.

For most instances, running a command as the root user or through the sudo application is the same. 

There are extremely rare cases where some complex commands may spawn a subshell and can cause some issues where one part of the command runs as root and the other as a regular user.  These instances can be fixed and are rare.

There is nothing particularly wrong with logging in as root in a shell to complete some administrative tasks.  However, for best security practices, being root at the shell should be used only when it is practical.  With a root shell session, each thing you do, is done as root.  So, there is added risk.

There are some differences relating to environmental variable settings in how you become root (ie: 'sudo su' vs. 'sudo su -').

---

### Post by jocampo on 2010-01-05
> **rany said:**
> why we have to log in as root user some times while we can use sudo in command line ,is it diffrent , does sudo dont have all access and all permessions?
i am really lost , i know little of alot of things in ubuntu ,but still missong alot of circles to make the complate picture some body help

Hi Rany

Thanks for your question. But please remember to post your question on the right forum, this one is for Virtualization ;-)  that will speed up the answer a lot.

For almost all normal desktop tasks, "sudo" is more than enough and you should not avoid it creating a password for "root". In fact, among others, the "root" account in disable state is one of the strongest points of Ubuntu when compared to other distros; in other words, no root account or disable...nothing to hack. But, for server management or more complex tasks, like scripts, "su" or the use of root account is easier to implement

---

### Post by bodhi.zazen on 2010-01-05
> **rany said:**
> why we have to log in as root user some times while we can use sudo in command line ,is it diffrent , does sudo dont have all access and all permessions?
i am really lost , i know little of alot of things in ubuntu ,but still missong alot of circles to make the complate picture some body help

1. This post was moved to general help.

2. The difference is in environmental variables 

See: [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

In addition, if using graphical applications, we have X and X security to consider, so gksu (kdesudo on KDE) is used with graphical applications.

---

### Post by Cheesemill on 2010-01-05
> **bodhi.zazen said:**
> 2. The difference is in environmental variables 
You can use
```
sudo -i
```
to give yourself a root prompt with all of roots variables.

---

### Post by wasd591 on 2010-01-05
Well dude,
The difference between sudo, root and the normal user are all different. But before we get started I would like to make you aware that **sudo** is not a user. It is a **command** used to give Administrator permission, which is what root is. Here is an example, let's say your user name is called Jon. Jon wants to install a program through terminal. Jon uses the command '*sudo apt-get install music-player*'. It gives Jon a error. He can't install the program. Because he doesn't have the permissions to install the program, so he can't download and install it. That's what the root user is for. He is like god, he controls everything. The command **sudo** is used to let Jon have **root** permission to install the program. Just like you have to have a drivers license to drive. The computer checks his drivers license and it passes. So he is able to install the software by using the command: '*sudo apt-get install music-player*'. He has to put **sudo** in to get root access to the computer...make sense?

---

### Post by Cabs21 on 2010-01-05
> **wasd591 said:**
> Well dude,
The difference between sudo, root and the normal user are all different. But before we get started I would like to make you aware that **sudo** is not a user. It is a **command** used to give Administrator permission, which is what root is. Here is an example, let's say your user name is called Jon. Jon wants to install a program through terminal. Jon uses the command '*sudo apt-get install music-player*'. It gives Jon a error. He can't install the program. Because he doesn't have the permissions to install the program, so he can't download and install it. That's what the root user is for. He is like god, he controls everything. The command **sudo** is used to let Jon have **root** permission to install the program. Just like you have to have a drivers license to drive. The computer checks his drivers license and it passes. So he is able to install the software by using the command: '*sudo apt-get install music-player*'. He has to put **sudo** in to get root access to the computer...make sense?

Um I understand what your saying but I think you typed it wrong. If 'sudo apt-get install music-player' give a permissions error then no one can install it not even root.  I think you mean jon uses 'apt-get install music-player' he would get the permissions error and would need to proceed the command with the 'sudo' command. Is that what you meant?

---

### Post by mcduck on 2010-01-05
Since nobody has mentioned it yet, sudo isn't actually about running admin tasks or anything. It's just a tool for running a command as some other user (**S**witch **U**ser **DO**). It just assumes that you want to run the command as root user if you don't specify any other user name.

For example "sudo -u mcduck firefox" would start Firefox as user "mcduck", assuming the user running the command has been given permissions to do such thing in the /etc/sudoers file.


(Same applies to "su", also often misinterpreted as administration tool, while it's just a command for switching to another user.)

Of course both commands are most commonly used for running commands as root user to avoid having to actually log in as root, or to be able to limit what admin tasks users are allowed to do in a more detailed way than what simply giving them the root password would allow.

---

### Post by lisati on 2010-01-05
> **mcduck said:**
> Since nobody has mentioned it yet, sudo isn't actually about running admin tasks or anything. It's just a tool for running a command as some other user (**S**witch **U**ser **DO**). It just assumes that you want to run the command as root user if you don't specify any other user name.

For example "sudo -u mcduck firefox" would start Firefox as user "mcduck", assuming the user running the command has been given permissions to do such thing in the /etc/sudoers file.


(Same applies to "su", also often misinterpreted as administration tool, while it's just a command for switching to another user.)

Of course both commands are most commonly used for running commands as root user to avoid having to actually log in as root, or to be able to limit what admin tasks users are allowed to do in a more detailed way than what simply giving them the root password would allow.

Thank you for mentioning the "switch user" side of sudo - I'd always thought of it in terms of "super user do"......

---

