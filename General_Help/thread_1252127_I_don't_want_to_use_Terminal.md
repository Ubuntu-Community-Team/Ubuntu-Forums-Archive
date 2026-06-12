---
title: "I don't want to use Terminal"
date: 2009-08-28
forum: General Help
---

### Post by ibrahim3d on 2009-08-28
Hello :)


I like Linux Ubuntu so much. But it is hard. I'm not used to use terminal or shell! for every thing I want to do. And to log as a root by "su" or "su du"!
Can I use my own computer as I want!
I want to be a root user. I want to have all the permissions. Can I have that!? I don't want to use The terminal.
please help me.

---

### Post by mike555 on 2009-08-28
go into your package manager and install "nautilus-gksu" ... that will let you simply rt. click on a file to open as admin .

---

### Post by skillllllz on 2009-08-28
> **ibrahim3d said:**
> Hello :)


I like Linux Ubuntu so much. But it is hard. I'm not used to use terminal or shell! for every thing I want to do. And to log as a root by "su" or "su du"!
Can I use my own computer as I want!
I want to be a root user. I want to have all the permissions. Can I have that!? I don't want to use The terminal.
please help me.

Only administrative tasks and critical changes to the system require the use of sudo; that being said, in normal everyday use you shouldn't need to login as root or use sudo. No one is stopping you for running as root, but doing so is not advised as it puts your machine at risk.

---

### Post by jmszr on 2009-08-28
ibrahim3d,

Root is not enabled for legitimate security reasons. This may be of interest to you: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) . Beyond that you will need to Google.

Edit: This may interest you: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by gastly on 2009-08-28
As everyone else suggested, granting yourself root privilages can be dangerous for your system. One wrong move and you could destroy everything on your pc ;)

And as for using the terminal, yes I know it's a bit frustrating at first, but for most tasks you won't have to use the terminal. Even when you're installing a package, you can use Synaptic to install it (no terminal required).
Linux these days have been made easy enough for even a 5 year old to operate :)

**But** if you know how to use a terminal and know common commands in it, you will be able to do things faster (like, one command to pack/unpack many files at once, without even having to select them with your mouse :P).

---

### Post by meho_r on 2009-08-28
> **ibrahim3d said:**
> Hello :)


I like Linux Ubuntu so much. But it is hard. I'm not used to use terminal or shell! for every thing I want to do. And to log as a root by "su" or "su du"!
Can I use my own computer as I want!
I want to be a root user. I want to have all the permissions. Can I have that!? I don't want to use The terminal.
please help me.

No, you really shouldn't be root user all the time because of "su du"

---

