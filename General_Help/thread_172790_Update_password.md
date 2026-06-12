---
title: "Update password"
date: 2006-05-09
forum: General Help
---

### Post by Lamorue on 2006-05-09
Allo everybody

I have tried several times during installation to set up proper password without succes. After several tries I manage to qive a root password and I had to add name and logging password after install with adduser

 My logging nor my root password is accepted for updating or to add application or sudo command. 
This is the answer I get  And I translate since my set up is in french.

[PHP]Échec lors du lancement de /usr/sbin/synaptic --non - inactive --hide main window avec l'utilisateur
root : wrong password[/PHP]
( Translation )
Failure to launch...               ... with user.

And with the terminal

[PHP]lamorue@ubuntu:~$ sudo update
Password:
Sorry, try again.
Password:[/PHP]

Is this password should be the logging password ?

I am new with Linux and I have been trying to solve that problem since 3 weeks 

Please somebody can help me. I realy need help.

Thank you
Lamorue

---

### Post by oscar on 2006-05-09
You shouldn't need to bother about root, particularly when you are new to linux. When you first install ubuntu the user account you make is a normal user account which has administrative privilages, whenever you need to run a command that in other distros would need to be run as root you just add a sudo at the beginning and use your user account's password. Whenever you are prompted for a password it is your password. Ubuntu functions perfectly well without a root account and it is disabled by default.
See:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
for more information

---

### Post by Lamorue on 2006-05-09
Thank you Oscar
I am  print and will reed your documentation (seems to be pretty good info )

Presently It does not accept my logging password. Is that the one I sould use Or I need to create an other one.
Anyway I read your doc and see what I can do

See you later 
Thank you again
Lamorue

---

### Post by s_h_a_d_o_w_s on 2006-05-09
Je ne suis pas sure que c'est ca, mais tu peux écire:

passwd

dans le terminal, tu pourras changer ton password si tu as besoin.

:-)

---

### Post by kbudurka on 2006-05-09
To change to root, simply type:
sudo su -
and type your USERS password.

---

### Post by Lamorue on 2006-05-11
Merci shadow thanks kubudurka

I made a new install on a new hard disk and I realised that my problem was not realy my password but sudo who does not respond to my commands because when I give an erronous password he tells me but with the right password he goes back on the propt again but no action taken

I have tried this

[PHP]lamorue@ubuntu:~$ sudo update
Password:
Sorry, try again.
Password:
lamorue@ubuntu:~$ sudo upgrade
lamorue@ubuntu:~$[/PHP]

I also tried that

[PHP]lamorue@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Password:
lamorue@ubuntu:~$[/PHP]

With these commands on both of my HDD no answer no downloads.

Where is the problem and how can I solve it

Thank you in advance 
lamorue

---

### Post by jtibau on 2006-05-11
hi there,

I tried "sudo update" and "sudo upgrade" in my machine, just to make sure, but my shell says there is no update or upgrade command.
As for "sudo apt-get update && sudo apt-get upgrade" gotta say it did work though it didn't donwload anything since I already routnely ran those commands about two hours ago :)

For what I read in your posts, ubuntu is not fully translated to french... since some of the keywords like "password" are still in english.

Have you tried to install the english language packages so as to make english the default language. It may be that the error messages are missing for french, although I would expect that they would still show in english if not.

I don't think that they would actually leave you with no error messages whatsoever (meaning at least in english) but I guess it is worth giving it a try.

Good luck

---

### Post by Lamorue on 2006-05-11
Allo jtibau

I just tried tu use add application from the menu and it says and I translate :

> Echec lors du lancement de /usr/bin/gnome-app-install avec l'utilisateur root :

Child terminated with 1 status

Translation : Failure when launching ...         ...with user root :

Please I need help to solve the problem 
I also thought to install the english ver and thats what I might do. But my little kids dont know english yet.

Thank you 
lamorue

---

