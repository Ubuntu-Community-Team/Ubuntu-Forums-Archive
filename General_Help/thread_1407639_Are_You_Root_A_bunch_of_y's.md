---
title: "Are You Root? A bunch of y's"
date: 2010-02-15
forum: General Help
---

### Post by TheDarkSix on 2010-02-15
New to ubuntu was trying to install, I use Xbuntu and basically i visited [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/)

I followed one command and it asked if i was Root? I typed Y and then a whole bunch of y's filled the command window...it did not continue to keep going but it filled to window nonetheless/...what the heck was that? hope im not compromised

I used sudo aptitude and it worked flawlessly and installed some other things along with it...like 16 packages but everythings fine

I suffer from paranoia so sorry if this thread was pointless i am a new user to linux

I actually love linux more than windows i had a huge malware problem on windows and it was being manipulated to death so i had to scrap it ASAP:popcorn:

Also i need a easy to use firewall and one that is trusted by the community as a whole 

THanks everyone...Much much much love

---

### Post by SPr on 2010-02-15
> **TheDarkSix said:**
> New to ubuntu was trying to install, I use Xbuntu and basically i visited [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/)

```
sudo apt-get install flashplugin-nonfree
``` should work
> **TheDarkSix said:**
> 
I typed Y and then a whole bunch of y's filled the command window...it did not continue to keep going but it filled to window nonetheless/...what the heck was that? hope im not compromised

That sounds like the y key got stuck.
> **TheDarkSix said:**
> 
I used sudo aptitude and it worked flawlessly and installed some other things along with it...like 16 packages but everythings fine

That sounds normal. aptitude (or apt-get or synaptic) will automatically download everything that is needed for the program you are installing.
> **TheDarkSix said:**
> 
Also i need a easy to use firewall and one that is trusted by the community as a whole 

You should already have a firewall (iptables) running. If you want a gui to configure it try searching synaptic for "firewall". I have no reommendations as to which one to try.

---

### Post by gsmanners on 2010-02-15
For a firewall, I would suggest you use ufw:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by TheDarkSix on 2010-02-15
> **SPr said:**
> ```
sudo apt-get install flashplugin-nonfree
``` should work

That sounds like the y key got stuck.

That sounds normal. aptitude (or apt-get or synaptic) will automatically download everything that is needed for the program you are installing.

You should already have a firewall (iptables) running. If you want a gui to configure it try searching synaptic for "firewall". I have no reommendations as to which one to try.

are you sure the y key got stuck? I NEVER had keys get stuck on me and i've been maliciously hacked when using windows xp because i downloaded a game trainer and it gave me complete hell

I dont know these names but it was a FUD RAT...fully undetected malware that people pay a lot of money for and it's very very real in the windows realm...It was horrible even i used rootkit detectors and it didnt work

I typed y once and hit enter and it spammed a whole bunch of y not in a row but in a downwards position...it was pretty nasty looking to be honest and i got extremely paranoid and thought adobe wanted to root my system for some unknown
reason because you know linux users are also BUSINESS users too...So you NEVER know

How can i even tell if i am rooted>?

---

### Post by TheDarkSix on 2010-02-15
wow this is unbelieveable when i enter 
sudo ufw enable it aks for my password and then my keyboard ceases to function

Can someone PLEASE tell me what is going on here

---

### Post by bodhi.zazen on 2010-02-15
> **TheDarkSix said:**
> wow this is unbelieveable when i enter 
sudo ufw enable it aks for my password and then my keyboard ceases to function

Can someone PLEASE tell me what is going on here

When typing your password you will not see anything typed in the terminal, not letters, not number, not * or #.

Type your password and hit the enter key.

---

### Post by jamesisin on 2010-02-15
> **TheDarkSix said:**
> i've been maliciously hacked when using windows xp because i downloaded a game trainer and it gave me complete hell

I dont know these names but it was a FUD RAT...fully undetected malware that people pay a lot of money for and it's very very real in the windows realm...It was horrible even i used rootkit detectors and it didnt work

You are beginning your liberation process from the world of Windows.  The transition can be difficult at times, but you are assuredly on the road to recovery.

I took a look at the instructions in the link in your opening post.  Those instructions only involve Ubuntu approved repositories of approved and tested software.  Those repositories will never contain malware of any kind.  It is *possible* to add malicious repositories, but those instructions do not do so.

As long as you stick to the software natively available through Synaptic (and its command line equivalents) you should be free from the concerns of typical Windows users (malware and the likes).

For now, you may want to concentrate your searches on these forums (until you are better adapted to Linux) for solutions to your issues.  For instance, here is an excellent tutorial for getting audio and video set up on a new system:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by TheDarkSix on 2010-02-15
> **jamesisin said:**
> You are beginning your liberation process from the world of Windows.  The transition can be difficult at times, but you are assuredly on the road to recovery.