### Post by credobyte on 2009-08-28
You can have that, tough, suggesting this would be against forum TOS ( and I don't think that someone would want to get an infraction ).

---

### Post by P4man on 2009-08-28
Thats like saying you've never used a gun, but you want one without such a stupid safety pal. 

Sudo is there for good reason. You would ordinarily only need it to install programs and set stuff up. Once your system is configured, you pretty much won't need it at all. The few times you do need it,  all it takes is entering your password once (or once per 15 minutes). 

You're probably annoyed because you can't write to your filesystem outside your homefolder. At the same time, I bet you have no clue what /etc /proc or /dev "folders" are. Again, there is good reason you can't accidentally write or delete there! You only need your homefolder for normal usage.

As for the command prompt. 99.9% can be done without a terminal. However, if you ask here "how do I install nvidia driver" or whatever, it is so much easier for us to type the command than explaining all the menu"s and mouse clicks to go through. Its easier for you too: you just have to copy/paste the command.

For fun, lets compare. Say, you would ask here, "I want to be able to watch encrypted DVDs. How do I do that?". A likely response would be:

enable medibuntu and install libdvdcss2:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get install libdvdcss2

```

Explaining the same through a GUI:

Go to system, administration, sofware sources. 
Type your pw. 
Click on third party software tab.
Click add. 
In the apt line box type in:
 "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty". 
Click OK. 
Click "reload".
Go to system > administration > synaptic package manager. 
In the search box type in "libdvdcss2"
Right click the package
select "mark for installation"
click the "apply" button 
..

See the difference? 
And then you get back to us and say: "I can't find system > administration". Why? Because you have a French ubuntu with French menu's. Or you are using the netbook remix with a different GUI. Or you are running Kubuntu.. we just typed half a screen of instructions you can't follow.

 The command line however, would work in all cases. French or Chinese, NBR or kubuntu, it doesn't matter

Bottom line: **you** dont have to use the terminal at all. But if you ask questions here, expect the answers to be command lines, because its easier that way for the helpers and for you. I admit its easier with the gui to "find" things, so if you"re experimenting, by all means use the gui :)

---

### Post by smakand on 2009-08-28
In terminal type:

```
sudo apt-get install nautilus-gksu
```

---

### Post by P4man on 2009-08-28
> **smakand said:**
> In terminal type:

```
sudo apt-get install nautilus-gksu
```
[B]
He doesn't want to use a terminal[/B], so you have to say:

Go to system > administration > synaptic package manager
type your password
look for the search box
type nautilus-gksu
rightclick the package in the list
"mark for installation"
click apply
click ok

Oh and it you have the NBR then do ..
And if you have xubuntu then look in..
and if its in German, then the menu is called...



:D

---

### Post by snowpine on 2009-08-28
The terminal is the best thing about Linux. It only seems hard because you're not used to it. :) It's like saying "I want to drive stick but I don't want to use the clutch."

---

### Post by smakand on 2009-08-28
> **P4man said:**
> [B]
He doesn't want to use a terminal[/B]

:P just bringing some light humor, someone else suggested the same solution earlier.

---

### Post by ibrahim3d on 2009-08-29
I must use Linux because it is required to run a php script.
I downloaded Xampp "Apache Server" for Linux. I looked at the file ! It's not an installation file!! Long story. Then I knew that I must install it from Terminal.
tar xvfz xampp-linux-1.7.2.tar.gz -C /opt
I understood the line. It is going to extract on the folder "/opt" ! I said to my self "Copy it and Past it to the /opt folder". When I did it. I got a message "Access Dinned"!

Then I wrote the line on Terminal and It did install. Now I want to move the script to the folder /opt/lampp/...
I said how can I do it. I wrote a book on terminal and nothing happened. After a while, I put the script on a "tar.gz" type and I changed the line and It worked.

Linux is much better and fun but it is the opposite of windows.

--------------
Thank to all who helped Or explained :)
mike555 thanks it will help a lot :)
gastly I am 4 years old :)
P4man Yes I see the difference. I know it is better and safe a lot of time. But I like the waste-of-time way. because I used to it and it keeping me a way for having a headache :) Thank you :)
smakand thank you :) I downloaded but I didn't know how to install it.

Thank you guys. I found it. I will use VMware-Player.

---

### Post by CatKiller on 2009-08-29
> **ibrahim3d said:**
>  P4man Yes I see the difference. I know it is better and safe a lot of time. But I like the waste-of-time way. because I used to it and it keeping me a way for having a headache 

It's not your time that you're wasting; it's the time of people that are volunteering to help that gets wasted by having to give instructions like that. That's the point.

Terminal commands are quick to type out for the person giving the help, and quick to copy-and-paste for the person asking for the help. No muss, no fuss.

It's not like you need to use the terminal much in day-to-day usage, but you may have noticed that this forum is text-based. Demanding that people help you in a way that isn't the best for this text-based communication device, and in a way that won't also help others with a similar problem even if they're using a different graphical environment is... ungrateful. At best.

---

### Post by P4man on 2009-08-30
> **ibrahim3d said:**
> I must use Linux because it is required to run a php script.
I downloaded Xampp "Apache Server" for Linux. I looked at the file ! It's not an installation file!! 

You are assuming wrongly that installing stuff in linux is just like in windows.. downloading executable files from the internet. But its not. The easy way to install a LAMP server in linux is using the repositories:

```
sudo apt-get install apache2 phpmyadmin mysql-server
```

And if you are allergic to a  terminal, you can install those same packages through system > admin > synaptic

The great thing about package managers is that they install everything for you, they take care of installing and maintaining dependencies, ensure you get a version that was compiled and tested specifically for your OS version, and then keeping it all up to date.

The hard way is downloading "exe's" :)

---

### Post by ibrahim3d on 2009-08-30
[P4man]("http://ubuntuforums.org/member.php?u=412374") Thank you very much for your explaining :) :) I tried VMplayer but it fells wrong. I will use an installed Linux Ubuntu and I will learn till I get used to it.
> 
It's not your time that you're wasting; it's the time of people that are volunteering to help that gets wasted by having to give instructions like that. That's the point.
I don't have to use a thing because they spent a lot of time on it. If I don't want to use it that doesn't mean I wasted their time.

---

### Post by uylug on 2009-08-30
> **P4man said:**
> [B]
He doesn't want to use a terminal[/B], so you have to say:

Go to system > administration > synaptic package manager
type your password
look for the search box
type nautilus-gksu
rightclick the package in the list
"mark for installation"
click apply
click ok

Oh and it you have the NBR then do ..
And if you have xubuntu then look in..
and if its in German, then the menu is called...



:D

:lolflag:

---

### Post by CatKiller on 2009-08-30
> **ibrahim3d said:**
> []("http://ubuntuforums.org/member.php?u=412374") I don't have to use a thing because they spent a lot of time on it. If I don't want to use it that doesn't mean I wasted their time.

Nice way to completely miss the point there :shock:

---

### Post by jerome1232 on 2009-08-30
> **P4man said:**
> 
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get install libdvdcss2

```

Explaining the same through a GUI:

Go to system, administration, sofware sources. 
Type your pw. 
Click on third party software tab.
Click add. 
In the apt line box type in:
 "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty". 
Click OK. 
Click "reload".
Go to system > administration > synaptic package manager. 
In the search box type in "libdvdcss2"
Right click the package
select "mark for installation"
click the "apply" button 
..

See the difference? 
And then you get back to us and say: "I can't find system > administration". Why? Because you have a French ubuntu with French menu's. Or you are using the netbook remix with a different GUI. Or you are running Kubuntu.. we just typed half a screen of instructions you can't follow.

 The command line however, would work in all cases. French or Chinese, NBR or kubuntu, it doesn't matter

Bottom line: **you** dont have to use the terminal at all. But if you ask questions here, expect the answers to be command lines, because its easier that way for the helpers and for you. I admit its easier with the gui to "find" things, so if you"re experimenting, by all means use the gui :)

I realize I'm not contributing to this thread in anyway shape or form but I have to say, 

this actually made me lol!
:lolflag:

---

