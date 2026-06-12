---
title: "Administrative Permission??"
date: 2009-10-23
forum: General Help
---

### Post by ex-windowuser on 2009-10-23
I just got the CrunchBang Linux dvd.  I tried to install VirtualMachine and is popped a line saying I need "administrative Permission" to load.  What heck, I'm the only one on this computer.  I am the administrator!  What am I missing gurus.  thanks in advance

---

### Post by KlinerDraken on 2009-10-23
In Linux no one but the user "root" is an administrator and by default that account is disabled for security reasons. All other accounts are just users. This is one of the things that makes Linux such a secure OS, because if any virus or spyware gets ran accidentally by a user that software can not make any changes to the system files.

---

### Post by wilee-nilee on 2009-10-23
> **ex-windowuser said:**
> I just got the CrunchBang Linux dvd.  I tried to install VirtualMachine and is popped a line saying I need &quot;administrative Permission&quot; to load.  What heck, I'm the only one on this computer.  I am the administrator!  What am I missing gurus.  thanks in advance

 So when you installed the software you created a password, this is one way of reaching a root install. For example if you want update your computer you can open a terminal and run sudo apt-get update it will ask for your password which will not show on the terminal screen when input but just hit enter. So sudo in Ubuntu is the clue to the computer that you want to mess with the root or in windows word administrative actions. You will get the hang of this shortly if you haven't already and as the first answer you got says it is what helps in keeping your root system more secure under ideal usage. Others will be able to explain this better, but here is a link to a guide that you can download which may be helpful, there are many books out there but the forums can be very helpful. [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)  So I believe crunchbang updates are done the same as Ubuntu regular but you just have some crunchbang repositories. Actually with Koala about to be released crunchbang was a good way of getting codecs and a few extra things as part of the main install, but Koala comes with some extras not included before so you might consider downloading a live CD after the main release and checking it out. There are over 300 types of Linux based and nix based releases it is rather fascinating journey to start going through all the possibilities if your so inclined.

---

### Post by kixome on 2009-10-23
> **KlinerDraken said:**
> In Linux no one but the user "root" is an administrator and by default that account is disabled for security reasons. All other accounts are just users. This is one of the things that makes Linux such a secure OS, because if any virus or spyware gets ran accidentally by a user that software can not make any changes to the system files.

"root disabled" this is true of ubuntu, and some other distro's, but not by definition LINUX, actually most other distro's do not remove access to root,even debian (the base for ubuntu){on debian it is an install option} which after distro hopping has proven to be quite convenient. su is much more convenient than typing sudo before every administrative command, in a simple productivity point of view.

---

### Post by wilee-nilee on 2009-10-23
We might want to recognize the OP new users status and keep within a understandable nomenclature rather then argue over personal interpretations of stuff.;)  Lets help the op not strut our ego's

---

### Post by alexcckll on 2009-10-23
Ubuntu Linux works according to the adage of Least Privilege Required.  For instance, it's always best to edit text files, browse etc etc with regular user privs.. only boosting them for actions that actually *need* admin privileges.

Hence Ubuntu's use of sudo.  In the Windows world, this would be actioned by a RunAs command... or by running an installer under SYSTEM context.  

Basically - if you are able to do something - a rogue task running as you can.

---

### Post by snowpine on 2009-10-23
> **ex-windowuser said:**
> I just got the CrunchBang Linux dvd.  I tried to install VirtualMachine and is popped a line saying I need "administrative Permission" to load.  What heck, I'm the only one on this computer.  I am the administrator!  What am I missing gurus.  thanks in advance

Hi Ex-WindowUser, nobody has really answered your question. :)

I am not familiar with an application called VirtualMachine. I personally use VirtualBox for managing virtual machines. You can install it in Ubuntu or Crunchbang with the following terminal command:

```
sudo apt-get install virtualbox-ose
```

When prompted for a password, enter your user password that you created at the time of installation. (If you are still running from the Live CD, you won't need a password, but you might run out of RAM!)

There are many other options for virtual machines, discussed in great detail on this sub-forum: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by ex-windowuser on 2009-10-23
When I tried to install Virtual Machine, it asks me how to open it.  Terminal or Text editor.  Of course I clicked Terminal.  The Terminal popped up so quick that I had a hard time reading it.  Meaning, everytime I try, it pops up and closes so quickly.  I had to do it several times to see what the heck it says.  I was able to read it and it says "you need administrator permission to install" and then the Terminal box closed on its own.  Then I tried text editor and that did the same thing and it wouldn't let me put in a password.  It just say "Press and key to close window.":confused:

---

### Post by snowpine on 2009-10-23
> **ex-windowuser said:**
> When I tried to install Virtual Machine, it asks me how to open it.  Terminal or Text editor.  Of course I clicked Terminal.  The Terminal popped up so quick that I had a hard time reading it.  Meaning, everytime I try, it pops up and closes so quickly.  I had to do it several times to see what the heck it says.  I was able to read it and it says "you need administrator permission to install" and then the Terminal box closed on its own.  Then I tried text editor and that did the same thing and it wouldn't let me put in a password.  It just say "Press and key to close window.":confused:

What is "it" and where did you get it?

---

### Post by nicol_bolas on 2009-10-23
You need to add the user you wish to run the VM to the group vboxusers (virtual box) or what ever group setup by your VM.

To add a user to a group goto system->Administration->users and groups
unlock
click on manage groups
find the group and highlight it then click on properties
check the user you wish to add.
start your vm.

hope that helps

---

