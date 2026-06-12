---
title: "Several Ubuntu problems (major one: random shutdowns)"
date: 2010-04-02
forum: General Help
---

### Post by d00derino on 2010-04-02
I really hate coming here because all I do is moan and complain. I really want to love Ubuntu, and the more I play with it the better I get. Except that Ubuntu has several faults (both hardware/software and design). Before I start, here is the machine I have:

HP Laptop (Pavilion zv6000)
~100GB
2.67GhZ
1GB RAM 

My MAJOR complaint is that recently I've been getting random shut-downs. It first started when I used DeVeDe to turn my Pulp Fiction .avi into an .iso to burn (see below for more criticism). I set it to convert and then went to bed. When I woke up, the computer was turned off. I recently turned remote desktop on, so I can use this Windows machine to play with my Ubuntu machine which servers as kind of a media hub for me. At random times (like at class) I'll be able to sign in remotely, but if I try again in like 20 minutes, it'll be shut off. Right now, I turned the machine on this morning and am trying to remotely access it and can't. It has a steady IP address. I can't because it turned itself off. It never did that before. Is it because I set the computer to never go to sleep? Is that where the fault lies?

Another hardware/software issue I'm having is that Ubuntu doesn't know how to hibernate. At all. When I try to hibernate the computer it will store the data and shut down the computer, but when I turn it back on, it freezes (or loops or something) and never makes it to the desktop. 

To add onto that, Ubuntu doesn't seem to save options. I tried changing the option for better laptop power management (can't find the exact script now, but you change .../.../../laptop-mode from 0 to >0 to enable it) and it doesn't stick! I had to do it in the root account, and when I go back into my account it shows it as 0. What's worse, sudo doesn't even work with it. 

Now for the fun part, design flaws. I'm a computer science student who is heavily involved in software engineering. While I can't say that Ubuntu isn't designed very well (because it is), I think a lot more time should be taken back to the design and specs stage to make Ubuntu more user-friendly. Before you go on, Ubuntu is the most user friendly distro I've encountered. But there are so many more things that would make life so much easier:

1) A freakin' DVD-Video burner OUT OF BOX. Why is so it so complicated to do this on Ubuntu? 

2) A way to uninstall un-Ubuntu "store" programs. If there is a way, it's very foreign and not very accessible. Limewire is freezing like a mofo. 

I'll keep updating this topic. I don't want to come off bitter, and I do want to help the community as much as I can. I'm kind of a nut for user experience/interface, so I'd love to help out with that. I'm also good with documentation and planning, which many coders aren't. It's a skillset that is lost among many Computer Science/IT students and it's a shame. A lot of people just go willy-nilly into coding, and it's not a good idea at all. Not saying that's what's happening with Ubuntu, but from my experience, having someone with a gameplan first and coding skills second is much better than a lot of people in many "coding communities".

---

### Post by llamabr on 2010-04-02
Limewire freezes because it's a crappy port.  And if you're not careful with it, it'll get you sued by the RIAA or some wuch fascist organization.

Re: shutdown, ubuntu will shut itself down if the machine gets too hot.  Evidence of that is that you're burning some dvd overnight, and running other high cpu things.  scroll through dmesg and /var/log/ and see if you can find it.  I'll bet it you start ripping another dvd, and sit there for 20 minutes, you'll see it happen again.  do your fans come on?

---

### Post by Gunman1982 on 2010-04-02
> 1) A freakin' DVD-Video burner OUT OF BOX. Why is so it so complicated to do this on Ubuntu? 
You can do that easily with k3b

> 2) A way to uninstall un-Ubuntu "store" programs. If there is a way, it's very foreign and not very accessible.
I guess you mean programms you installed through make? If you want to you can create a package of them so you can install the package and uninstall it easily. Creating such a package might be a little bit difficult though but since you are a "computer science student who is heavily involved in software engineering" that shouldn't be a problem ;-)

Keep in mind that most contributions to GNU/Linux are from private parties and not from big software companys. So the focus is more on getting the stuff done than making a fancy looking interface. Doesn't mean that they won't get a fancy GUI but thats most of the time not a priority. 

Sry if I offend you but I don't like this "I want to have that, I could help but instead I just tell you all that I would do it differently and way better." ... participate in projects and maybe you get what you want.

Update: Relating the temperature issue, you can check the cpu temp with wmtemp or as an applet in your panel with sensors-applet.

---

### Post by agnes on 2010-04-02
> Another hardware/software issue I'm having is that Ubuntu doesn't know how to hibernate. At all. When I try to hibernate the computer it will store the data and shut down the computer, but when I turn it back on, it freezes (or loops or something) and never makes it to the desktop.

With the risk of stating the obvious, installing the packages uswsusp & hibernate could fix that. 