I took a look at the instructions in the link in your opening post.  Those instructions only involve Ubuntu approved repositories of approved and tested software.  Those repositories will never contain malware of any kind.  It is *possible* to add malicious repositories, but those instructions do not do so.

As long as you stick to the software natively available through Synaptic (and its command line equivalents) you should be free from the concerns of typical Windows users (malware and the likes).

For now, you may want to concentrate your searches on these forums (until you are better adapted to Linux) for solutions to your issues.  For instance, here is an excellent tutorial for getting audio and video set up on a new system:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

ok it  works fine now...But why did i see a bunch of y's i cant get that out of my head and im 100 positive the key did not get stuck because it did not move in a horizontol...it moved vertical a bunch of times

There were like over 15 y's....Never happened to me in  windows, Must be an xubuntu bug then or a terminal problem...HMmm 

but anyway how do i find out if i am rooted...WIndows destroyed me from the inside sorry if i am typing unnecessary paranoia

---

### Post by jamesisin on 2010-02-15
> **TheDarkSix said:**
> but anyway how do i find out if i am rooted...WIndows destroyed me from the inside sorry if i am typing unnecessary paranoia

You quoted my post but did you read it?

---

### Post by Richard1979 on 2010-02-15
> **TheDarkSix said:**
> ok it  works fine now...But why did i see a bunch of y's i cant get that out of my head and im 100 positive the key did not get stuck because it did not move in a horizontol...it moved vertical a bunch of times

There were like over 15 y's....Never happened to me in  windows, Must be an xubuntu bug then or a terminal problem...HMmm 

but anyway how do i find out if i am rooted...WIndows destroyed me from the inside sorry if i am typing unnecessary paranoia

You are almost certainly not.
What the program probably did was just accept a Y as being Y for every input command.
If you want to be sure that you are installing software the safe way, then use the graphical utility found in System > Admin > Synaptic Software Manager.
Search for Flash and the one you have installed should have a green icon overlayed on it.

---

### Post by gsmanners on 2010-02-16
Most likely some hardware issue or PEBKAC, but if you really want to be sure you haven't been rooted, you will need to use chkrootkit or rkhunter. These can be installed from the repository.

[http://www.chkrootkit.org/](http://www.chkrootkit.org/)
[http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/)

---

### Post by bodhi.zazen on 2010-02-16
> **TheDarkSix said:**
> but anyway how do i find out if i am rooted...WIndows destroyed me from the inside sorry if i am typing unnecessary paranoia

Best to check your Windows paranoia at the door.

Linux is not Windows and Linux security is not the same as Windows security.

If you are interested in security I suggest you start with :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Assuming that any and every problem you have is some kind of virus or root kit will not help you much in either Windows, and much less so in Linux.

No offense, but you are jumping at your own shadow. You are learning a new OS and you do not yet know what "normal" is, and you are assuming anything yo do not understand is a Virus or Rootkit.

---

### Post by Vince N on 2010-02-16
> No offense, but you are jumping at your own shadow. You are learning a new OS and you do not yet know what "normal" is, and you are assuming anything yo do not understand is a Virus or Rootkit.

+1 to that.  Linux is NOT windows.  It does not look the same, function nor behave the same under the hood.  Getting virus's and rootkits is very difficult.  Unless you've added 3rd party repositories (which I doubt, trust me it takes enough doing that you know whats going on) it's almost impossible to get a virus or rootkit.

Everything you've discribed seems to be pretty normal.   Relax, Read some of the links provided in the parent posts and You'll do well. 

I was there once too ;-)

---

### Post by TheDarkSix on 2010-02-16
Ok here are some pics, guess im not rooted 

Edit bodhi.zazen: Picture deleted. Please do not post such huge screen shots, use thumbnails with hot links to larger images. Large images take a ton of bandwidth and some people live on slow connections or limited bandwidth.

---

### Post by jamesisin on 2010-02-16
Looks pretty normal.

Please allow me a moment to discuss some forum etiquette.  Large images embedded directly into posts bork the page layout.  You will want to use thumbnails/links to images.

You can edit your post above, go into the Advanced using the button near the bottom, and you will find a paper clip button in the buttons panel at the top of your edit window.  That will allow you to put up an image without worrying about image size and page layout.

---

### Post by TheDarkSix on 2010-02-16
> **jamesisin said:**
> Looks pretty normal.

Please allow me a moment to discuss some forum etiquette.  Large images embedded directly into posts bork the page layout.  You will want to use thumbnails/links to images.

