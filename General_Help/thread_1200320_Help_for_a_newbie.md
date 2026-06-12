---
title: "Help for a newbie"
date: 2009-06-29
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-06-29
System Info:
I'm using ubuntu 9.04 on a notebook (hate vista)
Hp Compaq
[http://i41.tinypic.com/21mb7mu.jpg](http://i41.tinypic.com/21mb7mu.jpg) - system stats
VGA compatible controller: nVidia Corpation GeForce 8200M G (rev a2)

I have a few questions and a complaint.
Questions:
&#8226;How do I change it to 16 bit mode? (Mainly to conserve a little battery power)
    [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]solved terminal command:gksu /usr/bin/nvida-settings
     [COLOR=White]----[/COLOR]Note disable desktop effects with this setting or you will not have a title bar
&#8226;how do I turn the shutdown beep off? (It is annoying BTW it is a system beep not a wav file)
    [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]partly solved terminal command:sudo rmmod pcspkr 
        [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]How do i make it not have to be done every time i boot?
            [COLOR=White]--[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]It quit doing it now
&#8226;What is the directory to where applications are installed?
    [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]figured out what i needed to know \usr\bin\
&#8226;What is the command to run as root? (I know it is not recommended)
    [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]solved terminal command:sudo -i
    [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]set root password-terminal command:sudo passwd root
    [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]this really helps terminal command:gksu nautilus

Complaint:
&#8226;The Update Manager by default marks the restricted packages for installation. Which can't be fully installed causing an error. and it will not let you remove them either. Which make adding new software impossible. (I reinstalled the OS to fix it)

Note:
&#8226;Sorry if this is in the wrong forum.
    [COLOR=White]-[/COLOR][COLOR=White]-[/COLOR][COLOR=White]-[/COLOR]i guessed right :)

---

### Post by Megrimn on 2009-06-29
K, here it is (most of it)

- 16-bit: download and install the "Nvidia X Server Settings". You can find it in Applilcations > Add/Remove Applications.  Just copy and paste the phrase in the search bar and it will come up.

Once that is installed, Open it from System > Administration > Nvidia X Server Settings, and click on "X Server Display Configuration"

-Shut-Down Beep: System > Preferences > Sound > click on the system beep tab.

-root in terminal: [http://tombuntu.com/index.php/2007/12/07/get-a-root-terminal-in-ubuntu/](http://tombuntu.com/index.php/2007/12/07/get-a-root-terminal-in-ubuntu/)

---

### Post by philcamlin on 2009-06-29
•how do I turn the shutdown beep off? (It is annoying)

rmodpcspkr :)

 
•What is the command to run as root? (I know it is not recommended)

sudo - you need it to install things 

•Sorry if this is in the wrong forum.

its not :popcorn::popcorn:

---

### Post by pqwoerituytrueiwoq on 2009-06-29
@[Megrimn]("http://ubuntuforums.org/member.php?u=769124")
There is no 'system beep tab'
it says it can't apply changes cause i change it ti that mode XP
@[philcamlin]("http://ubuntuforums.org/member.php?u=834502")
Not for just one command i mean run the system as root (you know so there are no password prompts)
is 'rmodpcspkr' a terminal command or a application?

---

### Post by paul_be on 2009-06-29
su -switches to superuser 'root'
sorry if you have not set a password for root run sudo su
the terminal will have $ for a regular user and # for root
type exit to exit from root

---

### Post by starcraft.man on 2009-06-29
1. I may be wrong but I don't think degrading the color saves that much power. Most of the power to my knowledge comes from the Components running (i.e. processor, gpu, HDD) and the back light of the screen. Whether or not your screen is displaying 24 bit color, I don't believe changes the power drain much, it's the act of having it on that does the power drain. I'm certain dimming it would probably save the most.

If you insist, install the Nvidia drivers. Please not by the add remove panel but by the System > Administration > Hardware drivers menu. Just enable the driver there and it will install and configure them for you. Once installed, check either under the application menu or the system > administration menu to find the nvidia panel. Go to the display configuration menu (on left) then select panel and go to the xscreen tab and pick your color setting.

I still don't think it's a big saver. 

2. System > Preferences > Sounds > Sounds tab > Go to the main pane, scroll down to desktop and disable log out effect (log in too I guess). I think that's it.

3. sudo for the terminal commands. Gksudo to start a graphical app in a terminal. [Explained here.]("https://help.ubuntu.com/community/RootSudo") 

