---
title: "Whats the purpose of root?"
date: 2011-06-08
forum: General Help
---

### Post by kexus on 2011-06-08
So, I'm fairly new to Ubuntu, and I'm curious as to what the point of having a root account is, if you can just use the sudo command.  Is it just so you don't have to bother using sudo and entering in your password?  Or is there more to it?

---

### Post by doas777 on 2011-06-08
sudo is a new kind of thing, whereas root is an ages old thing, so some distros have adopted it and others haven't. some people that are used to using a root-friendly distro often don't like sudo, so they might enable their root account. also a couple years ago, there were one or two things that sudo could not do, that had to be done as root, but they were very rare (never had the need myself).

hope that helps

---

### Post by IWantFroyo on 2011-06-08
The "sudo" command still runs it as root. 

The reason for the difference lies in security reasons. People get a bad impression of Ubuntu if they can just type:
"su"
"rm -r /etc"
and more or less total the system.

If you want to check out the powers of root, run this:
```
sudo su
```

---

### Post by FormatSeize on 2011-06-08
> **kexus said:**
> So, I'm fairly new to Ubuntu, and I'm curious as to what the point of having a root account is, if you can just use the sudo command. 
Root is to be as walking amongst the Gods!
 
 
 
... or to just screw up your system, lose everything, and become upset with yourself (and perhaps the world). 
 
There are upsides and downsides to it; I found this in the [RootSudo Ubuntu documentation]("https://help.ubuntu.com/community/RootSudo#root account")
 
Personally, I only use root when a system blatantly lets me with no warning, which Ubuntu doesn't. Other than that, the downsides of sudo or the upsides of root down apply to what I'm doing.

---

### Post by Rocket2DMn on 2011-06-08
Long story short is - don't use root unless you really know what you're doing :)

It is similar to the Administrator on a Windows computer - it is all powerful.  It is also insecure to operate as the root user for normal desktop sessions. Most users will never need to use a real root account because of Ubuntu's use of sudo, which is a lot more configurable.

---

### Post by lisati on 2011-06-08
"root" is kind of like a super user who can do just about anything, including doing serious damage to your system.

To casual home users, having users with limited privileges on a system might at first sight seem like a foreign concept that's not really necessary. After all, it's your system and you should be allowed to do what you want with it.

To cut a potentially long and boring story short: When you do stuff like connect to the internet or just want to let your friend use your computer, you don't want just anyone to access to your system and get up to mischief. This is where the idea of user privileges come in. Chosen wisely, they help protect against both mischief and accidents.

At work, the idea can be extended to making sure that you don't overstep the bounds of your responsibility. Many years ago, I worked for a company that processed a lot of confidential data for various clients and which was a bit paranoid about security. I couldn't just take a 5 minute walk down the road to a friend's workplace (which happened to be for one of my employer's client companies) and log in as myself. Because my work didn't usually take me out of the office, any attempt by someone to login as me from somewhere other than my usual location was blocked.

** anecdote ends **

---

### Post by el_koraco on 2011-06-08
> **doas777 said:**
> sudo is a new kind of thing, whereas root is an ages old thing,

Sudo was created in the 80's, so it's not a new kind of thing. The purpose of sudo goes beyond assuming superuser powers, the manpage even says it's for executing commands as another user. In the old days, when running Unix systems with multiple users was the norm, executing commands as another user had its use - not so much on single user systems that most of our personal computers are today. 

The use of sudo as a general purpose root substitute is relatively new though, dating from OSX, and popularized in Linux by Ubuntu.

---

### Post by renkinjutsu on 2011-06-08
But doesn't su also give the power to run commands as a different user?

```
su username -c "command to run"
```

---

### Post by el_koraco on 2011-06-08
> **renkinjutsu said:**
> But doesn't su also give the power to run commands as a different user?

```
su username -c "command to run"
```

I'm guessing the paths are different.

---

### Post by doas777 on 2011-06-08
> **el_koraco said:**
> Sudo was created in the 80's, so it's not a new kind of thing. The purpose of sudo goes beyond assuming superuser powers, the manpage even says it's for executing commands as another user. In the old days, when running Unix systems with multiple users was the norm, executing commands as another user had its use - not so much on single user systems that most of our personal computers are today. 

The use of sudo as a general purpose root substitute is relatively new though, dating from OSX, and popularized in Linux by Ubuntu.
indeed, but root was introduced in unix in 1972. all things are relative....

you are correct, sudo is more of a "runas" than  a "runas root" utility.

---

### Post by sisco311 on 2011-06-08
> **renkinjutsu said:**
> But doesn't su also give the power to run commands as a different user?

```
su username -c "command to run"
```

Yep, su and sudo are [setuid]("http://en.wikipedia.org/wiki/Setuid") root applications which allow a user to run a command as another user.

---

### Post by renkinjutsu on 2011-06-08
So what is it that sudo does that makes it more secure?

