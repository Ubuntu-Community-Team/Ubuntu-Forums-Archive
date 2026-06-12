---
title: "Root and User"
date: 2009-11-09
forum: General Help
---

### Post by ibbill on 2009-11-09
when I try to open my spare drive or other drive continually  get the authentication nag for password.

How can I stop this please. If no fix then how can I boot up and be root from now on.

This nag is like a (vista nag)

---

### Post by The Funkbomb on 2009-11-09
Automount the drive at boot.

---

### Post by ibbill on 2009-11-09
sorry should have posted also authentication needed when I click on software source, computer janitor, just to name a few  via system> administration

This is really aggravating how can I log on as root from now on I really don't need to be asked every time I try to do something.

---

### Post by The Funkbomb on 2009-11-09
These are there for your protection.

One of security features in linux is you need a password to do any major changes.  I'm sure there is a way to disable it but it's not a good idea.  It's like leaving your keys in your car's ignition.

---

### Post by ibbill on 2009-11-09
The Funkbomb thanks for the reply but I really don't want to have to type my password in all the time it is like going back to VISTA all over again.

Can I reinstall and set  a root  log on along with a  user account. If so I will reinstall.Thats if there is no way to change it to root now.

I am the only user of this computer I do no banking no credit card stuff I do nothing that I care anyone sees. Just hate being Nagged all the time.

Could have stayed with my first 2 wives for that :lolflag:

---

### Post by The Funkbomb on 2009-11-09
Again, I HIGHLY suggest that you don't.

While you may not do anything important with your machine, someone with root control of your machine could use it to cause havoc for other people.

You only need root for a few things.  Basically things that will alter your system.  Just try to do all the root stuff all at once and then you won't have to deal with it for a while.

---

### Post by ibbill on 2009-11-09
Okay thanks  Dam I just hate being told what I can do and cant do with my computer. 

 I understand with linux as its free and their choice on what restrictions they feel is best for all users.

Guess I will have to wait for googles new system this summer as I will never go back to windows.

Thanks again for your help and for being here to help us all.

Bill

---

### Post by Merk42 on 2009-11-09
> **ibbill said:**
> Guess I will have to wait for googles new system this summer as I will never go back to windows.

As the 'nagging' is something in Linux, and ChromeOS is based on Linux, I don't know if it'll be any different.

---

### Post by The Funkbomb on 2009-11-09
> **ibbill said:**
> Okay thanks  Dam I just hate being told what I can do and cant do with my computer. 

 I understand with linux as its free and their choice on what restrictions they feel is best for all users.

Guess I will have to wait for googles new system this summer as I will never go back to windows.

Thanks again for you help and for being here to help us all.

Bill

Google's new OS is, from what I've read, a linux OS with a new windowing system.  I'm fairly sure the core will work the same as any other linux system just with a different interface.

I know it's a pain but it keeps ya safe.  Whatever you choose, good luck.

---

### Post by malangaman on 2009-11-09
ibbill,

I feel your pain.

The links below shows how to log into Ubuntu as root.

<snip>

Everyone should have the right to choose their own preferred level of protection. Knock yourself out!

---

### Post by Durden on 2009-11-09
It's always been amazing to me how hypocritical Linux apologizers are on this issue. People here and elsewhere give Vista hell over the constant nagging for passwords and the popup reminders etc etc but then sing praise over Linux/Gnome doing the exact same thing in a more intrusive and obnoxious way. It really boggles the mind how they can justify that nonsense. 

On to your issue however, you can try Kubuntu which is less obnoxious since it removes Gnome fromt he equation. Additionally, you can get to know the under pinnings of the OS and tweak it to remove this nonsense.

---

### Post by ibbill on 2009-11-09
Thanks.for all your help gang. i am very happy now.marking is solved.

Jumped ship NEVER but I must have a choice of what I want and don't want be it free or not.

---

### Post by Paqman on 2009-11-09
> **ibbill said:**
> sorry should have posted also authentication needed when I click on software source, computer janitor, just to name a few  via system> administration

This is really aggravating how can I log on as root from now on I really don't need to be asked every time I try to do something.

If you want to run as root all the time then just switch to another distro of Linux. Ubuntu is a bit unusual in that it doesn't have a root account available by default.

Running as root is a genuinely bad idea though. It's the main reason why Windows has so much malware. You should expect your box to be compromised if you choose to do this.

---

### Post by The Funkbomb on 2009-11-09
ugh...  I don't even know why I bother.

---

### Post by ibbill on 2009-11-09
> **The Funkbomb said:**
> ugh...  I don't even know why I bother.

Funk I appreciate all your help more than you know.

---

### Post by mc4man on 2009-11-09
the whole deal with non persistent authorizations has nothing to do with security, running as root ect. ect.

