---
title: "Like windows, do ubuntu updates crash your system?"
date: 2011-09-14
forum: General Help
---

### Post by Ed_Ziffel on 2011-09-14
Getting error when starting Firefox;
> Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.

Fresh install 10.04 lts no added anything.  Real hardcore about that as just about every ad on seems to make the systems unstable. Been using Ubuntu for about 2 years.  Just the updates since about 1 month ago when did a clean install as system was became unusable after trying new application. 

Should I turn off the updates to keep my system for getting messed up?  After doing a fresh install of course.  

FYI.  The nvidia restricted drivers, recommend ones according to the alert box, screw up my machines. Have 2 multicore modern machines both turn to crud when installing the restricted drivers. Have dual booted. Zero problems with windows on the machines, xp or 7, of course the updates are turned off and don't go online with them so also not running antvi. Have not had to reinstall the windows OSs since day 1, just the Unbuntu.    

Tried this and that to fix Ubuntu system problems, but quickest fix seems to be just doing a reinstall.  2 hours max and no wild goose chases.  Don't keep anything on root partition using default install partitioning, swap and / only as... guess what?... using manual partitioning tends to make the system unstable.  Way fewer problems with default install.  Also what good is manual partitioning if almost all partitions get wiped with a fresh install invent of a crash? 

Is Ubuntu turning into windows?  IE everything is fine until you do something that isn't geared towards a 6th grader, like music, videos, games etc., or am I just doing something wrong on every machine I'm trying to use Ubuntu on?

What can I do to limit the system crashes/failures?

---

### Post by 2F4U on 2011-09-14
> using manual partitioning tends to make the system unstable.

How comes you think that? I am always doing manual partitioning and my systems are very stable.

> Also what good is manual partitioning if almost all partitions get wiped with a fresh install invent of a crash? 

Only if you choose to format the partition.

To be honest, I am running Ubuntu, Xubuntu and Lubuntu (11.10 beta) on  three different machines and don't see the problems you describe. Even  the beta seems to be pretty stable for me.

---

### Post by hwttdz on 2011-09-14
1) system updates from the repo generally only make things more stable, as you won't get new major versions from the repo.  So in general new releases are least stable i.e. 11.04 immediately after release, and old ones are most stable, i.e. 11.04 right before end of life (of course it's also most outdated then). 

2) there are a few things you can do. 
   a) check that your hard drive has space
   b) check that the directory that firefox wants to write in has write permissions
   c) this sounds like a firefox problem more than anything else, so maybe remove your .mozilla folder and start from scratch there if you've messed up your firefox config (or move it to a different name and then you can restore if you want)

3) Manual partitioning will only make the system unstable if you mess up the fstab.  

4) linux is not at all like windows in limiting what you can do, it's all open source so if you can write it from scratch you can do anything you want to.  That said there are a multitude of wonderful tools that make doing anything you want much easier, for instance I archive my home directory every day and keep the archives of the last 3 days, +1/week for the last month, +1/month before that.  I could never do that easily and without buying some proprietary software that I'd have to update on it's own in windows.  My alarm writes itself to go off at a different time every day.  I've a website that I can access on my phone that can control rhythmbox (play/pause,next,previous,volume...).  Even getting apache working on windows would be a nightmare (I have done it before, it took significantly longer than "sudo aptitude install apache2; sudo a2enmod userdir").  Then you starting thinking about all the security holes you're opening letting system commands be run from the web.

---

