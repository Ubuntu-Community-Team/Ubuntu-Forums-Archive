---
title: "your username is unknown to sudo"
date: 2009-11-04
forum: General Help
---

### Post by 824957q on 2009-11-04
ok i have linux kubuntu i think i took my self out of the administraters thingy and it says your username is unknowm to sudo! what do i do i cant install anything and i stilll do need to install the flash!!!!!!! hellllllp

---

### Post by sisco311 on 2009-11-04
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by yeats on 2009-11-04
I've done that before.  See here:

[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Edit: sisco beat me to the punch! :-)

---

### Post by OffAxis on 2009-11-04
reboot into 'Recovery Mode'.

Drop to a root prompt.
```

usermod -g admin <username>
```
-g means group
"admin" is the group you to get into
username is the account you want back in the group (admin).

---

### Post by 824957q on 2009-11-04
omg! im the only account on my cp! and when i try to go into the grub menu at the begingin by pressing escape nothing happens it just proceeds to start up and then again im the only one in therte!

---

### Post by sisco311 on 2009-11-04
> **OffAxis said:**
> 
-g means group
"admin" is the group you to get into
username is the account you want back in the group (admin).

-g sets the user's new initial login group


the correct command would be:
```
usermod -aG admin username
```
```
adduser username admin
```
or 
```
gpasswd -a username admin
```

---

### Post by sisco311 on 2009-11-04
> **824957q said:**
> omg! im the only account on my cp! and when i try to go into the grub menu at the begingin by pressing escape nothing happens it just proceeds to start up and then again im the only one in therte!

If you are using Karmic (grub2) hold down Shift instead of Esc.

---

### Post by 824957q on 2009-11-04
:""( i dont get it can you help me like bye step bye step pweeeease can u gimme good instructions

---

### Post by Ant59 on 2009-11-04
What version of Kubuntu are you running? Is it 9.10?

---

### Post by sisco311 on 2009-11-04
> **824957q said:**
> :""( i dont get it can you help me like bye step bye step pweeeease can u gimme good instructions


Follow this instructions:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

but instead of pressing Esc to display the grub menu hold down the SHIFT key.

---

### Post by 824957q on 2009-11-04
i did jold down the shift key but NOTHING and idk what version it just says kubuntu

---

### Post by 824957q on 2009-11-04
Help me!!!!!!!!!! I am not in the sudoers file!! I have a linux kubuntu and when i try to go into thwe grub menu it just keeps going to kubuntu!!!!!!! Help i need step bye step instructions!!!!!! Please i need a linux genius

---

### Post by sisco311 on 2009-11-04
Open a terminal: KMenu -> System -> Terminal Program (Konsole)
and post the output of:
```
lsb_release -a
```

---

### Post by Ant59 on 2009-11-04
Ok.

How long have you had Kubuntu installed? Have you ran any commands recently that you've found on the internet? Have you purposely edited your sudoers file or your user account's membership to the admin group? You must have done something to your system to cause this problem.

To solve the problem, all you need to do is follow the instructions on the link posted by the other's in this thread. It will tell you what to do.

If nothing is happening when you press ESC or SHIFT when your PC starts, then explain when you're pressing them please, because it may be that you are not pressing them when GRUB is counting down.

If none of this helps you, explain what happens when your PC boots up. Are you using a dual-boot system (ie. Windows and Ubuntu, with a menu to choose between the two?)

I'm just trying to think of everything here, so just say if any of this helps at all, and I'll continue from there :)

---

### Post by 824957q on 2009-11-04
No lsb modules are available!!!!! Why!!!! Lol help

---

### Post by Ant59 on 2009-11-04
That message is irrelevant. What is the version displayed underneath?

---

### Post by sisco311 on 2009-11-04
> **824957q said:**
> No lsb modules are available!!!!! Why!!!! Lol help

then:
```
cat /etc/lsb-release
```
and
```
id
```

---

### Post by cariboo on 2009-11-04
Please quit bumping so much and quit using so many exclamation points, it makes your posts hard to read.

---

### Post by Ant59 on 2009-11-04
[quote=824957q]ok look it takes me a long time to turn on my computer so i want you to give me a list of instructions to get to recovery mode ok? and what to do from there[/quote]

Ok. When you get to the menu, go down to recovery mode and press <Enter> to boot into recovery mode. Select "root" from the next menu. This will drop you to a terminal as the root user.

First, run this command:
```
adduser yourusername admin
```

Replace yourusername with your user account!

Next, you must edit your sudoers file, to make sure you didn't stop the "admin" group from being allowed to "sudo".

Type this:

```
sudo nano /etc/sudoers
```

This will enter you into "nano" which is a terminal-based text editor, so that you can change the file.

Make sure that the file looks like this (if not, change it):

```
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

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```


Press Ctrl+X, Ctrl+Y and then <Enter> to save and exit.


Next, type:


```
exit
```


This will log you out of the terminal, and return you to the recovery mode menu.


Select "resume" from the menu, and you will continue to boot into (k)ubuntu as normal.


This should be all you need to do!

---

### Post by 824957q on 2009-11-04
i need the help of everyone!!!!!!!!!!!! i have linux kubuntu and it says i am not a administrater but im the only one there when i try to enter th grub menu i press esc and shift but non of the buttons let it enteer what can i do!!!!!! if a clean install is the only answer then plaease give me directions on how to do it ):P

