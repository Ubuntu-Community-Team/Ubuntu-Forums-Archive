---
title: "I can't get into Ubuntu even after reinstalling"
date: 2011-06-15
forum: General Help
---

### Post by yahya_no_1 on 2011-06-15
OK so I had this problem a long time ago(like a year ago), but ignored it because I didn't need Ubuntu at that time, but now I need it now.(windows is infected again -_-")

My problem is after I upgraded to ubuntu 10.4+(frogot the vr. number), after the installation was complete, I always get this "> [COLOR=black][grub: ]("http://ubuntuforums.org/showthread.php?t=1779828")[/COLOR]" and nothing else happens after that.

When I press Esc it gives me a bunch of choices like  a something/something/menu.something, reboot command line so on.

When I choose any of the choses (except for reboot and halt) I go right back into [COLOR=black][">grub:]("http://ubuntuforums.org/showthread.php?t=1779828")".

I tried everything, reinstalling from inside windows, from outside, formate and create a partition just for Ubuntu, nothing seems to work.

The only way I have access to Ubuntu now is threw the liveCD(which I am on now), can someone please tell me how to fix this.

Thank you
[/COLOR]

---

### Post by Ghostmn on 2011-06-15
Are you using ubuntu to remove malware from the windows partition? Because if you are just doing that, you can remove it with the live cd.

---

### Post by yahya_no_1 on 2011-06-15
No I am using it for other reasons, anyway I tried re-installing grub....nothing

I even formatted a whole partition and after I finally did all that, I didn't get the option to select ubuntu the at start up 

Just stuck with the old ubuntu installation choice, that keeps going into >grub:

or go to windows 7/ older windows

---

### Post by yahya_no_1 on 2011-06-15
Anybody plz help, I am kinda stuck here

---

### Post by rothux.j on 2011-06-15
Hmm... is it a new version of ubuntu? 11.#?
Try this:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078")

---

### Post by yahya_no_1 on 2011-06-16
OK so I just saw this since I just got acess to internet again. how do I use the link?

Thnak you for the help

---

### Post by nzjethro on 2011-06-16
> **yahya_no_1 said:**
> OK so I just saw this since I just got acess to internet again. how do I use the link?

Thnak you for the help

Boot from a Live CD, then follow the steps in the link. Thi link tells you how to mount your Ubuntu partition, then chroot (CHange Root) to your Ubuntu partition so that you can run commands that will affect that partition. Finally, the command
```
dpkg-reconfigure grub-pc
```
reconfigures your grub. Maybe type
```
update-grub
```
while you're chrooted in too. I had this issue a few weeks ago after forgetting to update my grub. and this is the exact way I fixed it. And if you have any issues with any of the steps, post here and someone will help.

---

### Post by wildmanne39 on 2011-06-16
> **rothux.j said:**
> Hmm... is it a new version of ubuntu? 11.#?
Try this:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078")Hi, if you look at that link it has a program that you can burn to disk that will repair your grub for you, and you do not have to do it manually. Also if you have problems run this script and  post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by yahya_no_1 on 2011-06-16
> Boot from a Live CD, then follow the steps in the link. Thi link tells you how to mount your Ubuntu partition, then chroot (CHange Root) to your Ubuntu partition so that you can run commands that will affect that partition. Finally, the command
Code:
dpkg-reconfigure grub-pc
reconfigures your grub. Maybe type
Code:
update-grub
while you're chrooted in too. I had this issue a few weeks ago after forgetting to update my grub. and this is the exact way I fixed it. And if you have any issues with any of the steps, post here and someone will help.

Well I downloaded the CD on the link and tried that, it tells me for the first command line:

package 'grub-pc' is not installed and no info is available.

the second line doesn't work, The thing is I deleted and uninstalled all the Ubuntu OS I have in my PC to start fresh, BUT I STILL geta Ubuntu choice when I boot up my pc and I can't seem to remove that.

I am guessing it has to do with the main problem, because every time I pick that I just end up in that whole "Grub>"  screen, and when I install another ubuntu the same thing happens to that too, I never got this problem before........like ever

---

### Post by wildmanne39 on 2011-06-16
> **yahya_no_1 said:**
> Well I downloaded the CD on the link and tried that, it tells me for the first command line:

package 'grub-pc' is not installed and no info is available.

the second line doesn't work, The thing is I deleted and uninstalled all the Ubuntu OS I have in my PC to start fresh, BUT I STILL geta Ubuntu choice when I boot up my pc and I can't seem to remove that.

I am guessing it has to do with the main problem, because every time I pick that I just end up in that whole "Grub>"  screen, and when I install another ubuntu the same thing happens to that too, I never got this problem before........like ever
Hi, we really need to see the boot information script as posted in my previous post and please read how to post the information here between the brackets.:)

