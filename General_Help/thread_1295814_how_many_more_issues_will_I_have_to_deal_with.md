---
title: "how many more issues will I have to deal with?"
date: 2009-10-19
forum: General Help
---

### Post by not-too-pleased on 2009-10-19
I'm attempting to run ubuntu (ver 7.something) on an older celeron 1.4.  I've got plenty of ram...all the hardware works great.  This pc works fine on every Windows based OS I've installed on it.  Don't have a legal license to keep on it so went for linux instead.  Trying to set this up as a simple file server with one main public file share.  This install and setup has been anything but simple.  Frankly I'm amazed.  With the amount of time I've wasted on this I could have gone and bought an SBS 2003 key.  

So to my issues....

Attempted ubuntu server install and all seemed to go well until I booted it up and saw no gui and no apparent option for one.  Rather than get any actual help online I was berated for even WANTING a gui on a server as it would reduce performance.  Frankly performance is a non-issue with this system.  I need a gui for the users to be able to manage their backups and there is NO WAY that they'll be able to us a command line interface.  They can barely use Windows.  After digging around, searching and begging for more help I was able to find some commands that were apparently the exact solution I needed but none of them had any effect.  All returned errors.

Installed xubuntu and it wouldn't even boot.  Tried a number of times with multiple cd's (all tested as fine) and finally gave up.  installed kubuntu and it wouldn't even get through the install without telling me that I didn't have the right permission to continue.  Never seen something like that before.  So that's out.

Finally dug up an older copy of ubuntu I've had for a while but never used (ver 7.something... don't ask I don't know) and it installed fine.  Setup users and networking.  Everything looked great until I attempted to share a folder.  Given a popup saying that the share services weren't installed and when I select them and tell it to install the system pauses for a second and I'm presented with the same message. 

