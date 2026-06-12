---
title: "Should I worry?"
date: 2012-07-28
forum: General Help
---

### Post by JamesKenny on 2012-07-28
I am a nub, but my laptop recently fell into the wrong hands for almost ten days.

I checked syslog and there are 5 days missing compared to the auth.log

---

### Post by TheFu on 2012-07-28
> **JamesKenny said:**
> I am a nub, but my laptop recently fell into the wrong hands for almost ten days.

I checked syslog and there are 5 days missing compared to the auth.log


You can't trust anything on that laptop ever again.  Time for a fresh OS reinstallation, then recover your apps and data from the last backup prior to the laptop disappearance.

If you have a 100% backup from before, you could write a little script that compares the files between the backup and the system - I've done this myself, but it was many, many years ago.  I used a directory compare tool after using rsync in test-only mode to see which files had changed. For me, it was after a cracker broken into an internet server.  I was able to see exactly which files had been touched ... only in /tmp/ for my box. I didn't even reboot the machine after cleaning out the cracker scripts and disabling the service they used to break in.

To prevent this concern in the future, might I recommend** drive encryption [https://help.ubuntu.com/community/EncryptedFilesystems](https://help.ubuntu.com/community/EncryptedFilesystems) for all portable devices, especially laptops and smartphones**?  If you do use encryption, it is really, really, really important to have good backups since a minor file system logical or physical issue can make that disk/partition/file system completely unavailable to you.

OTOH, if your device(s) / laptop are ever misplaced or stolen, then you'll have the comfort to know your data won't be accessible by someone else - assuming you use a non-trivial passphrase that is 20+ characters and not commonly used words.

**Once an unencrypted computer has been out of your hands with an untrusted person, you can't trust it again.**

---

### Post by David Andersson on 2012-07-28
As for the system. Yes, a fresh install of the operating system sounds like a reasonable thing to do. After that, you re-install all programs you use from the repository/software center.

As for your documents (anything in /home). TheFu's suggestion to either compare them with a backup or restore them from a backup seems like the best approach. A restore is simpler, but with a compare you have the chance of saving work you have done after the backup, or finding out if the villain have done things they shouldn't have.

Before logging into the fresh system, make sure documents have been restored, or compared, or moved from /home, not to transfer any trojan to the new system.

---

### Post by Cheesemill on 2012-07-28
+1 for a fresh install and then restore all your personal files from the last backup that you made before your laptop fell into the wrong hands.

---

### Post by JamesKenny on 2012-07-28
Thank you guys, luckily I dont store to much on my computer, thats what FB,lastpass and google docs is for :)

I have gone through to many restores to do anything silly like that any more (not really since i quit windows)

 I am more worried about them being able to see what I am actually doing now, both over the internet and key logging. Call me crazy yeah I now but I am dealing with two plotters and conspirators. its kind of driving me crazy

---

### Post by jonnyboysmithy on 2012-07-28
[LEFT]Do you get firefox to remember passwords? They can be easily viewed. Edit>Preferences>Security>Saved Passwords>show passwords
That easy. Might want to change them. 

[/LEFT]

---

### Post by JamesKenny on 2012-07-28
> **jonnyboysmithy said:**
> [LEFT]Do you get firefox to remember passwords? They can be easily viewed. Edit>Preferences>Security>Saved Passwords>show passwords
That easy. Might want to change them. 

[/LEFT]


No I use lastpass which probably isnt that great either , my concern is some sort of logger, I have written code long enough that all you need is to know how something works to manipulate it. I ran avg, rkhunter and chkroot. 

The main reason I looked is is that i noticed ufw.log is empty and not being written too

---

### Post by JamesKenny on 2012-07-28
Since I re enable ufw.log

~~~ personal info removed

---

### Post by TheFu on 2012-07-28
> **JamesKenny said:**
> Thank you guys, luckily I dont store to much on my computer, thats what FB,lastpass and google docs is for :)
I am more worried about them being able to see what I am actually doing now, both over the internet and key logging. Call me crazy yeah I now but I am dealing with two plotters and conspirators. its kind of driving me crazy

Are the people capable of inserting hardware into USB headers and network ports to replicate traffic?  If so, dump the machine and get a new one. The software-based keyloggers will be gone after you reinstall the OS, so those don't matter at all.  It is the physical devices that are scary.  I've seen people receive a new keyboard or mouse in the mail that they didn't order and immediately plug it in and start using it without any consideration for how it might have been modified.  Dropping a flash drive in a parking lot outside a company is an easy way to get your spyware or virus installed on a corporate PC too.  Drop it where the expensive cars are or near the VP reserved spaces for best effect.

When companies send people to China, they assume the PCs have been physically compromised if it is ever out of the person's site. It is simply good business. I don't take my main laptop overseas, just a weenie netbook that I'm happy to sell when I get back home if I have any feeling it was compromised.  My piece of mind is worth $300 for a new netbook.

Trusting FB and Google with any sensitive information is worse than taking your chances with average crooks.  The more you know, the scarier those two companies are.  I know lots of people trust LastPass and they appear to have acted responsibly with any published potential breaches, but with really high value data like passwords, I prefer to keep that local, encrypted with strong pass phrases and backed up in more than 5 different places. 

