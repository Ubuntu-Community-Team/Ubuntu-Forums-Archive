---
title: "new to ubuntu ! got a lot of questions :)"
date: 2011-06-18
forum: General Help
---

### Post by hitch_11 on 2011-06-18
hi all !
i got ubuntu 10.10 couple days ago ! and im facing some probs coz im not good in ubuntu world lol 
im tryin to upgrade to ubuntu 11 but i cant it says : Failed to run /tmp/update-manager-dvTJWJ/natty as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

thats was the first prob lol ! and i have no idea what the hell that suppose to mean ! 
another prob : when i was using win7 ..my wireless signal was always 100% but since i got the ubuntu i have to stay like dumb next to my router or i dont get a good signal ! furthermore i use the int for couple hours then it disconnet by itself and i wont reconnet again ... what can i do for that guys !! ??

and do i have to get an antivirus or no ?
what about sounds ! ? on my win7 my music had a higher sound :) !!!
and i have the hp -620 hewlett packard do i need to download any driver after having ubuntu ??

so it just the begining u ll see a lot questions later in the forum lol so if u guys wanna help me ( and please do LOL ) dont forget that im new to ubuntu so try to be simple as much as u can ( damn i feel like a idiot right now ) :P and thanks in advance 
+ what do u think is the thing i should know it the best using the ubuntu !

---

### Post by TheDoctorX on 2011-06-18
> **hitch_11 said:**
> hi all !
i got ubuntu 10.10 couple days ago ! and im facing some probs coz im not good in ubuntu world lol 
im tryin to upgrade to ubuntu 11 but i cant it says : Failed to run /tmp/update-manager-dvTJWJ/natty as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

thats was the first prob lol ! and i have no idea what the hell that suppose to mean ! 
another prob : when i was using win7 ..my wireless signal was always 100% but since i got the ubuntu i have to stay like dumb next to my router or i dont get a good signal ! furthermore i use the int for couple hours then it disconnet by itself and i wont reconnet again ... what can i do for that guys !! ??

and do i have to get an antivirus or no ?
what about sounds ! ? on my win7 my music had a higher sound :) !!!
and i have the hp -620 hewlett packard do i need to download any driver after having ubuntu ??

so it just the begining u ll see a lot questions later in the forum lol so if u guys wanna help me ( and please do LOL ) dont forget that im new to ubuntu so try to be simple as much as u can ( damn i feel like a idiot right now ) :P and thanks in advance 
+ what do u think is the thing i should know it the best using the ubuntu !

in linux for many operations you have to log in as admin ... so to do that you have to open the terminal and write "sudo" + the operation you want to access .. for the wifi you need to make a complete update ... this magic thing helps so much :D

linux does not need an antivirus because all the operations need you approval .. so a virus can't do anything without your permission :) if u want u can download a free antivirus "clamav" ... it's totally free a fully supported , but i repeat it's not necessary :)

---

### Post by nitstorm on 2011-06-18
@TheDoctorX:

I think the problem is that the user is not in the sudoers list.. look at the error the OP posted:

> Failed to run /tmp/update-manager-dvTJWJ/natty as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by lightstream on 2011-06-18
how are you upgrading hitch_11?

Best way is to use the Update Manager (look in the System > Administration menu)

---

### Post by TheDoctorX on 2011-06-18
yes but says that (sudo) doesmn't alloud him to access to the operation ... mmm, really the first times i worked on ubuntu i had the same problem and i solve it with the sudo autentication ...

---

### Post by nrundy on 2011-06-18
Any chance you're willing to do a fresh install? Just backup your HOME folder onto a CD/DVD, then do a fresh install of 11.04.

---

### Post by cptrohn on 2011-06-18
hitch_11 are trying to do a distro-upgrade to 11.04?

---

### Post by TheDoctorX on 2011-06-18
> **nrundy said:**
> Any chance you're willing to do a fresh install? Just backup your HOME folder onto a CD/DVD, then do a fresh install of 11.04.
 YEAH this is the real solution ... or maybe try wubi , with that thing u can install ubuntu "natty" like a simple program on win and u can remove it like a simple program ... just unistall !! it's the best thing if u are new of ubuntu .... so u can use win & ubuntu from the boot.ini menu of win:p

---

