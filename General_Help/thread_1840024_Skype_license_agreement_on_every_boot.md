---
title: "Skype license agreement on every boot"
date: 2011-09-06
forum: General Help
---

### Post by wastvedt on 2011-09-06
A few days ago, before loading X, Ubuntu displayed some sort of message about errors in the file system. It scanned, and fixed, and then booted up just fine, with a couple files added to Lost+Found. The only difference I have noticed is that now Skype prompts me to accept its license agreement every time I log in. I have Skype set to start up and log in in the background, which was working just fine until now. I tried purging Skype and reinstalling, to no avail. Any thoughts?

Trygve

---

### Post by pieta9999 on 2011-10-20
Same problem exactly as per above! but additionally my logitech webcam 9000 microphone records and transmits sound at a very quick speed/ wrong frame rate (and people tell me I have to stop doing this on purpose). I don't know if the two issues are related or not...

Help, please!

---

### Post by Burfee on 2011-11-11
same problem for me... ubuntu 11.10 x64

---

### Post by FokkerCharlie on 2011-12-05
I've just started seeing this.  Did anyone figure it out?

Charlie

---

### Post by mr.interested on 2011-12-11
I have the same problem since the latest update of Ubuntu a few days ego.

---

### Post by bkallay on 2011-12-14
Take a look in your ~/.Skype directory for a file called shared.xml.  If this is a 0 byte file remove it and try opening skype and accepting the agreement for hopefully the last time, now you should see shared.xml with content.

I was having the exact same issue and finally got annoyed enough to start looking for solutions.  For some reason this file was not getting updated (honestly I removed it and now I can't recover the specifics) my guess is the permissions were muddled somehow.

Hope this helps someone.

---

### Post by wastvedt on 2011-12-27
Awesome! For me, shared.xml was actually a directory in ~/.Skype containing one file. I deleted the directory, and on next run, Skype replaced it with a file by the same name. Now it works. Thanks bkallay!

Trygve

---

### Post by mr.interested on 2011-12-30
> **bkallay said:**
> Take a look in your ~/.Skype directory for a file called shared.xml.  If this is a 0 byte file remove it and try opening skype and accepting the agreement for hopefully the last time, now you should see shared.xml with content.

Many thanks, I can confirm that this works!

Also, this fixes proxy settings. Before each time I run Skype, and after accepting the licence, I had to manually change proxy settings. Deletion of the file shared.xml fixes also this problem.

---

### Post by don.benard on 2012-01-02
Excellent and simple solution.

I deleted the file whilst Skype was running and it was immediately replaced the zero byte file with one that was 53 kbytes.

This solves my need to: a) accept the License Agreement on each start-up and b) uncheck Skype's automatically altering sound controls (which left checked leads to a locked up Skype inside of one minute of use.

Thanks again.

db

---

### Post by FreeMinded on 2012-01-04
Great that solved it for me. In my case there were two files called shared.lck and shared.tmp. No shared.xml. I deleted both. The license agreement doesn't show up anymore.

BUT now Skype tells me that my password is wrong on startup. I type the password and login works. Strange. Of course I have automatic login enabled. Any ideas?
Thanks in advance!
FM

---

### Post by fightling on 2012-01-18
Same issue on my computer. I first removed the shared.xml and .lck. The license agreement appeared once more and never again. But then skype tells me the password is wrong at every start.

I renamed the whole .Skype folder to deactivate it. This fixed the problem by causing Skype to create a new one but it also cleared the chat logs :( 

So I looked further into the .Skype folder where I found a config.xml file within my user folder (.Skype/<username>) and a config.lck. I replaced these with the newly created copies and re-renamed the original folder to reactivate it. 

And it works.

So I think it's the same problem with the .Skype/<username>/.config.* files like with the .Skype/shared.* files and you may just remove these files and restart Skype to recreate them. But I didn't do it that way. But because config.xml had size 0 a backup shouldn't be necessary ;)

Hope this helps.

---

### Post by birdsarah on 2012-06-16
Same problem for me - needing to accept user agreement and settings lost. 

Slight difference, in my .Skype folder, my shared.xml was listed as taking up 41P (on doing ls -hal) which is obviously insane as my hard drive is only 80M.

Deleting the shared.lck and shared.xml made the user agreement go away but still had the problem of settings being lost.

For that I removed the username/config.xml & config.lck (which were showing at 0 size) and then all was happy again.

I'm on 12.04 and have been using Skype on Ubuntu for ages, this just started happening this week.

Thanks for all your help.

---

### Post by Virus666 on 2012-08-19
> **bkallay said:**
> Take a look in your ~/.Skype directory for a file called shared.xml.  If this is a 0 byte file remove it and try opening skype and accepting the agreement for hopefully the last time, now you should see shared.xml with content.


That worked. Thanks a lot... :-)

---

### Post by SillySod on 2013-05-20
I had a similar problem with Skype giving me the licence agreement every time I started it, and also forgetting some of my settings (such as deciding to allow chat and calls from anybody!!).

This happened after I followed a solution to another problem, which was that the whole of Skype crashed every time I tried to attach a file to a chat message.  The solution I'd found was to start Skype as root user, which I did using "sudo Skype" from a terminal.  It solved my file attaching problem but started these other problems.

What it looks like had happened was that the shared.xml and config.xml files referred to above had changed to root permissions, so I had to chown these back to my own user to get back to how things were, and it's now working again as previously.

---

