---
title: "Converting school to linux"
date: 2011-10-17
forum: General Help
---

### Post by shovenose on 2011-10-17
Hello!
I want to switch our smaller (we have 2) to Linux (as a proof of concept that it works nicely) then hopefully the main one, the library, the teachers, and the entire school district...
but let's focus on this first computer lab shall we ;)

The computers are a mixture of Dell P4/Pentium D with a few HP/Compaq P4 or Core 2 Duo machines. All currently run XP Pro, and are on the school district domain. Each student has his/her own login (based on their first and last names) and a password for the domain (last 5 digits of student id#)

I really want to use Ubuntu for this (not Edubuntu or Kubuntu or otherwise). 
And yes I'm a student at this high school, but I've got authorization to do this conversion, at least of the small computer lab, and if all goes well hopefully I'll be able to demo it to the school district tech people, and they will allow me to do this with more of the school computers.

Anyway, back on topic, how exactly would I accomplish this? I would rather have the clients do as little processing and data storage as possible, and have the user accounts reside on a huge server we can use (it's simply sitting around unused, a huge IBM best)...

I want to mimic the windows XP domain scheme they;re using now, basically have everybody have their own username and password to log in to the server. Thanks for any advice or opinions. Please let me know how to do this!
I already have basic Linux terminal skills, have set up a web server using Ubuntu Server once or twice in the past, and I've got the help of another student there who does linux sys admin stuff professionally, so I can get his help if I'm totally lost (but I rather do it myself lol)
O:)

---

### Post by gsmanners on 2011-10-17
You have a faculty advisor (teacher or principal) to help with this task specifically? That may come in handy at some point.

---

### Post by shovenose on 2011-10-17
> **gsmanners said:**
> You have a faculty advisor (teacher or principal) to help with this task specifically? That may come in handy at some point.
Nope. They are not helpful at all. I'm on my own here I'm afraid.

---

### Post by gsmanners on 2011-10-17
You have some kind of student council? You at least filled out whatever paperwork they might ask of you, right?

---

### Post by fixerdave on 2011-10-17
Lofty goals, you have.  But, eventually, you might get that entire school district switched over.  You might be as old as I am by the time you get there... but they will, eventually, switch.  I've been working on my college for half a decade, or more... Yeah, I support student computer labs for a living.

Putting aside the bureaucratic inertia problem, here are a few other issues you will need to deal with:

1) deployment.  Do you really want to go to each system and install from scratch?  That might be okay for a small lab, but a school district is slightly more challenging.  Any system you build will need to include deployment, and deployment will be your biggest problem.

2) networking.  Where do your IPs come from?  Likely a school DHCP server, and you'll have to piggyback off that.  They won't like you running up your own.  Thus, you'll need to figure out DNS for your clients... they'll need to register with the DNS server... again, probably the main one for the school, or you will have to resort to using IP numbers to talk with systems - not fun.

3) user accounts.  How are you going to make them?  You will need to script this and to do that you will need access to the school enrollment system, or at least extracts of it.  That brings up data security and all kinds of protection of privacy... it gets ugly fast.  Trust me... my Perl scripts make 10,000 accounts a year - the subtleties of this will surprise you.

4) home folders.  Said users will need network home folders to store their stuff.  That will come from your server, but then you will need to get a backup system and maintain it.  Okay, personal network shares aren't entirely necessary these days... but they are nice.

Notice that all of the above are infrastructure... not even talking about the desktop yet.  

So... how about an alternative:  Rather than mimicking the XP domain (Windows AD domain in all probability) why don't you just piggyback off of it?  You know, let those server admins that set it up deal with all that DHCP/DNS/home folder stuff and just let your Ubuntu lab systems just use that.  I believe there is a package you can install (don't remember the project name at this point) that will set up Ubuntu to authenticate off of a Windows AD domain.  You could probably configure it to map the Windows home folder as well.

You can also look into other projects for image (as in hard drive image) distribution instead of doing each one-off.  Clonezilla comes to mind, but I also scanned a project a while back that aims to replicate entire labs... again, don't remember the name.