And why your machine gets so hot, it could be you did not install the right video driver. If I'd run Ubuntu or Puppy or OpenSUSE or whatever, without any driver (xVesa), my HP Pavilion+ATI laptop got so hot it shutted down after a while.

> 2) A way to uninstall un-Ubuntu "store" programs. If there is a way, it's very foreign and not very accessible. Limewire is freezing like a mofo.

Some source-installed-programs provide an uninstaller themselves... well actually I have only seen it once or twice. For Ubuntu to uninstall them would hardly be possible. 
Creating a package first is a hassle. You could make a script that take as argument the program's name; then searches all files/directories beginning with that name; then prompts you for each if you want to delete them (should not be hard for you).

> Keep in mind that most contributions to GNU/Linux are from private parties and not from big software companys. So the focus is more on getting the stuff done than making a fancy looking interface.
That's not always true. If you look at the Lucid blueprint for example, the "foundations-linux-boot-experience" is "Approved" and "In good progress", guess what is not:
```
Essential   	 kernel-lucid-suspend-resume   	 1  Pending Approval   	 6  Slow progress   	 Manoj Iyer   	 lucid-alpha-3
```
And even in 8.10 my Realtek ethernet controller wouldn't work after suspend.

---

### Post by Gunman1982 on 2010-04-02
*sighs*
> Keep in mind that **most** contributions to GNU/Linux are from private parties and not from big software companys. So the focus is more on getting the stuff done than making a fancy looking interface. Doesn't mean that they won't get a **fancy GUI but thats most of the time not a priority**. 
> **That's not always true.** If you look at the Lucid blueprint for example, the "foundations-linux-boot-experience" is "Approved" and "In good progress", guess what is not:

interface != design/blueprint (in that context graphical user interface
most of the time == not always

---

### Post by d00derino on 2010-04-02
Let me clear the air here: A computer science student != code-monkey. It doesn't mean that I know 32 languages by heart, rather my specialty lies in the philosophy and logic behind computing systems. I can easily learn an OOP language because I know the fundamentals of what an OOP language should include. Or I can pick a certain scripting language based on my particular need.

When I sounded very pious before, I hope nobody took it personally. What I meant to say in my rush between typing while I had cranky kids needing a ride and talking to my girlfriend and typing out my post is that from my experience, I've encountered a lot of "code-monkeys"; people who pride themselves on their knowledge of a language or languages, but don't really have the practical applications of such down. Formal software engineering classes are a fairly new thing, and a fairly new requirement for software engineers, exemplified by the masses of mid-30s returning students. My understanding from my experience is that many pro-bono "software engineers" are usually people who don't really go through a design process -- rather go straight to the code.

All of which explains why I haven't gone ahead and wrote scripts to fix my own problems. I'm not a domain expert in Linux. I use Linux for web servers and compiling homework. You want my domain, it's OOP and web design/development. I primarily use Windows and I come off as an average consumer, because I'm not savvy to kernel scripting. Ironically, I love UI design and would love to take a crack at a Linux OS and design one, but I'm God awful at integrating hardware into code (I don't know how I'm getting past Operating Systems myself, I've grown to hate writing parallel processes).  

Back to my original post, I never thought that it was overheating. I can't even think why it would do so, especially on something so non-intensive as creating a image disk or just on standby! Crapily, I don't think that my hardware set suites Ubuntu (or Linux I suppose). I'm guessing I have the wrong drivers; maybe I should go back to XP. 

As for LimeWire, I understand. I think it's a Deb build, but everything you install off the Internet isn't accounted for in Synaptic. That's where I thought everything you had as well as the repository was, I didn't realize it was only installed programs from the repository that show up. Like I said, I'm no expert at kernels, but would it be to hard to scan the drive for executables and list them? Even at it's most basic, you'd get the location so you know where to delete it when you're done.

Also, I didn't think K3B was for the Gnome version. I thought it was for KDE only.

---

### Post by Gunman1982 on 2010-04-03
> **d00derino said:**
> Let me clear the air here: A computer science student != code-monkey. It doesn't mean that I know 32 languages by heart, rather my specialty lies in the philosophy and logic behind computing systems. I can easily learn an OOP language because I know the fundamentals of what an OOP language should include. Or I can pick a certain scripting language based on my particular need.
Didn't expect you to be a code monkey but to be a person who is used to work with computers and able to do more work intensive tasks like building a deb.

> 
When I sounded very pious before, I hope nobody took it personally. What I meant to say in my rush between typing while I had cranky kids needing a ride and talking to my girlfriend and typing out my post is that from my experience, I've encountered a lot of "code-monkeys"; people who pride themselves on their knowledge of a language or languages, but don't really have the practical applications of such down. Formal software engineering classes are a fairly new thing, and a fairly new requirement for software engineers, exemplified by the masses of mid-30s returning students. My understanding from my experience is that many pro-bono "software engineers" are usually people who don't really go through a design process -- rather go straight to the code.