### Post by dougalkerr on 2011-06-18
Since no-one else has replied yet, I will have a go for you. I am by no menas an expert but, I have been using Ubuntu Ultimate edition for around a year full time at home.
For starters everyone that uses Ubuntu seriously will tell you not to bother trying to 'upgrade' to another future version using the 'Update manager'. Always download the latest version to a cd or dvd and install from that. It helps to get rid of a lot of problems in installation.
If Ubuntu is to be your only system on the HP then run through the install accepting all the defaults and all should be well.
The 'sudo' relates to use as a user gaining administrator privileges for installing updates, programs and running commands that will change system files and more.
You will probably need to become familiar with using the sudo command. Almost everyone does at some point if even to install a simple program or adjust something about the system. Todays Ubuntu however, should allow you to work with the system and programs without having to use the sudo command (along with whatever other instructions are needed) at all. It will limit you though.
Next your problem with the wireless signal could well be due to an inappropriate driver being used for your wireless modem in the laptop. Ubuntu can use the Windows drivers and the latest Ubuntu is better than ever at doing this so it will be well worthwhile installing at the latest Ubuntu although not everyone likes the new Unity interface (I don't) but, there is the option at Login to change to the Gnome Desktop environment. A lot of people like the KDE desktop environment (again I don't, I find it breaks every time I try to stick with it). Graphics cards (or at least the drivers for them) are notorious for going wrong with Linux. I tend to stick with the graphics drivers that come with the system which work by and large but, can be limiting for effects, eye candy. then you have to try the proprietary drivers when they are available from the graphics card manufacturers. It is best to do this as soon as you have installed Linux and have it working because these drivers can often screw up the Linux system meaning it has to be installed again as the drivers can be a hassle to uninstall if you are not used to using Ubuntu.
At least is doesn't take too long to install the system. Mine usually takes around 20 minutes but, I use Ultimate Edition with everything loaded. Plain Ubuntu should take around 12 to 15 minutes on a modern fast-ish laptop.
Next antivirus is not absolutely necessary on Linux as the hackers tend to attack the big boys - Microsoft and Apple. Apart from this the way Linux continually updates means they would have to continually change the structure of their viruses to match (not worth the hassle). Having said that, Clam antivirus is installed by default with some Ubuntu systems and you don't even know it is there.
Next sounds - it will depend upon which sound software has been installed by default with Ubuntu. I am not up to scratch with them but, once you get used to Ubuntu I am sure you will find that it is easy to change from one sound handling program to another popular one till you find the one that best suits your system. I know for a fact that the Ubuntu sound software on my PC at work is far superior to the Microsoft effort because when I am in the Ubuntu environment the sound suddenly become alive with lots of real stereo that I never noticed when in Windows 7. All sound drivers should already be downloaded with install and usually you will have the choice of at least two to choose from so, have a poke around. It will do no harm to try changing from one to the other when you find your way around the sound applet which is often within the volume control, right-click and choose preferences.
Next - the best thing about Ubuntu for me is how straightforward and simple things become compared with Windows. For example, a couple of weeks ago I decided to install Window 7 on an old computer. It installed okay but, the graphics card could not support the resolutions needed for the monitor in high colour 1280 x 1024. the best I could get with Windows 7 was 800 x 600 and 64,000 colours. Also, it could not install my one year old HP multi function printer, copier, scanner.
I decided to scrub Windows 7 and install Ubuntu 11.04. It installed easily and allowed me to get the proper resolution for my monitor with no hassle and true colour too. Then the icing on the cake, the HP device installed within 10 seconds with absolutely no fuss and within another 20 seconds I had a scanned copy of a document I needed to copy before sending the original away. Hows that??? If I was still in the Windows environment I would never have been able to scan the document. Now I am not saying that Ubuntu has installed the HP software, no that is usually not possible because like too many large companies, HP does not pander to the honest Joe trying to keep costs down and productivity high by using Ubuntu so we have to take a different approach. Ubuntu kindly installas a simple scanning program called 'Simple Scan' and this did the job for me very easily. Allowing me to scan anything I want for later use in whatever program I want to use. The GIMP for example is a very good graphics manipulation program and a lot of people would say rivals Photoshop in a lot of areas and is absolutely free.
But, the nicest thing about Ubuntu for me is the eye candy, the effects you can have if your graphics card allows. With everything from wobbly widows when moving them to a cube that can rotate at your will to change to another desktop with other work you may have or web browser or whatever. you can have six sides to choose from with eahc having all the everyday controls and menus but, still allow space for whatever program you want to run and any desktop. I have never successfully used a multi-desktop environment in Windows without it crashing. Ubuntu however has never crashed with its multi-desktops.
What else? Just ask. I am sure someone will answer. We can be a very friendly bunch working for one another as opposed to software houses. Download a new copy today and enjoy. If you still have problems with Ubuntu you can try one of the other 'lighter' distributions. Perhaps you will find that Ubuntu per-say is not for you but, Linux mint might be. The main thing is to have fun with 'your' operating system and never have to think about 'activating' your system ever again.

