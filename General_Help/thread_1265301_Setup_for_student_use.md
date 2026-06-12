---
title: "Setup for student use"
date: 2009-09-13
forum: General Help
---

### Post by lordyosch on 2009-09-13
Hi,

I've come into possession of several 'redundant' former WXP machines at work (a secondary school) and a colleague and I have plans to install Edubuntu on them for student use (partly as a showcase for Linux -our school's IT bill is enormous).

We need to ensure that the students cannot wreak havoc on the wider network or we'll get nowhere.

I've been looking into restricted user status and definitely no access to the 'SUDO' command.

What is the best/safest/easiest way to ensure a user can only access the internet, use programs stored on the PC itself, without access to settings and restricted files.


Thanks,

Jay

if this works we'll have broken windows (ahem) hold on the school

---

### Post by NoaHall on 2009-09-13
Look up iTalc for one.

Then make sure they aren't in the sudoer's file.

There. They can't do anything important. 

Look at going to "System -> Admin -> Authorisations" where you change the advance settings.

---

### Post by lordyosch on 2009-09-17
Ok.

Restricted access, NO access to Sudoers list.

I employed a student who is 'known' for his ability to do things that he shouldn't be able to with the school's computers.

He used grub, got into a Superuser terminal and then deleted a file from my home directory! (i'd put it there for him to try to delete it)

So, I need to lock down boot up. Delete recover mode from GRUB is going to be my first step.

What next?

I'm frankly shocked that GRUB lets you in as an SU with no password checks!


Jay

---

### Post by danwood76 on 2009-09-17
You can put a password on most BIOS to stop people booting live cds which will easily give access to all files on the machine.

Then just make sure that the user accounts are not admin accounts.

---

### Post by NoaHall on 2009-09-17
Well, there's not much left after disabling grub from showing recovery mode(ps, it's needed for recovery... that's why it's called that. And it's not grub that does that, it's Ubuntu. Grub is just the choosing bit.) Maybe I'd increase the speed of the menu to 1, make sure root can't be logged in, disable "ctrl + alt + backspace" and "alt + k + printscreen". I'd also remove things like terminal from the menus, so they can't get to that, and hide the "system" bit.

---

### Post by nikhilbhardwaj on 2009-09-17
you need to use a password in grub
read the instructions here

[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

also remember when someone has physical access to a computer then it isn't safe
no matter what they might tell you otherwise

i'm a student myself and love to do stuff that i'm not supposed to technically
but anyways best of luck

---

### Post by mcduck on 2009-09-17
Just create normal (non-admin) user accounts for students to use, set up a Grub password, disable booting from CD/USB in BIOS and set a BIOS password & lock the case.

If you need, you might also want to check Pessulus, which is Gnome's tool for limiting features of user desktops. This would be useful if you manuy users are using the same account instead of everybody having their own, as it allows you to lock down the user interface and menus. On the other hand if everybody has their own accounts there's no need for that, since users are strictly restricted to their own home directories anyway.

Grub lets you in as root since that's very useful in many cases, and it's not a security issue since physical access to a computer should pretty much be considered as root access anyway, there's not much that any OS could do to that unless you secure the computer itself. With physical access to physically unsecured machine anybody could just pop in a live-CD, boot from that and gain full access to the computer anyway so restricting physical access is the first priority, everything else comes after that.

(removing recovery mode from Grub menu is pointless, Grub has it's built-in shell & editor that would allow booting to recovery mode, menu entry or not, so you need to set up the password anyway and once you have the password set having the entry in the menu is safe)

---

### Post by nikhilbhardwaj on 2009-09-17
> **danwood76 said:**
> You can put a password on most BIOS to stop people booting live cds which will easily give access to all files on the machine.


i really wouldn't rely on bios passwords for security

removing the cdrom and usb ports is the only possible fool proof solution
but then thats insane

---

### Post by nikhilbhardwaj on 2009-09-17
> **mcduck said:**
> 
Grub lets you in as root since that's very useful in many cases, and it's not a security issue since physical access to a computer should pretty much be considered as root access anyway, there's not much that any OS could do to that unless you secure the computer itself. With physical access to physically unsecured machine anybody could just pop in a live-CD, boot from that and gain full access to the computer anyway so restricting physical access is the first priority, everything else comes after that.

i couldn't agree with you more.

---

### Post by NoaHall on 2009-09-17
> **nikhilbhardwaj said:**
> i really wouldn't rely on bios passwords for security

removing the cdrom and usb ports is the only possible fool proof solution
but then thats insane

Why not? These are students. I doubt they will ever be fully alone with a computer, and if they are, then you can consider it gone anyway. They aren't going to have time to remove the case as clear cmos/ remove and put back in the battery. I expect the cases are locked too.

---

### Post by mcduck on 2009-09-17
> **nikhilbhardwaj said:**
> i really wouldn't rely on bios passwords for security

removing the cdrom and usb ports is the only possible fool proof solution
but then thats insane
I agree that BIOS password alone is pointless, unless you lock the computer case as well.

If the case isn't locked resetting BIOS password only takes couple of seconds.

However having the CD drive and USB ports are most likely requirements for the machine to be useful, so the way to go is to disable booting from them, setting up BIOS password to stop people from enabling them again and then locking the case to stop people from resetting BIOS password. :)

---

### Post by nikhilbhardwaj on 2009-09-17
it isn't very difficult to remove a bios password without opening up the case either
plenty of software on the net for that

and most bios also have a master password  too
again its not rocket science to find that out

if someone wants to really hack into a machine
and has physical access then there's nothing you can do

but for most of the situations
i do concede that its quite enough

---

### Post by NoaHall on 2009-09-17
But if they can't use the cd drive/ usb, then they can't use the software.

---

### Post by DeMus on 2009-09-17
I am shocked. Completely shocked. I was told and I also keep reading about it: Linux is so much safer than Windows. There is no way to do "illegal" stuff on a Linux computer as ordinary user.
Now I read there are many ways to get in and do those things anyway. Did people lie to me? Did I read fairy tales about Linux? What is going on here?
This is something I never expected and to be honest I hate it. This is something I never saw coming, until this thread came along.
Well, I just read the different posts again and try to make my Linux as closed as possible, knowing now I can never close it completely.
Bummer.

---

### Post by nikhilbhardwaj on 2009-09-17
> **NoaHall said:**
> But if they can't use the cd drive/ usb, then they can't use the software.

read the first post
they can access the internet
you can download what you want

---

### Post by NoaHall on 2009-09-17
DeMus: What? It is a lot more secure than Windows, if you configure it correctly. And if they have physical access to your computer, not even a huge 128 character password to everything can save you.

nikhilbhardwaj: There's ways of stopping people download things. Easy ways. Just because they can access the internet, doesn't mean they know how to :

1) Install things on Linux
2) Run new things on Linux
3) Have the motivation to hack the bios or have the knowledge that these things exist.

