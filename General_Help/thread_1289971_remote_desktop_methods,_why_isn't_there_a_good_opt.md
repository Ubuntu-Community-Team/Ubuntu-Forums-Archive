---
title: "remote desktop methods, why isn't there a good option!?"
date: 2009-10-13
forum: General Help
---

### Post by lordofduct on 2009-10-13
(warning this is both a rant and also a question in that if anyone knows of OTHER options then I am OPEN to any suggestions to play around with)

Ok, so this is something I've been toying with for years now. And I've played with several different methods. Remote Desktops in Ubuntu (or linux in general) just come with so many weird and awkward issues... despite the network capabilities of X itself! It's aggrivating.

Sometimes I set up a certain thing just to see that it can be done. Other times I want something for actual use.

And it's really annoying because when it comes down to brass tax most options blow donkey.

A run down:


--ltsp (linux terminal server project) - this is really cool. The first I played with it was when edubuntu came out and it was designed as a thin-client server (I don't know if this is their default objective with edubuntu today, but it was when I used it). A little annoying to get set up, and PXE is awkward at times (especially at the time I used it when PXE or other netboot methods weren't as common on mobos). Thing is from an end-user point of view it's not that useful. It's got its uses yes, but really the user-base for this type of thing is really tiny. Most people don't need a bunch of thin clients around the house very much. Except maybe as media clients or something...


--xdmcp (X-display manager control protocol) - this thing is a freakin' headache and a half. Getting it to actually function properly is arduous and boring to say the least. The controls through the Ubuntu GUI really aren't all to helpful either... I usually end up getting as far as getting to the login screen that is jarbled, or worst black with a X as a mouse cursor.

My biggest complaints with both of these as well is that they act as sessions. Which means you have to log out of your current session and log into these (ltsp being the most annoying to start a session on as you have to netboot into it). As remote desktop goes, these options are way to complex, convoluted, and really not to useful in the end.



--VNC (or any other version there of, tight, lite, uber, pooper, whatever) - I don't know who the hell thought up the asinine idea of incorporating VNC into LINUX! What in the heck is wrong with you!?

