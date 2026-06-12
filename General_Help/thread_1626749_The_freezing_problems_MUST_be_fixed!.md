---
title: "The freezing problems MUST be fixed!"
date: 2010-11-20
forum: General Help
---

### Post by ivarn on 2010-11-20
Ok so there are at least 3 threads about 10.04/10 problem here on ubuntuforums, and as much as I love ubuntu and linux in generally I really wish this problem will be fixed soon.
They both work fine at first but after a few updates and stuff they started freezing and hanging.. Now I am back on 10.04 after I tried 10.10 for a few weeks for some odd reason.
What happened to "Linux is faster and gives you less pain than Windows"?
With all this freezing and stuff, we can't say the same anymore.
People are having these random freezing and hangup problems with not only the new ubuntu distros but the new mint 10 and suse as well.
I mean common guys, what the hell is going on here?
What will happen is a Windows user goes from Windows to these new buggy versions of linux? I am not saying this to sound like I am against Linux or anything, but simply because something just needs to be done right freaking now.
There are literally 100 different people posting on these threads I was talking about, and they are probably not even 10 procent of all the people who are using these distros.

People have tried everything from different kernels, disabled gfx, etc.. but no luck.
What I am saying is, this is a frustrating problem.
Linux is on a very early stage and more and more people are changing from Windows, and just imagen if they discover all these problems? They will go right back to windows and they will never try linux ever again.
I mean, spyware and viruses are nothing compared to random freezing and frustrating hang ups all the time.
I know some people are probably working on this but I can't stress this enough. 
This should (or must) have first priority.
Remember, most of us are normal everyday people, and not beta testers for something new and undiscovered. Because that's how it feels sometimes.
Again, this is not a hate message or anything. I just want to push things forward.

---

### Post by blazemore on 2010-11-20
I guess you'd better get on it then!
We're rooting for you.

---

### Post by ivarn on 2010-11-20
> **blazemore said:**
> I guess you'd better get on it then!
We're rooting for you.
Did you even read the post?
As I said in the last line 
> Again, this is not a hate message or anything. I just want to push things forward.I said that because I knew some people would post idiot messages like that.

---

### Post by Queue29 on 2010-11-20
Works For Me [SIZE="3"]™[/SIZE]


Seriously though, do you really think making a thread like this is productive in any way, shape, or form? If you want to push things forward, submit some patches, some debugging information, or at the very least, your hardware specs and a real description of what is wrong.

---

### Post by oregonbob on 2010-11-20
I've been working on PC's for many years. Anytime I get freeze-ups it is almost always **hardware failure** - motherboard or memory. My first guess would be memory. Once in a while it is bad sectors on a hard disk.

---

### Post by garvinrick4 on 2010-11-20
I do not seem to be able to reproduce these problems you have all the time.
I try to keep my installs all updated and run to check dependencies (dpkg --configure -a)
keep the file systems clean (fsck). In older versions and Alpha versions I maintain my installs. 
As well as I do in Windows that came with machine by chkdsk and defrag commands. 
There will always be some minor problems in all Operating Systems but I firmly believe 
the secret is in maintenance and how to run minor fixes,  or as some call it learning.
  I usually just ignore these posts most likely should have again.

---

### Post by ivarn on 2010-11-20
Thanks. That's all good and well, but I am more afraid of what noobs to linux would say when the first thing they got was freezing problems, and since this is a problem multiple people have gotten into, I'm afraid Windows users will stick to their old windows system instead of doing all the tweaking and fixing to repair all the freezing bugs.
I first thought it had something to do with memory but I have 4gb of ram. I have checked many different kernels, disabled the nvidia card and spent so much time with this.
Maybe I should have been more specific when I said freezing, but I thought you already knew what I was talking about.
Ok so it sometimes freezes when I do things quickly such as typing, browsing or open a program. It can freeze for only a few sec or up to a minute. Frustrating enough since this happens almost all the time.
Someone in one of the threads said something about a firefox's script causes the freezing problem when I scroll and text in firefox, and that's the only issue I have successfully solved by using Google Chrome instead.
This is a bug only in the 3.0 series of firefox according to him.