---

### Post by nikhilbhardwaj on 2009-09-17
> **DeMus said:**
> I am shocked. Completely shocked. I was told and I also keep reading about it: Linux is so much safer than Windows. There is no way to do "illegal" stuff on a Linux computer as ordinary user.
Now I read there are many ways to get in and do those things anyway. Did people lie to me? Did I read fairy tales about Linux? What is going on here?
This is something I never expected and to be honest I hate it. This is something I never saw coming, until this thread came along.
Well, I just read the different posts again and try to make my Linux as closed as possible, knowing now I can never close it completely.
Bummer.

no no no
nobody lied
and all of this is true

its much easier to do all that to a windows machine

on a network linux systems are way more secure
ofcourse nothing is perfect

and as it has been posted earlier
that once a person has physical access
he/she can do anything with the machine

so its quite secure
but yes not quite those fairy tales that you'd imagined

---

### Post by nikhilbhardwaj on 2009-09-17
> **NoaHall said:**
> DeMus: What? It is a lot more secure than Windows, if you configure it correctly. And if they have physical access to your computer, not even a huge 128 character password to everything can save you.

nikhilbhardwaj: There's ways of stopping people download things. Easy ways. Just because they can access the internet, doesn't mean they know how to :

1) Install things on Linux
2) Run new things on Linux
3) Have the motivation to hack the bios or have the knowledge that these things exist.
they are students
and 99 of 100 cant or wont even want
but 1 can 
and i bet you on that

again there are proxy servers and ways to bypass to your internet filter program

and i've never said that it will be done
only that it is very much possible

its good to be honest about it
so that they can know what actually happeed
if anything does happen
rather than tell people fairy tales

---

### Post by NoaHall on 2009-09-17
Here's the probability for you 

100C1 x 0.05^1 x 0.95^99 = 0.0312 to 4 dp.

Let me tell you, that's very unlikely. 

And a good internet set up won't allow access to proxy servers, no matter what you do.

---

### Post by nikhilbhardwaj on 2009-09-17
> **NoaHall said:**
> Here's the probability for you 

100C1 x 0.05^1 x 0.95^99 = 0.0312 to 4 dp.

Let me tell you, that's very unlikely. 

And a good internet set up won't allow access to proxy servers, no matter what you do.
there you go
you've said what i've been saying all along

its not impossible

btw how do you expect some who can't set a grub password to set a fool proof network

no offense meant to anybody

---

### Post by NoaHall on 2009-09-17
Haha, you're mean. Even if no offence meant ;) He just didn't have the foresight to do so. I expect they have set up a secure network for Windows, doing the same for Linux is easy.

And I'm not saying what you were, because you were wrong. I'm just agreeing that it's unlikely.