Spent even more time fighting with this thing and trying to find workable solutions online but nothing anyone suggested has worked.  Last hope was to run all upgrades to the most current version (don't know what that one is either) and it happily ran through the process, giving me prompts and taking up more time before I was told that I don't have the correct permissions to proceed.  How is this possible when I'm logged in as an admin and it's the ONLY user???

Obviously as you can tell I'm completely frustrated with this.  This was supposed to be a simple install for a very simple use.  I'm not designing rockets here.  I only want to share a folder to multiple versions of xp and vista that are currently having trouble seeing each other, and to provide one central file store for a friends business.  the only use this machine will see outside of this is to run the daily backups. 

So...where do I go to from here?  I'm amazed at how convoluted and difficult this install and config has been.  If it weren't for the cost issue I wouldn't have anything to do with this OS but I haven't been given any other option here.  I've heard great things about linux (and ubuntu specifically) but frankly this doesn't do ANYTHING to build my confidence in this as a viable option.  It was my thought that a pc that can run xp pro without any trouble should be able to run ubuntu but so far I haven't been shown that this is the case. 

Any suggestions or help would be greatly appreciated.  

Richard

---

### Post by HermanAB on 2009-10-20
The problem is that you are under a serious misconception.  Ubuntu is not the easiest Linux out there.  It is sort of intermediate to difficult.  If you want an easy Linux with pointy-clicky wizards for everything just like Windows SBS, then you should try Mandriva or Suse.

---

### Post by QIII on 2009-10-20
Part of the issue is that you "grew up" using Windows and now you are trying to learn a foreign language while trying to use it in a production environment.  Not an easy task and I don't envy your predicament.

"Linuxball" is a different game.  For those of us who have been at it some time, things that seem daunting to you may be trivial to us.  And some of us forget that when we try to help.  It is only human.

My first suggestion would be to install something newer in any case.  The 7.XX versions are coming to EOL.

Blow the "who needs a GUI?" guys off.  This is about choice, not about snobbery. 

Install the server version.

Come back here and ask how to add a GUI on top of it.  Make it the way YOU want it, not the way someone else tells you it should be.  If you need to GUI tools, by all means use them!

Get to the point where you can start and run the system itself, and then come back again and ask specific questions about how to get one thing up and running at a time.

Ask people to explain things in layman's terms.  Ignore the occasional snob.  They exist in every group.

---

### Post by undecim on 2009-10-20
First, try an updated version of Ubuntu. The current Long Term Service version is 8.04 and will recieve updates through April 2013. The current release is 9.04 (i'm actually not sure how long that one will recieve updates...)

As for the GUI, are your clients going to be accessing this computer directly with a mouse, keyboard and monitor? if that's the case, this isn't going to be a server, but a multi-user desktop. If they will be using this over a network, there are plenty of applications that can be used to manage files remotely. (FileZilla, for example)

If you would like to add a GUI to a server install, just run the command "sudo aptitude install ubuntu-desktop" which will install every package included with a Desktop edition install.

To set up a network share, you need to install samba with the command "sudo aptitude install samba" or by installing the samba package with synaptic package manager. You then will need to configure your shares either by editing the configuration file manually or installing a graphical config with "sudo aptitude install system-config-samba"

Also, by "online help", it doesn't seem like you tried the forums (since your post count is 1). In my opinion, the forums are the best place to get support, because the people helping you can give you all the information you need at once, and review the information they have before giving it to you.

If you have any other issues, post them here, and I'll see if I can help you.

---

### Post by DeMus on 2009-10-20
> **not-too-pleased said:**
> Last hope was to run all upgrades to the most current version (don't know what that one is either) and it happily ran through the process, giving me prompts and taking up more time before I was told that I don't have the correct permissions to proceed.  How is this possible when I'm logged in as an admin and it's the ONLY user???

What do you mean with logged in as admin and don't have rights? Are you logged in as "root", the official Linux administrator, or as user admin (windows administrator) and think you are "root"?
I have a feeling you are mixing Windows with Linux. Forget all you know about Windows and learn Linux before you start something.
Reading your story it seems to me you don't need a server version. Just install Hardy 8.04 with long term support (as mentioned by others as well). During install make a user (you, choose the name you want to use) and add a password.
You can then raise yourself to become "root" for a moment (by typing your password) to do some things "root" has to do, things you can not do. When done the root privileges are gone and the system is safe again.

Just try this and you'll see it will work. When having more questions, about Samba for example, ask again and/or read the answers others have given here already.

---

### Post by DouglasAWh on 2009-10-20
> **HermanAB said:**
> If you want an easy Linux with pointy-clicky wizards for everything just like Windows SBS, then you should try Mandriva or Suse.

Hmm, I don't know much about either of those, but OP, if you want to stick with the Ubuntu because it's popular, I'd highly suggest Linux Mint.  It comes out a bit after Ubuntu, but the 9.04 version (aka Linux Mint 7) is out in both GNOME and KDE.

I'd also echo the sentiments about getting on 8.04 or something newer.

The -server kernel is going to cause all sorts of grieve if you don't actually want a "server" but Ubuntu's definition.  You might not need wireless, but you won't get that in -server or in -rt in case you were thinking about installing ubuntustudio.  You might also find yourself wanting Flash.  Linux Mint has that.  I don't personally use Linux Mint because their closed beta process really rubbed me the wrong way. However, I always recommend it to people.  I don't know if I'll check out 8 since I'm pretty firmly entrenched into the Ubuntu and Fedora worlds (we made the switch from Ubuntu to Fedora at work for so reasons I can expound on if asked).

That's my two cents.  Are we back to two cents with the current economy? I was giving two dollars before I think...

---

### Post by egalvan on 2009-10-20
A correction and some examples...

> **undecim said:**
> ... try an updated version of Ubuntu. The current** Long Term Service **version is 8.04 and will recieve updates through April 2013.
 The current release is 9.04 (i'm actually not sure how long that one will recieve updates...)

It's LTS, Long Term **Support**. Not **Service**.

LTS releases are supported for 3 years on the Desktop version, 
and for 5 years on the Server version.

Non-LTS, such as 8.10, 9.04 and 9.10, are supported for 18 months on both Desktop and Server.

> 
If you would like to add a GUI to a server install, just run the command "sudo aptitude install ubuntu-desktop" which will install every package included with a Desktop edition install.

the following will install different GUI's.

sudo aptitude install ubuntu-core     <-- this is the smallest (least packages)
sudo aptitude install ubuntu-minimal  <-- medium install
sudo aptitude install ubuntu-desktop  <-- the largest (most packages)


If you prefer KDE, try these
sudo aptitude install kubuntu-core
sudo aptitude install kubuntu-minimal
sudo aptitude install kubuntu-desktop

for xfce,
sudo aptitude install xubuntu-core
sudo aptitude install kubuntu-minimal
sudo aptitude install kubuntu-desktop

Note:
there are minor differences between a Desktop Install,
and a Server Install with Desktop added.
The kernel is slightly different, the scheduler is set different,
etc.
None of which are of much concern, except that the Server Install with Desktop added will feel slightly less responsive, less "livelier" if you will.
Not by much, but some folks may notice.
The Server is designed to optimize data transfer between data storage and the network stack.

DeMus as some good suggestions, read them and heed them.


And have you resolved your

*multiple versions of xp and vista that are currently having trouble seeing each other*

problem?

Or has this proven to be

*convoluted and difficult *?

And has this done

*ANYTHING to build my confidence*

in XP and Vista?

:P

---

### Post by iMisspell on 2009-10-20
First off and not to piss you off, but trying to install a dated version of ubuntu seams like pure laziness (which is gonna cause a snowball effect). You can get a new ver strait from there site.

Anyway...
Im a PHP Dev who has been hiding behind windows for a long long time. One particular application i made gained popularity and i "needed" a better test environment so i headed to ubuntu.

> **not-too-pleased said:**
> Attempted ubuntu server install and all seemed to go well until I booted it up and saw no gui and no apparent option for one
About a year ago i ran down the same exact road with the server edition, reformatted and installed Ubuntu-desktop 8.xx being i only needed Apache and MySQL. About two weeks ago i started to do some research about server GUI's, re-installed the server with the following GUI tools to help me out.

_[openbox]("https://help.ubuntu.com/community/Openbox")_ (desktop - the version i got was completly bare)
_[fbpanel]("http://fbpanel.sourceforge.net/")_ (task-bar)
_[pcmanfm]("http://pcmanfm.sourceforge.net/intro.html")_ (file manager - simulare to windows explorer)

Right now im working on some perl scripts to do some maintaince on the server and when the time comes ill yank out the GUI stuff to help improve security.

> **not-too-pleased said:**
> I need a gui for the users to be able to manage their backups and there is NO WAY that they'll be able to us a command line interface.
What kind of back-ups are you talking about ?
Maybe if you explane what you or the Admin needs to do and also what the users need, people can give you suggestions of how they have done it. I dont see where a servers GUI would have anything to do with a user/client machine. Once you set up the shares on the GUI-less server, the clients will be conneting via windows and see files and folders.


> **not-too-pleased said:**
> I only want to share a folder to multiple versions of xp and vista that are currently having trouble seeing each other...Seams like your coving your problems with more problems.


Ive been a windows user for around 10 years, can program in vb6 a little in vb.net, c-sharp and enjoy PHP alot... But... doing stuff in Ubuntu is a bit different and to jump in when "the pressure is no" does not seam like a good move. 

If you did not bookmark or subscribe to this thread, im sure you have seen the amount of threads which get posted here while searching for your own. Maybe try and focus a little on your problems, explane what you want to do and people will help out.

good luck...

---

### Post by nothingspecial on 2009-10-20
Calm down

Download and install 8.04 server edition from the Ubuntu website.

Set up networking

```
sudo ifconfig eth0 up
```

```
sudo dhclient
```

Install your updates
```

sudo apt-get update && sudo apt-get upgrade
```

Make sure your server will connect to the network on boot

```
sudo nano /etc/network/interfaces
```

copy and paste these two lines to the bottom of that file
```

auto eth0
iface eth0 inet dhcp
```

Press Ctrl+O to save and Ctrl+X to exit.

Install samba
```

sudo apt-get install samba smbclient smbfs
```

Configure samba using [[COLOR="Magenta"]this guide[/COLOR]]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

and [[COLOR="Magenta"]this guide[/COLOR]]("https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html")

This will allow you to share that file with windows machines. If the other users are accessing the server remotely you won`t need a gui. If you really need one see previous posts.

If you get stuck at any point post back, but it might be an idea to change your thread title to "sharing over a network to windows machines" or something like that - alot of people will just skip past titles like yours. To do that edit your original post and choose go advanced.

Remember, everyone on this forum is just volunteering their time. You may not get help straight away but hopefully someone can get this sorted for you.

---

### Post by mojila on 2009-10-21
Hi,
 
   Thanks to ALL who helped  out this question. My hats off to them. 
I am new to Ubuntu... for years am using.. e.g. win ver 3.0... to todate Windows 7 Rc.
and Bought HP Mediasmart Home server also...
 
All windows OS.. I upgraded ..(Some I purchased .. Duplicate) long story short...
Yes have spent a lot money... I am trying... server....
I Installed   UBUNTU Server 9. ? I think its 9.1... and  :):) as window user Could not Login
 
now I can login in server but didnt have GUI... So I came to this FORUM...
Type question "GUI for Ubuntu Server"  I got this thread and read this Question..
Followed replies.. 
 
may be I found answer.. I would try if doent work will ask Question...
 
ANS that why.. I thank.. to ALL of you helping out to Others.....
 
Many Many Thanks...  =D>=D>=D>
 
                                                                             Mojila

---