I understand your opinion, I even second it, but the problem is that if no people with such a knowledge participate to a project and all the other members (since doing it for fun and/or in their free time) don't want to change or learn that there is no change. 

> 
All of which explains why I haven't gone ahead and wrote scripts to fix my own problems. I'm not a domain expert in Linux. I use Linux for web servers and compiling homework. You want my domain, it's OOP and web design/development. I primarily use Windows and I come off as an average consumer, because I'm not savvy to kernel scripting. Ironically, I love UI design and would love to take a crack at a Linux OS and design one, but I'm God awful at integrating hardware into code (I don't know how I'm getting past Operating Systems myself, I've grown to hate writing parallel processes).  

You don't have to write scripts or programs, I have seen many projects who had enough "code-monkeys" but were desperately searching designers or other members. 
^^ I guess I'm an average consumer too since I'm not savvy to kernel scripting either ;-). 
 
> 
Back to my original post, I never thought that it was overheating. I can't even think why it would do so, especially on something so non-intensive as creating a image disk or just on standby! Crapily, I don't think that my hardware set suites Ubuntu (or Linux I suppose). I'm guessing I have the wrong drivers; maybe I should go back to XP. 

Did you check if the problem is heat related? What hardware do you have? Do you have compiz enabled (desktop effects)? Maybe try to disable them.

> 
As for LimeWire, I understand. I think it's a Deb build, but everything you install off the Internet isn't accounted for in Synaptic. That's where I thought everything you had as well as the repository was, I didn't realize it was only installed programs from the repository that show up. Like I said, I'm no expert at kernels, but would it be to hard to scan the drive for executables and list them? Even at it's most basic, you'd get the location so you know where to delete it when you're done.

Do you have an example what you mean by installed off the internet? 
If you scan the hd for executable programs you would omit the libraries which were probably installed alongside the executable. If you go by name you expect the software and all related stuff to be named similar to the executable.
Using a package is imho the best way to handle that, that means the people in charge of the software are the ones who can create them which most ease. They know what the software depends on. Keep in mind tho that there are at least two types of packages deb and rpm and they need the hardware to build the binarys.

> 
Also, I didn't think K3B was for the Gnome version. I thought it was for KDE only.
You can use it with gnome too, installs some kde-libs and doesn't look as well integrated as in kde but works nontheless.
Just for info: When you use gnome or kde you can use kde and gnome software and if you have ubuntu you can install kde afterwards (vice versa with kubuntu and gnome) 


I hope I don't offend you, I just want to show you that you can't expect to have a development routine (specification->design->implementation->test) in free software projects like you have in a corporate company. Its more like evolutionary software development with testing outsourced to us users ;-). Doesn't mean that some projects have one, but again: you can't expect it.

---

### Post by d00derino on 2010-04-03
> **Gunman1982 said:**
> Didn't expect you to be a code monkey but to be a person who is used to work with computers and able to do more work intensive tasks like building a deb.

Nope, if I had used Linux anywhere outside of one computing course in community college (which was probably the straight up programming class I've taken, no IDEs, although assembly on a IBM 375 is a close second ;-))

When I get more free time (hopefully over the summer) I'd love to learn some Linux stuff, like building debs. I work with Windows and OS X. A lot of IT work is done with Linux, but I have a feeling a lot of software engineering is Windows, just because of the fact that most programs are for Windows. But that's a discussion for another time.


> 
I understand your opinion, I even second it, but the problem is that if no people with such a knowledge participate to a project and all the other members (since doing it for fun and/or in their free time) don't want to change or learn that there is no change.

Yes, of course. It's a shame, but I'd hope that bigger projects (such as LimeWire) would at least have been built with a better design in place. Although what you're talking about refers to me and my "Internet forum" knowledge, that dictates that the more domains you know makes you a better computer "guy" (we need better names for our profession), instead of breadth. It's the quality over quantity rule. 

And as a side note, everyone in this field, from circuit integration to graphic design is so nasty to each other! 

> 
You don't have to write scripts or programs, I have seen many projects who had enough "code-monkeys" but were desperately searching designers or other members. 
^^ I guess I'm an average consumer too since I'm not savvy to kernel scripting either ;-). 
 

I'd love to join a group once I get some free time. I'm really bogged down at the moment with school but have some great ideas for Linux. I love the fact that it's user-enabled and that the community builds it. It gives you a sense of self and an accomplishment that you are building it and this is your product. I want to be part of that!

> 
Did you check if the problem is heat related? What hardware do you have? Do you have compiz enabled (desktop effects)? Maybe try to disable them.