---

### Post by nikhilbhardwaj on 2009-09-17
> **NoaHall said:**
> Haha, you're mean. Even if no offence meant ;)
ya i know
probably shouldn't have said that

again i'll say that it can be done
lets say i need a something to reset the BIOS password with the command line 
i could just email it to myself and get it from there 

and lets just call it at
that if the person has implemented most of what has been said here
he'll have a system that will be unlikely to be hacked by most people

---

### Post by mcduck on 2009-09-17
> **DeMus said:**
> I am shocked. Completely shocked. I was told and I also keep reading about it: Linux is so much safer than Windows. There is no way to do "illegal" stuff on a Linux computer as ordinary user.
Now I read there are many ways to get in and do those things anyway. Did people lie to me? Did I read fairy tales about Linux? What is going on here?
This is something I never expected and to be honest I hate it. This is something I never saw coming, until this thread came along.
Well, I just read the different posts again and try to make my Linux as closed as possible, knowing now I can never close it completely.
Bummer.

No, normal users have very limited powers when running Linux.

Pretty much everything discussed here happens outside of the operating system. At that stage it makes no difference what OS you are talking about, since it's not running. For example accessing BIOS or using features of Grub are not parts of Linux itself, so Linux can't protect you from those things. It's not even running at the time when you access Grub or BIOS.

Like I said, physical access to a computer pretty much gives you all powers over that machine. Operating systems can't limit that apart from the parts that user's can/can't do from that operating system itself.

So, no fairy tales, Linux is very secure operating systems but there's much more to computer security than what operating systems can handle. And like I said in my previous post in this thread, restricting physical access to computer is the first thing you need to do, everything else comes after that.

(If you can't restrict unwanted physical access to your computer your only option for protecting your files is encrypting them. Everything else can be worked around, no matter what operating systems or other software you use)

---

### Post by lordyosch on 2009-09-18
> **nikhilbhardwaj said:**
> ya i know
probably shouldn't have said that

again i'll say that it can be done
lets say i need a something to reset the BIOS password with the command line 
i could just email it to myself and get it from there 

and lets just call it at
that if the person has implemented most of what has been said here
he'll have a system that will be unlikely to be hacked by most people

I'm totally unoffended by your remarks! I setup the computer straight from live CD's. I asked the student specifically to break it. I think my instruction was 'if you can delete the OS, then do it'. I wanted him to find all the ways he can to get in, he's 'part of the system' not against it. His mind works differently to mine!

So first hurdle cleared by student. Now I've added machine guns to grub. Its going to be fun to see where he goes next!



Jay

---

### Post by NoaHall on 2009-09-18
Has he used Linux before? I doubt many people in your school have, so I wouldn't worry about them finding too many loopholes.

---

### Post by lordyosch on 2009-09-19
> **NoaHall said:**
> Has he used Linux before? I doubt many people in your school have, so I wouldn't worry about them finding too many loopholes.

He has. He's probably the biggest geek we have (and maybe reading this, Hi Sam...)

You're probably right about the rest not being able/bothered but if we want to expand the use of Linux in the school (take over the world) then we need to show it's safe. My colleague (Head of IT) and I are about the only linux users on staff, we're trying to break M$ stranglehold on the school and thus save us a whole heap of cash.


Jay

---

### Post by NoaHall on 2009-09-19
Ah, if only my school was like that. It might have at least two computers in every room, but most don't have any more than 512 MB of ram, and around 500 mhz cpu. I don't know why they run windows on them. Linux would be much more suitable. 

He's used it before, so he knows his way around with it. I doubt anyone else would be able to do so.

---

### Post by lordyosch on 2010-01-27
The roll out has begun!

I have four working Ubuntu terminals in my classroom now (limited by space) and I've got some students helping me set up another four for another classroom.

I've recently got a bit more fired up about the project because I remembered by school has a Moodle VLE server, but no one uses it!

We had some half-a$$ed training 2 years ago and we promptly forgot all about it. No I've rediscovered it, and printed of the 'Using Moodle'book (free to reproduce) I'm full steam ahead.

I've had students doing experiments in class and instead of recording their results only in their books then sharing on the board, we put them straight into a moodle database and from there I can export to OOO and make graphs on the screen -Its a brave new world!


Jay

---

### Post by hwttdz on 2010-01-27
Couldn't one put the cd/usb on a network machine? That the student's don't have physical access to?  That way they could only access the cd/usb after booting (and in fact unless you set it up otherwise they don't have permission to mount/unmount the cd/dvd/usb, though you can set it up to automount).  It would also mean that they don't put any cd/dvd/usb in other than ones you want.  Though I don't know about multiple clients reading from one cd at a time.  

I'm imagining:
head machine - no physical access for students, with cd/dvd/usb drive
other machines - mount drive found on head machine over network

---

