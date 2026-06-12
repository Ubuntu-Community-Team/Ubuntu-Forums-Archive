---
title: "My Usplash only 1/2 works. Please help."
date: 2010-06-19
forum: General Help
---

### Post by theOGRE on 2010-06-19
About a week ago, I noticed that my usplash doesn't do the loading bar (this is with any usplash theme). When I shut down, it works. At boot up, I get the back and forth bar, but when it's time for the loading bar, I just get a black screen with a flashing under score until the gdm login screen appears. I'm sure I am probably to blame, as I am constantly changing stuff.
  Can someone point me in the right direction for debbugging this. What command will show some info about this, or is there some log file I should look to. I would be grateful for any help.

---

### Post by mjgrocks on 2010-07-08
Sorry Im not much help I also posted a usplash post, are we talking about the screen that shows UBUNTU and a moving bar under it, what version are you running.  I hope we can try to figure this out together, because my usplash screen has disappeared

---

### Post by theOGRE on 2010-07-10
Hey mjgrocks, thanks for the reply.  Yes, I  am talking about the same screen, and I'm currently using hardy.  My Usplash always worked, then it just broke out of the blue one day.  The weird part to me is that it loads the ubuntu pic, and does the bar that goes back and forth. My problem starts when the bar should begin slowly filling up. Thats when I get the black screen. Is your's doing the first part?

---

### Post by theOGRE on 2010-07-15
Hey man... give me a link to your usplash post, so I can follow it to. Is the other post getting more action than this one? I also had a problem with my tty[0-6], where they have the same flashing underscore instead of a login prompt.  When I turn off usplash, my tty's work. So I think that what ever is going wrong w/ usplash is screwing up the terminals. How 'bout you, If you push Ctrl+Alt+[F1-F6] does it take you to a login, or a blank screen?

---

### Post by Anxious Nut on 2010-07-15
10.04 is already out, my advice, install it! ... just saying

---

### Post by WorMzy on 2010-07-15
[QUOTE=Anxious Nut]10.04 is already out, my advice, install it! ... just saying [/QUOTE]

Installing 10.04 to fix a bootsplash problem is like sticking your hand down a bear's throat to scratch your nose... just saying. ;)

OP: Have you added any arguments to the end of your kernel line in grub?

And, do you get any options when running

```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by theOGRE on 2010-07-18
Anxious Nut: I use new ubuntu on my machine, but out of everything I tried (including other linux distros) Hardy works best on this old machine. Up until my usplash broke, which is recent, I've had few problems.  This is kind of a learning machine for me, because I don't care if I screw it up, and I can get to know linux a bit before I decide to mess up my new computer. But thanx for the tip homie.

WorMzy:
     Code:
     sudo update-alternatives --config usplash-artwork.so 
I didn't know about update-alternatives. Looks useful.  In this case it listed all of the usplash themes that I have installed, all of which behave the same way. 
As far as the options, are you talking about the `/boot/grub/menu.lst' file? That's where I disabled the splash, and found out that made my tty's work. As soon as I put the `splash' back in the line, the tty's act just like usplash... a black screen with an underscore. I don't know any of the other options. Is there a way to make usplash log some debugging info to a file or something? 

Thanx for the help you guys! :D

---

### Post by WorMzy on 2010-07-18
> As far as the options, are you talking about the `/boot/grub/menu.lst' file?

That was the file I meant, yeah.

I forgot to tell you to run

```
sudo update-initramfs -u
``` after you've changed your splash screen.

I know you said you're constantly changing stuff, but have you modified /etc/usplash.conf, or anything else that requires 'update-initramfs' to be run, recently?

---

### Post by theOGRE on 2010-07-19
No, I didn't know about that file. What should it look like? Thanks again.

---

### Post by WorMzy on 2010-07-19
I'm not sure about Hardy, but on Karmic, my /etc/usplash.conf looks like this: 
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1440
yres=900
```

Obviously it should have your screen resolution, not mine.

I'm not sure what else to suggest, but you could try following this tutorial and see if it helps: [http://www.benjarvis.org/tech/1280x800-console-framebuffer-in-ubuntu-804-hardy-heron/](http://www.benjarvis.org/tech/1280x800-console-framebuffer-in-ubuntu-804-hardy-heron/)