### Post by snowpine on 2011-09-14
Wow, your question is kind of all over the map, let me try to rephrase it for you (hope you don't mind):

"Dear UbuntuForums, when I try to launch Firefox, I get the following message:

> Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features. 

What does it mean and how do I fix it?"

Is that an accurate summary of the actual issue for which you're looking for help? If so I would [start with this page]("http://support.mozilla.com/en-US/kb/Could%20not%20initialize%20the%20browser%20security%20component") and also use the forum Search feature, as I see several users have had the identical error message in the past. If none of those solutions work, let us know what you've tried, and we'll take it from there, good luck! :)

---

### Post by Ed_Ziffel on 2011-09-14
Not really.  As stated only use the all the default settings.  Period as am trying to isolate issues.  Did not touch anything in any directory period.  If I had actually done something, then would generally assume it was my fault until otherwise proved to the contrary.  

Plenty of hard disk space.  Allocated 120gig for ubuntu on 600 gig drive with 100g for Win7, 100g for XP and 290 for a data storage drive on one machine and just ubuntu on another, and win7 and ubuntu on my laptop.  Have next to nothing in all ubuntu installs and zero, as in nothing not stock on the one with the current problem and no changes to system at all. Generally frustrated with it; Feel like in an alternate universe.   

No doubt firefox is the culprit here.  Will remove the .mozilla directory as advised. Thanks. Still WTF? 

The issue with the manual partitioning, have used manual partitioning on about 10 installs.  All generally seemed to run better with just the / and swap.  Did not change anything after partitioning after install.  All partitions set during install and yes they were the proper format for their use:  ie boot ext2, root ext4, swap at 2x mem etc.  Again was trying to isolate issues for system performance.  With that in mind, did make a concerted effort to use good control procedures.  IE, test, record, repeat, then change one parameter, test, record, repeat.  Probably have done a total of 100+ installs.  Thinking that there is probably a reason the default is / + swap. 

Been working with pcs since the commodore.  got a tech rating in '86.  Have yet to see anything that worked as advertised.  And have seen some really bad apple machines. Never owned one but worked on several.  All seemed quite limited as far as tweaking/customizing goes, which is probably why they seem to enjoy a better reputation in general.  My experience is that the fewer things you try to get one computer to do the better they work.  Have redone maybe 4,000+ window machines as a free lance tech. What it looks like to me.

---

### Post by Ed_Ziffel on 2011-09-14
Oh yeah, already went on the mozilla help joy ride before inquiring about the updates.  Would be back up by now if had just skipped it all and started fresh.  Hard to beat a 2 hour fix when it comes right down to it.  Would still like to know what caused it or how to prevent it in the future.

---

### Post by snowpine on 2011-09-14
Your commodore experience and 4,000 windows machines are irrelevant to getting your Firefox question answered; please try to stay on topic if you want a concise and relevant answer.

1. What are the permissions on the cert8.db file in your hidden ~/.mozilla/firefox profile folder?

2. Does creating a new Profile allow you to launch Firefox successfully?

Regarding "what caused this problem in the first place?" it sounds like a file permission problem. Am I correct that you did not perform a "fresh Ubuntu install" but rather, you recycled (did not format) your existing /home partition? Are you comfortable with Linux file permissions and use of the "chmod" and "chown" commands?

---

### Post by Mark Phelps on 2011-09-14
For the Firefox problem, perhaps the info in the link below will help:

[http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component]("http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component")

As to stability, MY experience has been that every release has been buggy to some extent -- which is why I generally advise folks to wait a couple of months after a new release before they switch.  

I also advise them to FIRST, use Clonezilla to image off their current install -- so they can restore it if something goes seriously wrong.  Since Canonical has yet NOT to provide anything like System Restore, if you do an upgrade and your PC crashes or fails severely, apart from restore from a backup, there is no simple way to go back to the (previously) working release.

One thing I do is use Clonezilla to image off the setup before I make any possibly serious changes or installs.  If the change has no problems, it only takes a couple of minutes to erase the backup.  And, if it DOES cause serious problems, the 15 minutes spent backing it up and then restoring it is well worth the time.

---

### Post by Ed_Ziffel on 2011-09-14
Permissions on the .mozilla file are owner Users(my user) read right and group my user.  Maybe change to root as owner with group as user read write?  That is what is needed for web development.

So sudo chown -R root:user .mozilla
sudo chmod -R 775 .mozilla?
Done. will give it a go. 

Not really worried about outside users but what permissions were you thinking about?   

Clonzilla sounds good.  Like you say, no restore function.  Thanks for the link

Again I have to say that I've been developing on another machine and did almost nothing with or to the one that mysteriously developed the problem, as no added programs etc.  Only changes were updates.  And it was a complete wipe and redo.  Always do a format because who needs left over junk. Don't know what the one person was talking about but the Ubuntu install absolutely reformats several partitions whether you want it to or not.  Don't remember exactly which ones but am thinking the var and etc for sure and maybe home boot and root.  Plus the frequency of reinstalls, and that the partitions don't survive a reinstall and the noted better performance with a stock default install stopped caring about which one could stay or not and just use a stock install. 

But to be fair, if you are trying new programs, my experience is that a lot of the time you will screw up your machine, so I'm not blaming Ubuntu.  This time however, the install was as clean as fresh snow.  Using the 10.04 LTS version.  Been on the "latest and greatest" ride.  Almost with out fail my experience has been that when you get on the cutting edge, you wind up bleeding.  lol  

Really looking forward to the next long term release.  Ubuntu has come a long way since 7.x.

---

### Post by Ed_Ziffel on 2011-09-14
Changing the permissions did not work.  Did several combinations of owners and permissions. And did check to make sure all changed as supposed to using the recursive structure.  Was on the brink of a wipe and go so decided to just trash can, as suggested by on of the posts, the .mozilla file, which is hidden in your home directory. Clicked on mozilla link in the panel and butta-bang-butta-boom working like brand new all over again. Was even able to drag the old file out of the trash to the desk top, hunt down the bookmarks file and reinstall all my bookmarks with out having to chase them down in my backup files.  Still not sure what the moral to that story is though.

Thanks all.  :-)

---

