---
title: "bad choice of security model for user accounts"
date: 2006-06-02
forum: General Help
---

### Post by m_pav on 2006-06-02
This posting was brought about by my trying to use partimage - a hard disk imaging program that requires root priveleges, not supplied with Ubuntu by default, but it's one of my favorites so I installed it via synaptic.

After touting the superior security model of Linux to hundreds of Windows users for the last 2 years while I immersed myself in the Mepis distributions, and though I already knew how Ubuntu set up the first user to have su priveleges using the same password, I have to give a big thumbs down to the use of _almost_ the same security model that has plagued microsoft windows users for as long as it's been there - the standard user has admin priveleges.  Don't get me wrong here, I absolutly love linux and what Ubuntu has done for Linux, but this is an area I have grave concerns about.

I am a computer technician that has to repair the damage done by children and teenagers that do not have the understanding of an adult on issues such as security, anonymity in certain places, general care and attention, not giving out your password and not letting just any of your freinds or acquaintences have access to your system. To me, giving a child (or computer novice) almost full access to a filesystem is like giving a child the keys to your V8 powered monster-truck. It's ludicrous that such a person be given full access to such power, and I am often advising parents to make a limited account on their windows systems for their children, right up to the age of 18.

Surely this model is fatally flawed and and will give rise to Ubuntu being the first linux distro to be attacked en-masse with worms and viruses.

I propose a change to the higher and better securtiy model as standard that has always been in place with debian, a seperate account for the super user with all users being set up as limited users and only the root can give then additional priveleges or at least an option to choose it during installation. If this is not possible, how about an option on first boot to inform new users and give them the option to change their setup.

What does the rest of the population think?

---

### Post by grsing on 2006-06-02
I believe the thinking of the devs with the su system was that making you type your password before doing anything that could really screw the system up would make you take pause and think before doing it.  I agree with kids and real novices (who have the benefit of a system admin or some sort or another) getting limited accounts, but making it the default could be frustrating (maybe the install could prompt with options).  I definitely see what you're saying, though, and it makes sense.

---

### Post by 23meg on 2006-06-02
[QUOTE=m_pav]Surely this model is fatally flawed and and will give rise to Ubuntu being the first linux distro to be attacked en-masse with worms and viruses.[/QUOTE]Please explain in clear technical terms how exactly this will happen. Right now it's floating in the air as an unsupported assumption.

It's been debated hundreds of times whether making the default user a sudoer is good or bad security; you can do a few web and forum searches to get to them. I say instead of that, here's what should be debated, if any debate is needed at all: **which one is the security scheme that makes sense for Ubuntu? **

1) one default sudoer with all powers, root disabled
2) all users regular, one root, enabled by default

As I've stated many times in similar discussions: every distro has its own tools that it adjusts for its own target audience and its own goals. Regardless of which security model is ultimately superior (and I don't believe in the presence of one ultimate security model that fits all uses; you may), what should be used is the scheme that fits Ubuntu's use(r)s the best.

---

### Post by eqisow on 2006-06-02
I think the Ubuntu setup is the best for single user systems, an option to use either setup during the install could be good, however. Then again, creating a new, limited privileges, user for your child isn't hard to do.

Speaking of which, what is the default setup on Edubuntu? I have never used it, but the default user should NOT have admin privileges in Edubuntu. After all, it's pretty much designed for kids. As long as Edubuntu is not done like Ubuntu, I think Ubuntu could stay like it is.

Edit: Actually the default security setup would be fine on Edubuntu if auto logon was turned on. They wouldn't need their user password at all then.

---

### Post by 23meg on 2006-06-02
[QUOTE=eqisow]I think the Ubuntu setup is the best for single user systems, an option to use either setup during the install could be good, however. Then again, creating a new, limited privileges, user for your child isn't hard to do.
[/QUOTE]
That's right; anyone aware of the dangers of giving their kids or friends or guests a full administrative account can easily set them a default account with no sudo rights. This has to do with basic knowledge of good administrative habits, not this or that security model.