### Post by jtibau on 2006-05-14
[QUOTE=Lamorue]Allo jtibau

I just tried tu use add application from the menu and it says and I translate :



Translation : Failure when launching ...         ...with user root :

Please I need help to solve the problem 
I also thought to install the english ver and thats what I might do. But my little kids dont know english yet.

Thank you 
lamorue[/QUOTE]

That's weird, I've never had that problem... Are you using the account you created during installation?
Is synaptics or apt-get running? You should have only one of this programs working or else you get some problems... 

About your children:
I live in south america. Speak spanish as a first language.
When I was 7 my family lived in Spain and my parents decided to buy a PC. That was back in 1994 I think. Needless to say, NOTHING was in spanish on that PC.
For what I remember, I did use the computer a lot. I think even back then, I learned faster to do a couple of things than my parents did. Even if the pc would've been in chinese I only saw icons and drawings and memorized a couple of key words.
Now Linux is surely much better than windows back then. And in my opinion is much better now than windows will ever be :)
So now I'm studying computer science. Speak, read and write in english better than anyone I know in my college classes. And I think that computer experience started it all. Although I'm very proud of my own language and culture (same as you I'm sure), I cannot deny that english is a much more universal language for IT proffesionals. Well actually it is much more universal for pretty much anything.

I tend to stretch too much my thoughts :)

My suggestion, give it a try for a couple of weeks. Encourage your kids to use it, and if it doesn't work for them... Switch to french again.

Maybe if you do an english install and then add french language support, it would keep english info/error messages. I don't know though since I've always kept my OS in english.

I guess you already thought of all of this. But I just couldn't keep myself from writing :)

Bonne Chance

---

### Post by Lamorue on 2006-05-14
Thank you to all

Problem solved 
Mustard gave me the answer see my thread **sudo does like me**

> Try this HOW TO to check if you have sudo set up correctly..


Use the 'Recovery Mode' from the Grub menu at startup.

Recovery mode will drop you to a root prompt. If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..


Code:
visudo  #this command does on thing.  It opens the sudoers file for editing
Note:- To save the sudoers file from visudo after editing you would use ctrl + o. To exit visudo use ctrl + x.

My sudoers file looks like this. Note the last line where I give my user sudo privileges. This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.


Code:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL
Method 1. Adding your username directly to sudoers

You can see my username on the bottom line. You would need to add your username to the bottom as I have done.

Assuming your user name was "bob'', then the line that would need to be added would be..

Code:
bob ALL=(ALL) ALL

**tjibau**

As far the language is concern I am French Canadian in Québec and I learn the english at school and I worked for 33 years in English as a scientific in electonics in a resurch and developpement lab.
My 3 kids speaks english necessary to work in Québec. But my little kids are too yong to speek english yet but the older one is learning it. 
As far the computer is concern I dont know that system yet and kids dont read but try and I dont know how they can damage my set up. 
The younger at 5 years old serch on google look for frenh language search his games download it and install it without letting me knowing. He does that under windows But with linux I dont know yet if it is so easy. He can put me in a big trouble.
I will give a try but on an other hard disk.

You are right English is the internationnal language and is necessary to learn

Thank you for your help
Lamorue

---

### Post by jtibau on 2006-05-14
You can give your children a Desktop user account. That way they won't be able to install anything new. I you are not root (administrator) you can't do much damage to your system.

---

### Post by Lamorue on 2006-05-14
jtibau

Good idia after my installation will be completed

Thamk yoy 
Lamorue

---

### Post by Lamorue on 2006-05-16
Bonjour tsibau

I will install an english version but I want to download an other copy .
Is there any way to know witch version is the most recent because everywhere I look they seams to be all at the same date. I had so mutch problems of entering my names because he does not want to accept it.
 Maybe in english it will be different.
Thank You
Lamorue

Can you explain to me Watt those names are and how to enter (I mean whatt not to do ) Did you have any problems with names at the install.

---