---

### Post by 824957q on 2009-11-04
i need the help of everyone!!!!!!!!!!!! i have linux kubuntu and it says i am not a administrater but im the only one there when i try to enter th grub menu i press esc and shift but non of the buttons let it enteer what can i do!!!!!! if a clean install is the only answer then plaease give me directions on how to do it 
824957q is online now   Report Post   Edit/Delete Message

---

### Post by overdrank on 2009-11-04
Hi and please don't create multiple threads on the same issue. Threads merged.

---

### Post by 824957q on 2009-11-04
i need the help of everyone!!!!!!!!!!!! i have linux kubuntu and it says i am not a administrater but im the only one there when i try to enter th grub menu i press esc and shift but non of the buttons let it enteer what can i do!!!!!! if a clean install is the only answer then plaease give me directions on how to do it

---

### Post by kansasnoob on 2009-11-04
You obviously hosed sudoers which requires editing with vi.

It can't be done unless you're calm, and even then it's difficult!

I'm too tired to help right now but I'll guarantee you you'll get no help at all if you just keep screaming!

---

### Post by 824957q on 2009-11-05
ok i have linux kubuntu i have 9.4 i think ok my problem is that i changed something and now i cant instsll anything cause it prompts me for a password and when i put my password it says your username is unknown to sudo and when i tr to boot into grub menu at the begining  i press esc or shift it doesnt go into that menu it just continues too boot i dont even have flash player yet plaease i need help plaes!!!!!!!!!!!!!!!!!!!! please!!!!!!!!!!!!!!!!!!!!!! and no i havent updated to 9.10 or whatever helpppp

---

### Post by liquidbee on 2009-11-05
Nvm .. 
---------------------

```
cat /etc/sudoers
```

What's the output ?

---

### Post by 824957q on 2009-11-05
cause theres a update and people are getting confused plaease can you help me!

---

### Post by 824957q on 2009-11-05
permission denied...

---

### Post by lukjad on 2009-11-05
Do you have the Kubuntu/Ubuntu CD?

---

### Post by 824957q on 2009-11-05
no....

---

### Post by 824957q on 2009-11-05
what can i do about this ps. i cant go into recovery mode because i cant access the grub menu i press the keys and everyrthing but it continues to boot

---

### Post by sliketymo on 2009-11-05
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by lukjad on 2009-11-06
Can you burn one, or get someone to burn it?

---

### Post by 824957q on 2009-11-06
ok i have a linux kubuntu and whenever i try to install or do somthing it sys you dont have neccery privleges or your username is unknown to sudo i tried goinmg into recovery mode but when i press escape or shift it just continues too boot can a linux genius help me lol or anybody!!!!

---

### Post by MaquinaX on 2009-11-06
Well... since internet and computers are more common now in days..., you can go to a buddy's house, download ANY Ubuntu/Kubuntu Live CD, burn it (would be nice to pay your buddy for the disk), and then you have a Live CD of your own, which is always important to have.
If for some reason you live in a remote location, with no friends for hundreds of miles from your home, you can go to Ubuntu/Kubuntu website, and order the Live CD for like $2. If you have a USB keyboard, you can also check to see if your BIOS has USB keyboard support at startup. Hope this helps.

MaquinaX

---

### Post by bodhi.zazen on 2009-11-06
You need to add your user to the admin group.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Lars Noodén on 2009-11-07
Or, instead of adding more users to the group **admin**, you can make use of fast user switching and briefly log in to the account with admin privileges and add the stuff you need.

---

### Post by 824957q on 2009-11-10
ok my computer is broken so i have to do a clean install because i broke sudo, so once i burn karmic koala to my blank disc and put it inside the computer will it boot by itself? ps. i can't acceess the grub menu when i press escape or shift it just keeps going so basicly my main question when i put in the install disc will it detect it and by detect it will it automaticly boot the cd? cause i can't put the cd drive as the first boot because i can't access the grub menu thank you for your help!

