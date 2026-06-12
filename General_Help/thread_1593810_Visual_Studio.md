---
title: "Visual Studio"
date: 2010-10-11
forum: General Help
---

### Post by DavidFelix on 2010-10-11
Hey I really wanted to know if Visual Studio C++ would work and compile correctly on Linux using Wine or any other software.

---

### Post by sendblink23 on 2010-10-11
> **DavidFelix said:**
> Hey I really wanted to know if Visual Studio C++ would work and compile correctly on Linux using Wine or any other software.

hmm if you are going to be using that kind of stuff, why not use real windows :P  

Just kidding, but reality here are 3 options:
-to use wine
-to install windows in a virtual machine (with VirtualBox)
-to use MonoDevelop

---

### Post by QIII on 2010-10-11
VirtualBox with a Windows guest works fine for me.  Native Windows, native .NET, etc.  Because of the limitations of the virtual hardware, you probably won't be developing games, though.

Mono is great, unless a client expressly specs native.

VS6 is rated Gold for Wine.  Visual Studio Express 2005 and 2008 are Bronze (work, sort of).  The rest are rated Garbage.  Wine is probably not the way to go.

---

### Post by DavidFelix on 2010-10-11
Well i'm not game developing, more like hacking haha. But still i'm so used to using VSC++ 2008. If I did use 2008 what problems would I encounter?

---

### Post by QIII on 2010-10-11
I had no problems.  I use 2010 now.

---

### Post by DavidFelix on 2010-10-11
> **QIII said:**
> I had no problems.  I use 2010 now.
What do you use? Wine?

---

### Post by DavidFelix on 2010-10-11
Bump?

---

### Post by DavidFelix on 2010-10-11
Hello?????

---

### Post by QIII on 2010-10-11
I use VirtualBox with a Windows guest.

Just a friendly bit of explanation.   Don't take this as scolding or being belligerent, please.  I just want to you understand that the absence of an immediate answer does not mean you are being cast to the wolves.

Remember that I, as does everyone else on this forum, have a life that is busy and I can't be here every moment of the day.  When I last responded to you I was on a train home from work, posting from my cell phone.  I have responsibilities at home, like everyone else.  Now that dinner is done, the foster kids have been bathed and put to bed and I have given my fatherly advice on matters varied and sundry to my own grown children, I am able to get back to this thread.

We are all here voluntarily as we have time.  Sometimes we don't have much time.

---

### Post by DavidFelix on 2010-10-12
Oh, no its fine. I just was falling asleep and wanted a quick answer before I got off because I knew it'd be a pain in the rear to find this thread again in the morning. 

So I should use VirtualBox?

---

### Post by TheAnachron on 2010-10-12
You should use [mono]("http://www.mono-project.com/Main_Page"). It's feature rich and works like a charm.
However, you can still use [Wine(HQ)]("http://www.winehq.org/") to emulate VS. However, VS is bad compated to Mono, so better learn mono and stick with it.
Emulating windows to use VS is to much trouble for a bad product. (Even if you are used to it)

Have a nice day.

---

### Post by Zanthir on 2010-10-12
The Anachron, I have a friend who wants me to help him with a game. He is using .NET/XNA/DirectX. Do you still suggest Mono if all I have available is Linux? I'm not really sure what my options are here. Do you have any experience with anything like this?
 
Also, DavidFelix, about finding this thread again in the morning, click the "Search" menu, and click on "Find All Your Threads." I use this, as well as the "Find All Your Posts," link almost every time I visit these forums first thing. And don't forget to mark this thread [solved] when you have the answer you wanted.

---

### Post by QIII on 2010-10-12
TheAnachron.

I disagree with you strongly.  This is not intended to be a flame.  It is intended to be commentary from someone who has been in and around the industry for many years.

Windows is not a bad platform.  My bile is raised by its purveyor's business practices.  Those practices are my primary reasons for using Linux.

Not only is Visual Studio not a "bad product", it is the most widely  used IDE in the Windows world.  It is used in an industry that - like it  or not - controls the lion's share of the market.  If you want to make a  living in a world where you can actually make a living, you had best be  proficient in Visual Studio -- and the most up-to-date version at that.

Using Windows natively in a virtual environment allows you to test your work in the environment your customers will expect it to work in.  Furthermore, Visual Studio is often specified by clients who want to be sure that the code produced, your deliverable, can be maintained by their staff after delivery.

I am firmly dedicated to Linux and the open source community.  If the world were as I wish it would be, then everyone would make a good living developing only open source products.  However, I  am pragmatic.  I earn an obscene amount of money developing software  for the Windows platform.  If you are not familiar with Visual Studio  and have only used MonoDevelop as your IDE, don't send me your resumé.

And that, in real world terms, can mean the difference between eating steak for dinner tonight or eating a spoonful of peanut butter.