---

### Post by theOGRE on 2010-07-21
Ok. On startup manager it says it's set to 1024x768(my res 1600x900 not an option), but the /etc/usplash.conf says:
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1600
yres=900

Another weird thing is that when I ran `sudo update-initramfs -u', It said it was doing 2.6.24-28 . I use  2.6.24-27-rt. Anyway, I didn't change that file. I do appreciate the help though. Did you catch the part about my tty's not working, unless I disable splash? I know that usplash does some console switching, so I don't know if it is to blame, or if something is wrong with my console. Anytime I get a console error message while building something, or look at a man page, I know my console has problems. Everywhere that should show a back tick (`), I see a lowercase (a) with a (^) on it, followed by some space. 
eg.
 grep understands two different versions of regular  expression  syntax:
       â€œbasicâ€  and  â€œextended.â€   In  GNU grep,  there  is  no  difference in

ok... that's what it looks like if I copy and paste, but on my term it's like ' â     basicâ     '.

I can say ` echo '`' and it works just fine. Well I probably need to make a different post for that.

Keep it comin' if you got more. I thank you for your time.

---

### Post by WorMzy on 2010-07-22
Sorry, I've got no more suggestions. All I can offer is a free topic bump and the hope that somebody else with more experience with this kind of problem can help you find a solution. :)

---

### Post by theOGRE on 2010-07-22
Well thanks for the replies anyway. I wonder if it has anything to do with it building 2.6.28 instead of the one I'm using: 2.6.27-rt? Anyways, I'm kind of just messing with this in my spare time, because the usplash means less to me than using the tty's, so I just boot with no splash for now. If I happen to figure it out, I'll post back for anyone else. But I don't think anyone else is having this problem, or I would have found an answer when I searched originally. I'm making a seperate post for help with my terminal problem, and maybe the two will tie together.
 By the way, what's the beans thing all about? Thanks man.

---

### Post by WorMzy on 2010-07-23
Yeah, that seems odd to me too (the kernel thing), does booting from the other kernel make any difference?

beans = posts; I've never understood it myself, but I think it's got something to do with coffee, since Ubuntu (the philosophy which Ubuntu is named after) comes from Africa, which also exports a large percentage of the world's coffee beans.

Or something.

---

### Post by theOGRE on 2010-07-24
Yes actually, it does make a difference. When I boot from the 2.6.24-28 it shows the first part of the splash, then the blank screen. The difference is that the picture is misaligned where part of it wraps around to the other side. 

'update-initramfs -u -k $(uname -r)' Updates the current kernal.
I wish I knew what to do with this. Reinstalling usplash doesn't do it. Oh yeh!. I just remembered what I did that probably messed it up! Around the time this started, I wasn't messing with usplash, but I was messing with imagemagick. if you try to uninstall imagemagick, it says it will also remove usplash and startup-manager. I did that and then built imagemagick from source( I need a newer IM). After building it I saw that synaptic wouldn't notice my imagemagick, it thought I still needed it for startup-manager and usplash. I just reinstalled usplash, startup-manager, and imagemagick. I bet anything that's when it happened. usplash requires IM, and mine is a little screwed up.

Ok, new question. How do you get your package manager to notice programs that you build from source? You know, for meeting dependencies and such. That's probably what I need.

---

### Post by WorMzy on 2010-07-24
I'm not sure. I think you'd probably need to convert the make'd stuff into a .deb, then install it via dpkg. But how you'd do that, or if it'd work, I have no idea.

Your best bet is to look for a repository with the version of IM that you need (best place to look is [launchpad]("https://launchpad.net/")), and add it to your software sources. Then do 'apt-get --purge imagemagick', followed by 'apt-get update', followed by 'apt-get install imagemagick'. If the version in the custom repos is more recent than the version in the normal repos, then it should install the newer version.

---

### Post by theOGRE on 2010-07-25
Thanks man, I'll try that out. Didn't know about the purge option.

---

### Post by theOGRE on 2011-01-23
I'm marking this as solved. I never solved it, but I changed my setup so it is no longer a problem.

---