---

### Post by hitch_11 on 2011-06-18
wow guys that was fast and clear  ! we have a lot of generous pple here lol .. i wanna thank u all for the help .. and all ur posts gave me a kinda image of how things going on ubuntu ,,! 

but u know guys reading all post something makes me feel that im a dumbass who never touched a pc before ! coz talking about sudo .. and utilmate version and i dont what else ...i didnt get how to do these things ! i like ubuntu and im looking to be someone who is knowing whats going on this *** laptop lol 
lets get serious now ! i changed the user type and i make it an administrator and when i go to install all the updates it says : Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

 i mean what the hell ! ? how come ??? updates from an authenticated sources ???  then i cannot install any update because of this problem .. so come on and hit with the solution lol 

now im upgrading to ubuntu 11 ..it works now and thank u for helping me doing this .. thank u all again :)

---

### Post by hitch_11 on 2011-06-18
> **dougalkerr said:**
> Since no-one else has replied yet, I will have a go for you. I am by no menas an expert but, I have been using Ubuntu Ultimate edition for around a year full time at home.
For starters everyone that uses Ubuntu seriously will tell you not to bother trying to 'upgrade' to another future version using the 'Update manager'. Always download the latest version to a cd or dvd and install from that. It helps to get rid of a lot of problems in installation.
If Ubuntu is to be your only system on the HP then run through the install accepting all the defaults and all should be well.
The 'sudo' relates to use as a user gaining administrator privileges for installing updates, programs and running commands that will change system files and more.
You will probably need to become familiar with using the sudo command. Almost everyone does at some point if even to install a simple program or adjust something about the system. Todays Ubuntu however, should allow you to work with the system and programs without having to use the sudo command (along with whatever other instructions are needed) at all. It will limit you though.
Next your problem with the wireless signal could well be due to an inappropriate driver being used for your wireless modem in the laptop. Ubuntu can use the Windows drivers and the latest Ubuntu is better than ever at doing this so it will be well worthwhile installing at the latest Ubuntu although not everyone likes the new Unity interface (I don't) but, there is the option at Login to change to the Gnome Desktop environment. A lot of people like the KDE desktop environment (again I don't, I find it breaks every time I try to stick with it). Graphics cards (or at least the drivers for them) are notorious for going wrong with Linux. I tend to stick with the graphics drivers that come with the system which work by and large but, can be limiting for effects, eye candy. then you have to try the proprietary drivers when they are available from the graphics card manufacturers. It is best to do this as soon as you have installed Linux and have it working because these drivers can often screw up the Linux system meaning it has to be installed again as the drivers can be a hassle to uninstall if you are not used to using Ubuntu.
At least is doesn't take too long to install the system. Mine usually takes around 20 minutes but, I use Ultimate Edition with everything loaded. Plain Ubuntu should take around 12 to 15 minutes on a modern fast-ish laptop.
Next antivirus is not absolutely necessary on Linux as the hackers tend to attack the big boys - Microsoft and Apple. Apart from this the way Linux continually updates means they would have to continually change the structure of their viruses to match (not worth the hassle). Having said that, Clam antivirus is installed by default with some Ubuntu systems and you don't even know it is there.
Next sounds - it will depend upon which sound software has been installed by default with Ubuntu. I am not up to scratch with them but, once you get used to Ubuntu I am sure you will find that it is easy to change from one sound handling program to another popular one till you find the one that best suits your system. I know for a fact that the Ubuntu sound software on my PC at work is far superior to the Microsoft effort because when I am in the Ubuntu environment the sound suddenly become alive with lots of real stereo that I never noticed when in Windows 7. All sound drivers should already be downloaded with install and usually you will have the choice of at least two to choose from so, have a poke around. It will do no harm to try changing from one to the other when you find your way around the sound applet which is often within the volume control, right-click and choose preferences.
Next - the best thing about Ubuntu for me is how straightforward and simple things become compared with Windows. For example, a couple of weeks ago I decided to install Window 7 on an old computer. It installed okay but, the graphics card could not support the resolutions needed for the monitor in high colour 1280 x 1024. the best I could get with Windows 7 was 800 x 600 and 64,000 colours. Also, it could not install my one year old HP multi function printer, copier, scanner.
I decided to scrub Windows 7 and install Ubuntu 11.04. It installed easily and allowed me to get the proper resolution for my monitor with no hassle and true colour too. Then the icing on the cake, the HP device installed within 10 seconds with absolutely no fuss and within another 20 seconds I had a scanned copy of a document I needed to copy before sending the original away. Hows that??? If I was still in the Windows environment I would never have been able to scan the document. Now I am not saying that Ubuntu has installed the HP software, no that is usually not possible because like too many large companies, HP does not pander to the honest Joe trying to keep costs down and productivity high by using Ubuntu so we have to take a different approach. Ubuntu kindly installas a simple scanning program called 'Simple Scan' and this did the job for me very easily. Allowing me to scan anything I want for later use in whatever program I want to use. The GIMP for example is a very good graphics manipulation program and a lot of people would say rivals Photoshop in a lot of areas and is absolutely free.
But, the nicest thing about Ubuntu for me is the eye candy, the effects you can have if your graphics card allows. With everything from wobbly widows when moving them to a cube that can rotate at your will to change to another desktop with other work you may have or web browser or whatever. you can have six sides to choose from with eahc having all the everyday controls and menus but, still allow space for whatever program you want to run and any desktop. I have never successfully used a multi-desktop environment in Windows without it crashing. Ubuntu however has never crashed with its multi-desktops.
What else? Just ask. I am sure someone will answer. We can be a very friendly bunch working for one another as opposed to software houses. Download a new copy today and enjoy. If you still have problems with Ubuntu you can try one of the other 'lighter' distributions. Perhaps you will find that Ubuntu per-say is not for you but, Linux mint might be. The main thing is to have fun with 'your' operating system and never have to think about 'activating' your system ever again.