Consider that the encryption used today needs to be strong enough for the next 20-40 yrs.  Lots of people are cracking password safes from 10 yrs ago and getting access to unexpected information.  More reasons to consider stronger pass phrases [http://blog.jdpfu.com/2012/04/05/future-proofing-passwords](http://blog.jdpfu.com/2012/04/05/future-proofing-passwords)

BTW, I hope you've already wiped that machine and put a fresh OS on it.

---

### Post by TheFu on 2012-07-28
Did you look up where those IPs in your firewall log pointed?
* google
* rr - your ISP?
* internal networking ... perhaps the router or a file server?

I didn't see anything funny ... well, except the google things.  I doubt google is doing anything harmful.  Lots of ad networks piggyback on your browser requests to gain return access to your PC through the firewalls on common routers.  Running a filtering router AND a software firewall is just good practice these days.

---

### Post by warm cardigan on 2012-07-28
> **TheFu said:**
> Trusting FB and Google with any sensitive information is worse than taking your chances with average crooks.  The more you know, the scarier those two companies are.

Agreed.

Here's a slightly related thread which I posted a few weeks ago. [http://www.twoism.org/forum/viewtopic.php?p=169763](http://www.twoism.org/forum/viewtopic.php?p=169763)

---

### Post by JamesKenny on 2012-07-29
I dont really keep that much on the pc, I meant my pictures and documents for the most part.

Is there any  can I reason multicast would be sending stuff?
How see what it sending?

I did find out some stuff is being re routed to another ip in local area (not mine) traceroute takes it the rr server and then starts hiding things
which is where the guy with the skills would be and the other multi cast  stuff is being sent to a server in Virginia, which is where my ex wife is

I would really like to bust his *** for this, as far as i know i can press charges, if i can prove it

---

### Post by sakamoto on 2012-07-29
> **JamesKenny said:**
> I am a nub, but my laptop recently fell into the wrong hands for almost ten days.

**I checked syslog and there are 5 days missing compared to the auth.log**


he probably watched some pr0n and erased his moves :twisted: just walk on the safe side and do a clean re-install

---

### Post by JamesKenny on 2012-08-03
Ok what I found was, the remote desktop was automatically connecting to both the IP in Seminole and the ip in Virginia, I did use the laptop most of the week for work only, they have not connected to the remote server I usually have mounted (sshfs for work) but I guess they could have just accessed it through my system. 

Somehow  my sudo pw changed while I was working the other day and seeing as it is Friday I have a fresh install on disk I am getting ready to install after the last data disk burns on my laptop.

Does wire shark come pre installed on Ubuntu? I noticed my desktop has it installed now and it crashes when I try to run it. I only learned about it after I seen the process running in Task Monitor. 

Could they have access to this machine too seeing as it is on the same router? 
I am starting to feel like a paranoid guy

After the fresh install is there any extra precautions I can take for security?

---

### Post by IWantFroyo on 2012-08-03
> **JamesKenny said:**
> Ok what I found was, the remote desktop was automatically connecting to both the IP in Seminole and the ip in Virginia, I did use the laptop most of the week for work only, they have not connected to the remote server I usually have mounted (sshfs for work) but I guess they could have just accessed it through my system. 

Somehow  my sudo pw changed while I was working the other day and seeing as it is Friday I have a fresh install on disk I am getting ready to install after the last data disk burns on my laptop.

Does wire shark come pre installed on Ubuntu? I noticed my desktop has it installed now and it crashes when I try to run it. I only learned about it after I seen the process running in Task Monitor. 

Could they have access to this machine too seeing as it is on the same router? 
I am starting to feel like a paranoid guy

After the fresh install is there any extra precautions I can take for security?

Reinstall! Reinstall! The end is near!

No, Ubuntu does not come with wireshark.

They shouldn't have access, but who knows what they did while they had it.

Install gufw or another firewall tool, enable your firewall (assuming it's not already installed - I forget), and encrypt your hard drive.

---

### Post by JamesKenny on 2012-08-04
> **IWantFroyo said:**
> 
Install gufw or another firewall tool, enable your firewall (assuming it's not already installed - I forget), and encrypt your hard drive.

Wow I love Ubuntu installs so much faster than installing Windows, (until you have to figure out whats wrong with wireless anyway)

Is there a difference that makes gufw better or more advanced  than ufw?

---

### Post by Cheesemill on 2012-08-04
> **JamesKenny said:**
> Wow I love Ubuntu installs so much faster than installing Windows, (until you have to figure out whats wrong with wireless anyway)

Is there a difference that makes gufw better or more advanced  than ufw?
GUFW is just a graphical front-end for UFW, which is in turn a front-end for iptables.

---

### Post by JamesKenny on 2012-08-04
gufw, ahh ok, so it really doesnt do anything that i cant to from the command line?

 i think i have come to the conclusion that trying to monitor activity and secure your system completely will make you insane, I have spent way to much time on it already and googling all of these ip address's ........... pfffffft i give up, let em have it, they can watch me play on the computer all day, i am not going to go crazy with some conspiracy theories trying to figure it out

---

### Post by JamesKenny on 2012-08-04
maybe i will watch some pr0n too :D

---