let me step back for a second. I use VNC, it works... it's so freakin' easy to set up and just freakin' works. Even if you want to tunnel through ssh it still freakin' works! A moron can use this... my brother Mark (who doesn't even know what linux is) can use the thing... it's that easy.

And that's what sucks... it's the ONLY easy choice. But as functionality goes, it SUCKS. Who here has used it on a regular 100 Mbit network? It crawls... it freakin' just crawls. I've only used it over the internet once... won't ever try that again. Oh wait, my friend and I also logged into it through his iPhone once... oh God... VNC over G3 is excruciating!!!!

What blows my mind is people though this was a good idea. Let's take "screenshots" of the desktop, compress them, and send them over the network! How... childish. I mean yeah if you don't really have any API or interface to attach to this works. But it's slooooooowwwwwwwwwwwwwwwwww. It makes me want cry.

And that's thing, an API does exist. X-windows has it built in! It's right freakin' there.

oh yeah, x has it built in... so next up:


--ssh x-tunneling - this option is really freakin' cool. I love it. I freakin' love it. But I have issues with it. Ok, if I want to do stuff just in the terminal, I ssh like a mo#######r. But the x-tunneling... oh dear here is where I start to get annoyed. Though my big annoyance is the "gnome/kde" battle crap. All right I like gnome, it's simple, it's nice, it's to the point for the most part. KDE is just to much for me, it feels like it's trying to be OSX (or OSX is trying to be KDE, whatever). But that's not here or there. Thing is application wise I like gui's for certain tasks, sometimes gui's are really necessary... hence the x-tunneling. But some applications are just really grrrrr about only supporting kde or gnome. I like rhythmbox which is gnome, I hate azurachahowever (sp?) bloated piece of crap... which is KDE. But I also like ktorrent as my torrent manager... it has some cool features. But to run it you need this package or that package and other crap.

Now the machine I have ktorrent on is the machine I want to work on remotely... it's where my large network storage is as well and all that. It makes sense to run it over there. But I can't x-tunnel it because I don't have the kde packages it needs on this machine.

Lastly ssh x-tunneling doesn't really perform well in starting a desktop session of any sort. And I like having desktops, it's a nice visual clarification of where this application is. I use a lot VMs for windows and solaris, and it just feels nice and streamlined to me. Hence my use of VNC, which crals. Oh but wait, you can... that's next.


--ssh x-tunnel session (you can access this through the login window) - you can log in via ssh and start a remote session directly through the login screen (and why this isn't shown off is beyond me... this functions so much nicer then xdmcp). But this comes with issues as well. It's its own session... I have to logout of my current session to log into the ssh tunneled session.

I don't like this changing sessions crap. LIke I said I run virtual machines left and right. I usually have about 4 or 5 VMs open at any time running different operating systems. The idea that to get to my server I need to start a new session just aggrivates me... so step in VirtualBox


--ssh x-tunnel session through a VM - this is just like the last one. Only I run a virtual machine. It's kind of just a stupid hack way of getting a session started on my server quickly and easily on a remote machine. And it works great. It's what I'm going to stick to for now over VNC (just started doing this today) as it is speedy and smooth, and I just freakin' love it. Most importantly I don't have to be logged in on my server... the server just has to be ON. YEY!!!!

But wait, I got a gripe... it's a freakin' virtual machine. Damn it those aren't resource friendly. They take up quite a bit of space on my machine... you need a bit of space for the virtual hard drive, you need to intall linux on the thing, and it just grrrrr. It needs to emulate a processor and video card and sound, and all that crap. It's overkill.

Luckily my machine can handle the overkill. I have the intel i7 chipset and 12 gigs of RAM. So it's not like I'm pressed for resources... but still. Just because you drive a corvette, doesn't mean you should burn 2 miles a gallon all the time just because you can.

(you can also consider a virtual machine thin client using xdmcp or ltsp here as well... it's essentially the same thing just with the modification of the complaints for each one from earlier).




And the griping continues.

X-ming - when I was on Windows I learned about X-ming. It played around with it as it was pretty novel. And I ATTEMPTED to use XDMCP with it... which sucked. But ssh x-tunneling was great! Best of all, it supported its own desktop WINDOW! Oh yes... a freakin' window to contain all my remote applications in like its own little virtual desktop.

And the best part... it wasn't a damn virtual machine emulating all the little parts of a freakin' computer. It was light weight and light on the resources.

Why don't we have that!? Why doesn't linux have that. X-ming is a freakin' x-windows for Windows. What the hell... Ubuntu has X-windows built into the freakin' thing. It's there, it's ready to go, why can't I open a freakin' window and start a freakin' remote ssh tunnel session right there.

Why not?

Or can I?

Am I ignorant? Is there actually something out there already that does this? Please tell me there is... my big concern though is the package dependencies though. Because I could ssh x-tunnel say ktorrent on this machine. But that means installing kde packages on this machine. And i don't really want the kde package global wide on this machine. They cause weird issues... namely a lot of bloated nonsense is included in those packages. I never start kde sessions, I just happen to run some kde applications on my server. Why can't we have some type of nice little contained x-windows session manager dealy. Something that I can put the kde, gnome, and other dependencies into and run stuff through... very similar to x-ming. weeeeeee. But I don't even need that, if I had to have all the dependencies installed globally, I'll do it... as long as I could have a nice contained virtual desktop window of some sort.



So who here shares my complaints!?

---

### Post by cybergalvez on 2009-10-13
give NX a try, either the free version from noMachine or FreeNX, they work great!

---

### Post by StuartN on 2009-10-13
> **lordofduct said:**
> Lastly ssh x-tunneling doesn't really perform well in starting a desktop session of any sort. And I like having desktops, it's a nice visual clarification of where this application is.

Can you please explain how to get a desktop session using ssh x-tunneling?

I often use **ssh -X my_other_machine.local** and run graphical applications, which works really well. I don't know how to get my_other_machine's desktop to appear - every method I tried bombs out in error messages and messes up my local desktop. Apparently it works really well without any Gnome etc, just plain X.

---

### Post by 3rdalbum on 2009-10-13
I haven't used X-Ming, but I think you'll want to look at Xnest or Zephyr.

I don't know what your gripes are with SSH -X, or VNC. X tunnelling works fine for me. Performance is good, and as long as I know what terminal command will launch my programs, all is fine. It's kinda neat that any remote programs can still access the notification area of the client.

VNC is slow to start, but once running the performance is good enough over wireless G to allow me to surf the 'net on my server. The server runs Compiz.

Honestly, I don't have any complaints about remote desktop methods on Linux. I haven't tried XDMCP or LTSP so I can't comment there. The only thing I'd change about SSH -X is that I'd like to be able to connect to already-running programs, and reconnect to running programs if I got disconnected. But that's what I use VNC for.

---

### Post by StuartN on 2009-10-13
I really hate VNC, mostly because it works so well.

Someone in the accounts department of a major utility told me that they leave VNC running all the time, with an employee's name for the password and, hooray!, they can access the customer relations database on their secure server from anywhere, even home.

That is why I hate VNC.

---

### Post by lordofduct on 2009-10-13
> **3rdalbum said:**
> I haven't used X-Ming, but I think you'll want to look at Xnest or Zephyr.

I don't know what your gripes are with SSH -X, or VNC. X tunnelling works fine for me. Performance is good, and as long as I know what terminal command will launch my programs, all is fine. It's kinda neat that any remote programs can still access the notification area of the client.

VNC is slow to start, but once running the performance is good enough over wireless G to allow me to surf the 'net on my server. The server runs Compiz.

Honestly, I don't have any complaints about remote desktop methods on Linux. I haven't tried XDMCP or LTSP so I can't comment there. The only thing I'd change about SSH -X is that I'd like to be able to connect to already-running programs, and reconnect to running programs if I got disconnected. But that's what I use VNC for.

I didn't say I had any problems with using ssh with x-tunneling in the idea of using the terminal, or running single applications. My complaint is as a remote desktop it sucks. You can't start a self contained desktop to use as a remote desktop.

As for VNC's performance... I really want to know what you're talking about. Because in my opinion, it crawls. It does just that... crawls at a meager 10 or 15 fps... sometimes even less. The mouse sometimes has a hard time keeping up with local mouse. With all the other options and programmatic APIs available out there (most notably the network client-slave relation of X-server) VNC is the most childish piece of software. I get its existence, but the fact it is so widely popular blows me over... the fact ssh and x-tunneling (with advanced features) hasn't really been developed on... but VNC goes on as popular as ever just blows me away! Especially with remote desktopping becoming so prevalent over the internet, I mean come on... you have to admit VNC is slow, bandwidth heavy, and impractical as a remote desktop protocol.

Furthermore I don't like VNC because when dealing with multiple users it gets even more annoying. Say I try to login when someone is using the machine, we can't quite share the desktop... and the user hosting a vnc server has to be logged in. This causes for issues. In this instance I prefer ssh and x-tunneling because I can log in as "userX" while someone else is still working as "userY" and yet another person can remotely log in as "userZ" and so and so forth. VNC can't really handle this all to well.

I can't imagine how a company or corporation deals with it with VNC when me in my own home and network of maybe 7 computers can barely deal with the BS. I couldn't tell you how many times my girlfriend gets bothered because she can't log into the computer in the other room to do something because I'm already remotely connected via VNC. Of course this is resolved now with my hacky virtual machine and ssh tunneled session. I just want an even better option.


> Can you please explain how to get a desktop session using ssh x-tunneling?

as for the question about running ssh with x-tunneling... my point was that a self contained desktop window isn't available directly with just ssh. You can login to a session from the login screen and have a desktop (but it means logging out of your current session).

All that needs to be set up is an ssh-server on the host side. And on the client when you boot up and are at the login screen click "options" and select "login via remote ssh" or something like that. It will ask for the IP address of the host, and then the password for the user you're trying to login as. And then it's done.



> give NX a try, either the free version from noMachine or FreeNX, they work great! 

oh yeah I forgot about freeNX and the sort. It's been years since I played with it. I should check that out again.


My whole point of this post though is all about how the most common and most well known options are pretty damn crap. I had forgotten about NX and that is basically what I'm talking about. It is an actual window based remote desktop utilizing X-server and ssh to create remote sessions contained inside an already running session while giving the look and feel of a normal desktop inside of a desktop. This is a very important thing to me, as I've stated in my earlier post, I run numerous Virtual Machines all day, bouncing between different operating systems for different reasons (some software I need for development is windows only, or I want to debug something new I made to make sure it runs outside of Ubuntu, etc etc). And every time the disucssion of remote desktopping comes up I'm always blasted with the suggestion of VNC or SSH with simple x-tunneling. Both of which are just feable and lackluster... and everyone is like "I think it's great"... really? REALLY? They aren't. They are ok, well ssh is all right (VNC sucks). But beyond simple tasks ssh just doesn't cut it. I'm sorry kids, but it's 2009, terminals and command prompts are long gone for users who expect to get anything done. Terminal for me is about restarting some servers or some low level system management, but beyond that I want a freakin' gui. I have enough damn terminology and syntax memorized in my head... I've learned numerous languages from C, C++, C#, Java, Python, PHP, ruby, AS3, etc... I really don't feel like dealing with yet more syntax to do what everyone can freakin' do via a damn gui now a days.

So yeah... thanks cybergalvez for reminding me of NX.

---

### Post by lordofduct on 2009-10-13
to give you a visual idea...

with out self contained windows tell me how I'd sort all three of these sessions inside my already running session:

[IMG]http://img.photobucket.com/albums/v333/lordofduct/MessBoard/remotes.png[/IMG]

With regular old ssh or vnc this here becomes a nightmare.

---

### Post by driftingprogrammer on 2009-11-05
Totally agreed, i want to have the flexibility of starting my *desktop* session on my **computer** and be able to see the same *desktop* from my **laptop** while some one else is using the **computer**.

I install _vista_ i get this setup by default, probably spend 2 minutes for activating the RDP....

I install Ubuntu, firstly what i am asking for is not possible, so i end up opening a VNC session to a new *Desktop* while i am on the **computer** (instead of just using the machine i am sitting in front of, i have to vnc the machine from that very same machine, ridiculous hack which took a month to setup, as a side note tightvnc sucks, vnc4server is totally stable) which i can then VNC from my **laptop** as well later on when my girlfriend is on the **computer**...

---

### Post by n2stc on 2010-01-17
LOL!  I don't know if I share your complaints, but I sure got a chuckle from you post.  Thanks!  

BTW:  Ever find a good solution?

---

### Post by driftingprogrammer on 2010-01-20
NX is definately a much better option then VNC...still the hack remains, while sitting on the computer i have to open a nx session to the computer instead of just using the machine desktop.

---