---

### Post by philinux on 2009-11-10
It's your bios that determines the boot order i.e dvd, hard disk, usb etc. On mine I press the delete key to go into the bios.

Yours maybe set to boot from cd/dvd first.

---

### Post by prem1er on 2009-11-10
What is the make of your computer?

---

### Post by 824957q on 2009-11-10
oh ok! so accesing the grub drive and accesing the bios drive are 2 completely diffrent things?? ok and  could you give me a hint on how to access my  bios drive when i start my computer it says hp hewlett packrd do you have any idea what i press to access my bios drive?

---

### Post by prem1er on 2009-11-10
HPs are normally the F1, F2, or ESC keys to enter the bios menu.

---

### Post by 824957q on 2009-11-10
i cannot acces my grub menu.. or my bios menu i figured out why when the menu to press the escape key opens mykeyboard isn't turned on yet until it statrts booting kunbuntu how do i make my keyboard boot before that?

---

### Post by kio_http on 2009-11-10
> **824957q said:**
> i cannot acces my grub menu.. or my bios menu i figured out why when the menu to press the escape key opens mykeyboard isn't turned on yet until it statrts booting kunbuntu how do i make my keyboard boot before that?

Please take the time to write the post properly. The language isn't very understandable. Also what do you mean "how do i make my keyboard boot before that"

Booting a keyboard!:KS

---

### Post by 824957q on 2009-11-10
i cannot acees my grub menu or bios menu because my keyboard does not boot til;l after the menu dissapears

---

### Post by kio_http on 2009-11-10
> **824957q said:**
> i cannot acees my grub menu or bios menu because my keyboard does not boot til;l after the menu dissapears
You mean your keyboard is not detected. Try restoring your bios to defaults. What's your keyboard model. Do you have any other spare keyboards to identify whether the problem is keyboard or motherboard?

---

### Post by 824957q on 2009-11-10
no,no,no look my computer starts my keyboard is not usable until i hear the little "beep" but the key board is not booted or on yet when the "press escape key to enter this menu" my keyboard is not on yet until that menu dissapears and my keyboard is a belkin

---

### Post by mr_steve on 2009-11-10
If you have a USB keyboard, this usually means you have to change the "USB Legacy Support" or similar option in your BIOS.

There is a problem with this sometimes though. I've found on some of my machines that if USB Legacy Support is set one way, I can access the Grub menu but the keyboard doesn't work once booted. Whereas with it set the other way, the keyboard works fine after boot, but I can't access the Grub menu.

I haven't found a perfect solution to this yet.

---

### Post by 824957q on 2009-11-10
i dont have a usb key board....

---

### Post by QIII on 2009-11-10
That "beep" is part of the POST process.  Your keyboard probably wouldn't respond during that process.  Immediately after that, you should be able to use the keyboard to enter your BIOS.
 
 Are you saying that your keyboard is essentially non-functional until an OS is actively running?

Can you use your function keys as specified by the manufacturer to enter the BIOS?

If not, my first inclination would be to suspect the keyboard itself.  Perhaps the esc key is the specific culprit.

Do you have a spare keyboard to try?

---

### Post by 824957q on 2009-11-10
well its not the keyboard the keyboard is inactive until i see the kubuntu loading

---

### Post by QIII on 2009-11-10
> **824957q said:**
> well its not the keyboard the keyboard is inactive until i see the kubuntu loading

If your keyboard is not active until an OS is "live", there is an underlying problem unrelated to the OS itself.

If it is not the keyboard, then it may be other hardware or a BIOS problem.

It might serve you well to google your model of computer and see if the help/technical forums indicate that others are having similar problems.

It could be that some kindly hardware guru will stop by and see your post, so keep checking back.

Diagnosing the problem would be made much easier if you would post the full specs of your machine -- every detail you can find.

---

### Post by 824957q on 2009-11-10
i broke sudo what can i do to fix it?

---

### Post by 824957q on 2009-11-10
help? pweaaaaaaaassssse

---

### Post by mick55 on 2009-11-10
You can't break sudo.

Go into users and groups select the user in question (you)
and check the box for "administer system"

Then you should have your admin rights back.

cheers
mick

---

### Post by 824957q on 2009-11-10
i have the program kubuntu 9.4  and want to install karmic koala  i have the iso ready to burn but once its in setup what do i doo from there ps im doing this because my sudo broke

---

### Post by whoop on 2009-11-10
> **824957q said:**
> i have the program kubuntu 9.4  and want to install karmic koala  i have the iso ready to burn but once its in setup what do i doo from there ps im doing this because my sudo broke