You can edit your post above, go into the Advanced using the button near the bottom, and you will find a paper clip button in the buttons panel at the top of your edit window.  That will allow you to put up an image without worrying about image size and page layout.

Ok sorry, Also when i got the are you root it also displayed something like  Unable to lock the administration directory (/var/lib/dpkg/), *are you root*? [B].

It said Unable to do something so i wasnt quite sure, But THANKS a lot for all the help:P
[/B]

---

### Post by DrMelon on 2010-02-16
> **TheDarkSix said:**
> Ok sorry, Also when i got the are you root it also displayed something like  Unable to lock the administration directory (/var/lib/dpkg/), *are you root*? [B].

It said Unable to do something so i wasnt quite sure, But THANKS a lot for all the help:P
[/B]

That's just the install thing - you need to type "sudo" before the command to give it root access.

---

### Post by nerdy_kid on 2010-02-16
i have the key sticking thing happen to me every now and then, never figured out what causes it.  but, its rare enough that it doesnt bother me.  The key was probably not stuck, it is a bug of some type.

---

### Post by TheDarkSix on 2010-02-17
> **DrMelon said:**
> That's just the install thing - you need to type "sudo" before the command to give it root access.

i did but in xubuntu it used sudo aptitude so yea thanks for the help once again.

I appreciate the linux community and all communities. 

Microsoft is an evil monopoly...well in my opinion they are i used them for 10 years and got sick of them and when i say sick do i really mean "A grave illness" Security is one of my major concerns

When i used windows i had a fully undetected malware living in it and no matter what i did i even used anti rootkits and hidden process detectors and nothing helped so i needed to reformat and it traumatized my brain...lol at least i can laugh about it

I still feel bad for all the sheep using windows and all the poor people who have no idea what it really is and how unsafe it is you can use a firewall configured to death but there exist "Firewall bypassing" rats and all sorts of crazy malware that not
even i want to know about or hear about...windows never was safe and never will be

Security companies make HUGE profits off of windows security holes...It's a huge business. 

Open source is just the way to go

Also i still have windows on one of my paritions, i used wubi < is wubi vulnerable to anything on windows? i hope malware cannot embed itself in wubi and infect my linux files

---

### Post by TheDarkSix on 2010-02-20
sorry for double post but when i once was trying to figure out how to install flash i entered a line in the 
/etc/apt/sources.list for the flash player...

it didnt do anything and i installed via terminal easily without the help of
the sources.list. I could NOT even save the line with mousepad it gave me an error so i just exited the sources.list and i said to myself "HMM ok i can't add a line??" oh i got a "CANT OPEN FILE TO WRITE" 

im just curious what was the point in the beginning to add a line and it made no sense. 
in the[FONT=Verdana,Arial,Tahoma] repository if all i needed to do was open terminal and type [/FONT]. *sudo apt-get* install flashplugin-nonfree


also is it dangerous to have things added to your sources.list can that
possibly compromise you?

I am just wanting to learn

---

### Post by jamesisin on 2010-02-20
You should never add a repository that you do not both know and trust.  You are giving yourself the ability to download and install applications through that repository.

This post is well commented and trusted around here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It contains these lines:

> IMPORTANT: If you haven't already, you need to enable the Medibuntu repository. The first command below is compatible with any version of Ubuntu, but the manual instructions are aimed at Ubuntu 9.10 Karmic Koala users, so if you are using a different version of Ubuntu, you will have to edit the sources accordingly. If you do have to edit the sources, you can do so by changing the word "karmic" to whatever version of Ubuntu you are running.

Quick Method: Open the terminal (Applications > Accessories > Terminal or KMenu > System > Terminal Program (Konsole) in Kubuntu and Applications > System > Terminal in Xubuntu) and paste the following command into it:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

It becomes a matter of trust at some point.  This is normal in any security situation.  What is the source of truth and who can you trust?

Use your best judgment and think critically.

---

### Post by TheDarkSix on 2010-02-20
> **jamesisin said:**
> You should never add a repository that you do not both know and trust.  You are giving yourself the ability to download and install applications through that repository.

This post is well commented and trusted around here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It contains these lines:



It becomes a matter of trust at some point.  This is normal in any security situation.  What is the source of truth and who can you trust?

Use your best judgment and think critically.

Thanks a lot for the info, but the line for flash i tried to add to the sources.list did not even write to it so i guess it's not a problem. It was instructed i do so on many websites so i really had no idea.

anyway i have 178 avaible updates in my update manager...

nothing seems really that important.

and i made a mistake in the update manager everything was "Checked" by the boxes and i click "Checked" Thinking it would remove the checks from all the boxes but then some update process started but i quickly exited it, everythings okay right?

thanks for all the help once again

---

### Post by jamesisin on 2010-02-21
You should go ahead and run your updates.

---