I'm not saying not to use MonoDevelop.  I am saying that it is unwise to blow Visual Studio off as a "bad product" and dismiss it out of hand.

---

### Post by DavidFelix on 2010-10-12
Thanks everyone soo much :)

QIII: Right now I have 10.4. Should I install that then upgrade to 10.10? And then install VirtualBox then Win7 on VirtualBox or how does it work? Is it like Virtual PC? And thanks everyone for the support and help!!

---

### Post by QIII on 2010-10-12
If you do not have VirtualBox installed, then it's just as well to upgrade your OS first.  No harm, no foul.  But remember that you do not "have" to upgrade if you don't want to take that on right  now.  You have an LTS version that is stable.  You can upgrade if you  want to, but consider your needs.

I'm rather short on time, so I can't provide all the details you will want.  Actually, this may be time for a couple of new threads.

When upgrading, remember to completely remove your video driver, as leaving it can cause severe problems when upgrading rather than reinstalling.  Reinstall it after upgrading.

If you have done this before and know how to preserve your installed applications, then go ahead.  If you don't know how to, start another thread and we'll help you there.

Get upgraded (or not), and then search the forum for instructions on how to install VirtualBox and the Guest Additions for Windows. 

You might try googling 

```
site:ubuntuforums.org VirtualBox install Windows Guest Additions
```The best documentation is at [http://www.virtualbox.org](http://www.virtualbox.org)   But, frankly, sometimes reading a manual is more confusing than helpful.  "RTFM" is a bad bit of advice to give someone, because "TFM" often assumes you know what it is talking about.  I offer it only as one source of information, but it may be difficult for you to decypher.

At any rate, if you can't find something that helps, we're here (when we can be!).

---

### Post by DavidFelix on 2010-10-12
Thank you so much! Time to backup all my VSC++ 2008 Projects haha and then install 10.4. I'll upgrade when I feel comfortable. And one more thing. The game I making DirectX hooks for is for windows. Will VirtualBox support it? Also about removing the video driver. Sorry for all the questions!

---

### Post by QIII on 2010-10-12
When your Windows guest is running inside VirtualBox, you are running Windows.  You don't need to worry about your Windows APIs.  They are there because you are running Windows.  You won't need to hook any Windows APIs from Linux or the opposite.

But your "hardware" will be virtual and will be limited to what VirtualBox provides.  You may or may not like what you get.

Think of it as having two different machines.  One running Linux, one running Windows.  The nice thing is that with the Guest Additions installed, you can just move your mouse cursor from one to the other without having to use a KVM switch or a separate mouse/keyboard.

I have multiple screens, so when I am running a vm I have VirtualBox up on one screen and Ubuntu on the rest.

---

### Post by DavidFelix on 2010-10-12
Last question :)I burned the disk a few weeks ago, how do I know if you got the desktop version or the Netboox version before I install it?

---

### Post by sourchier on 2010-10-12
Insert the cd. Then go into folders dists then lucid. Double click on the file named Release. If you don't understand it's contents then please post the contents of the file here.

---

### Post by TheAnachron on 2010-10-14
Hi QIII,

I have used VS for some months. I never got used to it. (Maybe thats why I don't see any use).
There are better IDS, like Netbeans. Sadly that IDE does not support .NET. 

Anyway, I wasn't saying VS is bad and unuseable, it's more that I really learned to honor linux products, because no matter how you turn it, they are well thought-out.

Basically I was trying to show him an alternative, and if he would only know the alternative, I'd show him VS. It's just so that he sees both sites.

---

### Post by mastablasta on 2010-10-14
> **TheAnachron said:**
> Hi QIII,
 
I have used VS for some months. I never got used to it. (Maybe thats why I don't see any use).
There are better IDS, like Netbeans. Sadly that IDE does not support .NET. 
 
Anyway, I wasn't saying VS is bad and unuseable, it's more that I really learned to honor linux products, because no matter how you turn it, they are well thought-out.
 

 
ok but the fact remains that majority of the world still operates on MS products and that is why QIII said he is being pragmatic in order to make money. ;-)
 
To me MS products are good, but i also enjoy some alternatives that popped up in the last years. some are even better than MS.

---

### Post by Zanthir on 2010-10-15
mastablasta, which IDEs are better than VS?
 
I realize this question can be taken as hostile and in support of MS/VS. It is not. I am curious because I believe in free software, and I really want to support free software.
 
I think that free software and Ubuntu have come to be rivals, or near equals with proprietary software and Windows/Mac. And there are some things that Windows/Mac users can be jealous of. Notably the repositories of software that are so easy to install via the command line. Though, that doesn't seem to excite most of my friends.> So. I'd rather go to a website, download a file, and install it through my GUI anyways.Right! The package manager! That is awesome.
 
Apache is awesome.
 
Let me know what IDE you think is awesome.

---