In other words, what you are doing is entirely possible, but I recommend you take the smallest part - the desktop - and just do that.  Forget about that big old IBM server for now.  Once you get a client playing nice with the existing school infrastructure, maybe take that old IBM and make an image server for deploying your setup - but that would be project #2.

---

### Post by mastablasta on 2011-10-17
You will be doing the deployment of OS (to couple of labs) and you actually don't know how. this should be interesting. oh and good luck, you will need it. :D
 
> **fixerdave said:**
>  
You can also look into other projects for image (as in hard drive image) distribution instead of doing each one-off. Clonezilla comes to mind, but I also scanned a project a while back that aims to replicate entire labs... again, don't remember the name.

 
I am sure Clonezilla has the option of network wide deployment. maybe the best thing would be to use something like it to deploy the OS on more computers at the same time and making usre all have same settings.

---

### Post by Drenriza on 2011-10-17
> You will be doing the deployment of OS (to couple of labs) and you actually don't know how. this should be interesting. oh and good luck, you will need it. 

Deploying the Linux Ubuntu OS is not a problem -.- you can easily do it by creating a script to install the components, or get the clients to connect to a host over the LAN at bootup and get their installation file from their.

Throw me a PM if u need help shovenose

---

### Post by fixerdave on 2011-10-17
More info:

To authenticate Ubuntu on an AD domain:
[https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

The deployment tool I had in mind is this:
[http://www.fogproject.org/](http://www.fogproject.org/)
but it's for deploying Windows clients via linux... no good for what you want.

There are multiple ways to copy a hard drive to another system via the network.  The issue with doing this is that the each target system needs to then be individualized.  Most importantly, the name will have to change, and then there are hardware differences to deal with.  It can get fun - I'd look for an existing solution if I were you.

Another option might be to streamline the install process.  You could probably get Ubuntu to do a scripted install, maybe even build your own Boot DVD/USB drive with every package you want installed.  That way, all you'd need to do at the client is pick a name.

Don't be discouraged... it is possible.  Just get a desktop working the way you want, then worry about the install part later.

---

### Post by fixerdave on 2011-10-17
One more point:

I know you said no Edubuntu... but have you looked at this?
[http://sourceforge.net/projects/ltsp/](http://sourceforge.net/projects/ltsp/)

This is an entirely different approach where the clients just boot into a small client that that then connects to a server, in this case your big old IBM box.  A quick scan of the manual for that says it can be configured to authenticate against an AD domain.

It would make for an entirely manageable project... you've got the box to play with.  Just make sure you're really clear about the DHCP/DNS/PXE/TFTP stuff before enabling any of it, or you'll have really -bleeped- off school Network admins.  Trust me on that one too... I've got one that's rather annoyed with me right now.  Hey, I asked him if he wanted to stress-test the network.  Is it my fault it couldn't handle bittorrenting a 40GB file to 280 computers at once?:-({|=

---

### Post by gsmanners on 2011-10-17
> **fixerdave said:**
> Is it my fault it couldn't handle bittorrenting a 40GB file to 280 computers at once?:-({|=

That is one heck of a download. :popcorn:

---

### Post by fixerdave on 2011-10-17
> **gsmanners said:**
> That is one heck of a download. :popcorn:

Not my fault they want to run Win7 ](*,)
I'm just trying to figure out the quickest way to get it to all the systems in my labs.  The latest try was a multicast FTP... seems to keep Network Operations (the NO! people) happier.

---

### Post by shovenose on 2011-10-17
> **fixerdave said:**
> More info:

To authenticate Ubuntu on an AD domain:
[https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

.
This is genious. I will try this on a test machine.

---

### Post by fixerdave on 2011-10-17
Just noticed the above link is old (from my bookmarks, 8.04... shows the last time I looked at this stuff).  The current link is:
[https://help.ubuntu.com/community/LikewiseOpen](https://help.ubuntu.com/community/LikewiseOpen)

---

### Post by shovenose on 2011-10-19
I had a whole lot of trouble with Ubuntu on the two test computers.
1. Unity was too much for the Pentium 4 CPU with integrated Intel graphics and only 512MB RAM...the computers were significantly SLOWER than with Windows XP, and that's not what I want. 
2. I couldn't get Likewise Open to work.

But then I was like BINGO! I accidentally noticed a Use Network Login button in the CentOS6 installer... OMG IT'S BUILT IN! I'm super happy about this, and I'm going to test it out today...

First we're going to put the computers on the Windows Domain as a proof of concept, then we're going to spread it to everywhere once administration knows it's doable.

Thanks for all the help guys and I'm sure I'll come back later with "CentOS6 works now we have a computer with Ubuntu on it how the heck do I make it work? lol...

---

### Post by gsmanners on 2011-10-19
And if you don't like the help you get here, you could actually call up Microsoft (who have been offering support for CentOS). :P

---

### Post by collisionystm on 2011-10-19
> **shovenose said:**
> Hello!
I want to switch our smaller (we have 2) to Linux (as a proof of concept that it works nicely) then hopefully the main one, the library, the teachers, and the entire school district...
but let's focus on this first computer lab shall we ;)

The computers are a mixture of Dell P4/Pentium D with a few HP/Compaq P4 or Core 2 Duo machines. All currently run XP Pro, and are on the school district domain. Each student has his/her own login (based on their first and last names) and a password for the domain (last 5 digits of student id#)

I really want to use Ubuntu for this (not Edubuntu or Kubuntu or otherwise). 
And yes I'm a student at this high school, but I've got authorization to do this conversion, at least of the small computer lab, and if all goes well hopefully I'll be able to demo it to the school district tech people, and they will allow me to do this with more of the school computers.

Anyway, back on topic, how exactly would I accomplish this? I would rather have the clients do as little processing and data storage as possible, and have the user accounts reside on a huge server we can use (it's simply sitting around unused, a huge IBM best)...

I want to mimic the windows XP domain scheme they;re using now, basically have everybody have their own username and password to log in to the server. Thanks for any advice or opinions. Please let me know how to do this!
I already have basic Linux terminal skills, have set up a web server using Ubuntu Server once or twice in the past, and I've got the help of another student there who does linux sys admin stuff professionally, so I can get his help if I'm totally lost (but I rather do it myself lol)
O:)

You will need a server to control the logins with ldap. I suggest Zentyal. It is based on Ubuntu 10.04. [www.zentyal.com](www.zentyal.com)

I really urge you to use that rather than configure a regular ubuntu server. It will save you time and a lot of headaches.
There is even a program they make to easily integrate Ubuntu Machines into their ldap system. It provides a link to their Shared Network folder, disables terminal access and even supports roaming profiles if you so choose. AND it integrates easily into a Windows Active Directory.

2nd, be careful about your choice of ubuntu on those machines. Not the Ubuntu distro itself, but what version you choose. 10.04 is only supported until 2013 and with the specs of those machines you have, it is probably the only version that will run good on them. Try Xubuntu or Kubuntu on the side.

---

### Post by grahammechanical on 2011-10-19
Ladies and gentlemen, may I say that I am impressed. You people have and are giving good support. Well done!

Regards.

---

### Post by fixerdave on 2011-10-19
> **shovenose said:**
> ...1. Unity was too much for the Pentium 4 CPU

2. I couldn't get Likewise Open to work.


But then I was like BINGO! I accidentally noticed ... CentOS6 ... 

1.  Not being enamoured with Unity, I tried out Lubuntu.  I'm impressed by it's speed.

2. If you go with CentOS, make sure you tell the old people that it IS RedHat but they changed the logos to eliminate the maintenance contract.  

3. Don't forget your third option... using that IBM box for terminal services.  If you get that going, I expect the school board people WILL stand up and take notice.  


I'll end by saying not to get discouraged if things don't just work out of the box.  You are doing enterprise installs here and that adds a whole new layer to what you're doing.   Even installing XP is much harder in an enterprise environment.  It just is.  You are going to have to learn a bunch of new stuff, but you can.  Lots of people do this; it's not rocket science.  But, there is a learning curve, and you're on it.  Hang in there.

---

### Post by ballantony on 2011-10-19
Just as a matter of interest, how many pupils on roll in this school?

---

### Post by shovenose on 2011-10-19
I think it's about 1400. why?

---