Sadly, my computer is back at my dorm and I'm stuck at home for the weekend. I don't think it's compiz, and if it is I'd be in shock because it's just the top window menu transparency that's enabled (Emerald). I'm more surprised that it overheats when converting an .avi to a .iso. I also did find something to download that lets you download straight to Video DVD in a Linux magazine, but the fact that I a) had to find it at a Barnes and Noble b) tried several applications beforehand and c) read through several forum threads post-dated way before my version of Ubuntu makes it very user-unfriendly. If Brasero does all-in-one disk burning needs, why isn't that packaged in instead? That would be much more friendly to new adapters and the casual user.

> 
Do you have an example what you mean by installed off the internet? 
If you scan the hd for executable programs you would omit the libraries which were probably installed alongside the executable. If you go by name you expect the software and all related stuff to be named similar to the executable.
Using a package is imho the best way to handle that, that means the people in charge of the software are the ones who can create them which most ease. They know what the software depends on. Keep in mind tho that there are at least two types of packages deb and rpm and they need the hardware to build the binarys.


Yes, I downloaded LimeWire from the website. I've also downloaded theme .debs from DeviantArt that haven't worked either. And why do people package them in .zip?

> 
You can use it with gnome too, installs some kde-libs and doesn't look as well integrated as in kde but works nontheless.
Just for info: When you use gnome or kde you can use kde and gnome software and if you have ubuntu you can install kde afterwards (vice versa with kubuntu and gnome) 


I wasn't aware of this. Thanks!

> 
I hope I don't offend you, I just want to show you that you can't expect to have a development routine (specification->design->implementation->test) in free software projects like you have in a corporate company. Its more like evolutionary software development with testing outsourced to us users ;-). Doesn't mean that some projects have one, but again: you can't expect it.

You're right, but I guess I'm thinking more along the lines of major software, like Ubuntu itself. I just read a blog on Gnome's site where some guy stated the same things I've been thinking. If you want Ubuntu to take off as a viable netbook platform or anywhere in the consumer marketplace, more time has to be spent making the simple things simple, and worrying less about adding new features. Linux has always been a niche OS for the moderately computer savvy, but for the rest of the world, it's way too complex and time intensive to learn for everyday use. Social workers don't have time to learn how to run a terminal in order to enable laptop-mode, something that should be standard. Judges and police officers don't have the time to go online on a non-Ubuntu machine to figure out that to enable their hardware they need to plug in an Ethernet card, install a driver and then get wireless internet access! 

The point of the personal computer is to ease our lives, not make them more complex. While many computer savvy users don't mind and like to learn about this stuff, they don't realize how off-putting it is for the rest of the world who use computers for simplicity and practical uses. Below is the excellent blog:

[quote=http://gnomerocksmyworld.blogspot.com]
GNOME, and GNU/Linux, will forever be a niche desktop/OS until it is substantially better than Windows and OSX. Being free (either as in beer or freedom) is, evidently, not enough.

What is the road to such superiority? History has shown that technical superiority is no guarantee of market superiority. History has shown that marketing can help.

What is marketing? I have been thinking about that a lot lately. Here's a starter for 10:

Marketing can be encapsulated by a pair of principles. They are:

(1) Make good products / give good service / co-create good value; and
(2) Respect your customers (both current and potential)

That is all.

So, kudos to the Evolution team for including a way for customers to give feedback when they are having trouble (Help -> Report a problem). But simply punting that information to community forums or pointing to a FAQ is a waste of incredibly useful information. If someone asks a question with a known or "obvious" answer, you have a UI design problem. And usability is bug number 1 is most software these days.

But developer time is limited. Where should priorities lie? Adding more functionality or making simple things simple? Bling or ease of use? And why do I have to drop to a terminal and go "sudo chown me /dev/raw1394" in order to see video from my handycam? Every time?

Sigh.

In other news, thanks to all the Free software developers for making an OS and Desktop that is, in the main, at least as good as the major non-free alternatives. You guys and girls rock. Hard.

May all sentient beings achieve nirvana,

John. [/quote] 

A bit off topic, but that blog encompasses my feelings of Ubuntu to a T.

---

### Post by d00derino on 2010-04-04
Sorry, it appears that Brasero can burn DVD video, and in the magazine I was browsing yesterday showed a very different (and much more inviting) interface than mine has. 

I installed K3G and it's still a bother to get working. Why is it so hard to burn a DVD video on Linux? Every other operating system comes with a very, very simple (IQ >70) solution to this.

---

### Post by SiathLinux on 2011-09-22
Only in on the 'hardware' side of you problem - (as the software problems are beyond my expertise).

I just posted here (post #5)  [http://ubuntuforums.org/showthread.php?p=11276689#post11276689](http://ubuntuforums.org/showthread.php?p=11276689#post11276689)
about that laptop - as I've just been given one for free. If I work out my 'case mod' that I talk about there, I'll post a 'printable' formate for others to use.

---