---

### Post by grahammechanical on 2011-06-08
> So what is it that sudo does that makes it more secure?

The bit that they all forgot to mention. The power that you get through sudo only lasts as long as the activity that you are doing. Try this out with Update Manager. You need to authenticate to install the updates. This is like putting sudo in front of a command in the terminal. Enter your log in password and a small icon of a key will appear in the top panel. Once the download is completed and you close Update Manager then the icon of a key will disappear and you will no longer be using administrator privileges. So, if you leave the room no one else can make changes to the system even though they have access to a working OS.

I have a noticed that when using sudo in a terminal the administrator privileges last for a few minutes and then deactivate.

Regards.

---

### Post by sisco311 on 2011-06-08
> **renkinjutsu said:**
> So what is it that sudo does that makes it more secure?

Both su and sudo are well-written setuid applications. If they are used properly, then they are equally secure.

---

### Post by sisco311 on 2011-06-08
> **grahammechanical said:**
> 
I have a noticed that when using sudo in a terminal the administrator privileges last for a few minutes and then deactivate.


Yep, in Ubuntu, sudo's default timestamp_timeout (the number of minutes that can elapse before sudo will ask for a passwd again) is 15. The vanilla sudo defaults to 5.

---

### Post by renkinjutsu on 2011-06-08
> **grahammechanical said:**
> The bit that they all forgot to mention. The power that you get through sudo only lasts as long as the activity that you are doing. Try this out with Update Manager. You need to authenticate to install the updates. This is like putting sudo in front of a command in the terminal. Enter your log in password and a small icon of a key will appear in the top panel. Once the download is completed and you close Update Manager then the icon of a key will disappear and you will no longer be using administrator privileges. So, if you leave the room no one else can make changes to the system even though they have access to a working OS.

I have a noticed that when using sudo in a terminal the administrator privileges last for a few minutes and then deactivate.

Regards.

I remember sudo being active for a period of time.. meaning if one does

```
sudo whoami
```
if one uses sudo again within a certain amount of time, it will not ask for a password again.. so..

```
sudo whoami
# person finishes task and moves out of room
sudo su
# full root privileges
```

---

### Post by dhave-dhave on 2011-06-08
So, what's the difference between these two commands?

$ sudo su

and 

$ sudo -i

Thanks.

---

### Post by Dave_L on 2011-06-08
> **dhave-dhave said:**
> So, what's the difference between these two commands?

See this: [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by dhave-dhave on 2011-06-08
> **Dave_L said:**
> See this: [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)
Very informative. Thanks.

---

### Post by doas777 on 2011-06-09
> **renkinjutsu said:**
> So what is it that sudo does that makes it more secure?

basically it challenges the user to approve administrative access happening within their shell. essentially you are not an admin all the time, only when you really want to do something administrative. 

Sudo does have a grace-period, that allows a shell to invoke a a succession of sudo commands without password recheck, which does represent a small risk of [confused deputy]("http://en.wikipedia.org/wiki/Confused_deputy_problem") attacks. you can limit the sudo graceperiod using these instructions: [http://helpdeskgeek.com/linux-tips/eliminate-the-grace-period-for-the-sudogksu-commands/](http://helpdeskgeek.com/linux-tips/eliminate-the-grace-period-for-the-sudogksu-commands/)

so, when you are browsing the web and come across a piece of malware, you are not an admin, so you can't bork your whole system. but when you are reconfiguring your fstab, you can become an admin at will, without having to login as root, and switching to that session.

---

### Post by el_koraco on 2011-06-09
> **grahammechanical said:**
> The bit that they all forgot to mention. The power that you get through sudo only lasts as long as the activity that you are doing. Try this out with Update Manager. You need to authenticate to install the updates. This is like putting sudo in front of a command in the terminal. Enter your log in password and a small icon of a key will appear in the top panel. Once the download is completed and you close Update Manager then the icon of a key will disappear and you will no longer be using administrator privileges. So, if you leave the room no one else can make changes to the system even though they have access to a working OS.

I have a noticed that when using sudo in a terminal the administrator privileges last for a few minutes and then deactivate.



There is a difference between using USC and update manager, and using sudo in terminal. When using Update Manager, you're not acquiring sudo powers, but interacting with PolicyKit, which only elevates your authority specifically for the task at hand. Try to use one of those and Synaptic, which doesn't interact with PolicyKit, but with gksudo, and you'll see different dialogs. In UM you'll get a notice saying "System policy prevents...", in Synaptic you'll see "Enter your password to preform administration tasks". Also, you have to input your password before starting up Synaptic, and don't have to do it when opening UM or USC. PolicyKit is more like windows UAC than graphical invocation of sudo.

---

### Post by kexus on 2011-06-10
So, basically root is just something that has been in for a long time, and just hasn't been taken out?  I think I have a better understanding of it now. Thanks guys!

---