wow man thank u a lot ... u helped me out a lot .. i like ur reply the most helpfull one ..thanks a lot .. now tell how to go to the ulimate version lol ! and i ll be back after finishing upgrading to ubuntu 11. to post more of my problems and stupidity lol coz its gonna take much time i dont have a fast int :( .. its just because i liked the ubuntu and i dont wanna go back to win7 thats why im nagging to get the best use :) so where do i can get the photoshop by the way ! 
usually i have problem with reading forums coz i dont like to read a lot lol but i read all ur post word by word and thanks a lot again :P :):P

---

### Post by hitch_11 on 2011-06-18
> **cptrohn said:**
> hitch_11 are trying to do a distro-upgrade to 11.04?
 
LOOOL sorry man but what is a disto-update ??? i ll tell what i was doing .. i went to update manager and then click on the update button .. if u call this a disto-update well yes im doing it lol and if no im not doing it :P 
 
no seriously let me know what is a disto-update when u r back ! greetings ! :)

---

### Post by hitch_11 on 2011-06-18
> **TheDoctorX said:**
> yes but says that (sudo) doesmn't alloud him to access to the operation ... mmm, really the first times i worked on ubuntu i had the same problem and i solve it with the sudo autentication ...

hey thats what im looking for in ubuntu .. to solve problems through commands :) please let me ask u : what is the difference between terminal and sudo ? and do u know where do i can get a list of the powerfull commads in linux ??? thanks a lot :)

---

### Post by nitstorm on 2011-06-18
> **hitch_11 said:**
> hey thats what im looking for in ubuntu .. to solve problems through commands :) please let me ask u : what is the difference between terminal and sudo ? and do u know where do i can get a list of the powerfull commads in linux ??? thanks a lot :)


In the olden days all you had was the command-line. And that's how you would pass instructions and commands to the computer, then GUI came along. The terminal is just an emulation of that olden (yet golden) command-line interface. So it's let's you run command-line stuff even when you are using GUI.

sudo is a feature where a user is given temporary super-user or root permissions to execute a command.

The best place to start learning all the command line stuff is here - [http://linuxcommand.org/](http://linuxcommand.org/)

> LOOOL sorry man but what is a disto-update ??? i ll tell what i was  doing .. i went to update manager and then click on the update button ..  if u call this a disto-update well yes im doing it lol and if no im not  doing it :razz: 
 

A distro-upgrade or a distribution-upgrade is when there is a newer version of the distribution that has been released. The update-manager automatically finds this new version when it is released and gives you the option to upgrade to the new distribution release if you want to. 
Example : There are many versions of Ubuntu out there, the most recent being 10.04, 10.10, 11.04 
Now say, you are on 10.10 and 11.04 just released or something, then when you open the Update Manager, there is an additional option that allows you to upgrade your distribution to 11.04 . That's called a distribution-upgrade or a distro-upgrade for short

When you go to Update Manager and click "Install Updates" , you are doing an upgrade of the packages (programs) installed on your computer. That does not make it a distro-upgrade.

Hope this answers your questions :) And a huge welcome to UbuntuForums and Ubuntu in general :)

