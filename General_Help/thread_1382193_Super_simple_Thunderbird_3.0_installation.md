---
title: "Super simple Thunderbird 3.0 installation"
date: 2010-01-15
forum: General Help
---

### Post by PDA1 on 2010-01-15
Here's a simple install for Thunderbird 3.0 (Shredder);

[URL="http://www.atoztoa.com/2009/12/thunderbird-30-in-ubuntu.html"]http://www.atoztoa.com/2009/12/install-thunderbird-30-official-release.html
[/URL]

---

### Post by Cheesemill on 2010-01-15
Your link is for testing versions, that's why it's called Shredder.
Here's an easier way to get the final stable Thunderbird release:

[UbuntuZilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

---

### Post by PDA1 on 2010-01-15
I'll give it a try but I really doubt I'll be able to install it.  I've been working on this for over 2 days (about 20 hours) and never seem to get it right.  Either the explanations leave some critical information out or I just lack the understanding of what to do- the results have been the same- no successful installation.


Having said that....i just looked at ubuntuzilla and have NO idea what the heck they're talking about. 

All I want to do is install TB3 and I want a step by step explanation how to do it.  Synaptic doesn't provide a successful installation.

---

### Post by PDA1 on 2010-01-15
I tried all of the steps.  I even went to another page to get "installation scripts" or whatever they're called.  I tried to install Ubuntuzilla ....here are the results-

earl@earl-laptop:~$ sudo apt-get install ubuntuzilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntuzilla
earl@earl-laptop:~$ sudo apt-get ubuntuzilla
E: Invalid operation ubuntuzilla
earl@earl-laptop:~$ 

I still have Shredder on my computer.

What a waste of time.


How do I get Mozilla- Thunderbird to run?

---

### Post by aysiu on 2010-01-15
I've tested UbuntuZilla myself. It does not install Shredder. It also is vastly simpler than the "simple" installation you just linked to.

Just paste (with your mouse) these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
sudo apt-get update && sudo apt-get install thunderbird-mozilla-build
```

---

### Post by PDA1 on 2010-01-15
I used your commands.  Here's what terminal says, 

Reading state information... Done
thunderbird-mozilla-build is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So I click on my email icon and here's what I got......take a look at the attached picture.

---

### Post by aysiu on 2010-01-15
Right-click the launcher, and select Properties

What command does your email icon launch?

---

### Post by ftabor on 2010-01-15
> **aysiu said:**
> I've tested UbuntuZilla myself. It does not install Shredder. It also is vastly simpler than the "simple" installation you just linked to.

Just paste (with your mouse) these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
sudo apt-get update && sudo apt-get install thunderbird-mozilla-build
```

Seems like there may be a problem there:

```
W: Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
```

64 bit may not be available yet?

---

### Post by PDA1 on 2010-01-15
Here's what it says-


thunderbird-3.0 %u

---

### Post by Cheesemill on 2010-01-15
> **ftabor said:**
> Seems like there may be a problem there:

```
W: Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
```64 bit may not be available yet?

If you read the instructions on the UbuntuZilla site it clearly states that Mozilla only release 32-bit builds.

I got round this by downloading the .deb directly from here:
[http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.0-0ubuntu2_i386.deb/download](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.0-0ubuntu2_i386.deb/download)
and using:
```
sudo dpkg -i --force-architecture thunderbird-mozilla-build_3.0-0ubuntu2_i386.deb
```
to install.

---

### Post by PDA1 on 2010-01-15
Possible solution.

Here's what I did-  In my root folder (using Terminal) I typed Thunderbird.

TB started and it is indeed ver. 3.0.

So, it does run.

What a PAIN.

---

### Post by PDA1 on 2010-01-15
Thank you for the help but I have no idea what to do.  32 bit....64bit....meaningless to me.

---

### Post by aysiu on 2010-01-15
If you don't know if you have 64-bit or not, you don't.

Change the launcher command from ```
thunderbird-3.0
``` to just plain ```
thunderbird
```

---

### Post by PDA1 on 2010-01-15
Success (dumb luck)!

Here's what I did-

sudo apt-get remove --thunderbird-3.0

Ok...so that got rid of Shredder....FINALLY.

Honestly, what sort of mind comes up with a name like that for an email program anyway?

Then, I restarted Ubuntu.

And....as it was supposed to happen....Mozilla build of Thunderbird appeared in my Internet Applications list.  I clicked it...and it started!

I deleted the ./mozilla thunderbird folder and replaced it with my previous ./mozilla thunderbird 3.0 folder and everything migrated perfectly.

Thanks for all of your suggestions.  I really wish this stuff was fool (and fool) proof.  There're just too many steps and differing opinions on how to do anything with Linux and most posts assume too much.

I'm a computer user.

---

### Post by Seventh Reign on 2010-01-15
Why not just install the Mozilla Daily PPA, install TBird 3 and then disable the PPA .. or keep it active.  Seems like that would be the easiest way.

---

### Post by PDA1 on 2010-01-15
Wow! That sounds like a great idea.

[LEFT]Now, having said that.....how do I do it exactly, because, to put it simply I have no idea how to implement what you're suggesting.
[/LEFT]

---

### Post by Uncle Spellbinder on 2010-01-16
[Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation) is, indeed, the answer. The official Thunderbird 3, current stable release appears in Synaptic...

---

### Post by PDA1 on 2010-01-16
Tried Synaptic.  No success.  TB 3 must install of something....but it sure doesn't run and there aren't any icons or mention of TB 3 (Mozilla-thunderbird) in Applications folders anywhere.

---

### Post by Uncle Spellbinder on 2010-01-16
@ PDA1

It's not in Synaptic unless you add [Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) to your sources.list first. 

From my sources.list:

```
#### Ubuntuzilla
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
## To install the current stable release of SeaMonkey, Thunderbird or Firefox, use the following in terminal:
## sudo apt-get install firefox-mozilla-build
## sudo apt-get install thunderbird-mozilla-build
## sudo apt-get install seamonkey-mozilla-build
```

---

### Post by jamesisin on 2010-01-16
I have:

[http://switch.dl.sourceforge.net/project/ubuntuzilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt)

Tb doesn't appear in Synaptic.  What's the difference?

---

### Post by nanotube on 2010-01-16
> **Seventh Reign said:**
> Why not just install the Mozilla Daily PPA, install TBird 3 and then disable the PPA .. or keep it active.  Seems like that would be the easiest way.

because daily ppa installs not releases, but the latest daily builds. e.g., right now you'll get not the released 3.0, but 3.0.2pre.

---

### Post by nanotube on 2010-01-16
> **jamesisin said:**
> I have:

[http://switch.dl.sourceforge.net/project/ubuntuzilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt)

Tb doesn't appear in Synaptic.  What's the difference?

the difference is that you have the old ubuntuzilla repository for the ubuntuzilla script, not the new ubuntuzilla repository for mozilla releases.

see the ubuntuzilla website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/), and follow the installation instructions.

---

### Post by PDA1 on 2010-01-16
Well, what I now have installed and running is 3.0.2pre.

However, I did have Mozilla-Thunderbird 3.0 installed yesterday....before I messed it up.


Shredder works fine.

---

### Post by PDA1 on 2010-01-16
> **nanotube said:**
> the difference is that you have the old ubuntuzilla repository for the ubuntuzilla script, not the new ubuntuzilla repository for mozilla releases.

see the ubuntuzilla website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/), and follow the installation instructions.




Did that already. 

Here's my results when doing the sudo stuff-

earl@earl-laptop:~$ ## sudo apt-get install thunderbird-mozilla-build
earl@earl-laptop:~$ 
earl@earl-laptop:~$ 
earl@earl-laptop:~$ sudo apt-get install thunderbird-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunderbird-mozilla-build is already the newest version.

---

### Post by Uncle Spellbinder on 2010-01-17
> **jamesisin said:**
> I have:

[http://switch.dl.sourceforge.net/project/ubuntuzilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt)

Tb doesn't appear in Synaptic.  What's the difference?

According to your quote, you have....

```
http://switch.dl.sourceforge.net/project/ubuntuzilla/apt
```

It should be

```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

On three different installs of Karmic (2 desktops and a laptop), Thunderbird shows up in Synaptic.


Also, see here: [http://ubuntuforums.org/showthread.php?t=1373596](http://ubuntuforums.org/showthread.php?t=1373596) 

and here: [http://ubuntuforums.org/showthread.php?p=8642447#post8642447](http://ubuntuforums.org/showthread.php?p=8642447#post8642447)



.

---

### Post by nanotube on 2010-01-17
> **PDA1 said:**
> Did that already. 

Here's my results when doing the sudo stuff-

earl@earl-laptop:~$ ## sudo apt-get install thunderbird-mozilla-build
earl@earl-laptop:~$ 
earl@earl-laptop:~$ 
earl@earl-laptop:~$ sudo apt-get install thunderbird-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunderbird-mozilla-build is already the newest version.

so, that means it's installed and should be working fine.
in your applications menu, look for "mozilla build of thunderbird", which should start it.

---

### Post by PDA1 on 2010-01-18
"mozilla build of thunderbird" doesn't appear anywhere in Applications (internet, office, etc)


Is there a "sudo" command I should execute to make it work?

---

### Post by nanotube on 2010-01-18
> **PDA1 said:**
> "mozilla build of thunderbird" doesn't appear anywhere in Applications (internet, office, etc)


Is there a "sudo" command I should execute to make it work?

only 'sudo apt-get install thunderbird-mozilla-build', which you already did...

check and see where your thunderbird menu link is pointing. if it is pointing to /usr/bin/thunderbird (or just thunderbird), then it should be pointing to the mozilla build, assuming it's installed.

also check "ls -al /usr/bin/thunderbird" to see if that link is pointing in the right direction.

---

### Post by PDA1 on 2010-01-18
Here's what it says-  thunderbird-3.0 %u  


I found that stuff under the System>Preferences>Main Menu  stuff.

Here's the other reference you mentioned in the fancy code stuff----

earl@earl-laptop:~$ ls -al /usr/bin/thunderbird
lrwxrwxrwx 1 root root 24 2010-01-16 03:28 /usr/bin/thunderbird -> /usr/bin/thunderbird-3.0

---

### Post by nanotube on 2010-01-18
> **PDA1 said:**
> Here's what it says-  thunderbird-3.0 %u  


I found that stuff under the System>Preferences>Main Menu  stuff.

Here's the other reference you mentioned in the fancy code stuff----

earl@earl-laptop:~$ ls -al /usr/bin/thunderbird
lrwxrwxrwx 1 root root 24 2010-01-16 03:28 /usr/bin/thunderbird -> /usr/bin/thunderbird-3.0

well... so, first: thunderbird-3.0 is a link specifically to the 'shredder' version from the mozilla-daily repository.

second, since /usr/bin/thunderbird points to thunderbird-3.0, rather than to /opt/thunderbird/thunderbird (which is where ubuntuzilla's version goes), that indicates to me that 'thunderbird-mozilla-build' is not installed (or the link got overwritten by something else you did).

so... if everything is working fine for you and you're happy, don't do anything, and just let it be.

if you for whatever reason really want the mozilla-build of the release instead, best thing to do would be to uninstall all thunderbird packages (including 'thunderbird', 'thunderbird-3.0', 'thunderbird-mozilla-build'), then install again just the 'thunderbird-mozilla-build' package.

---

### Post by FrancoNero on 2010-01-24
> **Cheesemill said:**
> If you read the instructions on the UbuntuZilla site it clearly states that Mozilla only release 32-bit builds.

who's idea was that? :(

---

### Post by nanotube on 2010-01-24
> **FrancoNero said:**
> who's idea was that? :(

mozilla's. if you google around you'll see they're not planning 64bit releases until firefox4...

---

### Post by atoztoa on 2010-02-02
> **PDA1 said:**
> Here's a simple install for Thunderbird 3.0 (Shredder);

[URL="http://www.atoztoa.com/2009/12/thunderbird-30-in-ubuntu.html"]http://www.atoztoa.com/2009/12/install-thunderbird-30-official-release.html
[/URL]

The post was not for Shredder, it was for official release of Thunderbird, Shredder is the testing codename. The post was specific for Thunderbird 3 and will not work now, coz the setup file is no longer in server.

Try this link instead:

[http://www.atoztoa.com/2010/01/install-thunderbird-latest-official.html](http://www.atoztoa.com/2010/01/install-thunderbird-latest-official.html)

---

### Post by aysiu on 2010-02-02
> **atoztoa said:**
> 
Try this link instead:

[http://www.atoztoa.com/2010/01/install-thunderbird-latest-official.html](http://www.atoztoa.com/2010/01/install-thunderbird-latest-official.html) Adding and using the UbuntuZilla repository is easier:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by koolchoice on 2010-02-15
> **aysiu said:**
> I've tested UbuntuZilla myself. It does not install Shredder. It also is vastly simpler than the "simple" installation you just linked to.

Just paste (with your mouse) these commands into [the terminal]("http://www.psychocats.net/ubuntu/terminal"): ```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
sudo apt-get update && sudo apt-get install thunderbird-mozilla-build
```


-------------------------

After a couple of tries this worked like a dream-

many thanks!;)

---

### Post by PDA1 on 2010-02-15
I wish I never put this post up.

If it were so simple it could've been solved in 1 reply.

---

### Post by aysiu on 2010-02-15
> **PDA1 said:**
> 
If it were so simple it could've been solved in 1 reply. It was. Post #2 links you to UbuntuZilla.

---

### Post by jamesisin on 2010-02-15
You don't have to be right to be important.  Look at Jean-Baptiste [Lamarck]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FJean-Baptiste_Lamarck&ei=xAx6S4KiBYWmswOa-tzLCA&usg=AFQjCNG8wv_lfV3ZwdzwMiRI4OnLvFivCw&sig2=nninayzeI6kEUsqC2GJU7g").

---

### Post by PDA1 on 2010-02-16
> **aysiu said:**
> It was. Post #2 links you to UbuntuZilla.


So it links you to UZ....so what?  It didn't work for me.  If it were so simple to do then this post and this entire forum wouldn't even have been necessary.    I just looked at post #2 and went, again, to UZ.  So, it says click for installation.  So I did.  Does it mention Ubuntu 9.10?  Of course not.  It doesn't tell you exactly how to do it if you're using 9.10.  Didn't the genius that wrote that thing take into consideration that there are some dopes out there that won't know what to do unless you are specific?

I don't have the time to waste studying the intricacies of Ubuntu or any other OS for that matter.  Mankind has wasted way too much time on completely unproductive solutions to computer problems while be chided by those that do waste their waking hours in the pursuit of it all.

Make solutions simple, understandable and well written and most problems will be fixed easily.  Make too many assumptions, leave out important parts (like MOST of the help stuff on the web) and there will be a lot of trouble for folks.

---