---

### Post by elamericano on 2006-06-03
Only the first user is automatically in the admin group. You're not proposing locking people out of their own computers for their own good, right? Mepis had a root password, right? If your point is only that it shouldn't be the same password, I kind of agree, but I haven't seen too much support for that.

[http://www.ubuntuforums.org/showthread.php?t=181877](http://www.ubuntuforums.org/showthread.php?t=181877)

---

### Post by BoyOfDestiny on 2006-06-03
Besides, if these people have access to the machine in the first place.

When grub loads, choose recovery mode. Then you are root, feel free to mess with whatever. Need a gui. Type 

startx

So time to password protect grub

Let's use a livecd and do whatever we want.
So you better password protect the bios and set the hard drive as the first thing to boot.

I guess my point is, if the system admin is a complete...um... Well makes accounts and gives them full rights. I see how it can compromise 1 machine. As for worms and viruses as the like... no. You'd have to give your password to install it then execute it.

My advice is, don't use anything outside the repos or trusted sources. Otherwise sure, those users will ruin their machines. It wouldn't really effect anyone else. All my ports are closed (as per Ubuntu's defaults...) All the software I run natively is from the repositories or built from trusted sources (literally)...

Whether one root account or sudoers etc, is really irrelevant it seems... Nothing is bullet proof.

It is however better than being root/admin all the time. At least you get a chance to pause and think when typing in your password. Not to mention you aren't running every single app with root privileges...

---

### Post by m_pav on 2006-06-03
[QUOTE=23meg]Please explain in clear technical terms how exactly this will happen. Right now it's floating in the air as an unsupported assumption.
..........
 if any debate is needed at all: **which one is the security scheme that makes sense for Ubuntu? **
1) one default sudoer with all powers, root disabled
2) all users regular, one root, enabled by default
[/QUOTE]

While the issue of viruses is floating in the air as an assumption, whether you believe it or not, linux machines do come under attack, but nowhere near as commonly as windows, and it's only a matter of time before we'll hear of viruses that attack linux and cause their desktops to do strange things, as reported by a macintosh user that recently got infected. They thought they were immune.

How will it happen? My guess it will be mostly from sheer foolishness, like it is in the windows world. Peer to peer file sharing, chat and peoples gullibility to phishing scams. Too many people use the same password for every site, system they use and even their bank accounts, and for a thief to discover just a single password, such a person would be as if they did not have any protection at all. Unsecured wireless is way too common, and with the currrent Ubuntu model, the first users password is set to have root access, so a simple packet sniffer can capture the info and the system can be easily compromised at the root level. 

Therein lies my defence of having a root account with a seperate password as default, but the user should be given a choice during installation as to what security model they prefer rather than bundling in root access with a first users password as default. Using Debian with KDE, the default is to not allow a root login to a GUI environment and I really like and fully endorse this model, even though it may appear to be more difficult, but isn't that the safest way? Having decent and workable restraints is a good thing, automotive manufacturers know this and we all appreciate it after seeing many lives saved as a result of seatbelt use. If all computer users were properly educated and/or initiated into their computer use the same way, we too would be of the same mindset, and system fatalities due to "mostly human" failures may become less of an issue. Ubuntu's current model flies in the face of what I believe to be a better system.

Microsoft have finally cottoned onto it after watching the linux camp for years and they are finally implementing it with longhorn. If Ubuntu doesn't change it's default, soon this particular flavour of linux will be thought lesser of as a result of Microsofts step in the right direction, even though it's taken the fat (as in wallet) redmond bullies more than 10 years to get that one thing right.

---

### Post by seth0x2b on 2006-06-03
One simple question: What's stopping you or me or anybody else to enable the root password right after installation,then change it so it doesn't match the first user's?!
Are you botherd only by the fact that the two don't differ during installation?!