---

### Post by idoitprone on 2011-06-18
To kind of explain what Linux is, you have to explain what an operating system is. And the thing about an operating system is that you're never ever supposed to see it. Because nobody really uses an operating system; people use programs on their computer. And the only mission in life of an operating system is to help those programs run. So an operating system never does anything on its own; it's only waiting for the programs to ask for certain resources, or ask for a certain file on the disk, or ask to connect to the outside world. And then the operating system steps in and tries to make it easy for people to write programs.
-Linus Torvalds

[http://en.wikiquote.org/wiki/Linus_Torvalds](http://en.wikiquote.org/wiki/Linus_Torvalds)


Remember an operating system is defined by its bloat. Xserver, gui and even some command line utilities are bloat as nitstorm noted. 

Heck, if we put window7 and vista side by side, all the vista haters cannot tell the difference

So, do like bloated linux?

---

### Post by hitch_11 on 2011-06-18
> **nitstorm said:**
> In the olden days all you had was the command-line. And that's how you would pass instructions and commands to the computer, then GUI came along. The terminal is just an emulation of that olden (yet golden) command-line interface. So it's let's you run command-line stuff even when you are using GUI.

sudo is a feature where a user is given temporary super-user or root permissions to execute a command.

The best place to start learning all the command line stuff is here - [http://linuxcommand.org/](http://linuxcommand.org/)



A distro-upgrade or a distribution-upgrade is when there is a newer version of the distribution that has been released. The update-manager automatically finds this new version when it is released and gives you the option to upgrade to the new distribution release if you want to. 
Example : There are many versions of Ubuntu out there, the most recent being 10.04, 10.10, 11.04 
Now say, you are on 10.10 and 11.04 just released or something, then when you open the Update Manager, there is an additional option that allows you to upgrade your distribution to 11.04 . That's called a distribution-upgrade or a distro-upgrade for short

When you go to Update Manager and click "Install Updates" , you are doing an upgrade of the packages (programs) installed on your computer. That does not make it a distro-upgrade.

Hope this answers your questions :) And a huge welcome to UbuntuForums and Ubuntu in general :)

ok i got it :) and yes i am doing a distro-update lol :) thank u man that was helpfull

---

### Post by hitch_11 on 2011-06-18
> **idoitprone said:**
> To kind of explain what Linux is, you have to explain what an operating system is. And the thing about an operating system is that you're never ever supposed to see it. Because nobody really uses an operating system; people use programs on their computer. And the only mission in life of an operating system is to help those programs run. So an operating system never does anything on its own; it's only waiting for the programs to ask for certain resources, or ask for a certain file on the disk, or ask to connect to the outside world. And then the operating system steps in and tries to make it easy for people to write programs.
-Linus Torvalds

[http://en.wikiquote.org/wiki/Linus_Torvalds](http://en.wikiquote.org/wiki/Linus_Torvalds)


Remember an operating system is defined by its bloat. Xserver, gui and even some command line utilities are bloat as nitstorm noted. 

Heck, if we put window7 and vista side by side, all the vista haters cannot tell the difference

So, do like bloated linux?

well actually i like everything about linux :P but ask this quest about a month and lets see lol

---

### Post by hitch_11 on 2011-06-18
guys i found this while i was reading ! 
"Don't operate the computer as     the superuser. You should only become the superuser     when absolutely necessary. Doing otherwise is     dangerous, stupid, and in poor taste. Create a user     account for yourself now!"

i am using an administrator account ! so is it the same as superuser ? do i have to create another account ? 
and do i have to switch accounts everytime i have to download   how many accounts u guys usually use ! coz i set all passwd the same lol so everytime it asks me for a passwd i enter the same one so i dont care if its the superuser passwd or root pass or whatever ! and what the difference between account types as well ? how many kind r they !! i know u r sayin now this dumb will never stop asking lol but u r the only source to get the right info :) thanks in advance

---

### Post by idoitprone on 2011-06-18
Even though your account is an administrator account. You are not constantly running as a super user. Ubuntu disable root on default. The way admin accounts work in Ubuntu is just like Vista UAC. You must grant program elevated permission to make changes to the system. Yes, asking you for your password is elevating your permissions.

You can elevate your user by using the command sudo or su (disable in ubuntu i believe ) to enter root shell

Remember linux is designed as a multi-user operating system. 

```
cat /etc/group

```
will add some ideas on how resources are managed

---