---

### Post by yahya_no_1 on 2011-06-16
To make life eassy for everyone this is what i get after I install any Ubuntu now:

[http://imageshack.us/photo/my-images/705/photo0006tp.jpg/](http://imageshack.us/photo/my-images/705/photo0006tp.jpg/)


I can't copy paste any of my problems because I am using the laptop, since my PC can't get any internet usage for virus problems(even after format it is still there)

---

### Post by holycow131415 on 2011-06-16
Since windows is virus bombed, i would assume you wouldnt care to just reformat your hard drive /partitions completely instead of just hassling around with this problem. Reformatting everything, and then installing would erase the grub errors.
 Just back up your data in both operating systems and reformat everything... they will all work better and you wont have a hassle anymore... it would also ensure everything is installed correctly and not  messed up from your old old ubuntu install that you may have incorrectly deleted.

---

### Post by yahya_no_1 on 2011-06-16
Well looks like I destroyed my windows boot loader, I can't get into windows without repairing it it first.

Anybody found a fix for my problem :(


> Since windows is virus bombed, i would assume you wouldnt care to just reformat your hard drive /partitions completely instead of just hassling around with this problem. Reformatting everything, and then installing would erase the grub errors.
Just back up your data in both operating systems and reformat everything... they will all work better and you wont have a hassle anymore...

I already formatted my computer 2 times this week, the virus is still there and so is the grub error :/

---

### Post by holycow131415 on 2011-06-16
I dont think you are reformatting then... Do not do repairs, you have to completely wipe the hard drive and reinstall. Just use the liveCD of ubuntu to back up your files from windows and reformat.

---

### Post by yahya_no_1 on 2011-06-16
I have over 1 terra of information on 10 different drives, it would take forever to transfare all the files on each drive format it, then put them back in.

This was my goal in the long run but first I need ubuntu to work first so I can start doing that.

So far doesn't look like this is gonna happen anytime soon :S

---

### Post by wildmanne39 on 2011-06-16
> **yahya_no_1 said:**
> I have over 1 terra of information on 10 different drives, it would take forever to transfare all the files on each drive format it, then put them back in.

This was my goal in the long run but first I need ubuntu to work first so I can start doing that.

So far doesn't look like this is gonna happen anytime soon :SHi, you can do that from a livecd or usb stick, usb stick runs almost as fast as having it installed on your system. I am going too give you a link that will tell you how use the livecd to get your files from your other drives.
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by idoitprone on 2011-06-16
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

please post and put into code tags

or you can reinstall ubuntu from scratch

either way as wildmanne39 said we need proper information

---

### Post by yahya_no_1 on 2011-06-16
> Hi, you can do that from a livecd or usb stick, usb stick runs almost as fast as having it installed on your system. I am going too give you a link that will tell you how use the livecd to get your files from your other drives.
[http://www.howtogeek.com/howto/15761...buntu-live-cd/](http://www.howtogeek.com/howto/15761...buntu-live-cd/)


I only have the live CD atm, this WILL take a long time


> [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

please post and put into code tags

or you can reinstall ubuntu from scratch

either way as wildmanne39 said we need proper information

I would love to but I don't know what kind of info are you guys talking about, my main problem is that image up there, every time I install Ubuntu after the boot up menu it stops there.

And when I try to reinstall Grub or update it it tells me "something went wrong :("

So from the looks of it I am stuck doing it the long way

---

### Post by nzjethro on 2011-06-16
> **yahya_no_1 said:**
> Well I downloaded the CD on the link and tried that, it tells me for the first command line:

package 'grub-pc' is not installed and no info is available.

the second line doesn't work, The thing is I deleted and uninstalled all the Ubuntu OS I have in my PC to start fresh, BUT I STILL geta Ubuntu choice when I boot up my pc and I can't seem to remove that.


So on your computer you have no Ubuntu OS, yet you are trying to boot into Ubuntu from Grub? I think this could cause some problems. :p
Could you please clear up what your situation is, and what you are trying to achieve. I think everyone here is a bit confused as to what you have, and what you are trying to end up with.

---

### Post by yahya_no_1 on 2011-06-16
> So on your computer you have no Ubuntu OS, yet you are trying to boot into Ubuntu from Grub? I think this could cause some problems. 
Could you please clear up what your situation is, and what you are trying to achieve. I think everyone here is a bit confused as to what you have, and what you are trying to end up with.


Trust me my situation is confusing me as much as it is for you guys.

Let me list what my problems are in the correct order(what happened first) maybe it could help clear things up.

1- Every time I install Ubuntu, after the instillation is complete, I get to choose to boot from windows or Ubuntu, of course I choose Ubuntu, after words I end up with this page:

[http://imageshack.us/photo/my-images...oto0006tp.jpg/](http://imageshack.us/photo/my-images...oto0006tp.jpg/)

And can't go on from here

2-Even though I completely removed Ubuntu from my PC, I still get the option to choose ubuntu on the boot up menu even though I removed it, so it might be a grub problem somewhere in my drives I can't find.

3- I just screwed up my windows boot loader(loool I am awesome) and its asking me to repair the start up using the windows disc


So thats what I got right now, problem 1 led to 2 and problem 2 led to 3 loool


I know this is confusing but trust me, if the problem was that simple I would not have created an account and completely given up on google finding an answer, as it seems no one got this problem before

---

### Post by nzjethro on 2011-06-16
> **yahya_no_1 said:**
> Trust me my situation is confusing me as much as it is for you guys.

Let me list what my problems are in the correct order(what happened first) maybe it could help clear things up.

1- Every time I install Ubuntu, after the instillation is complete, I get to choose to boot from windows or Ubuntu, of course I choose Ubuntu, after words I end up with this page:

[http://imageshack.us/photo/my-images...oto0006tp.jpg/](http://imageshack.us/photo/my-images...oto0006tp.jpg/)

And can't go on from here

2-Even though I completely removed Ubuntu from my PC, I still get the option to choose ubuntu on the boot up menu even though I removed it, so it might be a grub problem somewhere in my drives I can't find.

3- I just screwed up my windows boot loader(loool I am awesome) and its asking me to repair the start up using the windows disc


So thats what I got right now, problem 1 led to 2 and problem 2 led to 3 loool


I know this is confusing but trust me, if the problem was that simple I would not have created an account and completely given up on google finding an answer, as it seems no one got this problem before

Oh man, that's a mess. Haha. Where abouts is you "terra of information" kept? Have you wiped your Ubuntu partition? Do you want to keep Windows? It may be easiest just to back-up what data you need from your Ubuntu and Windows partitions (if they exist), then wipe both OSes, and then re-install Ubuntu. I had the issue with "Minimal bash-like ..." on grub before, but I chrooted and ran update-grub and it resolved the issue. :confused:

---

### Post by idoitprone on 2011-06-17
```
Trust me my situation is confusing me as much as it is for you guys.
```

Go to the link I gave you. There is a reason why I gave you that link. Follow those directions and post the results. Since you are mubbling random details. I cannot take your word.

while your at it post the result of ```
sudo fdisk -l
```
when you boot to the live cd

---

### Post by wildmanne39 on 2011-06-17
Hi, you said your goal is to get your data from your drives, in post #16 I gave the answer and a link if you just want to retrieve your data. There is nothing we can do about the booting problem unless you give us the information we need from the boot script. You do not have to have your computer able to boot ubuntu to get your data, just refer to post #16.

---

### Post by yahya_no_1 on 2011-06-19
Alright I am back, after 3 days of removing->formating-> put the info back I solved most of my problems

I fixed my windows boot loader and got rid of the annoying broken Ubuntu option on startup.

All that is left for me is to know how to fix the grub

I know this was asked in the previous posts, but just so I can get a clear way to get things started right.

After I download the link given to me to fix the grub, I burn it on a CD/DVD then.........(yah this is where I need to know what to do exactly and what to post back so people can help me)

Thank you for all your help

---

### Post by yahya_no_1 on 2011-06-19
NVM Ubuntu installation worked, guess 3 days of formating every drive I had paid off, whatever was the problem with Grub in one of the drives is gone now.

Thanks for the help :D

---

### Post by wildmanne39 on 2011-06-19
> **yahya_no_1 said:**
> NVM Ubuntu installation worked, guess 3 days of formating every drive I had paid off, whatever was the problem with Grub in one of the drives is gone now.

Thanks for the help :DHi, your welcome glad you got it working, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