Cheers

---

### Post by Khaine on 2006-06-03
> One simple question: What's stopping you or me or anybody else to enable the root password right after installation,then change it so it doesn't match the first user's?!
Are you botherd only by the fact that the two don't differ during installation?!

No by default in ubuntu root is disabled.  The first user installed has sudo power (is in the wheel group).  From the sudo main page:

> Sudo (superuser do) allows a system administrator to give certain users (or groups of users) the ability to run some (or all) commands as root or another user while logging the commands and arguments.

The password sudo users is the [b]users[b] password, not roots, like su uses

---

### Post by B0rsuk on 2006-06-03
[QUOTE=seth0x2b]One simple question: What's stopping you or me or anybody else to enable the root password right after installation,then change it so it doesn't match the first user's?!
Are you botherd only by the fact that the two don't differ during installation?!

Cheers[/QUOTE]

They do differ. There is a root account in Ubuntu, but with a strong random password.
What's stopping you ? Many Ubuntu graphical utilities are configured to work with sudo, not root. They may act strangely or even break your system integrity if you use them as root.
--------------

I have a feeling the original poster doesn't know what is he talking about. From what I learned sudo model is not worse, not better, just different than using root. For average users, sudo may be even better than root, because it discourages using root a lot (dangerous) and leaving open root consoles.

