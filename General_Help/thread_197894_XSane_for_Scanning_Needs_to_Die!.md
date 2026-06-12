---
title: "XSane for Scanning Needs to Die!"
date: 2006-06-16
forum: General Help
---

### Post by kscelt on 2006-06-16
Having essentially one linux approach to supporting the use of scanners may have sounded like a good idea, but it has proved to be a poor choice. It's time for some new alternatives for the open-source crowd. Linux to succeed has to support user's hardware, and Xsane just does not do that. 

Support for new (As in the last two years) scanners has slowed to virtually nothing. Try looking at the scanners on store shelves and what is supported by Xsane. Good luck finding a match. The odds of a new linux user finding his existing scanner is supported are slim. 

This is just not a good situation for linux in general, which of course includes we Ubuntu lovers. If I had the ability and knowledge to do so, I'd begin a new solution myself, but I do not. 

So here's a call to those who do - How about a new project?  And in doing so, all of us linux users with useless scanners should be yelling at the manufacturer to provide linux support! It's shameful that companies like HP get away with doing nothing to support it's scanners in linux, yet try to position itself as a leader in Linux with it's website declaring:

"Open Source and Linux from HP - Choice, integration, and confidence" and "HP & Linux - Leading in the Global Enterprise".

What chutspa when they do not even support their own scanners, and for that matter, their own printers! They just want to profit off linux and open source without even basic internal support. Well, you get my point.

Perhaps this should have been two threads;

1. Scanner support alternatives
2. The need to put pressure on companies that force us to use Windows, or throw our hardware in the trash.

---

### Post by Stinger on 2006-06-16
Your headline doesn't really deserve an answer !
So I'll just leave a comment , [Xsane]("http://www.xsane.org/") is a graphical frontend to [Sane]("http://www.sane-project.org/").

Please don't go bashing at some poor developer , who actually does a great job ! 

And please get the facts right ! 

But making a new back and frontend seems like some kinda project , huh

Why not "just" start writing backends for the unsupported scanners and after doing that , you could write a new graphical frontend that fit your needs.

Personally I just love [Xsane]("http://www.xsane.org/") , furthermore I think the developers of both Sane and Xsane are doing a really great job !

---

### Post by brickbat on 2006-06-16
I am not convinced that dealing with a persons frustration by waving smileys at them is very helpful.

The guy was obviously frustrated in his search for a new scanner that works with SANE/XSANE.  His idea was that perhaps a new application would help.  I think he is completely wrong this.  He is correct about hardware manufacturers.  I have already sold a Canon multifunction printer and an ASUS wifi card and I have bought replacements (Brother multifunctional and Gigabyte wifi card) that are fully Ubuntu compatible out of the box.  I also contacted all the  companies before and after I switched to make sure they know why I switched.  

Finally, kscelt, it looks like Epson scanners have good SANE driver support at the moment.  I would check them out and ask people in the forums for their experience.  That is probably more useful than what you initially tried.

---

### Post by Stinger on 2006-06-16
[QUOTE=brickbat]I am not convinced that dealing with a persons frustration by waving smileys at them is very helpful.
[/QUOTE]
I was not trying to be helpful.

Better now ?

---

### Post by niviche on 2006-06-16
Scanner support can really be a pain on Ubuntu (on Linux in general, I guess). It seems that most printers, sound cards & so on are well detected and "work", but a lot of scanner are just as good as scrap when one switches to Linux.

In this sense, the original poster is right about this. It would be nice if SANE could support more scanners, or if something else (with more scanners supported) was to replace it.

Anyway, to ask something constructive: how can a non-technical, non-programming Linux user help SANE? I've got a scanner here that is not recognized at all. I have no idea about programming, and I don't want to open it. Can I help?

---

### Post by Stinger on 2006-06-16
[QUOTE=niviche]Anyway, to ask something constructive: how can a non-technical, non-programming Linux user help SANE? I've got a scanner here that is not recognized at all. I have no idea about programming, and I don't want to open it. Can I help?[/QUOTE]

It's not a lot to go on , but have a look here [SANE - Contributing]("http://www.sane-project.org/contrib.html")
paragraph "Reporting Unsupported Scanners and Adding more information".

Fill in the form [Report an unsupported device]("http://www.meier-geinitz.de/tinc?key=rDoQ7lrj&formname=adddev")
And Sane has [mailing lists and IRC Channel ]("http://www.sane-project.org/mailing-lists.html") too.

I reported my Epson Perfection 1670 back in 2004 , it's now fully supported by the snapscan backend.:D

---

### Post by zxee on 2006-06-16
[QUOTE=Stinger]I was not trying to be helpful.

Better now ?[/QUOTE]

Actually I don't think this is the sanctioned ubuntu way. You will have to be assimilated. But it was extremely funny and given the provocative topic title it's probably warranted. 

When you really look at how some manufacturers have marketed the hardware and kept open source develpers in the dark regarding that hardware it's really amazing that we have any scanners that work at all. And I do know a little about sane and scanners some years ago I got a parallel port scanner working in suse but I had to recompile the kernel to get it working-then the dam thing died anyway.