simply just that a function hasn't be returned, so atm the authorization lasts for 300 secs, then needs to be redone (by entering password.

Simple fix till hopefully addressed thru an update at some point

[http://ubuntuforums.org/showthread.php?p=8259743#post8259743](http://ubuntuforums.org/showthread.php?p=8259743#post8259743)

---

### Post by ibbill on 2009-11-13
This is the last whine about passwords.

As you have explained to me that using Root is a no no so have gone along with that.

As the one that logs into MY COMPUTER and ubuntu system. I really need to know why after using a password to log on that I am continually asked for my password.

Terminal okay anything else I should NOT have to type the password in AGAIN.

Note: with all the nagging about passwords again and again no wonder people find a way to log in as root. I don't blame them at all.

That's it finished griping thanks for listening.

Bill

---

### Post by ibbill on 2009-11-13
As you have explained to me that using Root is a no no so have gone along with that.

As the one that logs into MY COMPUTER and ubuntu system. I really need to know why after using a password to log on that I am continually asked for my password.

Terminal okay anything else I should NOT have to type the password in AGAIN.

Note: with all the nagging about passwords again and again no wonder people find a way to log in as root. I don't blame them at all.

That's it finished griping thanks for listening.

Bill

---

### Post by guriinii on 2009-11-13
Just change the settings so you don't have to give a password for everything.

Simples

---

### Post by snowpine on 2009-11-13
Hi Bill, Ubuntu has that feature because the majority of users DEMAND it. I personally would not use a Linux distro (Puppy comes to mind) that gives the user automatic root priviledges. You can easily change this default behaviour (Google "sudoers") but I guarantee you it will always be the default; Ubuntu is not going to change it based on your rant. :)

---

### Post by ibbill on 2009-11-13
Change the settings? I don't want to use root as they have said its dangerous.

Just want to log in to my computer and not be asked again for a password do you thing that's asking to much.:confused:

---

### Post by Gaweph on 2009-11-13
When it is asking you for your password it is asking if it is ok to perform some sort of operation which required root privilages.

Think of it this way.  If you get a virus or someone manages to start executing something as your user, then arent you glad that it stops them/the virus and asks for password before it is able to do something destructive.

Even Windows 7 now asks you to confirm that it is ok to run specific operations.

As an example, say your running windows XP, and a virus starts executing, since it doesnt need to ask for permissions, it simple is alowed to executre, and can kill your entire system.

---

### Post by snowpine on 2009-11-13
> **ibbill said:**
> Change the settings? I don't want to use root as they have said its dangerous.

Just want to log in to my computer and not be asked again for a password do you thing that's asking to much.:confused:

Hi Bill, if you can do anything you want without ever being asked for a password, then you are, by definition, root. :)

---

### Post by ukripper on 2009-11-13
> **ibbill said:**
> T
Terminal okay anything else I should NOT have to type the password in AGAIN.



Like what else?

---

### Post by John Bean on 2009-11-13
> **ibbill said:**
> Change the settings? I don't want to use root as they have said its dangerous.

Just want to log in to my computer and not be asked again for a password do you thing that's asking to much.:confused:

Rather than continuing to rant please do what snowpine suggested and Google "sudoers". Clue: It's nothing to do with logging in as root but it should tell you all you need to allow you to no longer need to type passwords.

---

### Post by egalvan on 2009-11-13
You are asked for your password because you are about to do something as root (sudo).
There is no (practical) difference between logging in as root,
and being permanent sudo.

Running as root is running as root...

The terminal is just one way to access.
GUI's are just a graphical window on top of the command line.


There are security issues at work, not just the possibility you might hose your system.

Yes, the machine belongs to YOU, but when you connect it to the Internet, it now belongs to EVERYBODY.

The large majority of zombie machines are single-user machines, just like yours.
The large majority of spam-bot machines are single-user machines, just like yours.


Root Access is the Holy Grail of the Cracker.


And yes, I have a Linux laptop that I run as root,
but THIS MACHINE IS NOT CONNECTED TO ANYTHING,
no wired, no wireless, no bluetooth, NOTHING.
Once or twice a month, I re-boot with a limited user account,
connect to the network, update the machine, then disconnect and reboot.
This machine will NOT become a zombie. :)

---

### Post by aysiu on 2009-11-13
> **ibbill said:**
> 
Just want to log in to my computer and not be asked again for a password do you thing that's asking to much.:confused: It is asking too much on these forums.

As the official Ubuntu Forums, we support the default security model, and we will offer support if you want to make it even *more* secure but not if you want to make it *less* secure.

If you are clever enough to figure out how to get no more password prompting, then you are.

If you aren't, then it's probably for the best you stick with the defaults, for security reasons.

More details here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