Whatever you run from your account, it won't affect anything outside your /home/username account. Because you don't have write privileges elsewhere. As far as I know there's no simple way to retrieve your password. So it's far from working like windows, where you can write/delete anything you like, no questions asked.
**Unlike original poster, I will back my claims up:**
> 
b0rsuk@dziupla:~$ rm /boot/*
rm: remove write-protected regular file `/boot/abi-2.6.12-10-386'? y
rm: cannot remove `/boot/abi-2.6.12-10-386': Permission denied
rm: remove write-protected regular file `/boot/abi-2.6.12-9-386'? y
rm: cannot remove `/boot/abi-2.6.12-9-386': Permission denied
(...)
b0rsuk@dziupla:~$ 


See what I mean ?
The worst that can happen is that you remove your own data files. But there's no cure to stupidity other than education.
Once you create a new user for kids, (if you do it via adduser like I did, you'll have to add the account to 'audio' group or whatever it's called), they aren't allowed to use sudo by default.
And if you turn your back on untrusted people while they have physical access to your computer, there are MANY ways in which things can go wrong.

---

### Post by astoltz on 2006-06-03
The merits of the 'default' user being able to use admin tools VS. having a separate root account have been well debated in many places outside Ubuntu.  It is a well accepted method of user security.  I hate to say "try a google search" but really, this issue was hammered out years ago.

But I just want to point out that the default user does NOT run all the time as root as is the case in Windows.   He must escalate his privledges using the sudo command.  Yes, it is the same password, but if a hacker can discover a user password, he can just as easily discover a password for the user 'root'.  However, most attacks on windows do not need a password - they trick the user into running the offending program (or it runs via some flaw in the code).  And since on Windows, the user is running with admin privledges all the time, everything runs at the same level.  This cannot happen in the Ubuntu user model where the user is NOT running with admin privledges except when specifically granted via sudo.

[EDIT]B0rsuk beat me to many of my points - sorry for the repeat[/EDIT]

---

### Post by seth0x2b on 2006-06-03
> Whatever you run from your account, it won't affect anything outside your /home/username account. Because you don't have write privileges elsewhere. As far as I know there's no simple way to retrieve your password. So it's far from working like windows, where you can write/delete anything you like, no questions asked. That's what I thougt.
Basically, the administrator is the one deciding how good the "security model" is.
To ensure local security, simply DON'T give anyone the root/sudo password.
As for sniffers, Firestarter does it's job really good. You should see my logs :D

Cheers

---

### Post by steve196 on 2006-06-03
You do not normally need to secure the computer against yourself. the danger of Windows is, that for administration you need to login as admin and run the whole GUI and all programs as admin. A user with sudo privilege runs only those programs that need privileges with them. If a web applet or a filesharer or a game wants me to sudo it, i won´t do it and it can´t just sudo itself either. 
No system is secure against a deliberate attack from an admin (and that is the scenario you described).

---

### Post by Lil_Eagle on 2006-06-03
I can agree with the sudo model, but I know many users get tired of typing sudo all the time, so they do this:

sudo /bin/bash

Then they're root!  Try this:

sudo cp /etc/fstab /etc/fstab.temp
sudo /bin/bash
rm /etc/fstab

you'll see that the rm works, even though you don't use sudo!

If you really were stupid enough to do that, then:

mv /etc/fstab.temp /etc/fstab
exit

Now you'll not have problems booting.
See that you're now back in your user account?

My point is: that such a terminal left open is just as dangerous as an open root terminal, so there's no point in not having a root account if the superuser is going to do something like stated above.

However, as previously stated, if you enable root, it won't help with many of the utitities that are expecting the first user's password, not the root password, even though they are asking for the root password.

---

### Post by m_pav on 2006-06-04
[QUOTE=B0rsuk]They do differ. There is a root account in Ubuntu, but with a strong random password.
What's stopping you ? Many Ubuntu graphical utilities are configured to work with sudo, not root. They may act strangely or even break your system integrity if you use them as root.[/QUOTE]
Interesting comment about the strong random password for the root acocunt, but it doesn't hold a toothpick against a tree when the same password is used for the first user and for root access, though I had already discovered that changing a Ubuntu system to the seperate root account does as you have stated, confuse users about which password to use, the user account (weak model) or the seperate account (stronger model) This is what I am alluding to with the current security model.](*,) and trying to change it to a seperate root acount does little the sense of greater security as far as the gui is concerned.

[QUOTE=B0rsuk]
I have a feeling the original poster doesn't know what is he talking about. From what I learned sudo model is not worse, not better, just different than using root. For average users, sudo may be even better than root, because it discourages using root a lot (dangerous) and leaving open root consoles.[/QUOTE]
That's a rash and unwarranted opinion from someone that knows nothing about me at all, but aside from that, we're sort of on the same wavelength here, and if you read my first post, which was written with care and concern, you'll see I am more concerned with the unbelievably easy access to admin priveleges by the use of the same password. I agree it is different, but the password issue will always be a weaker option when the same password is used. You could write a 500 page book detailing your opinions, but my few words will still stand, the same password is not safer.

While I think Ubuntus security model is stronger than the current windows model, it is still weaker than the default model used by almost every other linux distribution in existence by the simple use of the same password. Yes, the sudo model does not leave a console window open after it finishes it's job, and I applaud that, but I do not applaud the use of the same password as the system default. To break into a unix type system over a network requires the cracker to discover the password, and once they have the first users, they have the root.

[QUOTE=B0rsuk]
Whatever you run from your account, it won't affect anything outside your /home/username account. Because you don't have write privileges elsewhere. As far as I know there's no simple way to retrieve your password. So it's far from working like windows, where you can write/delete anything you like, no questions asked.
**Unlike original poster, I will back my claims up:**


See what I mean ?
The worst that can happen is that you remove your own data files. But there's no cure to stupidity other than education.
Once you create a new user for kids, (if you do it via adduser like I did, you'll have to add the account to 'audio' group or whatever it's called), they aren't allowed to use sudo by default.
And if you turn your back on untrusted people while they have physical access to your computer, there are MANY ways in which things can go wrong.[/QUOTE]
You are wrong, and I do stand by my claims. The fact that I am answering you directly is just a smattering of how staunch I am on this issue. There is no need to set about proving that a user account can't delete system files, we already know that, but in the real world, parents DO give in and tell their children their passwords and the children (especially young teens) DO break their systems *and* invite their friends to share what they have, which would be alright in a perfect world, but the world as we know it has very real threats. Most families do not use seperate accounts, they all use a single account, and do you for even one minute think this will be any different for Ubuntu users? Not likely.

I build, sell and repair computers for a living, and based solely on this issue, I have not yet installed Ubuntu onto a single system for a customer, I always go for one with what I deem to be a better security model like SimplyMEPIS with more cross-compatibility out of the box and less animosity towards paid software (see my first post). I wish I could install Ubuntu because it is in almost every sense of the word, a very, very good system, but having worked with computers for the last 10 years, there is a small chance that I might know a little bit more than you do about widespread computer use and how to avoid some of the pitfalls.

---

### Post by aysiu on 2006-06-04
Let's say I have a root account and a user account--traditional Linux model.

Then I choose passwords like *abc123* and *def456*, respectively. How is that any better than *sudo*, especially since everyone knows there's an account with the username *root*?

It would certainly be more secure to have a username that's not as common as *root* (something like *rescalli* or *qwuira*) that has admin privileges--since it then requires a malicious user to guess both a username *and* a password, as opposed to just a password.

Now, a weak password makes the whole argument pointless. If someone has a password like *def456*, it doesn't really matter if that password is for root or for a user with *sudo* privileges. It's easily guess-able either way.

If, however, someone has a password like *a~1*BNdl^^Rc*, it's a strong enough password that it really doesn't matter if it's a root password (the username for which everyone already knows) or a user password.

If I were trying to crack into someone's system I'd surely try the root account first, since I already know the username (*root*) and I know that username has full privileges.

However, if someone uses Ubuntu's security setup, that system could have several users--Bob, Jenny, and Eduardo. Maybe Jenny has *sudo* privileges. Maybe she doesn't. How do I know which one has *sudo* privileges?

For a fairly balanced weighing out of *sudo*'s pros and cons, read [this](https://wiki.ubuntu.com/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac).

---

### Post by professor_chaos on 2006-06-04
Good link aysiu!

I have seen too many requests, here on the forum and on the irc, new users (I'm guessing recently migrating from windows) asking desperately how to log in as root, as they have heard that "root" is the administrative account. When you ask them, why??? they tell you what they are trying to do, what commands they are trying to execute.... OMG, the answers you recieve, it boggles the mind I wont even give an example, in case they are apart of this forum. Anyway, if they did what they are thinking of doing as root, say goodbye OS.
So, sudo is a bit helpful in this regard. No, is wont protect you from doing anything you really want to do. BUT, it will help the user take pause and decide if this is really worth doing as administrator.

m_pav, I suggest you read aysiu's link, try ubuntu and sudo for a while and then let us know what you think.

---

### Post by tsb on 2006-06-04
I just wish there were a way to have your password automatically entered after the first time for the entire remainder of the session.  If there is, please tell me how it's done.  :)

---

### Post by aysiu on 2006-06-04
[QUOTE=tsb]I just wish there were a way to have your password automatically entered after the first time for the entire remainder of the session.  If there is, please tell me how it's done.  :)[/QUOTE] If you do that, you might as well just log in as root.

By the way, [there is a way to do this--just extend the *sudo* timeout](http://ubuntuforums.org/showthread.php?t=20724) to be... five hours or something.

---

### Post by simonn on 2006-06-04
[QUOTE=tsb]I just wish there were a way to have your password automatically entered after the first time for the entire remainder of the session.  If there is, please tell me how it's done.  :)[/QUOTE]

man sudoers

"timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for
                   a passwd again.  The default is 15.  Set this to 0 to
                   always prompt for a password.  If set to a value less than
                   0 the user&#8217;s timestamp will never expire.  This can be used
                   to allow users to create or delete their own timestamps via
                   sudo -v and sudo -k respectively."

EDIT: 
With regards to the original post. What is the problem with using the first user ceated as a seperate adminstrator account, like root, but with the additional safety feature of having to use sudo before anything scary?

---

### Post by aysiu on 2006-06-04
[QUOTE=m_pav]in the real world, parents DO give in and tell their children their passwords and the children (especially young teens) DO break their systems *and* invite their friends to share what they have, which would be alright in a perfect world, but the world as we know it has very real threats. Most families do not use seperate accounts, they all use a single account, and do you for even one minute think this will be any different for Ubuntu users? Not likely.[/QUOTE] All the more reason to use *sudo* instead of root.

Do you really think people will want to log into a separate account to make root changes? If so, they'll just use that separate account, just as they did in Windows. Can you say Linspire? (Yes, I know you can choose to add other users in Linspire, but the default user is still root.)

*sudo* makes the most sense to people who want to have one single account that can do everything. It does it... but it prompts you for a password when you're making system-wide changes. It works for Mac OS X, and it works for Ubuntu.

Force people to have a root login and user login, and they'll log in as root--at least the families you're talking about.

---

### Post by tsb on 2006-06-04
[QUOTE=aysiu]If you do that, you might as well just log in as root.

By the way, [there is a way to do this--just extend the *sudo* timeout](http://ubuntuforums.org/showthread.php?t=20724) to be... five hours or something.[/QUOTE]


If I add this I will never be asked for a password?

```
# Added by Ubuntu installer
reed ALL=NOPASSWD: ALL
```

Ps - I already changed my timeout to -1 and it doesn't seem to work, maybe 9999999999999999999999 would be better

Pss - Maybe it does.  kdesu kate .... seems to open evry time now, kdesu konqueror hangs (fails to load) like it always did before after numerous runs (the reason I don't want to be asked for a password)

Sometimes the password dialog never displays, that's a problem I've always had with KDE

---

### Post by Half-Left on 2006-06-04
Well Vista will have a UNIX like security model, Miscrosoft have come around to the idea that restrictions by default are needed now days.

Normal users should NEVER have acess to sensive parts of the system, it dont take many braincells to work out why.

---

### Post by m_pav on 2006-06-04
[QUOTE=aysiu]
It would certainly be more secure to have a username that's not as common as *root* (something like *rescalli* or *qwuira*) that has admin privileges--since it then requires a malicious user to guess both a username *and* a password, as opposed to just a password.

If I were trying to crack into someone's system I'd surely try the root account first, since I already know the username (*root*) and I know that username has full privileges.[/QUOTE]
Me too. Thanks for the link. I have a presentation to make at the local lug tomorrow on administering your system, so I'll touch on this subject.

Thanks to all that contributed

Mike P

---

### Post by reclusivemonkey on 2006-06-04
Tell me if I am wrong here, but isn't becoming root as easy as;

```

sudo su

```

??? That's what I have been using for now. If we were talking about machines in a work environment, I could understand the OP's comments, but the user with sudo is going to be the person who took the decision to install Ubuntu. They *should* have admin rights, thats so obvious is doesn't even need explaining. Ubuntu is "Linux for Human Beings" and as such I think the sudo method works well. I am pretty confident that if it didn't work this way, a lot of people would be tempted to login as root, which we all know is *not* a good thing.

---

### Post by 23meg on 2006-06-04
[QUOTE=aysiu]
sudo makes the most sense to people who want to have one single account that can do everything. It does it... but it prompts you for a password when you're making system-wide changes. It works for Mac OS X, and it works for Ubuntu.

Force people to have a root login and user login, and they'll log in as root--at least the families you're talking about.[/QUOTE]Exactly. It all starts and ends at the kind of security policy **the user(s)** have, or lack thereof, as is in the case of most Windows users I've seen, the kind of family mentioned here being a perfect example. The sudo model will encourage **them** to have passwords of their own, whereas the root-only model and the Windows model encourage not having passwords at all, or having one common password that's passed around (forgive the pun) between users and becomes worthless.

---

