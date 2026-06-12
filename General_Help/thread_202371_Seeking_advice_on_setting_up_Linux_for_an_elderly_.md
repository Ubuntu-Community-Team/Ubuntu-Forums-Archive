---
title: "Seeking advice on setting up Linux for an elderly person"
date: 2006-06-23
forum: General Help
---

### Post by qwertymonster on 2006-06-23
Hello,
I'm setting up a computer for my grandmother who is 75 and currently uses Windows 3.1

She needs to be able to:
[LIST]
[*]Word Process (and have the ability to create MS Word Documents)
[*]Browse the Internet
[*]Email
[*]Talk to me (IM probably)
[*]Get remote desktop support
[/LIST]

She is not very computer literate so it needs to be as simple as possible.  She will never EVER touch the terminal.  I dual boot Ubuntu and XP but am not in any way a Linux expert so I thought I'd ask for any advice you have.

Some questions:
Is Linux suitable?
Is Ubuntu the best distro for the purpose?
bearing in mind she wants simple Word Processing, would AbiWord be better than OpenOffice?  Are there any other good Word Processors?
Can someone recommend a very user-friendly email client? Or would web mail be better?
A simple Instant messenger, GAIM? Others?
Remote Desktop? VNC suitable? Can it be set up so that it shares its desktop but as a client, connecting to my computer as the server?

Do you have any other advice on making things as simple as possible?

Any advice very much appreciated :D

---

### Post by zxee on 2006-06-23
You will probably get lots of opinions on this. I think that thunderbird's email program is as easy as anything M$ has created-probably easier but since you mentioned it online email is pretty simple too. Try [www.inbox.com](www.inbox.com) or gmail.

Let's see now. For a distro that is super simple, I nominate pclinuxos. Although ubuntu is often put in that class it's not as simple as pclinuxos and if your grandmother is used to windows the default desktop for that distro is kde-quite windows like IMO. You could also try kubuntu. 

Firefox or epihaney are the most popular browsers in linux so I don't see any reason to buck that trend. 

Word processing: Abiword opens faster and supposedly is compatible with or will create MS documents-I don't do this so-all I know is I like the light weight-unbloated feel of abiword, or you can use kword which is kde's desktop word processor. Hope that helps-my 2 cents.

---

### Post by kewldude606 on 2006-06-23
I think Ubuntu is the best distro for this :).

I would stick with OpenOffice because it, IMHO, has a better MS import filter and I doubt you want to explain "if it doesn't work, open it in office."  Also it has better spellcheck.

I would say Thunderbird or Gmail, probably Gmail because it is sooo simple.  If she has broadband, definitely Gmail although I would go for Thunderbird otherwise because it is still simple and you can view old email offline and write new emails offline.

Definitely go with GAIM but set up her buddy list and accounts for her.  Show her how to do the 2nd to last buddy to add and make her add the last contact.

Ubuntu has VNC built in.  System-->Prefs-->Remote Desktop.  Forward ports for her then set up DynDNS or something so you don't have to fuss with dynamic IPs.

As for anything else, make it auto logon and put shortcuts on her desktop so that she can see them right when she boots up.  Don't even mention Terminal or the idea of 4 virtual desktops or anything.  KISS (Keep It Simple Stupid).

---

### Post by x64Jimbo on 2006-06-23
First of all, I have to say Good Choice! Ubuntu is probably the single most newbie/elderly friendly Linux distro out there due to its simplicity. 
Use AbiWord. If she's been using Win3.1 I guarantee you she wouldn't know what to do with all the features of OO.o. AbiWord can compose MS Word files in RTF format though, so if she really needs MS Word binary functionality, she'll need OO.o.
She should use Firefox for browsing the web. I've got all my family using it, and they all love it. Make sure you install the flash plugins and such so she doesn't run into trouble there. 
Set her up with an aMSN install and account, and put yourself on her buddy list. 
Use webmail. Dealing with an email application is probably the hardest thing she could do.
Remote Desktop Support - could be tough. I'd recommend installing x11vnc as a system service that only accepts connections through the loopback interface and then installing SSH so you can tunnel in. Otherwise, VNC is pretty insecure. After that, you'll need to set up a dyndns.org account for her computer so you can connect to a dns name instead of her (potentially dynamic) IP address. If she has any of the pretty mainstream routers on her internet connection, it will have an option to link up with the dyndns.org account that you create for her, and it will auto-update whenever she has an IP address change. 
If I've missed anything, let me know.

---

### Post by qwertymonster on 2006-06-23
Thanks for all of your comments.  I'm going to try the PCLinuxOS live cd and see what it looks like, if I don't like it I'll stick with Ubuntu.  I think I will go with AbiWord since come to think of it an RTF export would do.

I always intended to use Firefox and will do so.  As she will have broadband I think I'll go with GMail.

I've found out I can run a VNC-viewer with the -listen switch so that she connects to my static IP when she needs to.  I will be listening constantly.

I personally like GAIM so I think I'll go with that, I can then configure it to use her GMail account through Jabber protocol.

Thanks again for taking the time to write your answers! :)

---

### Post by x64Jimbo on 2006-06-23
Just thought about this - why not just use the chat built into Gmail?

---

### Post by marcw on 2006-06-23
If you choose Ubuntu, you'll do fine.  I set up my father-in-law first with Hoary over a year ago and upgraded him to Breezy.  I'll be upgrading him again to Dapper within the next couple of weeks.

His requirements were exactly like yours.  Thunderbird works great for email.  For IM we chose ICQ on Gaim.  He uses it all the time.  We made the default document in OOo to be that of MS (.doc, .xls, etc).

For remote access, I set him up with vnc4server with xvnc4viewer on my end.  That way, I have to put my machine in listen mode and he has to initiate the connection I built a desktop icon for him to do this).  My thinking in doing it this way was that it would put him "in charge" of remote connections.  I wouldn't be able to remote into his machine whenever I felt like.  It works well.  He's only needed my help a couple times, but it's come in very handy on those occasions.

(I forgot to mention...  He's 82)

---