Edit: By default, the root account is disabled for good reason it's unnecessary to run as such. If you need a whole sessions in terminal as root, use su. You shouldn't have that many prompts once your set up, it doesn't take that long.

4. Why can't they be completely installed? Please copy paste the error here. You should be able to. Would be helpful if you list the exact names of the packages. Go System > Admin > Software sources. Make sure first tab, has everything from top to source code checked (exclude source code). Then go to updates and make sure important, security and unsupported are checked. If it persists, post more details.

---

### Post by philcamlin on 2009-06-29
> **pqwoerituytrueiwoq said:**
> @[Megrimn]("http://ubuntuforums.org/member.php?u=769124")
There is no 'system beep tab'
it says it can't apply changes cause i change it ti that mode XP
@[philcamlin]("http://ubuntuforums.org/member.php?u=834502")
Not for just one command i mean run the system as root (you know so there are no password prompts)
is 'rmmodpcspkr' a terminal command or a application?


you  run it in terminal :)

EDIT! its rmmod sorry my typo :P

sudo rmmod pcspkr

---

### Post by dtoronto on 2009-06-29
you can log in as the root user but first you need to set your root password with:

```
$sudo passwd
```

after that you can use the su to log in as a super user.

```
$su
```

---

### Post by Megrimn on 2009-06-29
> **pqwoerituytrueiwoq said:**
> @[Megrimn]("http://ubuntuforums.org/member.php?u=769124")
There is no 'system beep tab'
it says it can't apply changes cause i change it ti that mode XP


the system beep thing must be a distro difference... I haven't done much with Jaunty yet.

And here are a few suggestions for your update problem:

Try uninstalling the individual packages in System > Administration > Synaptic Package Manager.  Just type the names of the packages in the search bar and uncheck the boxes.  Don't forget to hit the "apply" button on the way out.

If that doesn't work, try opening a terminal and use this code:
```
$sudo apt-get --purge -r package
```

where "package" is the name of the package you wish to remove


Another one you can use is 
```
$sudo dpkg --purge package
```

---

### Post by pqwoerituytrueiwoq on 2009-06-29
@[starcraft.man]("http://ubuntuforums.org/member.php?u=250927")
With the error i really don't want to reproduce it. As I mentioned I reinstalled the OS to get around it. (even tried recovery mode from boot menu)
You cant do it fresh install -> open update manager and click install/apply (what ever the word was)
the system lagged like this thing does till I enabled that video driver
[http://i40.tinypic.com/24g0wb8.png](http://i40.tinypic.com/24g0wb8.png)

Every little bit helps.
BTW: error [http://i40.tinypic.com/2818mdl.png](http://i40.tinypic.com/2818mdl.png)

---

### Post by pqwoerituytrueiwoq on 2009-06-29
@[paul_be]("http://ubuntuforums.org/member.php?u=856471")
It gives me an Authentication error when i try the command su
tried su {username}
then inserted my password
entered exit
then exit again to close it the $ never changed to a #

---

### Post by lovinglinux on 2009-06-29
> **pqwoerituytrueiwoq said:**
> &#8226;What is the command to run as root? (I know it is not recommended).

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=119428&stc=1&d=1246333661[/IMG]

If you want to run as root for regular usage you will probably get into several permissions problems, not to mention the security concerns. If you find the password requests annoying, then [increase it's timeout](http://ubuntuforums.org/showpost.php?p=5334935&postcount=2).

> **pqwoerituytrueiwoq said:**
> 
&#8226;The Update Manager by default marks the restricted packages for installation. Which can't be fully installed causing an error. and it will not let you remove them either. Which make adding new software impossible. (I reinstalled the OS to fix it)

I don't think it does. Restricted packages are not installed by default because they are not free.


*UKeywords: 649167 2009 june root sudo*

---

### Post by pqwoerituytrueiwoq on 2009-06-30
@[lovinglinux]("http://ubuntuforums.org/member.php?u=649167")
"I don't think it does. Restricted packages are not installed by default because they are not free."
well it did

---

### Post by pqwoerituytrueiwoq on 2009-06-30
bump and have another error [http://i42.tinypic.com/23t5fk9.png](http://i42.tinypic.com/23t5fk9.png) - screenshot flash thinks im using XP  BTW wine is set to windows 2.0 and it is not on anyway also flash 10 is installed

---