---

### Post by linux18 on 2010-11-20
```
 rm -r $HOME/.config &&  sudo dpkg-reconfigure -a && sudo aptitude -f install && sudo update-grub 
```

---

### Post by 3rdalbum on 2010-11-20
> **ivarn said:**
> 
I first thought it had something to do with memory but I have 4gb of ram.
Maybe I should have been more specific when I said freezing, but I thought you already knew what I was talking about.

Have you taken out the RAM sticks one at a time to see if it is faulty memory? It doesn't matter if you have lots of RAM - one module can crash the computer.

---

### Post by ivarn on 2010-11-20
> **linux18 said:**
> ```
 rm -r $HOME/.config &&  sudo dpkg-reconfigure -a && sudo aptitude -f install && sudo update-grub 
```
What the hell was that suppose to fix?
Now I have to change my start menu, startup menu and all the dumb settings again. So thanks.
Well, thank you if it actually fixed something though but damn, so much work I have to  do now. Is there a backup of that config file here somewhere?

---

### Post by ivarn on 2010-11-20
> **3rdalbum said:**
> Have you taken out the RAM sticks one at a time to see if it is faulty memory? It doesn't matter if you have lots of RAM - one module can crash the computer.
No, is that possible to do from ubuntu?
I don't know where in the pc they are, also I don't think I wanna mess around with that stuff. Sounds "scary".

---

### Post by oregonbob on 2010-11-20
> **ivarn said:**
> since this is a problem multiple people have gotten into

Wow, multiple people have the same freeze ups, and maybe should go back to Windows? [Uh huh, like this freeze]("http://www.google.com/search?source=ig&hl=en&rlz=&q=windows+7+freezes&btnG=Google+Search&aq=4&oq=windows+7+fr")

Take out all your RAM. Try putting back different ones as first socket, and so on. You need to run an all-night memory test. I seriously doubt it is anything Ubuntu. More than likely it is your hardware.

---

### Post by Artemis3 on 2010-11-21
When you ask support about freezing issues, one of the polite things to do is tell us which hardware you have.

---

### Post by CharlesA on 2010-11-21
OP: Are you actually looking for support, or just here to vent?

---

### Post by ivarn on 2010-11-21
so how do I check the ram thing?
I heard about a new kernel patch that will fix these issues people have been dealing with lately. hope it will be release for ubuntu soon.

---

### Post by CharlesA on 2010-11-21
Run memtest86+

It should be listed in the GRUB menu, which you can access by hitting shift.

---

### Post by cd-r80 on 2010-11-21
Freezing problems

1 Hour Ago
by nunrgguy Go to last post
	1,325 	188,717

This freezing problem is just not someones memomory module problem.

Soon 200 000 views...

---

### Post by CharlesA on 2010-11-21
> **cd-r80 said:**
> Freezing problems

1 Hour Ago
by nunrgguy Go to last post
	1,325 	188,717

This freezing problem is just not someones memomory module problem.

Soon 200 000 views...

It helps to not be so cryptic.