Wouldn't it be easier and more educational to fix your broken sudo? shouldn't be hard.... 
(Re)installing is always the final solution, if nothing else works (which never happens off course).

How is it broken?
maybe this helps:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by 824957q on 2009-11-10
i have kubuntu 9.4 can you give me instructions to get my rites back

---

### Post by mick55 on 2009-11-10
K-menu->System Settings->Users and Groups                          .

To edit the properties of each user, click the *Modify...* button located in the main *Users* window. 

good luck
mick

---

### Post by 824957q on 2009-11-11
is there anyway that i can fix sudo and make me a administrater without going into recovery mode or doing a clean install?? please i have this problem forever please help

---

### Post by Giblet5 on 2009-11-11
Yes.

---

### Post by snowpine on 2009-11-11
That's *exactly* what recovery mode is for. :)

Here's a good tutorial: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by 824957q on 2009-11-11
i can't access the grub menu! is there another way!

---

### Post by overdrank on 2009-11-11
Duplicate [Here]("http://ubuntuforums.org/showthread.php?t=1322282") Thread closed

---

### Post by 824957q on 2009-11-12
can i fix this without  going into restore mode or a new reinstall please ive been looking for a answer forever i need a good answer

---

### Post by Ms_Angel_D on 2009-11-12
lol wow could you be any less descriptive ;) if your wanting help your going to have share more information about the problem.

---

### Post by t0p on 2009-11-12
> **824957q said:**
> can i fix this without  going into restore mode or a new reinstall please ive been looking for a answer forever i need a good answer


If you post the question, you may get an answer.

If you don't, you'll have to rely on one of this forum's telepathic members seeing your post.  Or "sensing" it.

---

### Post by Giblet5 on 2009-11-12
I have already explained to this person how to proceed (how to get into recovery mode, boot from CD, etc).

He never replies and then posts the same question awhile later.

There is clearly a language barrier problem here, but that doesn't explain the silence.

Now, he'll probably PM you, ask the same question again, and ignore whatever you suggest w/o responding.

I'm beginning to think it's someone's pet goat having fun with us. :)

---

### Post by Elfy on 2009-11-12
Thread closed - duplicate here [http://ubuntuforums.org/showthread.php?t=1322282](http://ubuntuforums.org/showthread.php?t=1322282)

---

### Post by 824957q on 2009-11-12
i have kubuntu 9.4 and i believe i made a new account but when i made a new account i forgot to make me a adminstrater of my computer and now i can't install or upgrade because it prompts me for a password and when i put in my password it sys "your username is unknown to sudo" so when i try to go into restore mode i press the buttons to access the grub menu but nothing happens and i don't have anybody that can burn me a copy of kubuntu so is there another way! please even if you can help me through the remot desktop client!!!!! please!

---

### Post by Bunnybugs on 2009-11-12
What did you do with your old Account??

Have you tried to use your old admin-account password for sudo??

---

### Post by t0p on 2009-11-12
I take it this post is to provide the details that you didn't provide in your other thread?

No reason to start this new thread.  You could have just added this info to your previous thread.

Anyway: the only way you can fix this is to go into safe mode/restore/whatever it's called, where you get a root prompt; then use the useradd (adduser?) command to give your user account admin privileges.  Check 'man useradd' (or 'man adduser') for info on how to use command.

Incidentally: sudo isn't broken.

---

### Post by 824957q on 2009-11-12
yeah but i deleted my old account! and im using the pre made account man! i did it by accident so is there any other way

---

### Post by module0000 on 2009-11-12
Use sudo with your old account to add your NEW account to the group 'admin'.  That will allow your new account to use sudo.

---

### Post by Elfy on 2009-11-12
Thread closed - do not keep opening new threads on the same question. The original is still open here

[http://ubuntuforums.org/showthread.php?t=1322282](http://ubuntuforums.org/showthread.php?t=1322282)

---

### Post by 824957q on 2009-11-12
I broke sudo help i cant go into recovery mode and it will take me too long to find someone to burn the disc can someone hhelp!!!!!!!!!!!!!

---

### Post by pennypincher824 on 2009-11-12
hi, i have sudo 9.4 and i took myself out of the sudoers file by accident by unchecking the admin box and i can't access the grub menu i press the buttons but nothin happens and it takes to long to find someone with a cd burner is there a way to fix sudo with a special code or something

---

### Post by aysiu on 2009-11-12
If you can't access the Grub menu or boot from a live CD, then, no, you can't fix sudo unless you physically remove the hard drive from your computer and put it as a slave drive in another computer.

More details here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by pennypincher824 on 2009-11-12
i could get a live cd but hopefully it works thanks for your help! oh and i want to get ubuntu not kubuntu how do i know wich one im getting

---

