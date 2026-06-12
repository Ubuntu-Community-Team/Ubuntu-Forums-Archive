---
title: "System freezes randomly (mostly while idle or not in use)"
date: 2011-02-28
forum: General Help
---

### Post by ckankiewicz on 2011-02-28
I have Ubuntu 10.10 Desktop 64-bit installed on my laptop and up  until a few weeks ago it has been running great.  Then one day, while I  was not using the laptop it froze. I was logged in as my user but had  locked the screen and closed the lid. I didn't notice that it had  frozen until I opened the lid and wiggled the mouse to try and log in.  The screen remained black and I got no response.  I immediately tried  Alt + F2, F3, F4, etc. but got no response.  The only thing I could do  was hold the power button to power off the machine.

  This is an ongoing problem and the time it takes to freeze varies widely. It has happened as quickly as within 10-20 minutes of the  system being locked and lid closed and as long as 4-6 hours. My  machine is NOT configured to go into standby when plugged in and this  has happened both on AC power and batter.  It's also frozen a few times while in use, but the system wasn't under heavy load and it seems a lot less likely to do so  

  **Troubleshooting I have performed:**
  
[LIST]
[*]I uninstalled programs I knew that I had installed between when it  was working fine and having problems.  Those programs were CrashPlan,  Shutter and Conky. After uninstalling ALL of these programs the freezing  still occurs.
[*]Next, I decided to SSH into the machine from my desktop and leave an  htop and tail of the syslog running.  Here are screenshots of the last  thing shown on both when the system froze: [htop]("http://i.imgur.com/HJMig.png"), [syslog]("http://i.imgur.com/dXjXv.png")
[*]Here is a [dump of my syslog]("http://pastebin.com/YqcpruKS")  after another freeze.  The freeze happened at 9:14 and I didn't notice  it until about 10 minutes later and rebooted, hence the 10 minute gap  from 9:14 to 9:24.
[*]In the above syslog dump I noticed a lot of NVRM: os_raise_smp_barrier(), invalid context!  and upon investigating that message learned it was from the proprietary  Nvidia driver I had installed. Thinking this could be part of the  problem I uninstalled the Nvidia driver and reverted to using the  Nouveau driver. The computer still froze after a few hours.
[*]I ran Memtest86+ and it made it through two complete passes without any errors.
[*]I also thought the problem could be caused by overheating so I used  compressed air to blow out any dust in the CPU vents and all other  openings on the laptop.
[/LIST]
          **None of the above troubleshooting has helped and the freezing  still occurs. What other steps can I take to troubleshoot and/or fix  this problem?**

---

### Post by Royke on 2011-02-28
Hello ckankiewicz,
Believe me when i say i know how you feel;)
At least you could try setting up your BIOS in an other way than it is now. (if you have windows on it, it will stop running in some cases:D)Most proberbly the problem can be solved here. Just dare to make changes in it you think might be correct. 
I conluded the following setting-issues on my pc:

* IRQ-sharing of devices. Idealy when every device has its own IRQ-channel your pc would never stutter in any way. That is how i understand it and knowing this i was able to fix a lot of systems, altough it can be hard to set up. If for example your keyboard, mouse, networkdevice, soundcard and video is all on IRQ 11..
* Try to disable - if your BIOS has the option - IOAPIC(that's when i said goodbeye forever to vista). The good thing is that i saw that Ubuntu manages this by itself. I used to have strange systemhangs mostly with ubuntustudio-install.

If you still can't fix it now, than please don't give up! I was prepared to buy a new pc for ubuntu(studio), but at the end it was not needed. 

Greetings,

Roy

---

### Post by ckankiewicz on 2011-02-28
Hey Royke,

Thanks for your suggestions.  I'll start poking around in the BIOS and see what I can find.  I want to remain hopeful, but I'm doubtful this will help because I haven't touched my BIOS since I got this laptop, and Ubunut ran fine for many months on the same settings before having problems.

I'll still poke around and change some stuff to see if anything makes a difference, but any other suggestions would be appreciated.

---

### Post by ckankiewicz on 2011-03-02
Well, I think I may have solved this problem by updating the firmware on my SSD.  Only time will tell, but so far it seems more stable.  Thanks for your help though.

---