Link: [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

---

### Post by HermanAB on 2010-11-21
Well, if anyone would actually bother to read the other freezing threads, then you'd notice that most of the problems are due to bad Nvidia video drivers and that it can be fixed by using the Vesa driver.  

All the Nvidia drivers are bad on my hardware, including the official Nvidia driver from the Nvidia web site, so I have been using the Vesa driver for almost a year already.

---

### Post by ivarn on 2010-11-21
Ok I finally found the kernel patch and guess what, it fixed everything.
Thank you everyone for helping me, so in-case you haven't seen the fix yet, here it is.
Btw, I found it on webupd8.org and this method will only work on ubuntu 10.04 and 10 distros.

Add this to your /etc/rc.local file (sudo gedit /etc/rc.local)
Code:
mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

and make it executable
Code:
sudo chmod +x /etc/rc.local

And then add the following to your ~/.bashrc file (to open it: gedit ~/.bashrc):
Code:
if [ "$PS1" ] ; then  
   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

Run the following command:
Code:
sudo gedit /usr/local/sbin/cgroup_clean

And paste this:
Code:
#!/bin/sh
rmdir /dev/cgroup/cpu/$*

then save the file and make it executable:
Code:
sudo chmod +x /usr/local/sbin/cgroup_clean

And finally, restart the computer or manually run the /etc/rc.local file ("sudo /etc/rc.local").

---

### Post by edward1978 on 2010-11-21
> **ivarn said:**
> Ok I finally found the kernel patch and guess what, it fixed everything.
Thank you everyone for helping me, so in-case you haven't seen the fix yet, here it is.
Btw, I found it on webupd8.org and this method will only work on ubuntu 10.04 and 10 distros.

Add this to your /etc/rc.local file (sudo gedit /etc/rc.local)
Code:
mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

and make it executable
Code:
sudo chmod +x /etc/rc.local

And then add the following to your ~/.bashrc file (to open it: gedit ~/.bashrc):
Code:
if [ "$PS1" ] ; then  
   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

Run the following command:
Code:
sudo gedit /usr/local/sbin/cgroup_clean

And paste this:
Code:
#!/bin/sh
rmdir /dev/cgroup/cpu/$*

then save the file and make it executable:
Code:
sudo chmod +x /usr/local/sbin/cgroup_clean

And finally, restart the computer or manually run the /etc/rc.local file ("sudo /etc/rc.local").

Hmmm, no way to just download the fix? Well. hope I don't mess my system up. Some post said some one fixed it by not using Gnome, I tried XFCE4 & it froze. :(

> Thanks. That's all good and well, but I am more afraid of what noobs to  linux would say when the first thing they got was freezing problems, and  since this is a problem multiple people have gotten into, I'm afraid  Windows users will stick to their old windows system instead of doing  all the tweaking and fixing to repair all the freezing bugs.
I first thought it had something to do with memory but I have 4gb of  ram. I have checked many different kernels, disabled the nvidia card and  spent so much time with this.
Maybe I should have been more specific when I said freezing, but I thought you already knew what I was talking about.
Ok so it sometimes freezes when I do things quickly such as typing,  browsing or open a program. It can freeze for only a few sec or up to a  minute. Frustrating enough since this happens almost all the time.
Someone in one of the threads said something about a firefox's script  causes the freezing problem when I scroll and text in firefox, and  that's the only issue I have successfully solved by using Google Chrome  instead.
This is a bug only in the 3.0 series of firefox according to him.

Froze in Chrome with me also. Plus, could I not just disable scripts in FF & get the same result?

---

### Post by ivarn on 2010-12-02
The problem came back, but not as jerky as it was.
To be more specific about this problem, everything freezes when I am working on more than one thing at the same time, when I use apps that takes more CPU (I.e songbird).
It's very lagy on hd and full hd videos. And by lagy I mean it's like when you watch a youtube video and your connection is bad it starts buffering, so the video pauses.

OK, how can this be a hardware problem, really?
People are complaining about these problems on this forum and have been doing it for quite some time now.
This isn't funny and we need a REAL fix here.
The 20 line kernel patch made things better (on websites without flash and stuff).
Youtube is still a pain when I watch a video and when I scroll up or down the page.
Before I installed the kernel patch it even got lagy sometimes when I typed.
Now, it still gets a little bit lagy a few times but not a big deal.
When I am in flash and write (ustream chat), it's sometimes horribly painful but I assume this is a flash problem and not ubuntu.
Ok so now, are there any real fixes out there that can help me with at least one of these things?

EDIT: The newest kernel made things more lagy (can't remember the version).
But the kernel I used before I updated to the new one worked way better, so do any of you guys know what version that was?
I was stupid and removed it from grub :/

---

### Post by mouldy on 2010-12-02
> **ivarn said:**
> The problem came back, but not as jerky as it was.
To be more specific about this problem, everything freezes when I am working on more than one thing at the same time, when I use apps that takes more CPU (I.e songbird).
It's very lagy on hd and full hd videos. And by lagy I mean it's like when you watch a youtube video and your connection is bad it starts buffering, so the video pauses.

OK, how can this be a hardware problem, really?
People are complaining about these problems on this forum and have been doing it for quite some time now.
This isn't funny and we need a REAL fix here.
The 20 line kernel patch made things better (on websites without flash and stuff).
Youtube is still a pain when I watch a video and when I scroll up or down the page.
Before I installed the kernel patch it even got lagy sometimes when I typed.
Now, it still gets a little bit lagy a few times but not a big deal.
When I am in flash and write (ustream chat), it's sometimes horribly painful but I assume this is a flash problem and not ubuntu.
Ok so now, are there any real fixes out there that can help me with at least one of these things?

EDIT: The newest kernel made things more lagy (can't remember the version).
But the kernel I used before I updated to the new one worked way better, so do any of you guys know what version that was?
I was stupid and removed it from grub :/

Youtube (or any website that relies on flash for that matter) is a pain because it uses flash. Flash player on linux isn't as polished as it is on Windows - and it's pretty bad on Windows. I don't know if they still do it, but youtube used to offer a lot of videos using HTML5's video tag, so you might have a better experience using that instead.

The fix you posted looks like the user-space version of the 200 line kernel patch people were raving about a few weeks ago. It might help a bit, but there's been a bit of a mixed reaction to it.

Despite being asked a few times, you still haven't provided us *any* details about your system. What hardware. What version drivers you're using. What version kernel you're using. What kernel modules are loaded. etc etc. Vague stuff like "The newest kernel made things more lagy (can't remember the version). But the kernel I used before I updated to the new one worked way better" is not at all helpful to anyone. If you're unable to help out by writing patches yourself, you could at least help people help you by providing useful information instead of just complaining and vague information.

---

### Post by ivarn on 2010-12-02
> **mouldy said:**
> 
Despite being asked a few times, you still haven't provided us *any* details about your system. What hardware. What version drivers you're using. What version kernel you're using. What kernel modules are loaded. etc etc. Vague stuff like "The newest kernel made things more lagy (can't remember the version). But the kernel I used before I updated to the new one worked way better" is not at all helpful to anyone. If you're unable to help out by writing patches yourself, you could at least help people help you by providing useful information instead of just complaining and vague information.

Ok thanks. As I said in the last post, I don't know what kernel version I have, hardware and hardware versions and all that. Ok I can reboot and grub will give me the kernel version, but is there a terminal command or something that will give me what you need here?

---

### Post by ivarn on 2010-12-03
BUMP

Also. flash isn't a pain, but scrolling on pages with flash sucks.
And let me tell you, flash is a bigger pain in Windows Vista and 7. For some reason everything worked smoothly in Win XP.
Oh well. things like that makes me glad (sort of). 
More an more people are ditching windows for either mac or linux.
Now, where was I? Oh yea, BUMP!

---

### Post by Sxynerd on 2010-12-04
I am running 10.10 and have been having issues playing .mov files as well as youtube videos.  The full HD .mov files are unwatchable and the youtube vid problem seems to come and go.

Is this the same issue as the OP's? I have an Nvidia card and this problem only just started happening after I updated my system.  I've started a thread about it but I just keep hitting a brick wall.  I've re-installed my OS twice now trying to get the problem to go away with success in the beginning but eventually it goes back to being all messed up.

---

### Post by ivarn on 2010-12-05
> **Sxynerd said:**
> I am running 10.10 and have been having issues playing .mov files as well as youtube videos.  The full HD .mov files are unwatchable and the youtube vid problem seems to come and go.

Is this the same issue as the OP's? I have an Nvidia card and this problem only just started happening after I updated my system.  I've started a thread about it but I just keep hitting a brick wall.  I've re-installed my OS twice now trying to get the problem to go away with success in the beginning but eventually it goes back to being all messed up.

Well, you can actually solve that problem.
Have you installed bot the libdirac-encoder0 and libdirac-decoder0 packages?
I Know one of them came with ubuntu-restricted-extras, so you should check synaptic and see if you got them both. Also, the new version of blender solved a few problems for me, but I'm afraid you have to download it from the website since synaptics version is old.

Now back to my issues on the subject. I still don't know how to get all the hardware info u guys need in order to help me with this. 
And also a problem I forgot to mention, is that folders with a lot of files takes forever to load.

---

### Post by IndyGunFreak on 2010-12-05
> **ivarn said:**
> Ok so there are at least 3 threads about 10.04/10 problem here on ubuntuforums, and as much as I love ubuntu and linux in generally I really wish this problem will be fixed soon.
They both work fine at first but after a few updates and stuff they started freezing and hanging.. Now I am back on 10.04 after I tried 10.10 for a few weeks for some odd reason.
What happened to "Linux is faster and gives you less pain than Windows"?
With all this freezing and stuff, we can't say the same anymore.
People are having these random freezing and hangup problems with not only the new ubuntu distros but the new mint 10 and suse as well.
I mean common guys, what the hell is going on here?
What will happen is a Windows user goes from Windows to these new buggy versions of linux? I am not saying this to sound like I am against Linux or anything, but simply because something just needs to be done right freaking now.
There are literally 100 different people posting on these threads I was talking about, and they are probably not even 10 procent of all the people who are using these distros.

People have tried everything from different kernels, disabled gfx, etc.. but no luck.
What I am saying is, this is a frustrating problem.
Linux is on a very early stage and more and more people are changing from Windows, and just imagen if they discover all these problems? They will go right back to windows and they will never try linux ever again.
I mean, spyware and viruses are nothing compared to random freezing and frustrating hang ups all the time.
I know some people are probably working on this but I can't stress this enough. 
This should (or must) have first priority.
Remember, most of us are normal everyday people, and not beta testers for something new and undiscovered. Because that's how it feels sometimes.
Again, this is not a hate message or anything. I just want to push things forward.

I've got Ubuntu 10.10 on my home machine, and "monitor' problems on two others(family).. and have not encountered a freezing problem one time since they were installed.

It's a priority, because it affects you... but it doesn't seem this is a huge, widespread problem.

---

### Post by edward1978 on 2010-12-05
> **IndyGunFreak said:**
> I've got Ubuntu 10.10 on my home machine, and "monitor' problems on two others(family).. and have not encountered a freezing problem one time since they were installed.

It's a priority, because it affects you... but it doesn't seem this is a huge, widespread problem.

Do you have flash installed? Can you provide hardware specs.? Info like in my sig.

---

### Post by frogotronic on 2010-12-05
> **ivarn said:**
> Ok so there are at least 3 threads about 10.04/10 problem here on ubuntuforums, and as much as I love ubuntu and linux in generally I really wish this problem will be fixed soon.
They both work fine at first but after a few updates and stuff they started freezing and hanging.. Now I am back on 10.04 after I tried 10.10 for a few weeks for some odd reason.
What happened to "Linux is faster and gives you less pain than Windows"?
With all this freezing and stuff, we can't say the same anymore.
People are having these random freezing and hangup problems with not only the new ubuntu distros but the new mint 10 and suse as well.
I mean common guys, what the hell is going on here?
What will happen is a Windows user goes from Windows to these new buggy versions of linux? I am not saying this to sound like I am against Linux or anything, but simply because something just needs to be done right freaking now.
There are literally 100 different people posting on these threads I was talking about, and they are probably not even 10 procent of all the people who are using these distros.

People have tried everything from different kernels, disabled gfx, etc.. but no luck.
What I am saying is, this is a frustrating problem.
Linux is on a very early stage and more and more people are changing from Windows, and just imagen if they discover all these problems? They will go right back to windows and they will never try linux ever again.
I mean, spyware and viruses are nothing compared to random freezing and frustrating hang ups all the time.
I know some people are probably working on this but I can't stress this enough. 
This should (or must) have first priority.
Remember, most of us are normal everyday people, and not beta testers for something new and undiscovered. Because that's how it feels sometimes.
Again, this is not a hate message or anything. I just want to push things forward.

Every single time I've had a freezing problem it was because the install didn't work properly.  Unfortunately, sometimes the warnings aren't seen and you have **no** way of fixing it.  I'd recommend re-downloading the ISO, reburning it; and re-installing.

- CH

---

### Post by cchhrriiss121212 on 2010-12-05
> 
Now back to my issues on the subject. I still don't know how to get all  the hardware info u guys need in order to help me with this. 
Try checking system monitor, that will tell you what CPU you have which will determine how smooth flash will run. Also try using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/"), which will check you have the correct version installed.

---

### Post by IndyGunFreak on 2010-12-06
> **edward1978 said:**
> Do you have flash installed? Can you provide hardware specs.? Info like in my sig.

Of course I have flash Installed....
1.8ghz Celeron, 1.5gigs Ram, Intel GM965 graphics... is my laptop
Another PC
2.6ghz Athlon, 3gigs Ram, Nvidia 79xx. Can't recall any more specifics about it, it's not in front of me.

Both are running the 32bit version of Ubuntu

---

### Post by ivarn on 2010-12-06
> **cement_head said:**
> Every single time I've had a freezing problem it was because the install didn't work properly.  Unfortunately, sometimes the warnings aren't seen and you have **no** way of fixing it.  I'd recommend re-downloading the ISO, reburning it; and re-installing.

- CH

Heh thanks but no thanks. For starters I don't use my pc for testing and crap, also this is a problem I've been dealing with just lately.
Also, it's not an error kind of freezing. It happens when ever i use a program that takes a lot of CPU but shouldn't. Such as Songbird. Whenever that program is open my PC is running lagy and jerky.

> **cchhrriiss121212 said:**
> Try checking system monitor, that will  tell you what CPU you have which will determine how smooth flash will  run. Also try using [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/"), which will check you have the correct version installed.

Oh you mean if I have 64 or 32?`As I said, everything worked smoothly at the begin with but I do thing this issue got something to do with the CPU and how its always getting overloaded or something. How can I check this btw?

> **IndyGunFreak said:**
> Of course I have flash Installed....
1.8ghz Celeron, 1.5gigs Ram, Intel GM965 graphics... is my laptop
Another PC
2.6ghz Athlon, 3gigs Ram, Nvidia 79xx. Can't recall any more specifics about it, it's not in front of me.

Both are running the 32bit version of Ubuntu
  
What I think he meant to say is "do you have the correct flash plugin installed".
But I assume you have since this was a high quality video problem and not a flash problem.
Did you follow my solution?

---

### Post by IndyGunFreak on 2010-12-06
> **ivarn said:**
>   
What I think he meant to say is "do you have the correct flash plugin installed".
But I assume you have since this was a high quality video problem and not a flash problem.
Did you follow my solution?

No, I didn't follow any solution, I installed flash and it worked fine.

---

### Post by cchhrriiss121212 on 2010-12-06
> Oh you mean if I have 64 or 32?`As I said, everything worked smoothly at  the begin with but I do thing this issue got something to do with the  CPU and how its always getting overloaded or something. How can I check  this btw?
You can check that with system monitor. The first tab will tell you what cpu you have, the next will show you your cpu usage when watching flash video or anything else.

---

### Post by ivarn on 2010-12-06
> **cchhrriiss121212 said:**
> You can check that with system monitor. The first tab will tell you what cpu you have, the next will show you your cpu usage when watching flash video or anything else.
Thanks, ok it uses 16,5 % but the weird thing is, I have 4gb, and it says I have 3 gb. that was weird.

---