My thought to consider for the orginal poster: The more you know about what these develpers have to go through to get hardware recognized and functioning the more you'll appreciate them.

---

### Post by kscelt on 2006-06-17
Well, at least I got some responses, which is the purpose of the post - to draw attention to the woeful state of scanner support in linux. Brickbat, bleating about the difference between xsane and sane, or the wonderful job of those developers does not change the facts. Far too many of the scanners out there today - old models and what is currently available, are not usable under linux.

Nor does adjuring users to just write their own firmware, something which the preponderance of users don't have the option of doing, provide realistic direction. We do need a better approach to the problem. I don't think most scanner owners  care if that means revitalizing an effort behind sane, or a totally new project.

Perhaps an approach like that taken to deal with the poor support of printers under linux is needed. A number of the major linux distribution folk organized a conference with the printer manufactures to begin solving the issues. Certainly lack of linux support by the scanner makers is at the root of the problem. 

Regardless, many people who have invested their hard earned bucks in equipment who might want to transition to linux will not do so if it means throwing that money away. Those that do will harbor ill will toward the brands they had to leave behind. It's not good for the linux community, the equipment manufacturers, or the average computer user. 

Was the original post title provacative? Certainly. It's a frustrating problem for many of us. I'm sure the development people behind sane are great human beings, but that does not mean that effort has provided an adequate solution at this point.

---

### Post by zxee on 2006-06-17
Maybe, but I think that open source is a different animal than what you are expecting. Basically you want the open source community to respond to a problem like you're their customer-but you're probably not paying them anything. 
I do think, as was mentioned, that it would serve you better to state what specific scanner needs developer attention than to make blanket statements. If you check out the sane hardware compatibility page you will find that a lot of scanners ARE supported. And the problem has little to do with the personal attributes, or lack there of, in those laboring to get scanners working in sane. You totally ignore that manufacturers won't reveal their hardware specifications to open source developers. The developers get these scanners that are supported working by using donated scanners.
So you're frustrated because a scanner you have or want doesn't work with linux.
Did you try searching for an alternative? There is a commercial product, I haven't used it, that claims to support scanners in linux: [http://www.hamrick.com/](http://www.hamrick.com/) or search on vuescan. Good luck.

---

### Post by Stinger on 2006-06-17
[QUOTE=kscelt] I don't think most scanner owners  care if that means revitalizing an effort behind sane, or a totally new project.[/QUOTE]
You are soooo right , most users don't care , but they should care!!

Don't ask what Linux can do for you !
Ask, what can I do to make Linux the nr. 1 desktop OS ?

> Perhaps an approach like that taken to deal with the poor support of printers under linux is needed. A number of the major linux distribution folk organized a conference with the printer manufactures to begin solving the issues. Certainly lack of linux support by the scanner makers is at the root of the problem. 
Now this sounds like a good initiative , when are you planning to do this ?

(See brickbat, no smileys :---) whoops ! sorry ! lol)

---

### Post by moopere on 2006-06-18
[QUOTE=kscelt]...
Regardless, many people who have invested their hard earned bucks in equipment who might want to transition to linux will not do so if it means throwing that money away. Those that do will harbor ill will toward the brands they had to leave behind. It's not good for the linux community, the equipment manufacturers, or the average computer user. [/QUOTE]

This is all about the manufacturers.  It doesn't really affect 'Linux' if those users who buy unsupportable equipment don't transistion to Linux.  It certainly would have an effect on manufacturers if all users stopped buying unsupported equipment.

The simple mantra to always keep in mind is to buy Linux friendly equipment.  Find out what works and go buy it.  If that model is not on the shelf at your local store ask them to get it in, or if they won't then use mail order.  

Whatever you do, buying unsupported equipment is just going to bring you tears before bedtime as I doubt many developers have an interest in supporting the vast numbers of <100 dollar scanners with no tech specs available when there _are_ models available from reputable manufacturers which _do_ work.

I won't recommend equipment to my clients which is 'windows only' even when they are a windows only shop. Reason?  I have no interest in supporting in any way manufacturers which don't properly support their own equipment.

With Linux, as with many things, its "do it yourself", or "pay for someone to do it for you" or "use what already works" - there is no compelling reason for developers to spend time and effort on supporting unsupportable equipment unless they have the kit themselves and feel like working on it.

Cheers,
Craig

EDIT: Just had a really quick look, Epson 3490 is listed as having good support, 3590 basic (no slide adaptor support), Canon LiDE 25 and LiDE 60 both supported (as good again).

So, theres 3 currently available usb type scanners, with good support (good meaning almost all native functionality on the scanner is supported, some esoteric stuff not supported), price range from AU$70 through to about AU$250.  Took just a couple of minutes to find em.

Now, from the look of things, the support for the abovementioned scanners is entirely due to the SANE developers work, nothing to do with either Epson or Canon.  This is not ideal and to be honest, I'd be looking to buy from a company with a demonstrated committment to providing Linux support, with money, directly available drivers or at the very least example hardware for the SANE project to work with.  Nevertheless, I could go down the road right now, buy a cheap Canon scanner, come home, plug it in and have it work.

Regards,
Craig

---

